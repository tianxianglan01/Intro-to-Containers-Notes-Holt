#### control groups
- google would be running multiple different processes right next to each other. If someone at google maps were to run away process that could possibly kill the google docs process
- so they wanted to limit resources, one core, 10% of cpu, etc. we're looking at cpu and memory
- control groups are: 

- we can do chrooted unshared environments and we can assign control groups to them where you can execute code but you can't screw anyone else up, the only person you can screw up is yourself
- real life ex: we're running a hosting service, bob and alice running servers within hosting environment, we don't want eve to connect to the env and start messing with peoples' process
- physical resources: how much cpu, how much ram
- htop is a view to see physical resouces used

#### create a new cgroup
- 
#### note: cat allows us to write to a file or print out the contents of a file. 
- So cat 'ex_txt.txt' would print out the contents of 'ex_txt.txt'. 
- you can also read the multiple files such as cat ex_txt1.txt ex_txt2.txt
- you can also write to a file with

cat > readme.txt
Example Text 1
Example Text 2
'ctrl + d' to exit out of command

- basically there are many different functions for catupdat