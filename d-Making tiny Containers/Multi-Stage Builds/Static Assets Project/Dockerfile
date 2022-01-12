# builds stage
# this selects the linux image that's based on node which is js node and 12-stretch which is a linux os
FROM node:12-stretch AS builder
# this cd's into 'app'
WORKDIR /app
# copy means to copy everything form our statics assets project local dir into destination app? 
COPY . .

# runtime stage
# install dependencies, && build final project
# this runs commands

RUN npm ci && npm run build
# could have a run underneath, if we have multiple things running and they accomplish the same thing, use &&

FROM nginx:1.17
# copy from previous 'one' and put it in the directory 'i told you to'
COPY --from=builder /app/build /usr/share/nginx/html
# don't put in cmd, cause it'll overwrite nginx, and we want nginx to do everything
