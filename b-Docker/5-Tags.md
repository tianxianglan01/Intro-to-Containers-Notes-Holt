#### Tags

docker run -it node
- is equivalent to
docker run -it node: latest

- the tag implicitly is using the *latest* tag where *:latest* is the tag
- when working with environments, you want it tied to a specific version
- think: "how can i capture this moment in time and not have it break in the future"
- you wnat to have the smallest container possible
- our example for debian, there are so many different versions of debian and so many tags that refer to that specifc version
- apparently 'stretch' is good for updating security patches in your container

#### How to pick which debian version
- for something like a node container, find latest lts for linux i'm on and latest lts for node/go/whatever and tie it to that
- if i'm messing around, just use latest 
