#### Difference between bind mounts and volumes
- bind mounts are files on your computer you're exposing to the computer 
- volume, something docker manages, for you, not exposed to host

- Docker says "you've created this new file system, i'll keep it. If you ask for it, Docker'll hand it to you.

= we're gonna use the file system as a db (bad idea)
- so anytime hits an endpoint, we read the file, see what number's in the file, and then give back to the user

- fs stands for filesystem 
- path is a path resolution kind of module for node
- write to ./data.txt file
- it's not even a web server, it's gonna run on container and exit containre

docker build --tag=incrementor .

docker run incrementor

- it says: 'file not found, writing 0 to file'
- because we haven't mounted it, it won't be able to find data.txt