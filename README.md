# spring-pet-clinic application  dockerization:
The Spring PetClinic is an open source sample application developed to demonstrate the database-oriented capabilities of Spring Boot, Spring MVC, and the Spring Data Framework.


## install spring pet clinic application manually 
The application runs on java 11. The port exposed is 8080.
`sudo apt-get update
` sudo apt-get install openjdk-11-jdk -y`
`wget https://referenceapplicationskhaja.s3.us-west-2.amazonaws.com/spring-petclinic-2.4.2.jar`
`java -jar spring-petclinic-2.4.2.jar`
>  the manual installation was done now build the image by writing a` Docker file`

## Building a image 
If you want to build a image you want write a Docker file for the application 
In this Dockerfile we write the sequence of instructions and values 
example
          ``` <instruction> <value>```
The basic instructions are 
```
FROM => Helps in choosing the base image
RUN => Adds the execution/installation on the base image to build our application
LABEL => ADDS metadata
ENV => Set ENVIRONMENT variables
EXPOSE => PORTS to be exposed by application
ADD/COPY => Content to be added into the image from local or from urlss
USER => User with which container has to be started (if not specified root)
WORKDIR => Working Directory
ARG => Build time arguments
CMD => Command that will be called when container is created
ENTRYPOINT => Command that will be called when container is created
```
## Dockerfile
Docker file writing for spring pet clinic application

The above mentioned instructions are used in this  docker file
 
It looks like this 
```
FROM openjdk:11.0.13-jre-slim
MAINTAINER anil anilrockstar@gmail.com
ADD https://referenceapplicationskhaja.s3.us-west-2.amazonaws.com/spring-petclinic-2.4.2.jar /spring-petclinic.jar
EXPOSE 8080
CMD [ "java", "-jar", "/spring-petclinic.jar" ]
```
In this we are took `openjdk:11.0.13-jre-slim` for base image
 
Maintainer is  as your wish

add/copy `spring-pet-clinic.jar` file and giving the path for this inside of a container

And exposing port outside of the container  by using the `8080` port

After creation of the container `CMD` commands will be executed 
 
After writing the Docker file  execute the docker build command
  
##  Docker build

Build an image from a Dockerfile

The `docker build`  command builds Docker images from a Dockerfile and a “context”. [click here](https://docs.docker.com/engine/reference/commandline/build/) .more info
After writing the Docker file execute a command with the name tag `-t`

```
docker  build  -t <imagename: tag> .
docker build  -t anildockerpractise/spring-pet-clinic .
```

> **Note** here `.` mens current working directory where Dockerfile is available

