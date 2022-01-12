cop- the whoami flag tells you which user is running in the container

docker run --init --rm --publish 3000:3000 my-node-app whoami
- so if we were to comment out USER NODE and rebuild our image, the user would be 'root'

COPY vs ADD
- they are similar in that add can copy from file a to file b
- ADD has some extra functionality through local file system
- however if we're creating dockerfiles similar to what we're doing in this tutorial, which is the local file system, just use COPY
- main take away, is use COPY
- ADD can go on to the network and download off the network: ergo add from github this particular file
- ADD unzips any zip or tar you get

- so inside COPY --chown... etc..., where is index.js being copied? A: the root dir of the project
- 