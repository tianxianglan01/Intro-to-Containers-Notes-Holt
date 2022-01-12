#### WHat is it?
- Docker Ignore is similar to .gitignore

docker run --init --rm -P my-node-app ls -lsah 

-p
- same as publish

- to have your git directory in your image is a security vulnerability because it contains your git history
- so we just create a file

.dockerignore

- and place 
.git/

node_modules/ (for node)

- every project should have .git in docker ignore