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


# Install docker on EC2 :
* Install docker by usg script :

```
1. download the script
#
#   $ curl -fsSL https://get.docker.com -o install-docker.sh
#
# 2. verify the script's content
#
#   $ cat install-docker.sh
#
# 3. run the script with --dry-run to verify the steps it executes
#
#   $ sh install-docker.sh --dry-run
#
# 4. run the script either as root, or using sudo to perform the installation.
#
#   $ sudo sh install-docker.sh
```

# Portfowarding:
* By using portforwarding we can access the application running in the container .

```
docker run -d -P imagename
docker run -d -p <nodeport>:<conatinerport> imagename
docker run -d -p 8005:8080 tomcat
```

# Document steps on VM :
* Take VM 
* Install java 
* Install tomcat 
* copy the code from local to the server(.wwar >> /var/lib/tomat8/webapps)
* restart the tomacat 
* publicip:8080

# docker steps :
* Dockerfile
    * baseimage : ubuntu 
    * install java 
    * install tomcat 
    * copy the war file to the image 
    * restart the tomcat when it is converted in to container
* convert the dockerfile to the image and run the container container


* Dockerfile
    * baseimage : tomcat 
    * copy the war file to the image 
    * restart the tomcat when it is converted in to container
* convert the dockerfile to the image and run the container container

# Dockerfile for sampledeployment :

```
FROM tomcat:9
LABEL Author="surya"
ADD https://tomcat.apache.org/tomcat-7.0-doc/appdev/sample/sample.war /usr/local/tomcat/webapps/
EXPOSE 8080
CMD ["catalina.sh", "run"] 

```

* Docker swarm - Orchestration 
* volumes in Docker 