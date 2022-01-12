- we'll talk a little bit about build performance
- everyitme you change a file inside of docker, Dockerfile which is inside of hte project is changed 

- say you change the port of your node js app to 5000
- well when you run docker build again, it goes through the Dockerfile line by line

- this didn't change, this didn't change, etc... 

- so in our docker file, our first change is

COPY --chown=node:node

- when there are no changes, docker uses the cached layers from before 
so once they notice a change, they start at that line

- in our example, right below COPY is RUN npm ci which takes a lot of time and bandwidth
- wouldn't it be nice to RUN npm install and then do COPY?

- layers: if you think of things in a  proper order, we can use the fact that docker build caches commands in the docker file to our advantage

- now everytime we change our dockerfile, i'tll keep a cached build up to the 

- so if we change package-lock.json or package.json, then it'll rerun npm ci but not the commands before because they'll be cached

- just a reminder, chown allows you to take ownership of the files in a directory. TO user node, give group node

- the idea of docker is building layers on top of layers on top of layers... etc

#### what happens if there's a security patch after you have ci'd your container
- well because you already ci'd, you can't update your security patch through your current dockerfile. However you can get a stale cache form that particular persepctive.
- only an affect in development
