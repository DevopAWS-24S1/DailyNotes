#  Docker :
* Docker is contanerization platform .
* By using docker insted of running your application on VM(Servers), we will run the application inside the containers.


# Write a Dockerfile for Java image :

## Steps for creating VM with JAVA:
* Create a VM 
* Run the Java installation commands 

## Steps for creating Java image 
* Baseimage - Ubuntu 
* Run the Java installation commands 
        ```
         apt-get update -y 
         apt-get install openjdk-11-jdk -y 
        ```

# Dockerfile syntax:

```
INSTRUCTONS <ARGUMENTS>
INSTRUCTONS <ARGUMENTS>
;
;
;
;
;
;
INSTRUCTONS <ARGUMENTS>

```

# Dockerfile for Java image:
* Vi Dockerfile

```
FROM ubuntu:22.04
RUN apt-get update -y 
RUN apt-get install openjdk-11-jdk -y

```
* Using all commands in single RUN INSTRUCTOR
```
FROM ubuntu:22.04
RUN apt-get update -y \
  && apt-get install openjdk-11-jdk -y \
  && apt-get install maven

```

# Run shell way: 

```
RUN apt-get install openjdk-11-jdk -y

```

# RUN Executable way : 
* Executable command syntaxes are specified in the form:
```
FROM ubuntu:22.04
RUN apt-get update -y 
RUN apt-get install openjdk-11-jdk -y

```
```
<instruction> [“executable”, “parameter 1”, “parameter 2”, …]
```

* Examples of executable commands include:

```
RUN ["apt-get", "-y", "install", "openjdk-11-jdk"]
RUN ["yum", "-y", "update"]
CMD ["yum", "-y" "install" "httpd"]
COPY ["./index.html/var/www/index.html"]
```

# Docker images Cheatsheet:

```
Build an Image from a Dockerfile
docker build -t <image_name>

Build an Image from a Dockerfile without the cache
docker build -t <image_name> . –no-cache

List local images
docker images

Delete an Image
docker rmi <image_name>

Remove all unused images
docker image prune 
```

# Docker image build :

```
docker image build -t imagename .
docker build -t imagename .
docker build -t imagename pathtothefile

```

# Create a Container using myfirstjavaimage:

```
docker container run imagename
docker run imagename
docker run --name myfirstjavacontainer myfirstjavaimage
```
* list containers:

```
docker container ls     >> list running containers
docker container ls -a  >> list container running & terminated
```

# Multiple modes of running a Container:
* Use tomcat image from docker hub and create a container :
```
docker conatiner run tomcat 
```
* Attached Mode : In attached mode the container runs on the foreground
```
docker run imagename
```
* Detached mode : In detached modethe container runs on background 
```
docker run -d imagename
```
* Interactive Way : Interactive mode helps us in interacting with the container using termonals
```
docker run exec -it containername/containeris /bin/bash
```