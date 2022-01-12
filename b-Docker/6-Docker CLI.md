- when your image is already downloaded, it's locally cached on your computer and is then fetched

docker run -it jturpin/hollywood hollywood
- lmao it's supposed to look like a hollywood hacker's console

docker inspect node:12-stretch
- outputs info about node:12-stretch 
- gives hash, tag, environmental variables

docker run -dit jturpin/hollywood hollywood

- -d of 'dit' means detached where it's running in the background

docker pause 'container_id'
- pause container and freezes process trees
docker ps
- shows that it's paused
docker unpause'container_id'
- to continue processes
- at the end, do 

docker kill 'container_id'

docker kill $(docker ps -q)
- to kill all processes

docker ps -q
- outputs the ids or the containers id which is then filled into the docker kill command

#### docker run vs docker exec
- docker run starts a new container while docker exec is oging to start something on an existing container
- so say you have a container with container_name fervent_kalam
- if you run
docker exec fervent_kalam pwd
- you're running pwd in the container, fervent_kalam
- also you can't run two docker containers of the same id at the same time

#### docker history
docker history node:12-stretch
- shows all changes and history in an image?
- where images are snapshots of containers, and images produce a container (you pull images from dockerhub)

docker info
- shows info about the host computer the container is on

docker run -dit mongo
- runs mongo in the backround

docker top 'container_id'
- same as ps aux, see all processes in container

docker ps --all
- this shows al containers active or none active

docker logs 'container_id'
- to get logs

docker rmi 'image'
- to remove an image

docker container prune
- remove all STOPPED containers

docker image prune
- remove all (not in use?) images

docker image list
- to see all images

docker restart 'container_id'
- restart container
- sometimes containers won't respond to restart signals sot hey might take some time to start up
- node# doesn't respond to restart signals

docker search 'image of interest'
- so if 'image of interest' was 'python', docker search would return lal images with a name containing 'python'
