#### Problem
- the cat function is currently not in our my-new-root directory
- how do we add this in?

#### Answer
- in my-new-root type
ldd /bin/cat

- note: ldd means list dynamic dependencies. This means we want to see the shared libraries required by each program or shared library specified in the command line. 
- ergo these libraries are what allows us to run functions such as cat

- so we look for the libraries for the cat function that is in our original root's bin
- then we compare the libraries from our root's bin to the libraries in our 'my-new'root' directory and see if the dependencies in our 'original root' that correspond to our cat function are in both ls lib and ls64

- note: when you use ldd, you'll see the dependencies (libraries) for linux 32 and linux 64 bit's lib so compare the files for 32 and 64

- because your dependencies are already there, just do cp /bin/cat bin 
- and then switch into your 'jailed' root 

chroot . bash 

- inside your 'jailed' root, it's completely cut off from all basic command line functions 
- for dependencies, if it doesn't give you a fully qualified path, then you can ignore it

ie  linux-vdso.so.1 (0x00007ffe43b9f000)

vs

 libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6

 (don't copy the numbers afterwards btw such as)

  libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f056c4f0000)
