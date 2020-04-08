# education_dockers

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




## The docker file 
Name of the file Dockerfile 
--
FROM python:3.6.1-alpine
RUN pip install flask
CMD ["python","app.py"]
COPY app.py /app.py
--

## Bash comands 

### ps -ef

 inspect the running processes
 
 



