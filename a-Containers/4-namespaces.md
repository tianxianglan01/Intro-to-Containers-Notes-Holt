- so if we have 2 chrooted envs next to each toher, we can still see each others processes
- ps: linux CL command to see all processes
- so company a (chrooted env 1) could kill company b's chrooted env 2 cause they can see each other's processes
- namespaces are the facets of linux where we can limit each jailed processes
- "hey you can only see your own process, your own process id, networking layer, and you can't mess with anyone else"

tail -f secret.txt

- starts a long running process, if anything is adde dto this, it would show that
- tail prints out the bottom 10 lines from a txt file
- '-f' 

#### Example of a shell 2 container 1 killing a process started by shell 1 container 1

docker exec -it docker-host bash 
- opens another shell in the same container

ps aux

- list all processes and their status and resource usage
- a = show processes for all users
- u = display the process's user/owner
- x = show processes not attached to a terminal

#### use a command call unshare
- create a better root

apt-get update
- updates your list of packages you can download

apt-get install debootstrap -y

- instead of having to copy all tools and looking at their libs one by one, use debootstrap that's going to set up a new, valid, change env

debootstrap --variant=minbase bionic /better-root

- download minimal amount of tools you'll
- can tell what kind of ubuntu you want to download
- get minimum set of filesystem to run a debian based unbuntu
- use this tool to bootstrap a new environment which you can chroot into

- 'exit' command takes you to the previous directory 

#### do unshare
- unshare the network, unshare the filesystem, unshare the utf
- after '--map-root-user', we tell the unshared environment to run 
unshare --mount --uts --ipc --net --pid --fork --user --map-root-user chroot /better-root bash
- in your chrooted environment, run 
mount -t proc none /proc

mount -t sysfs none /sys

mount -t tmpfs none /tmp

ps aux 

- then we can see from the host we can see inside of the child but form the child we cannot see outside of the host 
- from ps aux, we can see unshare, we can see bash 

- cause we unshared hte network, if we wanted it to connect to the network, we would have to do some stuff inside of the container

- changerooting is like unsharing a file system
- namespace is about sharing capabilities from these particular processes or controlling the capabilities that flow into these processes

### THIS IS AN ACADEMIC EXAMPLE OF A CONTAINER, NOT USEFUL WHEN DOCKER DOES IT ALL FOR YOU
