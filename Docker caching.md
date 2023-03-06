## Why caching?
- Building docker image can take significant amount of time.
- The shell commands (RUN/COPY/Download) are executed everytime we build the Docker image.
- Docker images store a series of read-only layers that represent changes to the file system, rather than storing the instructions for creating the file system.
- This layer-based approach to image creation allows for efficient use of storage space and easy reuse of common layers.

## Docker layers
- All changes caused by a single instruction in a Dockerfile

## Docker image
- All layers together created during a build or all instructions in a Dockerfile

## Docker caching
- Consecutive builds are much faster because Docker re-uses layers that haven't changed.  
![image](https://user-images.githubusercontent.com/117569148/223154119-d781ad96-40f5-4d50-a171-e149956fd7a6.png)

## Understandind Docker caching

- Consider you built below Docker image
```
FROM ubuntu
RUN apt-get update
RUN apt-get install -y python3
```
- Now if we re-build the image when a new python3 version is available Docker will not update it as it will use cached version of that layer.
- Hence, Dockerwill never know whether a new version of python3 is available.  
![image](https://user-images.githubusercontent.com/117569148/223156149-0f6b82e6-9a59-4124-a3b9-b9cd5f38047a.png)

## Use Docker caching to increase efficiency

- We can increase efficiency by ordering the instructions in a Dockerfile from least changing to most changing.
- See below example for clarity.

![image](https://user-images.githubusercontent.com/117569148/223156587-8130d391-1b9b-4832-a3c1-8beb53e09ded.png)

![image](https://user-images.githubusercontent.com/117569148/223156677-24aa59a3-797f-4533-8f37-c1d02a3d8c1d.png)

