# Docker for dummies(/junior devs) - from the horse's mouth

Based on the Docker documentation, with emphasis on points I have found important so far for clarification purposes or as a reminder to pay extra attention. May contain inaccuracies!  
  
  
Docker is NOT linux! many commands behave the same way, but there are often differences. It is wrong to expect it to act as though it is linux.  

Dockerfiles:

a receipe for the operation of the docker, including the starting point, building process, the running process, etc.  
Dockerfile instruction layers:  
`FROM` - origin docker  
`COPY` - files from the host  
`ENV` - set environment variable  
`ARG` - default value of argument  
`WORKDIR` - essentially like cd  
`RUN` - commands to run at build time (similar to make)  
`CMD` - commands to run at runtime! will not take place at build, but every single time the docker is ran.  

ARG vs ENV: arguments can be set at build time (when given as an argument, using the flag `--build-arg`) but are gone after this and their impact cannot be changed.  
Environment variables cannot be modified for building, but they can be changed later, at runtime using the `-e` flag (or `--env-file env.list` to import an environment variable file).  

Dockers do not change, every time a change is made, a new docker is made with the change included (such as a new file).  
Therefore, commands such as cd which do not change the state will not result in the creation of a new docker, and assuming such a change for the (separate) next command. However it possible to execute commands together , for example `cd dir && touch file`.  

# Authentication:  
docker login <http://website.com> : Login to a docker registry - such as artifactory. May require a username+password or an API key, especially corporate resources. May be a necessary step to retrieve registry specific dockers.  
When using a VPN on the host machine, it is possible that there would be a need to export http_proxy / http_proxy = <http://user:pwd@website.com> at least for some purposes, such as downloading a python module.

# Security and secrets:  
To add more  

# Networking:  
To add more  

# Container management:  
To add more  

# Important commands:
  build: build docker
  run: run docker
  ps: list containers (sort of equivalent of the linux command top)  
  
# Important flags:
  -t: tag (type/group)  
  --name: specify a name of the docker  
  --restart: specify a restart policy for the docker upon termination(?)  
    
  # Build time flags:
  --build-arg: add arguments at build time  
    
  # Runtime flags:
  -e: environment variable at runtime  
  --env-file: add environment variables file 
  -i: interactive shell  
  -p: maps a container port to a host port. e.g. 80:8080 maps port 80 in the host of the docker to port 8080 in the container. It is also possible to add a protocol, 80:8080/tcp would map tcp port 8080 of the docker. Alternatively instead of a host post number it is possible to put an actual IP address (through the host. Expand here some time?).  
  --rm: erase docker after termination. Particularly important when keeping in mind that a new docker is created for every change and the old one is preserved.  
 
