# Designing a Centralized Container Platform for a Multi-Cluster Enterprise Environment
## Keywords I like:
### Cluster Blueprint

Speaker: Till Schenk
Company: Robert Bosch [BOSCH]

## General Information
This talk was interesting in the sense that if we provide the ability for 'customers' to deploy containers and thats it. The issue is that Bosch is so large they are unable to go farther then the cluster itself.

Bosch ends the buck at the cluster itself, which is interesting but doesn't provide any support or help within the containers themselves.  They focus on the deployment and maintenance of the cluster.

Direct Quote: "We consider a cluster down if a manager is down, but if an application crashes we don't care."

I disagree with this statement in general, but it does draw a line in which SRE has an issue drawing.

Bosch is extremely vigilant about data protection and image security. They admit that even with their large team, image distribution and image maintenance is extremely difficult and is a bottleneck in their deployment.  They argue a registry (DTR) is a software distribution system.




Use Case Information:
- 62,500 R&D Associates
- 125 Engineering Locations
- Managing team consists ofr 7,750 Employees
    - IT Partner
    - IT Governance

### Why a new CI Service?
- Started with Docker 2016
- Growth started with developers
    + Investigation showed that most developers used Docker which drove adoption
- Technical Challenges:
    + DockerHub access -- Bosch doesn't allow easy web browsing for compliance
    + Tar file deployment of images to machines
    + Effort for deployment, operations and maintenance
- Requirements
    + Replace existing decentralied environments by clustered systems
    + Free up resouraces for the end user
    + Reduce the overall effort of container environment
    + Security/Compliance
- Workload must be executed as close as possible to the data
    + This kind of maps to the DS needs, clusters where the data exists and ease of deployability across the clusters

Things MassMutual SRE needs to work on:
- Ease of use for developers
    + Provide more access for self service developers to test...
        * RE


Stick with a standard cluster service.
- Deploy small, customer dedicate clusters as well as Large centralized worldwide for general consumption
    + Each customer cluster is owned by a single application owner. Don't care about the state of the cluster as base infrastructure is managed by IT, everything on top is meh.
- Multi-Cluster management in a single plane is a must.
- Optional, Approved and pre-installed services for different customer needs.
- NO SPECIAL CASES
- Provide Images that are certified for security
    + Rules come from Risk
    + Provide visibility when rules are not followed.
- Application Monitoring is deployed based on customer requests.


MassMutual vs Bosch
Both started with single container per instance and moved to orchestration
Both wanted and had a centralized repository