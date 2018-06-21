# Docker EE: An Architecture & Operations Overview
## Kubernetes Integration
### Description
#### Today’s UCP with additional orchestrator
  * Multi-orchestrator configuration
  * Allocate nodes to each orchestrator
  * “Vanilla” CNCF kube, no wrapping
  * Opinionated stack with “batters included” networking and storage
### Features/Benefits
  * Support for Docker and Swarm APIs
  * Support for Kubernetes API
  * EE features including LDAP/AD, RBAC, Scanning, Signing Enforcement, Security Policies, etc.
### Deployment Options
  * Deploy via UI or CLI
  * Docker EE uses standard Kube API and CLI
  * Use existing Docker Compose files and choose at runtime to deploy on either Swarm or Kubernetes
    * Simple compose spec for developers, IT ops have multiple options for deployment
    * Migrate existing Docker apps to Kubernetes at your own pace

## Secure Supply Chain
### Image Signing (Docker Content Trust)
  * Sign image to “approve” passing of each stage
  * Policy to check for signatures before deployment
### Image Security Scanning
  * Integrated security scanning and vulnerability monitoring with customized alerts
  * Binary level scanning provides deep visibility into all components
  * Works both online and offline
    * Great for air gapped scenarios
  * Scans both Linux (x86_x64) and Windows
### Image Distribution
  * Image Promotions
    * Only images without vulnerabilities are promoted
  * Image Mirroring
    * Synchronize content between two different DTRs to assure the content is available in both places
  * Image Content Cache
    * Push specific layers locally to a specific team to facilitate faster docker pulls
    * A CDN for Docker images

## Coming to Docker EE
### Federated Application Management
#### Features
  * Federated application management plane
  * Multi-cluster management
  * Shared authentication backend (LDAP, AD)
  * Common automation & governance system
#### Benefits
  * Enabled faster hybrid cloud & multi-cloud adoption
  * Centralized supply chain
### Enhanced Kubernetes Support
  * Windows Server 2019 support
  * Kubernetes RBAC support
  * Container Storage Interface (CSI) support
  * Built-in volume types (AWS EBC, Azure File, Azure Disk)
  * Latest Kubernetes versions
  
