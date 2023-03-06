# ARG
- ARG variables can only be used in Dockerfile
- To create variables in a Dockerfile
```
ARG <var_name> = <var_value>
```
```
ARG path = /home/repl
```
- Use $ sign to use the variable inside the instructions
```
COPY /local/project $path
```
- Setting ARG variables at build command  
![image](https://user-images.githubusercontent.com/117569148/223179964-8705d282-2322-49f8-bcc4-f7bcb8341471.png)

## Usecases for ARG instruction
![image](https://user-images.githubusercontent.com/117569148/223179328-da27206c-8553-4fb1-b087-0cbecafaf754.png)

# ENV
- ENV variables can be used in Dockerfile or at runtime
- To create variables in a Dockerfile
```
ENV <var_name> = <var_value>
```
```
ENV DB_USER = pipeline_user
```
- Use $ sign to use the variable inside the instructions
```
CMD pssql -u $DB_USER
```

## Usecases for ENV instruction
![image](https://user-images.githubusercontent.com/117569148/223181292-9c4f67f3-73cb-4273-bddc-99164a1a301b.png)

![image](https://user-images.githubusercontent.com/117569148/223181696-398e27b2-4b28-467e-a49b-a5019b08692a.png)

## Summary
![image](https://user-images.githubusercontent.com/117569148/223171195-dae8cd98-97b6-4d1e-be83-cc5b1ba9339a.png)
