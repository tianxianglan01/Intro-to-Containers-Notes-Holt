- so far we've build a nice little node js app on debian
- however debian is huge: a whole gb cause it's a whole os

- so let's work with Alpine Linux

#### Alpine Linux
- most barebones smallest distro of linux
- just tools to run app. Everything elese you have to put in yourself
- includes nothing you don't need
- is also secure because it has less 'stuff'

#### switch form stretch to alpine

cp -r more-complicated-nodes-app alpine-linux
- where -r means recursive copy of all files and dirs in source dir tree
- so we first copy our more-complicated-nodes-app into our alpine-linux dir
- and then we change in our dockerifle

FROM node:12-stretch

to 

FROM node:12-alpine

- and then we build

docker build my-node-app .

- and then we run 

docker run --init --rm --publish 3000:3000 my-node-app

#### distros of linux
- by default maybe use ubuntu or debian (as brian does)
- as for production, use alpine cause it's smaller and more secure
- alpine doesn't include bash, uses ash

