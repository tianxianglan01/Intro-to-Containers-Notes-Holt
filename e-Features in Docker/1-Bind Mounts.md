- bind mounts and volumes are similar topics with different results
- idea is to have persistent storage between runs

- ie i have a container and it does bunch of stuff and outputs to a bind mount or volume, and if i run that container again, that state will still be there. wee want to maintain state between runs
- so far we've been focused on self container containers

- we don't want snowflakes:special server running on production server that's a bespoke artisinal server that has proper versions and everything goes correctly. if it goes away, your system goes down. If it goes down, you have to recreate all the specific sets to recreate it 'working'. snowflake servers are not good
- we don't want snowflakes, we want cattle

- the idea is that you have many cattle and one cow is the same as any other cow

- so not everything can fit into a container all the time like a sql database 
- can spin up and down sql databases but the core data needs to be preserved between runs
- so we get into MOUNTS

- we will talk about BIND mounts and VOLUME mounts

- Bind Mounts are Portals to your host computer. Anything that happens on the host container shows up 

- useful for dev containers: ie don't have go on my computer, but could develop a code proj with container. By using a bind mount, anytime I modify the code, I could modify it in the container 
- source="$pwd" means output where I am

docker run --mount type=bind, source="$pwd"/build,target=/usr/share/nginx/html -p 8080:80 nginx1.17

- we are reading from our computer to fill up the container
- notice in the above, there is no dockerfile involved in the run and no need for a build.
- we're getting the nginx container from dockerhub

#### would i build this in production vs building it in a container?
- still build it in a container because it's self contained
- you can place the container anywhere (azure, aws)
- can execute the container
- to use a bind mount, there's more steps/snowflaky 

- OS container can't tell difference between bind mount and normal files there

- so they hand you a container, and then you can bind mount it, and then run container