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
