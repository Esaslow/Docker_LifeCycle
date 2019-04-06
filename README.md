# Docker Lifecycle Managment Technical Exercise

### Introduction
Today we are going to explore Container Lifecycle Management with Docker.  We will work with the basics of containers and work through how to use them directly for different applications.  This assignment is graded on completion by you.  If you do not make it all the way to the end of the tutorial, feel free to coninue to work on the assignment at home!

### Part 0: Checking Docker installation  
To begin, we must check to make sure that docker was installed correctly on your machine.  To do this, we are going to run the following command through your command line:
- `docker --version`
If after this command, your terminal printed out a docker version number with a build number, you are good to go!  Otherwise, make sure you have [installed docker](https://docs.docker.com/docker-for-mac/install/)

### Part 1: Running your first container
We will start at the very begining in using a container - *Hello World!* 

To do this, we will run the following command in the terminal:
- `docker run hello-world`

The Docker run command will be your bread and butter -- you will use this command every time that you want to start any container.
After you run this command, you should see the following print out:

```
Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.
```
Lets begin to talk about what just happened (and cover what is going on inside of Docker).  By using the run command, we are instructing the computer to look for a specific *image* on your machine and run this image.  Unfortunatly, we do not have the image locally, and therefore, Docker looks to DockerHub to identify if there is already an image that could be used in this case.  Quickly, if finds that this is the case, and brings the image to your local machine. Its useful to have all of this information, but what other questions could we answer right now?

- Is the container still running?
- Is the container still on my local machine?

We will answer this second question first: `docker image ls`

This command will return all the docker images that are on your computer.  As you can see the hello-world image is still on your computer, but is it running?

To check to see if your container is still running we can use the command: `docker ps`

When we run this command, we see that nothing shows up which implies that the container that we created has *exited* successfully.  With that said, lets be robust and make sure that we know that the container is exited successfully.  

To do this, we will be running the same command with the `-a` flag which is a short for `--all`

- `docker ps -a` 

This wills how you all of the containers that you have run and their current status.  You will see that your `hello-world` successfully exited under the column *status*.

To finish part 1, we will be using a bash command to write out our results to a text file.  To do this, we will use the same command as above, but will add the output to a file called `test.txt`.

To complete this, you must run the list command for docker and pipe the results into the text file:
1. `echo Docker Lifecycle Tutorial Part 1 > test.txt`
2. `docker ps -a >> test.txt`
3. `printf '%20s\n' | tr ' ' - >> test.txt`  

The last command just adds a horizontal line to the bottom of your test file to seperate part 1 and part 2

To check that this worked we can take a peak at what is inside of the 'test.txt' file using the following command:

`cat test.txt`


### Part 2: Life Cycle Management


