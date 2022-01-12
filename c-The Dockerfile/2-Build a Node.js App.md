- index.js creates a server that console logs "omg hi" everytime a request is made, and responds to a user with OMG hi, and then starts server on server 3000
- let's make a docker file that containerizes this application and runs the server for us
- just in case you forgot, when you run docker build ., docker knows to look for the file titled: 'Dockerfile'
- if you create a container with the same tag as a previous container, the new container with its tag will overwrite the old one
- so every cache (container_id below every 'Step n/3') that you see while running docker build on a dockerfile is a 'valid container'

- so after starting our my-node-app, our container starts but we are unable to connect to it at localhost:3000
- this is because we didn't share the network with it (namespaces)
- this container is intentionally limited to the outside world. It's trying to reach out but the host os prevents the container from actually interacting wiht the outside

- also ctrl + c doesn't work here in our shell that's running our container
- this is because doesn't respond to these kind of proceeses
- our ctrl + c is sent to docker who passes it to node who doesn't care what ctrl c does

- best practices to stop this container, go inside your node app and add (this is not a node course)

process.on('SIGTERM') 
- otherwise run in another shell
docker ps
- and then run
docker kill "container_id"

- then if you try

docker run --init my-node-app
- --init proxies the process and proxies the process (ctrl + c) which then shuts the container down for you when you type in ctrl + c
- maybe not the best idea to use --init with node, install --init into your docker file, and then executing node form TINI, otherwise you'll forget, run some production server, etc

#### expose that port

docker run --init --rm --publish 3000:3000 my-node-app

- remember --rm is used to remove everything associated with the container (and not the image) to save disk space