- platform for packaging shipping running application in container
- automates the development of applications within the lightweight containers
- enables applications to run consistently on different computing environment
- core software that manages these containers are called docker engines


### Docker image 
- docker image is the static read only template to create docker container
- it contains application codes with its libraries and dependencies
- they cannot be changed or modified once created i.e. they are immutable
- only solution to that is creating a new image by updating the docker file and rebuilding the image
- we use docker image to create docker container
### Docker container
-  running instance of a docker image
- we can create one or many container from the same docker image 
- we can make changes and interact with docker container example: changing the file system insider docker container
- to create a docker container from a docker image we can use docker run command
- ` docker run python ` 