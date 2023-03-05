# Basic Docker commands

- To check version of docker
```
docker --version
```
<br />  

- To access help for docker commands
```
docker --help
```
<br />  

- This command builds a Docker image from a Dockerfile
```
docker build <Dockerfile-name> <file-path>
```
<br />  

- This command pulls a Docker image from a remote registry
```
docker pull <image-name>
```
<br />  

- This command pushes a Docker image to a remote registry, such as Docker Hub
```
docker push <image-name>
```
<br />  

- This command lists all Docker images that are stored on your local machine
```
docker images
```
```
docker image ls
```
<br />  

- This command is used to run a Docker container from an image
```
docker run <image-name>
```
<br />  

- To start an interactive container
```
docker run -it <image-name>
```
<br />  

- To start a container in background or detached mode
```
docker run -d <image-name>
```
<br />  

- This command lists all running Docker containers
```
docker ps
```
![image](https://user-images.githubusercontent.com/117569148/222965330-e10c8def-b6bc-4ac8-a61f-3194947762d6.png)
<br />  

- To stop a container
```
docker stop <container-id>
```
<br />  

- To remove or delete a container
```
docker rm <container-id>
```
![image](https://user-images.githubusercontent.com/117569148/222965915-a7cdacad-6ab8-4856-b9ac-2f67477a1834.png)
<br />  




