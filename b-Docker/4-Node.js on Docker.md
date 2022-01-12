- can be assigned to java, go, ruby etc
- if you don't specify a version: docker will run latest
- tie node to debian stretch
- when we're using docker (in this example), we care about what version of node and what version of linux we're using

docker run -it node:12-stretch
- where 12 is the version and stretch is a specific version of debian
- debian is a version of linux
- 'stretch' is just a name that represents the latest version of debian
- after we run the above command, we get dropped into a repl (read evaluate print loop)
- we were dropped into the node REPL inside of a Debian Stretch Linux

- if you want to be dropped into the linux part of the container, you can add bash to line 6's command
- and from bash you can run things like

node -v

- just running
docker run -it node cat /etc/issue
- is useful for knowing which version of linux you're using
- use the linux distro you're most comfortable with