# Creating Basic Docker images

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

## Summary
![image](https://user-images.githubusercontent.com/117569148/222970167-794e03d5-6c9b-475b-b640-14835656ddd1.png)


# Managing files in image

## Copying files into an image
The COPY instruction copies files from our local machine into the image we're building
```
COPY <src-path-on-host> <dest-path-on-image>
```
e.g. To copy *pipeline.py* from host into image & rename it to *main_pipeline.py*
```
COPY /projects/pipeline_v3/pipeline.py /app/main_pipeline.py
```
If the destination path does not have a filename, the original filename is used.
```
COPY /projects/pipeline_v3/pipeline.py /app/
```

## Copying folders
Not specifying a filename in the src-path will copy all the folder contents
```
COPY <src-folder> <dest-folder>
```
e.g. To copy everything under *pipeline_v3* folder
```
COPY /projects/pipeline_v3/ /app/
```

## Copying files from Parent Directory
We cannot copy files from Parent Directory of our Current dtrectory(Where our Dockefile is present)
![image](https://user-images.githubusercontent.com/117569148/222971648-06c4023c-0852-4dd0-b8ae-a5f65ccf4a68.png)

## Downloading files
Instead of copying files from local directory, files are often downloaded in the image build

- Download a file
```
RUN curl <file-url> -o <destination-directory>
```

- Unzip the file
```
RUN unzip <destination-directory>/<file-name>.zip
```

- Remove the original file
```
RUN rm <copy-directory>/<file-name>.zip
```

## Downloading files efficiently
- Each instruction that downloads files adds to the total size of the image.
- Even if the files are later deleted.
- The soultion is to download, unpack & remove files in a single instruction.
```
RUN curl <file-url> -o <destination>/<file-name>.zip \
&& unzip <destination-directory>/<file-name>.zip -d <unzipped-directory> \
&& rm <destination-directory>/<file-name>.zip
```

## Summary
![image](https://user-images.githubusercontent.com/117569148/222972255-f6c22b0d-3da1-4362-a9e1-cae59755c25d.png)

# Choosing a start command for your Docker image

## Running a shell command at startup

The CMD instruction:
- Runs when the image is started.
- Does not increase the size of the image
- Does not add any time to the build
- If multiple CMD instruction exists, only the last one will have an effect

```
CMD <shell-command>
```

## Typical usage
 - Starting an application to run a workflow
```
CMD python3 my_pipeline.py
```
```
CMD postgres
```
<br />

- Starting a script that, in turn, starts multiple applications
```
CMD start.sh
```
```
CMD python3 start_pipeline.py
```

## When will it stop
- hello-world image -> After printing text
- database image -> When the database exits
 
A more general image needs a more general start command
- Ubuntu image -> When the shell is closed 

## Overriding the default start command
- Startring an image with a custom start command
```
docker run <image> <shell-command>
```

- Starting an image interactively with a custom start command
```
docker run -it <image> <shell-command>
```

## Summary
![image](https://user-images.githubusercontent.com/117569148/223144201-f27bb64a-3b6e-4d97-9b96-dfd0e6951653.png)
