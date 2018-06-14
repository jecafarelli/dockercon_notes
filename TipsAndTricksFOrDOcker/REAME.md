### Volumes
Dont mount a file, mount a folder. its has a parent directory. This is because the inode is mounted, but ides save to a new inode

### Cleanup
docker image prune
docker container prune
docker volume prune
docker network prune

### Building images
Build context: contains all the files that you want to send into the docker daemon
ignore artifacts that you dont need into the dockerignore file. Make sure your context is as small as possible.
install depencies first, then code

### Minimal images
use alpine
drop any build depecies for final images
create static binaries for your package to be ran in docker, you cna then use slim and make it real small
https://github.com/nexe/nexe

### Beware of latest
nothing special
not gurenteed to be new

### Use meaningful tags
you git revesion short or symantic versioning

### labels
Add labels to the docker images you build
docker build --labels `blah`
This will be useful in the meta

### startup dependably
do not require containers in start squence
dont crash container on depenency. is should wait
do it in the application code

### Shut down gracefully
attach docker to pid 1
use node to start your application, this will make sure to stop your application

### Healthchecks
inbuilt monitoring of conatienrs in kuberentes and swarm
fast feedback
essentially zero down time

### Swarm mode Healthchecks
HEALTHCHECK --interval=10s \
  CMD curl -f http:/localhost:1010

Need curl installed in container, which is a downside
elton stoman on docker healthchecks has a good blog on it

### Kuberentes Healthchecks
split into liveness and readiness nodes

readiness stops trafick
liveness is the health of the container

### Security
run your containers in read only. This way you cant modify the container and make nasty things happen

if there are certain files you want to write to, poke holes in the readonly by using mounted volumes like --tmpfs

### Dont run as root

Set a user in your docker files or use nobody

if you need root at startup, you can use `gosu` which you run as root at runtime, do your stuff then run gosu

### Docker in docker

normally a bad idea
* file system issues
* caching issues image storing
* jerome petazonni dont use dnd in ci

instead mount the docker socket
/var/run/docker.socket

Use dind image to run docker in docker

### Docker and guis
YOu can run gui apps in containers
jessie frazelle docker conatienrs on the desktop





```

```
