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

During demo, he setup a seperate utility to listen on another port that calls his application from within the container. He set a very small timeout to figure out if the response is slow or not and has manifest file hit this endpoint

This is a good idea, we can create a templated healthcheck for each language to do this.

#### Metrics

Metrics export utility
runs in background
exposes runtime metrics

In the demo, whe created a new entrypoiny that scraps .net metrics running in the container. he then exposes within the cluster, but not etenrally. Then he uses prometheus to scrape these metrics and collect run time information for his application.

