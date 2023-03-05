# Creating your own Docker images

## Starting a Dockerfile
A Dockerfile always start from another image, specified using the FROM instruction
```
FROM postgres
FROM ubuntu
FROM hello-world
FROM my-custom-data-pipeline
```
## Building a Dockerfile
Building a Dockerfile creates an image
- To build at given path
```
docker build /location_to_Dockerfile
```

- To build in current directory
```
docker build . 
```

## Naming our image
In practice we almost always give our images a name using the *-t* flag
```
docker build -t first_image .
```

```
docker build -t first_image:v0 .
```

## Customizing images
We can RUN valid-shell-commands
```
FROM ubuntu
RUN apt-get update
RUN apt-get install -y python 3
```
Use the *-y* flag to avoid any prompts:  
![image](https://user-images.githubusercontent.com/117569148/222970082-3e9c02d0-f726-474a-8324-8e4d05861d43.png)

# Summary
![image](https://user-images.githubusercontent.com/117569148/222970167-794e03d5-6c9b-475b-b640-14835656ddd1.png)

