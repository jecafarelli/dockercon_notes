# Automated Hardware Testing Using Docker for Space
## DART
Double Asteroid Redirection Test
  * Out of NASA Planetary Defense Coordination Office
  * Find, track, characterize near-Earth object that pose a hazard of impacting Earth
  * Plan and implement measures to deflect or disrupt an object

### Step 1: Build the spacecraft
  * DRACO imager
  * High Gain Antenna
  * Roll Out Solar Arrays
  * NEXT-C Ion Thruster
### Step 2: Hit the target
  1. Launch
    * Launch into any rideshare orbit, boost out of orbit using the Ion engine
  2. Cruise / Calibration
    * Flyby of PHA allows sensor calibration and control-gain tuning
  3. Target Detection / Course Acquisition
    * Weeks prior to impact, seeker detects primary
  4. Scene Classification
  5. Target Selection
  6. Deploy Selfie-Sat
  7. Homing Until Intercept
  8. Disrupt
### Step 3: Save the world (by validating the kinetic impact technique)

## Why Dockercon?
Space is hard! 
  * Extreme distances and timelines
  * Single shot
  * Vacuum
  * Infrequent Communications
  * Power
  * Radiation
  * Mass
  * Thermal
All factors drive:
  * Cost
  * Reliability
  * Low Memory (~16MB)
  * No virtual memory
  * 32 bit CPU (~100MHz)
  * Process
  * Testing. And more testing.

Software team is trying to solve:
  * Hardware scarcity
    * Testbeds cost > $300k
    * Configuration management is painful
    * Every developer/subsystem wants one
We want:
  * Hardware emulation
  * Evelop in software land
  * Test on real hardware
  * CD to other teams/real spacecraft

Enablers for DART
  * NASA Core Flight Executive
    * Hardware/OS Abstraction
    * Open source
  * Atlassian Bamboo 
    * CI/CD
  * Network architecture
    * SpaceWire
  * COSMOS
    * Ground System
    * Written in Ruby
  * Docker
    * Containers

## Dev Setup
### Container Setup
  * 4 Repos
    1. Flight Software
    2. Testbed Software
    3. COSMOS
    4. Docker_Env
  * 4 Containers
    1. Flight Software
    2. Testbed Software
    3. COSMOS
    4. VNC — allows inspection into COSMOS
  * Run-time voluming of source code, containers are stateless
    * Not focused at all on deployment
  * Provides outside dev environment with docker build capabilities
  * Keeps cross-compile toolchains standardized

### Network Setup
  * One instance comprises 4 containers (using docker-compose)
  * UDP SpaceWire abstraction between FSW and TBSW
  * TCP radio abstraction between Ground and TBSW
  * Xforwarding Ground to X11 Server to VNC

### VNC window
  * https://github.com/suchja/x11client
  * https://github.com/suchja/x11server
  * X11Server focuses on VNC and X setup
  * X11Client focuses on the application (COSMOS)
  * Brought up with compose, share auth cooking through voluming
  * Runs X virtual frame buffer with Openbox
  * Contains the X security issues to the containers (they think)

### Eclipse and Debugging
  * Eclipse Integration using Docker Tooling (Linux Tools project)
    * CDT Build within Docker container (including cross compiling)
    * Run/Debug FSW (x86 Linux) in Docker Container
    * Visually Debug FSW (LEON3 RTEMS) on Customer Flight Hardware
    * Run Multi-Container App and System Tests (Docker Compose)

## CI/CD for Space
### Software CI
  * Goal
    * Parallel software testing of our software sim
  * Limitation
    * We only had one server to prototype on
  * Execution
    * Bamboo with multiple agents on single server
    * Runs same setup as dev except for X11Server
    * Binaries/workbooks are passed through the chain, not containers
    * Re-tagged each docker image so there was no mangling with different branches
    * Docker-compose run with -p to provide unique keyed containers
### Hardware CI
  * Five complete sets of hardware (Testbeds)
  * Three flows, similar steps:
    * Binary cross-compiled inside container
    * Loaded to single board computer via GRMON
    * Serial output piped back via SSH/Screen
    * L3 InControl used as Ground System
### Lessons Learned
  * If your dev environment is the same as your CI environment, then its easier to debug
  * Permissions can be problematic
    * When editing volumes from outside, specify your user to run the container
  * Static IPs cause endless headaches
    * IP address spaces were not getting garbage collected, required daemon restart
    * Docker-networks can’t handle overlapping IPs/subnets
  * Bamboo assumes sandboxed code, Docker is global
    * Two layers of dependencies, jobs in a plan and branches in a plan
    * `Docker-compose -p` is magical
  * Out server can only handle 4 instances of our setup
    * Docker abstracts NEARLY* everything
    * Linux Message Queues appear abstracted but are globally held in the kernel
  * Bamboo latches the git commit once started
    * This is great for consistency, provides problems when tagging containers on commit hash “DETACHED HEAD”
  * Lock your Dockerfile FROM: version
    * Ubuntu:latest can change under the hood - lock a working version
  * Signal handling must go all the way down the rabbit hole
    * When using start scripts, signals must be propagated to the end application, particularly for graceful shutdown
  * Log Buffering - use “unbuffer” for better timestamps
    * Background processes output buffered causing timestamp bunching
  * Not everything HAS to get containerized
    * Docker bridge networks can be sniffer by host Wireshark
    * Permissions and display forwarding proved more pain than worth