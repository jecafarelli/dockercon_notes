### what is a container layer?
Read only layer
thin read/write layert

### Smaller images?
faster builds
smaller attack surface

### Reduce layers, how?
use a shared base image whenever possible
Limit data written to layers
chain run statements
prevent cache misses as much as possible

Size of the base image matters, use Alpine as much as possible, or smaller

Ubuntu - 81mb
Alpine - 4.1mb

Even better - Choose the offcial language. they are optimized

### when to use full image?
compliance
ease of development
more features

### flags to compress things
--cache-from ()
--compress (compress build context with gzip)
--no-cache (not sure why this works?)
--squash (squash new layers)

### whats build context?
when docker is called it sends the info to the daemon. this context is big, ginal image is big?????

### Docker cache
ADD and COPy with look at checksums for match

other then ADD and COPY only the sring will be used

Once the cache is broken, each layer will be build

### MAke it better

move just a requirements file over and install them first
put code copies at bottom
put run commands all together with `\` and `&&`
Switching users adds more

### Multistage vs seperate dockerfiles
both the same, multistage is cleaner

Look in slides at the end for links that show even more. READ IT!

### nodejs made better
use dockerignore, ignore the debuglog
cache the npm pacakges, add the package.json first, npm install, then verything
swapping base image, dropped 200mb going to Alpine
Suffled stuff around to use cache made it even Smaller

### Clean up
docker image prune -a
docker system prune -a

### Security
DOcker securit scanning
aqua CI assurance
Aqua micro scanner

### do garbage collector
spotify-gc
ECS and Kuebrentes has flags to modify

### Final lessons
smaller layers
choose image wisely
not all languages build the same
keep it simple, avoids extras
tools are here to help
