#### Make own node alpine image
- get the 80 mb down even further to 50 mb
- in our alpine-linux docker file, change 

FROM node:12-alpine

- to

FROM alpine:3.10

- and then add apk (alpine package manager), --update means get latest version 

RUN apk add --update nodejs npm

- (at this point we got rid of everything in our dockerfile except the above 2 lines)
- by default alpine doesn't have the node user installed, the node distribution does this for us

- to add user to linux, 

RUN addgroup -S node && adduser -S node -G node

- and

USER node

- btw our dockerfile doesn't work at this stage
