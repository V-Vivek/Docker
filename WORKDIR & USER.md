# Changing users and working directory

## WORKDIR instruction
- The WORKDIR instruction is used in a Dockerfile to set the working directory for any RUN, CMD, COPY, ADD, etc instructions that follow it.
- It is helpful when the file path is too long & which makes it very difficult to read an instruction.
```
COPY /projects/pipeline_v3/ /home/my_user_with_a_long_name/work/projects/app/
```
- Using WORKDIR:
```
WORKDIR /home/my_user_with_a_long_name/work/projects/
COPY /projects/pipeline_v3/ app/
```
![image](https://user-images.githubusercontent.com/117569148/223165155-0097a934-d33d-4c37-88f7-8552e7e986a7.png)

## USER instruction
- The USER instruction is used in a Dockerfile to specify the user or user ID that should be used when running the Docker image.
- Note that the USER instruction does not create a new user in the Docker image. Instead, it specifies which user or UID should be used when running the subsequent instructions. 
- If you need to create a new user in the Docker image, you can use the RUN instruction to run commands that create the user.
- Using the USER instruction can improve security by running Docker containers with reduced privileges
- Root is a special user with all permissions.
- ***Best practice:*** 
  - Use root user to create users with specific permission for tasks
  - Stop using root user  
![image](https://user-images.githubusercontent.com/117569148/223166996-ffcd1506-c726-48b3-a8c4-8d7beb88cb71.png)

- The last USER instruction in a Dockerfile will also control the user inside container once container is built
![image](https://user-images.githubusercontent.com/117569148/223167649-95cdb51b-0073-401c-938e-4a84b9c439fd.png)
