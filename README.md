# ApartmentManager-CI

### Files inside

In here we have the Dockerfile for adding the nginx.conf file that we ahve created into the new image we are going to make.

We also have the docker-compose.yaml file which sets up all the services with the image they are going to use, their container name (as we only want to have one instance of this running), and then selecting the ports that the conatiner needs to run on.

Lastly we have the nginx.conf file we create to setup up using our created certificate for ssl encryption, to secure an encrypted link between the browser and the web server. In this we also have the proxy passing whichlooks out for a specific url point after the base url and then sends it to that requested url, which in our case will be the different services. 

### Instructions

In this repository when cloned down and then entered with a commond prompt to **ONLY** use `docker-compose up -d` to start all services at the start (but will currenlty have no jobs).**NEVER** use `docker-compose down` on it's own as currently it will stop all the containers and deleted their images, this will make you lose all of the Jenkins jobs.

If you are needing to restart a container I recommend using `docker-compose restart {service name}` or you could use:
```
docker-compose down {service name}
docker-compose up -d {service name}
```
