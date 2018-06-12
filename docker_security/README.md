## Hand-on Lab

### docker trusted content

https://github.com/dockersamples/dcus-2018-hol/blob/master/security/trust/README.md


It's not easy to find the digest of a particular image tag. This is because it is computed from the hash of the image contents and stored in the image manifest. The image manifest is then stored in the Registry. This is why we needed a docker pull by tag to find digests previously. It would also be desirable to have additional security guarantees such as image freshness.

Enter Docker Content Trust: a system currently in the Docker Engine that verifies the publisher of images without sacrificing usability. Docker Content Trust implements The Update Framework (TUF), an NSF-funded research project succeeding Thandy of the Tor project. TUF uses a key hierarchy to ensure recoverable key compromise and robust freshness guarantees.

You cannot pull unsigned images with Docker Content Trust enabled. Once Docker Content Trust is enabled you can only pull, run, or build with trusted images.

### Encrypted netowrk creation

https://github.com/dockersamples/dcus-2018-hol/blob/master/security/networking/README.md

`docker network create -d overlay --opt encrypted net2`


### Security Scanning with Docker Trusted Registry

https://github.com/dockersamples/dcus-2018-hol/blob/master/security/scanning/README.md

Should turn on scanning on push to DTR

### extras to lock down the linux OS running swarm
https://github.com/dockersamples/dcus-2018-hol/blob/master/security/capabilities/README.md
https://github.com/dockersamples/dcus-2018-hol/blob/master/security/cgroups/README.md
https://github.com/dockersamples/dcus-2018-hol/blob/master/security/seccomp/README.md
https://github.com/dockersamples/dcus-2018-hol/blob/master/security/userns/README.md
