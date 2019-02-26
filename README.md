# ApartmentManager-CI

### Files inside

In here we have the Dockerfile for adding the nginx.conf file that we ahve created into the new image we are going to make.

We also have the docker-compose.yaml file which sets up all the services with the image they are going to use, their container name (as we only want to have one instance of this running), and then selecting the ports that the conatiner needs to run on.

Lastly we have the nginx.conf file we create to setup up using our created certificate for ssl encryption, to secure an encrypted link between the browser and the web server. In this we also have the proxy passing whichlooks out for a specific url point after the base url and then sends it to that requested url, which in our case will be the different services. 

### Instructions
**To use any docker-compose commands you need a docker-compose.yaml file presetn in the directoty**

In this repository when cloned down and then entered with a commond prompt to **ONLY** use `docker-compose up -d` to start all services at the same time. You can use `docker-compose down` to stop and delete all of the services containers.

If you are needing to restart a specfic container(s) I recommend using `docker-compose restart {service name}` or you could use:
```
docker-compose down {service name}
docker-compose up -d {service name}
```

These can also be added onto and do multiple at eh same time with `docker-compose resart {service name} {service name} ...` for example

The name of the services can be found inside of the docker-compose.yaml.

You will be able to check the logs of each container by using `docker logs {container name}` which can also be found in the docker-compose.yaml file.
