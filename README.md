# Docker and Kubernetes

<p align="center">
  <img src="utils/doc.gif">
</p>

## **What is Docker?**

* Docker is a tool for running applications in an isolated Enviroment.
* Similar to Virtual Machine
* App run in same enviroment
* Standard for Software Deployment.

### ⬇️ Install a specific Images.

I am using Nginx but you can choose any there are multiple options like alpine,mongo and many more.

`docker run --name nginx -d nginx` or `docker run postgres:9.6` or `docker run nginx:latest`

-d : detach mode

### 🏃‍♂️ Run Docker Container

`docker container run --publish 80:80 --detach --name webhost nginx`

or 

Exposing One Container to Different Ports 🔌:

`docker container run -d -p 8080:80 -p 3000:80 nginx:latest`

### 📝 List all Docker Containers

`docker container ls -a` or `docker container ps -a`

### ✔️ Checks logs

`docker container logs webhost`

### ✔️ Check Inner Docker Working

`docker container top webhost`

### 🔨 Remove Docker Container

`docker container rm [Container_Id]` or `docker rm $(docker ps -aq)`

**Note:** You can specify multiple Container Id to remove multiple Container but you cannot remove a running container due to safety measures.

Container ID looks like : 08gf345hjkmn but you can specify only first three letters of container to remove or to do various operations.

`docker container rm 06e 9fd`

To remove the running container you can use: 

`docker container rm -f 06fe`


## Docker: Volumes

<p align="center">
  <img src="utils/vol.png">
</p>

* Allow Sharing of Data,Files and Folder
* Between host and container
* Between containers

`docker run --name website -v ${pwd}:/usr/share/nginx/html:ro -d -p 8080:80 nginx`

-v : volume

### Volume between Container

`docker run --name website-copy --volume-from website -d -p 8081:80 nginx`

Note: website-copy and website are name of Containers

### Dockerfile

```
FROM python:3.7-buster
COPY . /app
EXPOSE 5000
WORKDIR /app
RUN pip install -r requirements.txt
CMD ["uvicorn", "app:app", "--host", "0.0.0.0", "--port", "5000"]
```

Build your Docker Image Using:

`docker build --tag website:latest .`

This file is the copy of one of my ml project this is the way we create a dockerfile, dockerfile allow us to run all docker commands in one go.




 
















