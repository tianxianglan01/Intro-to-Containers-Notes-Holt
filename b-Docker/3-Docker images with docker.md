- be explicit about the versions you're using: don't use "latest"
- alpine is a tiny linux: barebones neccesity for running web servers

docker run --interactive --tty alpine:3.10
- this drops you into an alpine ash shell inside of a container as the root user of that container
- run means you'll be executing a container
- entire idea of docker containers is that they'll be spun up and then destroyed. They are ephemeral. There's no idea of persistency 
- the second you exit out of a docker container, it's gone

docker run -it alpine:3.10 (example with alpine:3.10)

- ^ this puts you interactively (meaning you want to interact with the container) into the container vs

docker run alpine:3.10
- where docker spins up alpine and then exits out of it

docker run alpine:3.10 ls
- where docker spins up alpine, runs ls whereever it is in the container, and then exits out
- the order of your command is really important

docker command "flags" "name of container" "whatever you want to run"

docker run alpine:3.10 cat /etc/issue 
- etc issue is a system identification message so the above command outputs

"welcome to alpine linux 3.01... etc"

docker run ubuntu: bionic cat /etc/issue
- to clear up a lot of docker images run

docker image prune 
- (but you'll have to rebuild everything)

docker run -it --detach ubuntu:bionic
- --detach means to run the container in the background which means the container does not receive input or display output. You can reattach 

docker attach 'container_name' 'flags if so desired'

- to kill a container
docker kill 'container_id | container_name'

- to look at logs

docker logs my-alpine
- logs are kept around just in case you want to check them afterwards

docker --rm my-alpine
- erase everything related to the container, including logs
- you could also just do 

docker run -it --name my-alpine --rm alpine:3.10

- to run a my-alpine image and then remove it right afterwards
- --name means assinging a name to your container
- node:12-stretch has its own cmd, so if you run it directly, it drops into a REPL: ergo it has its own cmd
- cmd takes the last one it founds
- ergo if you have 