### Things to learn

Getting logs out of your container
getting configs into your container
getting depencies into your container
getting health out of your container
getting metrics out of your orchestrator

### Do all of this
without changing code
taking technology dependency
breaking dev workflow


### Logging

explicit log sink
log relay utility
runs in foreground

#### getting logs out of a container that logs to a file
IN order to solve this, you can come up a with an entrypoint that starts the process, then it `tails -f` on the file to get the logs

#### Config Docker

put a default configuration in the container
known file path
config injected by the platform

#### Depedencies

Check the depedencies during startup
runs once before startup
config aware and robust

Write the checker in the language of the application
change during the startup a check and stop the container if it fails after 3 retries.

This should be wrapped around things like databases, caches, and other required system for app operations

#### Health from application

healthcheck utility written in language of application
runs periodically
excercises app logic
