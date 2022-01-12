- so we've been using publish 3000:3000 

docker run --init --rm --publish 3000:3000 my-node-app

- we could write in docker file EXPOSE 3000
- add EXPOSE 3000
- but we'd sitll have to run it with a flag
- first build

docker build -t my-node-app .

- then run without publish

docker run --init --rm detach my-node-app

- remember detach means running in the background
- uhh this didn't work so the correct ocmmand is

docker run --init --rm --detach -P my-node-app
- where -P means to expose all the ports I put it on
- check with docker ps
- with EXPOSE and -p, going into the container is 3000, but coming out of hte container is 32768 (arbitrary ip decided by docker)
- EXPOSE isn't often used

--publish flag
- "i have this port iternally and this port externally" and i want to connect them together