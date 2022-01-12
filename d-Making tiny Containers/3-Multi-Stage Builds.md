#### How can we make this smaller?
- what do we need just for the build, and not for produciton? A: NPM
- 

#### Multi-Stage builds
- build something here, copy it into a new container, and go from 
- can build multiple containers multiple times

- so the first container is going to be used just for building things. It's a 'kitchen-sink', we build stuff and then throw it away 
- hence why we use node:12-stretch

- the user is root, because the end user wil not be root (it doesn't matter)

- (see notes online)

- you can build containers in a row, like here's my dev, my build and put them all in one docker file and it'll export for you

- keep in mind of what you don't need in production 

- dev.Dockerfile (your dev docker file ). Below is how to build @ a different docker file 

docker build -t my-node-app -f dev.Dockerfile . 