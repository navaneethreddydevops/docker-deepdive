# Docker Basics

# Docker Installation

```
sudo yum install docker-ce
sudo systemctl start docker 
sudo systemctl enable docker
sudo docker run hello-world
sudo usermod -aG docker $USER
```

```
docker pull alpine:latest
docker image ls
docker image rm alpine:latest
```
# Docker Build

```
docker build -t ${imagename}:${version} .

```

# Push to Docker registery
```
docker tag myimage:1.0 myrepo/myimage:2.0
docker push myrepo/myimage:2.0
```


# Container:

```
docker container run --name web -p 5000:80 alpine:latest
docker container stop web
docker container kill web
docker container ls --all


```

# Delete all Running and Stopped Containers

```
docker container rm -f $(docker ps -aq)
```

# Docker container logs 

```
docker logs -f ${containername}
docker container logs --tail 100 web
```