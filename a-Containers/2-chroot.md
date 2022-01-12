#### What makes a container?
- chroot (changeroot)
- namespaces
- control groups

- there's no idea of a single container, just three things together that makes a container

#### If you have 2 people running porcesses on the same host's OS, how do you make sure they can't see each other's files?
- we solve this through chroot or Linux jails

cat /etc/issue
- to check which distribution of linux you're in
