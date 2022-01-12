FROM node:12-stretch

USER node
# node container ships with user called 'node' which uses a usergroup called 'node'
# remember running things in root is bad. with the above line, the dockerfile is run with user as node
WORKDIR /home/node/code
# home directory of the node user
# the above command tells docker where to place the copied index.js

COPY --chown=node:node index.js index.js
# copy from source index.js to destination index.js
# format is --chown='user':'group'
# index.js that's copied over will be owned by USER node

CMD ["node", "index.js"]
