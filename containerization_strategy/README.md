# How To Build Your Containerization Strategy
Think about how to build a container platform for the non-enthusiasts
* Proof of Value
* Get some applications into production
  * let’s fail fast, fail often; learn from those initial attempts
  * helps to figure out a lot of things
  * containers are disruptive so there will be things that need to change in your organization
* Governance is required to get to production at scale
* Finally, you can get to innovation

## Proof of Value
### Build A Business Case
#### Why?
* Save money on capital expenditures
* Save money on operation expenditures
* Everything goes faster — agility
  * Get to market faster
  * Get new features before competitors, allows you to capture new markets and be a player
#### Application Migration Map
* Not all applications require the same level of effort to Dockerize
  * Clustered vs Standalone
  * Stateful vs Stateless
  * Go for the low hanging fruit first
* Develop a scorecard based on application criteria important to you
  * Focus on increased ROI
  * Example criteria:
    * Fast deployment times
    * Deployment frequency
    * Number of environments
    * Infrastructure cost
    * Security and Traceability
    * Application portability
    * Existing team culture
    * Technology stack compatibility
* It will take some investment, but you will see some immediate return on investment
  * Building up your skills
    * Motivates people because its a new technology
    * Increased retention because of motivation
  * You will start seeing operational savings because of automation, fewer required resources, etc.

## First App in Production
### Deployment methodology
* PoC
* An assessment
  * Measure the maturity levels of the teams
  * Choose the pilot application
  * Do some core training
  * Do a kickoff
* Launch into 4 work streams
  1. Governance
    * Non-technical
      * Support
      * Service
  2. Platform
    * Ops people
      * Deploying the cluster
      * Integration into infrastructure
  3. Pipeline
    * CI/CD systems
      * Secure all along the way
  4. Applications
    * Dockerizing the applications
    * Docker-compose files
    * Deploying using the pipeline, onto the platform as defined by the governance
* Then you go live
* When you need to onboard your next applications, you only need to run the top work stream over and over and over

## Production at Scale
Take a step back and think about your company’s organization and culture. This can affect what you’re going to build and how you’re going to build. If your company is highly centralized or distributed, you’ll think about what services to offer and how.
* If you’re centralized, you may want to do a simple, multi-tenant, one big cluster that all teams onboard onto
  * Containers as a service
* If you’re decentralized, you may want to provide the clusters and the know-how, but they will provide the infrastructure
  * Clusters as a service
  * Use Docker Trusted Registry to distribute images
* Some companies do a bit of both
### Containers allow you to distribute your software in new ways
* Centralized CI_CD, one main centralized CI_CD
* Distributed CI_CD, use DTR to distribute the CI_CD

### Services Classes
1. Sandbox
  * Good for training
  * Let people play around with docker
  * Low performance, doesn’t need to be highly available
2. Development
  * Application development
  * CI/CD Pipeline
  * Testing
  * Shared infrastructure
  * Multi-tenant
3. Production
  * Internal applications
  * High availability
  * High performance
  * Secure
  * Self-service
  * Business day support
4. Mission Critical
  * Mission critical applications
  * Highest availability 
  * Highest performance
  * Highest Security
  * White glove service to help them onboard 
  * Business critical support

## Marketing
This is a real concern for new technologies that you’re trying to introduce into your enterprise

* Make use of the sandbox environment for people to try out
* Docker Day
  * Have someone from docker come and share general information
  * Have early adopters in your company to share their experiences
* Champions Program
  * Enthusiasts in the company can become a champion and run technology workshops and start to evangelize 
* Swag
  * T-shirts, tickets, etc.

## Governance
So you’ve built and scaled out your container platform, you’ve done your internal marketing and you may have asked your CEO to make an announcement at the company meeting. What is the on-boarding experience going to be like for the teams coming on board?
* We will need to train them
* Build up support
* Define your operating model — what are your responsibilities and what are theirs?
* Knowledge Base

### Training
* Docker courses
* Culture Change
  * Pets vs Cattle
    * This can change the runbacks, operating model and automation of the infrastructure
* Operating model
  * Development model 
  * EOL / Volume Migration 
* Support
  Level 1. Self-service portal / Knowledge Base
  Level 2. Internal Support
  Level 3. Docker Support (a part of Docker Enterprise)

## Manage and Innovate


