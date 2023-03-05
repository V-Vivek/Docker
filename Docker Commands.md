# Basic Docker commands

- To check version of docker
```
docker --version
```

- To access help for docker commands
```
docker --help
```

- This command lists all Docker images that are stored on your local machine
```
docker images
```
```
docker image ls
```

- This command is used to run a Docker container from an image
```
docker run <image-name>
```

- To start an interactive container
```
docker run -it <image-name>
```

- To start a container in background or detached mode
```
docker run -d <image-name>
```

- This command lists all running Docker containers
```
docker ps
```
![image](https://user-images.githubusercontent.com/117569148/222965330-e10c8def-b6bc-4ac8-a61f-3194947762d6.png)

- To stop a container
```
docker stop <container-id>
```

- To remove or delete a container
```
docker rm <container-id>
```
![image](https://user-images.githubusercontent.com/117569148/222965915-a7cdacad-6ab8-4856-b9ac-2f67477a1834.png)




