- so far we've been focused on running existing containers
- so now we're going to focus on how to build containers with dockerfiles
- docker reads 'dockerfiles' to build containers for you
- create docker file > docker reads file > docker builds container
- we're gonna make a basic node docker file

#### Steps
- first, make a basic node container

FROM node:12-stretch
- go out to docker hub, find our node stretch, and this is the starting point. 
- we know node:12-stretch has node and npm installed on it, and other things that are created
- if we were to do a node project, we'd want to start out with something like this

CMD [ "node", "-e", "console.log(\"omg hi\")"]
- these are the actions the container will perform when it starts up
- the commands (after "node") are in an array
- -e means immediately execute this code (console.log("omg hi lol")) right after. ie
CMD [ "node", "-e", "console.log(\"omg hi lol\")"]
CMD [ "node", "-e", "console.log(\"rofl\")"]
- the second CMD overwrites the first CMD

docker build .
- "build ." means build right here
- after building, at least on my computer, it'll say "writing image sha256:*image id*"
- and then you can just write
docker run *container id* 
- to run your container
- CMD is not required for a dockerfile but it's useful to overwite the default previous "from"

docker build --tag my-node-app . 
- this builds the dockerfile without the container_id
- i think "--tag my-node-app ." names the dockerfile image you reated 'my-node-app'
- docker build, remember, defaults to latest
- you should version your containres

docker build --tag my-node-app:1 .

- suppose you first build the above image
- then change your commands in docker file to

FROM node:12-stretch

CMD [ "node", "-e", "console.log(\"rofl\")"]
- then run 
docker build --tag my-node-app:2 .