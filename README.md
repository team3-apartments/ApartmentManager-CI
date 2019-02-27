# ApartmentManager-CI

### Files in Repo

We have the Dockerfile for adding the nginx.conf file that we have created into the new docker image of nginx we are going to make.

We also have the docker-compose.yaml file which sets up all the services with the docker image they are going to use, their container name (as we only want to have one instance of this running), and selecting the ports that the conatiner needs to run on.

Lastly, we have the nginx.conf file that we created, to setup our certificate for ssl encryption, to secure an encrypted link between the browser and the web server. Also, the proxy passing which seeks for a specific url point after the base url. It is sent to the requested url, which in our case, will be the different services. 

# Instructions
**To use any docker-compose commands you need a docker-compose.yaml file present in the directoty**

When this repository is cloned down and entered with a commond prompt, **ONLY** use `docker-compose up -d` to start all services at the same time. You can use `docker-compose down` to stop and delete all of the services' containers.

If a specfic container needs to be restarted, I recommend using `docker-compose restart {service name}` or:
```
docker-compose down {service name}
docker-compose up -d {service name}
```

If multiple containers need to be restarted:
```
`docker-compose resart {service name} {service name} ...` 
```
For example

The name of the services can be found inside of the docker-compose.yaml.

Use `docker ps` to view all containers. If they are down, logs can be examined for each container by entering `docker logs {container name}` (found in the docker-compose.yaml file).

# Restarting Jenkins

If the Jenkins service and its container have been restarted, it will lose its docker-compose commands. **DOCKER-COMPOSE REQUIRED IN THE PIPELINE**

Docker-compose will have to be reinstalled by follwing the following commands in the VM(Virtual Machine), CMD(Command Line):
```
docker exec -it jenkins bash
sudo curl -L https://github.com/docker/compose/releases/download/1.21.2/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
exit
```
These commands allow the jenkins container to be entered using bash then installing docker-compose. The next line gives it the executable modifier, which allows commands to execute. Finally, 'exit' leaves the jenkins container. 
