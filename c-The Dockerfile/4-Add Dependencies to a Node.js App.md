- so what we worked on was a 'hello world' version of a container
- now we have to worry about dependencies (docker is known for being able to freeze/control dependencies)
- we ran

npm init -y
- init a package.json in your dir
npm install @hapi/hapi hapi-pino
- and we installed hapi/hapi and hapi-pino

- now let's create a dockerfile in our more-complicated-nodejs-app
- fill in your docker file and then run

docker build -t my-node-app .

docker run --init --rm --publish 3000:3000 my-node-app

- it's working but it's because we have npm on our computer
#### some problems
- if you're running in CI, then the node modules won't be there alread cause we don't commit our node modules
- node has the concept of node modules, (node sas), it'll build up for Mac OS, and if you copy it for ubuntu or debian, it won't work
#### to solve this
- we need to run npm install inside the container
- we first delete node_modules (mimicing the fact the container won't have access to our Windows node module in case they're mac)
- then we add a RUN to our Dockerfile

RUN npm ci

- in docker files with the RUN command, use RUN npm ci, and not RUN npm install 

- permisison errors are common in docker (i don't have this error on my computer) and this itme it's caused by 
- you can check which directories are owned by root with lsh -lsah. So when npm install tries to make changes to the root directory, this is a problem 

docker run --init --rm --publish 3000:3000 my-node-app ls -lsah

- btw, workdir is always root, you can't tell where to do workdir
- so instead we do

RUN mkdir /home/node/code

- anothe rpossible issue
- in our index.js, notice in hapi.server we bind to host: "0.0.0.0"
- if you bind to host: "localhost", this will not work. This causes a hard loopback that own't allow it to escape itself. this is why we use 0.0.0.0


