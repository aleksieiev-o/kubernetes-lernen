###### Create local unsecure registry, tag an image, push an image to local registry, pull an image from local registry
docker run --name registry -d --publish <hostname>:<repository-port> registry
docker run --name registry -d --publish 127.0.0.1:5000:5000 registry

docker tag <imageId or imageName> <hostname>:<repository-port>/<image>:<tag>
docker tag af340544ed62 localhost:5000/testimage:mytag

docker push <hostname>:<repository-port>/<image>:<tag>
docker push localhost:5000/testimage:mytag

docker pull <hostname>:<repository-port>/<image>:<tag>
docker pull localhost:5000/testimage:mytag

###### Commands
docker ps -a
docker build -t <imageName> .
docker rmi <imageId or imageName>
docker rm -f <containerId or containerName>

docker volume create <volumeName>
docker volume rm <volumeName>
docker volume inspect <volumeName>
docker run -it --volume <volumeName>:/src --workdir /src ubuntu

docker run -d --name=<containerName> <container>
docker exec -it <containerId or containerName> bash

docker system prune -a

###### View a full information by build process
docker build -t <imageName> --progress plain .


### Docker compose commands

docker compose up -d
docker compose down
docker compose ps
docker compose logs <containerName>
ocker compose exec <containerName> bash
