- References: https://docs.docker.com/manuals/
- platform for packaging shipping running application in container
- automates the development of applications within the lightweight containers
- enables applications to run consistently on different computing environment
- core software that manages these containers are called docker engines
>[!Note] Why Docker? What is it replacing?
> because its lightweight and its replacing virtual machine
> VMs are virtualizing hardware whereas docker virtualizes operating system


![[Pasted image 20251218203022.png]]


### Docker image 
- docker image is the static read only template to create docker container
- it contains application codes with its libraries and dependencies
- they cannot be changed or modified once created i.e. they are immutable
- only solution to that is creating a new image by updating the docker file and rebuilding the image
- we use docker image to create docker container
### Docker container
-  running instance of a docker image
- NetworkChuck states it as fast lightweight microcomputer 
- we can create one or many container from the same docker image 
- we can make changes and interact with docker container example: changing the file system insider docker container
- to create a docker container from a docker image we can use docker run command
- ` docker run python ` 
---
### Managing docker images

- we can view docker images using the command `docker images`

![[Pasted image 20251208142023.png]]

- we can download an image using `docker pull`
- Example: `docker pull ngnix`
![[Pasted image 20251208141756.png]]
- we downloaded latest version of docker images titles "nginx"
- images have labels called tags
- tags are used to refer  variation of an image
- an image can havesame name but different tags to indicate different versions
- while specifying the tags we must use colon
- for example: ` docker pull nginx:latest` or `docker pull nginx:22.04`

- we can use `docker image` command with appropriate option to manage docker images on local system
![[Pasted image 20251208142415.png]]

### Docker image ls
- it is the command that can be used to list all images in the system
- we can use this command to view the image is properly downloaded or not 
- and we can view more information of docker images like TAG, IMAGE_ID etc
![[Pasted image 20251208142747.png]]

### Docker image rm
- we can remove the docker image by using `docker image rm ` with name (or image ID)
- for example `docker image rm nginx:latest`
![[Pasted image 20251208143809.png]]



### Running the First Container
-  `docker run` creates the running container of the image
-  this is where  commands from dockerfile ( as well as our own input at a runtime) are run
- Syntax:  `docker run [options] image_name [command] [arguments]`
- the options of closed container are not compulsory in running the container
- docker containers can be run with various options  depending  on how will we use the container

#### Simply Running the Container
- we can simply run docker by using `docker run -it image_name /bin/bash` 
- here  `-it` is for interactive and `/bin/bash` is for shell
- or we can run it like this without generating the shell
![[Pasted image 20251208211454.png]]

- we can view the running docker containers using `docker ps`
![[Pasted image 20251208211555.png]]
- we can use `docker ps -a ` to view all containers even stopped 
- we can now connect to bash shell of centos using `docker exec -it pranaya bash`
![[Pasted image 20251208211727.png]]
![[Pasted image 20251208211758.png]]

### Practice : To pull alpine and run

![[Pasted image 20251208212019.png]]
![[Pasted image 20251208212028.png]]
![[Pasted image 20251208212133.png]]


### Docker options
| Option | Explanation | Relevant Dockerfile Instruction | Example |
|--------|-------------|--------------------------------|---------|
| -d | Runs the container in detached mode (in the background). | N/A | `docker run -d helloworld` |
| -it | Runs the container interactively with a terminal. | N/A | `docker run -it helloworld` |
| -v | Mounts a host directory/file into the container (volume). | `VOLUME` | `docker run -v /host/os/directory:/container/directory helloworld` |
| -p | Maps a host port to a container port (port binding). | `EXPOSE` | `docker run -p 80:80 webserver` |
| --rm | Removes the container automatically after it finishes running. | N/A | `docker run --rm helloworld` |
| --name | Assigns a custom name to the container. | N/A | `docker run --name helloworld` |

### Further on the container
- List running containers
```bash
  sudo docker ps
  ```

- List all containers (running + stopped)
```bash
  sudo docker ps -a
 ```

- Start a container (if it’s stopped)
  ```bash
  sudo docker start <container_name_or_id>
    ```

- Stop a running container
 ```bash
 sudo docker stop <container_name_or_id>
  ```
- Start a stopped container and attach to it
 ```bash
 sudo docker start -ai <container_name_or_id>
  ```
- Get a shell inside a running container (bash)
 ```bash
 sudo docker exec -it <container_name_or_id> /bin/bash
 ```
- Get a shell inside a running container (sh)
 ```bash
  sudo docker exec -it <container_name_or_id> /bin/sh
  ```



---

### Docker Files
- formatted text file which essentially serves as an instruction manual for what container should do and ultimately assembly a docker image
- Syntax : `INSTRUCTION argument`
![[Pasted image 20251209203804.png]]


• A Dockerfile is used to define how a Docker image is built  
• The Dockerfile instructions are executed top to bottom  
• The FROM instruction specifies the base operating system for the image  
• Ubuntu 22.04 is used as the base operating system in the examples  
• Containers use minimal operating systems, so many common tools may not be installed by default  
• Commands run with RUN depend on the operating system specified in FROM  
• WORKDIR sets the working directory inside the image  
• RUN executes commands at build time and creates permanent image layers  
• Files created during build (e.g. helloworld.txt) exist in all containers created from the image


``` Bash
# Use Ubuntu 22.04 as the base operating system of the container
FROM ubuntu:22.04
# Set the working directory to the root of the container
WORKDIR / 
# Create helloworld.txt
RUN touch helloworld.txt
```
this ia an example of a docker file which will create a docker image from `ubuntu:22.04` ams sets its base directory to `/` and make a file `helloworld.txt`
#### Building our first docker container

• docker build is used to create an image from a Dockerfile  
• The -t flag allows you to name (tag) the image  
• The dot (.) tells Docker to look for the Dockerfile in the current directory  
• Building an image also downloads the base image if it is not already present  
• docker image ls lists all images on the system  
• A newly built image appears alongside its base image

![[Pasted image 20251216212937.png]]

![[Pasted image 20251216213129.png]]



#### leveling up the docker file

• Images are templates and do not run applications by themselves  
• Containers are created from images using docker run  
• Multiple containers can be created from the same image

• Dockerfiles can be extended to install software such as apache2  
• apt-get update is required before installing packages on Ubuntu  
• apache2 can be installed using apt-get install  
```

# THIS IS A COMMENT
FROM ubuntu:22.04

# Update the APT repository to ensure we get the latest version of apache2
RUN apt-get update -y 

# Install apache2
RUN apt-get install apache2 -y

# Tell the container to expose port 80 to allow us to connect to the web server
EXPOSE 80 

# Tell the container to run the apache2 service
CMD ["apache2ctl", "-D","FOREGROUND"]

```
- we can declare the name of dockerfile using `-f` option while building the container
-  `sudo docker build -f apache_inst -t webserver .`

![[Pasted image 20251218204402.png]]

- then we can run the container using `sudo docker run -d --name webserver-container -p 80:80 webserver`

![[Pasted image 20251218204559.png]]

then we can see it in any browser using `http://localhost`
![[Pasted image 20251218204726.png]]


• EXPOSE documents which network port the container will use  
• Containers do not use systemd or traditional service managers  
• CMD defines the default command that runs when the container starts  
• apache2 must run in the foreground inside a container

• docker run -d runs a container in detached mode  
• -p maps a container port to a host port  
• Accessing the host IP in a browser confirms the web server is running
###  Optimising our docker file
• Dockerfile optimisation is important for performance and maintainability  
• Unnecessary packages increase image size and build time  
• Cached files should be removed when they are no longer needed  
• Smaller base images reduce overall image size  
• Alpine is significantly smaller than Ubuntu  
• Each Dockerfile instruction creates a new image layer  
• More layers result in slower builds

• Multiple RUN instructions create multiple layers  
• Chaining commands in a single RUN instruction reduces layers  
• Fewer layers improve build speed and efficiency

### Docker Compose
- docker compose allows multiple container (or application ) to interact with each other when needed while running in isolation from one another
- Docker Compose is a tool for defining and running multi-container applications
- it is the key to unlocking a streamlined and efficient development and deployment experience.
- Compose works in all environments - production, staging, development, testing, as well as CI workflows. It also has commands for managing the whole lifecycle of your application:
		-  Start, stop, and rebuild services
		- View the status of running services
		- Stream the log output of running services
		- Run a one-off command on a service

Why compose? : https://docs.docker.com/compose/intro/features-uses/
How it works? : https://docs.docker.com/compose/intro/compose-application-model/

![[Pasted image 20251218212124.png]]

- Individual containers can only run single applications
- Many applications require additional services to function properly
- Modern dynamic websites often use services like databases and web servers
- Each application or service can be considered a “microservice”
- Running multiple containers individually is cumbersome and inefficient
- Docker Compose enables creating and managing multiple microservices as a single service
#### Docker Compose commands
![[Pasted image 20251218212525.png]]

#### Syntax for Docker Compose
| Instruction  | Explanation | Example |
|-------------|-------------|---------|
| version     | This is placed at the top of the file and is used to identify what version of Compose the docker-compose.yml is written for. | '3.3' |
| services    | This instruction marks the beginning of the containers to be managed. | services: |
| name (replace value) | This instruction is where you define the container and its configuration. "name" needs to be replaced with the actual name of the container you want to define, i.e. "webserver" or "database". | webserver |
| build       | This instruction defines the directory containing the Dockerfile for this container/service. (you will need to use this or an image). | ./webserver |
| ports       | This instruction publishes ports to the exposed ports (this depends on the image/Dockerfile). | '80:80' |
| volumes     | This instruction lists the directories that should be mounted into the container from the host operating system. | './home/cmnatic/webserver/:/var/www/html' |
| environment | This instruction is used to pass environment variables (not secure), i.e. passwords, usernames, timezone configurations, etc. | MYSQL_ROOT_PASSWORD=helloworld |
| image       | This instruction defines what image the container should be built with (you will need to use this or build). | mysql:latest |
| networks    | This instruction defines what networks the containers will be a part of. Containers can be part of multiple networks (i.e. a web server can only contact one database, but the database can contact multiple web servers). | ecommerce |


### Docker Socket
- docker mainly consist of  two programs: Docker Client and Docker  Server
- it is a client server model
- it communicates with each other to form the docker we use
- docker achieves this communication using something called a socket 
- it is essential features that  allows data to be communicated
- a socket can either be a network connection or a file
- it allows interprocess communication (IPC)
- in docker context, Docker server is just an API
>[!note] API, which stands for Application Programming Interface, is a set of rules and protocols for building software and applications. An API allows different software programs to communicate with each other. It defines methods of communication between various components, including the kinds of requests that can be made, how they're made, the data formats that should be used, and conventions to follow.

- Server uses API to listen for request whereas client used API to send request
- Example:  `docker run helloworld`. The Docker Client will request the Docker server to run a container using the image "helloworld"

![[Pasted image 20251222211952.png]]
- we can interact to docker  server using commands like `curl` or API developer tool like postman
>[!note]
> the host machine running docker can be configured to  process commands sent from another device
> this is a dangerous vulnerability if not correctly configured
> it means someone can remotely start or stop or access docker container 
 









- 45.137.70.111

[https://n8n.io/](https://n8n.io/ "https://n8n.io/")
