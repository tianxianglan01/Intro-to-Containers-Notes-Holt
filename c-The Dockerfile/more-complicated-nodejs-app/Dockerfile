FROM node:12-stretch

USER node
# create /home/node/code
RUN mkdir /home/node/code 
# because this is USER node, the Run runs as user node
# cd into /home/node/code
WORKDIR /home/node/code
# layering
# start by creating 2 copies

# in the below line, the '/' in front of the '.' is important to let docker build know to put the copy in the dir
COPY --chown=node:node package-lock.json package.json ./

# insert this RUN npm ci and delete the RUN npm ci below
RUN npm ci

COPY --chown=node:node . .
# . . means copy everything form here into everyhtin over there

# RUN npm ci (deleted)
# where npm ci adheres to what's inside the package-lock.json file in our dir

EXPOSE 3000

CMD ["node", "index.js"]