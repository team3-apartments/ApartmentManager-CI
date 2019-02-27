# ApartmentManager-CI

### Files inside

In here we have the Dockerfile for adding the nginx.conf file that we ahve created into the new image we are going to make.

We also have the docker-compose.yaml file which sets up all the services with the image they are going to use, their container name (as we only want to have one instance of this running), and then selecting the ports that the conatiner needs to run on.

Lastly we have the nginx.conf file we create to setup up using our created certificate for ssl encryption, to secure an encrypted link between the browser and the web server. In this we also have the proxy passing whichlooks out for a specific url point after the base url and then sends it to that requested url, which in our case will be the different services. 

# Instructions
**To use any docker-compose commands you need a docker-compose.yaml file presetn in the directoty**

In this repository when cloned down and then entered with a commond prompt to **ONLY** use `docker-compose up -d` to start all services at the same time. You can use `docker-compose down` to stop and delete all of the services containers.

If you are needing to restart a specfic container(s) I recommend using `docker-compose restart {service name}` or you could use:
```
docker-compose down {service name}
docker-compose up -d {service name}
```

These can also be added onto and do multiple at eh same time with 
`docker-compose resart {service name} {service name} ...` 
For example

The name of the services can be found inside of the docker-compose.yaml.

Use this `docker ps` to see all the containers and if they are down, then you will be able to check the logs of each container by using `docker logs {container name}` which can also be found in the docker-compose.yaml file.

#Restarting Jenkins

If you have restarted the Jenkins service and its container, then it will have lost it's docker-compopse commands which are requiredin the pipeline.

To fix you will have to follw these commands in the VM(Virtual Machine) CMD(Command Line)
```
docker exec -it jenkins bash
sudo curl -L https://github.com/docker/compose/releases/download/1.21.2/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
exit
```
These commands will let you enter the jenkins container using bash then instlling docker-compose, next line is giving it the executable modifier, which lets it able to execute commands, and lastly exit to leave the jenkins container. 
