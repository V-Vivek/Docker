# Port mapping

- To assign a custom port to a container, you can use the -p or --publish option when running the docker run command.
```
docker run -p [HOST_PORT]:[CONTAINER_PORT] <image-name>
```
- **HOST_PORT**: Specifies the port on the host to map to the container port.
- **CONTAINER_PORT**: Specifies the port on the container to map to the host port.
<br />

- For example, to run a container with port 8080 exposed on the host and mapped to port 80 in the container:
```
docker run -p 8080:80 myimage
```
- This will run the container from the myimage image, map port 8080 on the host to port 80 in the container and expose port 80 so that it can be accessed from outside the container.

## Map range of ports
- You can also use a range of ports to map multiple container ports to the same range of host ports. 
- For example, to map all ports from 8000 to 9000 on the host to the corresponding ports in the container, you can use the following command:
```
docker run -p 8000-9000:8000-9000 myimage
```
- This will map all ports from 8000 to 9000 on the host to the corresponding ports in the container, so that you can access the container's services using any of those ports.

## View ports
- The ```docker port``` command is used to display the public-facing port mappings of a container.
```
docker port <container-id>
```

