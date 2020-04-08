# Education dockers

## Running a container 
docker container run -t ubuntu top

You use the docker container run command to run a container with the Ubuntu image by using the top command. 
The -t flag allocates a pseudo-TTY, which you need for the top command to work correctly.

top is a Linux utility that prints the processes on a system and orders them by resource consumption. 
Notice that there is only a single process in this output: it is the top process itself. 
You don't see other processes from the host in this list because of the PID namespace isolation.

Containers use Linux namespaces to provide isolation of system resources from other containers or the host. 
The PID namespace provides isolation for process IDs. 
If you run top while inside the container, you will notice that it shows the processes within the PID namespace of the container, which is much different than what you can see if you ran top on the host.

Even though we are using the Ubuntu image, it is important to note that the container does not have its own kernel. It uses the kernel of the host and the Ubuntu image is used only to provide the file system and tools available on an Ubuntu system.

# Lab 1 - Run Your First Container

## Docker commands 

### docker container ls 

With this command we can see the running containers

### docker container exec -it b3ad2a23fab3 bash

Use that container ID to run bash inside that container by using the docker container exec command. 
Because you are using bash and want to interact with this container from your terminal, use the -it flag to run using interactive mode while allocating a psuedo-terminal

### docker container stop [container id]
Stop the container 

### docker system prune
Remove the stopped containers

# Lab 2 - Add CI/CD Value with docker images

## Create and build the Docker image

### docker image build -t python-hello-world .(including the point at the end)

Build the Docker image. Pass in the -t parameter to name your image python-hello-world

### docker image ls

Verify that your image shows in your image list

## Run the Docker image

### docker run -p 5001:5000 -d python-hello-world

Run the Docker image

The -p flag maps a port running inside the container to your host. In this case, you're mapping the Python app running on port 5000 inside the container to port 5001 on your host. Note that if port 5001 is already being used by another application on your host, you might need to replace 5001 with another value, such as 5002.

### docker container logs [container id]

Will show you the logs for that running container

## Push to a central registry

### docker login

### docker tag python-hello-world [dockerhub username]/python-hello-world

The Docker Hub naming convention is to tag your image with [dockerhub username]/[image name]. To do this, tag your previously created image python-hello-world to fit that format.

### docker push username_fromtag/python-hello-world

After you properly tag the image, use the docker push command to push your image to the Docker Hub registry

## Deploy a change 

### docker image build -t jzaccone/python-hello-world .

rebuild the image 

### docker push username_fromtag/python-hello-world

### docker image history python-hello-world

Prints the history for that image

# Lab 3 - Orchastrate Applications with Docker Swarm


## The docker file 

Name of the file Dockerfile 

FROM python:3.6.1-alpine

RUN pip install flask

CMD ["python","app.py"]

COPY app.py /app.py



## Bash comands 

### ps -ef

 inspect the running processes
 
 



