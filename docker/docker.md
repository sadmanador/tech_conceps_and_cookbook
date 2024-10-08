# Docker CLI commands

## Pulling a image

```bash
docker pull nginx
```

## pulling a private image

```bash
docker pull dockerhub.myprivateregistry.com/classify_spam:v1
```

## Pushing image

```bash
docker image push image_name
```

## Tagging an image before pushing

```bash
docker tag classify_spam:v1 dockerhub.myprivateregistry.com/classify_spam:v1
```

## Push the tagged image

```bash
docker image push dockerhub.myprivateregistry.com/classify_spam:v1
```

## Login

```bash
docker login dockerhub.myprivateregistry.com
```

## Saving docker image as tar file

```bash
docker save -o image.tar classify_spam:v1
```

## loading a tar file

```bash
docker load -i image.tar
```

## Running a image

```bash
docker run -d nginx:latest
```

## check the running containers

```bash
docker ps
```

## check the help command

```bash
docker ps --help
```

## Stopping a container

```bash
docker stop nginx:latest
# or the id/name of the container
```

## Starting a container

```bash
docker start nginx:latest #name/id
```

## Removing a container

```bash
docker rm #id/name
```

## Removing a running container with force

```bash
docker rm -f #id/name
```

## See all running and stopped containers

```bash
docker ps -a
```

## See all running and stopped containers in quite mode to see only the ids

```bash
docker ps -aq
```

## Remove all running and stopped containers in quite mode to see only the ids

```bash
docker rm -f $(docker ps -aq)
```

## Assign a port to local:image in detached mode(runs the container in the background)

```bash
docker run -d -p 8080:80 nginx:latest
```

## Assign a port to local:image in interactive mode

```bash
docker run -it -p 8080:80 nginx:latest
```

## Assign multiple ports to local:image

```bash
docker run -d -p 8080:80 -p 3000:80 nginx:latest
```

## Assign a default name to local:image

```bash
docker run -d --name NewName -p 8080:80  nginx:latest
```

## Formatting ps command

```bash
export FORMAT="ID\t{{.ID}}\nNAME\t{{.Names}}\nIMAGE\t{{.Image}}\nPORTS\t{{.Ports}}\nCOMMAND\t{{.Command}}\nCREATED\t{{.CreatedAt}}\nSTATUS\t{{.Status}}\n"

docker ps --format=$FORMAT
```

## Assigning Volumes with a readonly mode

```bash
docker run -d --name NewName -p 8080:80 -v $(pwd):/usr/share/nginx/html:ro  nginx:latest
```

## Assigning Volumes without a readonly mode

- then enter into the image and make a file in the volume directory.
- then a file is made into the volume of image, that file will be made on the outside of the container as well.
- -v with sync both of the volumes

```bash
docker run -d --name NewName -p 8080:80 -v $(pwd):/usr/share/nginx/html  nginx:latest
```

## Enter into a docker image

```bash
docker exec -it nginx:latest bash
# then to exit
exit
```

## Replicate a contents from a already running container

```bash
docker run -d --name NewName-copy -p 8081:80 -v nginx:latest
```

## Check all the pulled images

```bash
docker images
```

## Remove a image from the machine

```bash
docker rmi #name/id
```

## Remove all unused (only the untagged) image from the machine

```bash
docker image prune
```

## Remove all unused image with confirmation from the machine

```bash
docker image prune -f
```

## Remove all unused image, and tagged with confirmation from the machine

```bash
docker image prune -a
```

## Remove all unused, used, untagged and tagged images

```bash
docker rmi $(docker images -q)
```

## Build from the docker-compose.yml

```bash
docker-compose build
```

## Build from other file name

```bash
docker compose -f docker-new-file-name.yml build
```

## Deploy the build

```bash
docker-compose up -d
```

## Deploy the build from other file name

```bash
docker compose -f docker-new-file-name.yml up -d
```

## check the images from other file name

```bash
docker compose -f docker-new-file-name.yml ps
```

## check the service logs from other file name

```bash
docker compose -f docker-new-file-name.yml logs -f userService
```

## Restarting a service from other file name

```bash
docker compose -f docker-new-file-name.yml restart userService
```

## Dockerfile

* dockerfile help so make specific images base on other image

```bash
FROM nginx:latest
ADD . /usr/share/nginx/html
RUN apt-get install -y node
```

## Build an image from Dockerfile
```bash
docker build .
# or 
docker build /location/to/the/file
```

## Naming the image while building
```bash
docker build -t file_name .
# or
docker build -t file_name:v1 .
```

## building the docker image

```bash
docker build --tag website:latest .
```

## Run a container based on newly made image

```bash
docker run -d --name website -p 8080:80 website:latest
```

## Check the newly made image

```bash
docker images
```
