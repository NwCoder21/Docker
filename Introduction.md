# Introduction 

Some of the things which will be covered are: 

* What is Docker and what is a Ccontainer+
* The difference between Docker and a Virtual Machine
* How to install Docker
* Main Commands in Docker  
* Debugging a Container 
* How to develop a Container locally
* How to run mutiple containers or services with Docker Compose
* How to build a Docker image with Dcokerfile and how to push it onto a private Docker repository on AWS
* How to deploy containerized application 


---

# What is Docker?


* A container is a way to package applications with everything they need inside of the package, including the **dependencies** and the **configuration** necessary.
* The package is portable, just the way any other artifact is.
* That package can be easily shared and moved around between a development team or development and operations team


The reason why Containers make the development and deployment process efficent is due to them being portable, and everything being packaged into one isolated enviroment. 



* Containers make the development process more easier and efficient
* Containers solve some of the issues with the deployment processes of applications    
* Container Repository is a storage for containers 

---

# Where are Containers Stored? 

Containers reside in a Container Repository - a special type of storage for Containers. 

* Public repositories - DockerHub is a public repository where you can browse and search for an application container 
* Private repositories - some companies have their own private repositories where the host or where they store all their containers

> Note: `DockerHub` is name of the public repository for Docker

![image](https://user-images.githubusercontent.com/107522496/199768836-46fe2e83-8093-41bf-9ab6-c1fa75154aa4.png)

In this public repository,  it says there are more than 100,000 container images of different applications hosted or stored

---

For almost every application, there is an offical docker image. For example, for Ubuntu:

![image](https://user-images.githubusercontent.com/107522496/199769973-410f1d0c-0d39-4642-9df0-c8e987a5371f.png)

But will also find non-official container images that third party developers post up here.  

When starting out with using containers, the public repository is the place to find any application image.

---

# How Containers Have Improved the Development Process 

Before Docker, when creating applications, developers need to install most of the services needed onto their own machine's operating system directly. 

For example, if they were creating a Javascript application and needed PostgresSQL and Redis, each developer would need to install and configure these services on their local machine and run them in their local development enviroment.  

* However, the installtion process would be different for every developer, depending on the Operating System they were using.
* When you have have to take multiple steps to install all the required services, there is more of a chance of something going wrong 
* Also, the process of setting up the correct enviroment so application can run, can be very time consuming 
*  For example, if the application you will be using needs to have 10 services, that would mean that this needs to be done 10 times on each operating system environment.

## How Containers Aim to Solve These Issues?

* When using Containers, don't have to install the services directly onto the Operating System as container is its own **isolated operating system layer with Linux based image**. 
* This means everything is packaged into one isolated enviroment 
* So, in the case of the previous example, will have:
  * PostgresSQL
  * Configuration 
  * Start Script 

in one container. So, instead of developers having to download individual services, can now find and download onto their local machine, using one single command, a container which contains them all. 

* No matter what operating system developer is on, the command, the Docker command for starting the container will be the same. 
* For example, if have a Javascript application which uses 10 applications, would have to run just 10 docker commands, one for each container.
* Can have different versions of the same application running on your local environment without any conflict.

All this makes the process a lot more effiecent 

---

# How Containers Improve the Deployment Process 

Before containers existed, the development team would create artifacts with set of instructions on how to install and configure these artifacts on the server.

* For example, would have a jar file or something similar for your application. And in addition, you would have some kind of a database service or some other service also with a set of instructions of how to configure and set it up on the server.
* The development team would then pass on these artifacts to the Operations team and they would set up the enviroment to deploy those applications.

However, doing this comes with its issues, such as: 

![image](https://user-images.githubusercontent.com/107522496/199951168-b4199a05-468e-4df2-aabd-0c0c21276122.png)

* Have to configure and install everything directly on the operating system - this can cause conflicts with dependency version and multiple services running on the same host
* Because Operartions team will be reading the set of instructions provided by development team, there may be a misunderstanding or things may be left out - Ops team then will have to go back to dev team for clarification and this will delays **until application deployed on server **

Containers address this issue by:

![image](https://user-images.githubusercontent.com/107522496/199951948-d3010e8f-eaf5-432f-a72a-002bdbca3264.png)


* Dev team and Ops team work in one team package the whole configuration dependencies inside the application
* Because encapsulated in one single environment, won't have to configure any of this directly on the server
* Only need to run a Docker command which pulls that container image that is stored somewhere in the repository and then run it
* Just need to install and set up Docker runtime on server so that can run Containers - this just needs to be done once

---

# Technicaly, What is a Container?

![image](https://user-images.githubusercontent.com/107522496/199956644-b2231a95-c847-4296-87b8-4f70896964a8.png)

A container is:

* Made up of stacked images, one on top of another 
* At base of most Containers, have a Linux Base Image - due to it being small in size - being small is one advantage of using Containers
* On top of Base Image, we have an Application Image - 
* In between Base Image and Application Image, we have intermediate images which lead up to the actual application image that is going to run in the container.
* Configuration data layer is under the Application layer 
* 

 
---

# Docker Vs Virtual Machines


Firstly, Operating Systems have two layers, OS Kernel and Applications Layer. 

* Kernel communicates with the hardware such as CPU and memory 
* Applications run on the Kernel Layer 
* Docker and Virtual Machines are virtulization tools - so, what parts of the system do these virtulize?

* Docker virtulizes the applications layer - this is why, when we download a Docker Image, it contains the application layer of OS and uses the kernel of the host as it does not have its own kernel. 
* Virtual Machines virtulizes the applications layer as well as having its own kernel, i.e., virtulizes complete operating system. This means when you download a virtual machine image on your host, it doesn't use your host kernel, it boots up its own. 

This means:

* Size: Docker Images are smaller in size - sometimes MBs compared to VMs which can be GBs in size 
* Speed: docker Images are faster to start and run as VMs have to also boot up the Kernel 
* Compatability: can run any virtual machine image of any OS on any other operating system host - not with Docker 
*  This means, if we have a Windows OS with a Windows Kernel, if we wanted to run a Linux based Docker Image on this Windows Host, issue is Linux based Docker Image might not be compatible with Windows Kernel  - this is the case for versions below Windows 10

First check if host can run Docker natively (i.e., is the kernel compatible with the Docker Image). If can't can use Docker Toolbox which abstracts away the kernel to make it possible for your hosts to run different docker images.

--- 

# Common Docker Commands

The commands we will cover will help in pullimg images locally, start, configure, and debug containers. 

# Difference between Containers and Images

Container is the running enviroment for the Image.

![image](https://user-images.githubusercontent.com/107522496/200297731-570f086d-e7e7-454c-be10-6088de1b35e6.png)

In the aboe diagram on the right, the application image, which runs the application such as postgres, redis, mongo, needa a file system where can store log files or configuration files and needs cinviroment configuration such as enviroment variables.

All these enviroment things are provided by the container.

* Containers also have a port that is binded to them. This allows them to talk to the application which is running inside of a container.
* In containers, file system is virtual as containers have their own abstraction of an operating system, including file system and enviroment 

> Note: when downloading an image from Docker Hub, the different layers of the image will be downloaded. 


# `docker pull`

This command downloads an image from Docker HUb. For example,

```yaml
$ docker pull redis
```

![image](https://user-images.githubusercontent.com/107522496/200308264-90b50877-390e-4c3c-a24a-787bcd53c88b.png)


This will pull a 3D image out of the Docker Hub to your laptop.

---

# `docker images`

This command displays existing images on machine 

![image](https://user-images.githubusercontent.com/107522496/200302510-190000c3-a499-4f52-9f64-9079fd442470.png)

> Note: tag is version of the image 

Can also see the size of the image.

These are images, not containers. If wanted to run the redis image so that the application can connect to it, we will have to create a container of that redis image.

---

# `docker run {name of image}`

By using the `docker run` and followed by the name of the image, it will run the image in a container 

![image](https://user-images.githubusercontent.com/107522496/200303587-d40f82f0-a55d-43a6-80cc-314c6d6ffa3f.png)

> Note: Container is a running environment of an image.
---

# `docker ps`

This command displays the current list of running containers 

![image](https://user-images.githubusercontent.com/107522496/200303711-4167723e-cdf6-49a1-91c5-768a4e503b24.png)

Here, the redis container is running based on the redis image. This also displays the port it is running on. 

> Note: Use `Ctrl` + `c` to stop the container 

---

Normally, when using `docker run` followed by the name of the image, it will run the container in attached mode. To run it in detached mode use `docker run -d` followed by the name of the image. It will run the image in a container and when running the `docker ps`, only ouptut the ID of the container. 

![image](https://user-images.githubusercontent.com/107522496/200309585-2d8a6560-b157-46eb-ac65-b6ebc8488c43.png)

If you wanted to re-start a container, this can happen due to an error or a crash, will need the first part of the container ID.


# `docker stop`

This command stops a container. The below stops the container:

![image](https://user-images.githubusercontent.com/107522496/200311405-52d1c63d-58f8-4c11-b0d1-d35eaa3915e2.png)

### `docker start`

To start it again, can use the same ID to do so, usch as: 

This command is used to start a stopped container.

![image](https://user-images.githubusercontent.com/107522496/200311787-0f8c24ce-2eb3-4510-beb5-f3de05e46295.png)

---

# `docker ps -a`

This command shows a list of running and stopped containers - can then take the ID of a stopped container and restart it again using `docker start ` followed by the contianer's ID. 

![image](https://user-images.githubusercontent.com/107522496/200312913-11e57780-af26-4f3e-bc59-405b08107aca.png)

---

# `docker run`

This command pulls an image and runs it in one go. This is like a two-in-one command. 

Let's say we wanted to download the redis image and call it 4.0, 

![image](https://user-images.githubusercontent.com/107522496/200313663-b8dc2a8f-a01b-4789-9ca2-16487eb30aac.png)

The `docker run redis:4.0` command will pull the redi 4.0 image and start it in a container. It will look like: 

![image](https://user-images.githubusercontent.com/107522496/200313965-0e071b97-2bf4-466f-9155-63091dde79e2.png)

We can see that it has been downloaded and started straight away. If we then run the `docker ps` command, we will see that it is now running  

![image](https://user-images.githubusercontent.com/107522496/200314247-142bd26c-dc93-4dc0-ae66-721592bce94e.png)

---

# How to use any container that you just started?

If we look at th eoutput when running the `docker ps` command, we will see the port number. This tells us what port number the container is listening to for incoming requests. 

### How do we ensure that there are no conflicts when two or more containers are running onm the same port? 

![image](https://user-images.githubusercontent.com/107522496/200316448-40366163-25f0-4e68-8957-9d5b699eca1f.png)

* A container is a virtual enviroment running on the host machine. Can have multiple containers running on your local host machine. 
* A laptop has ony certain ports available. We need to create a so-called binding between a port between laptop/host and the container.  
* In the first example, the container is listening to port 5000 and you then bind your laptop's port 5000 to that container;s port 5000. 
* We will have a conflict when we open two 5000 ports on host and will get an error message.


However, we can use the same ports on containers as long as they are bound to two different ports on your host machine, such as:

![image](https://user-images.githubusercontent.com/107522496/200332897-33482ae6-8112-4190-8aab-18e12614981c.png)

We can then connect to the runnning container using the port number of the host, such as:

![image](https://user-images.githubusercontent.com/107522496/200334593-50526ef0-00bb-46d6-bbe2-27ceedba85c9.png)

and the host then will know how to forward the request to the container using the port binding
---

![image](https://user-images.githubusercontent.com/107522496/200334978-4e1a4423-1f5a-4eed-8365-25f7cd63bbb8.png)

Containers have their ports and they're running on the same one. However, we haven't made any binding between ourlaptop's ports and the container port.
This is why the containers are unreachable as they have not been bound to a port on the host. 

![image](https://user-images.githubusercontent.com/107522496/200335098-2daa4b15-f2e3-43b3-900e-1ee2aa9c8f42.png)

## Binding a container to a port on the host 

![image](https://user-images.githubusercontent.com/107522496/200610539-99d1d6b1-5ebf-45c6-8b98-fbf436eca49a.png)

In the above example, we have ran the redis container and can see it is using port 6379. however, we need to bind it to a port number on the laptop

To bind a container to a port on the host, we need to specify this at the point of running the image.

```yaml
$ docker run -p6000:6379 redis
```

Here, the number after the `-p` is the host machine's port number and the number after the `:` is the container's port number:

![image](https://user-images.githubusercontent.com/107522496/200611681-4d67cfa8-912b-4d44-8bf8-d7895f1bd680.png)

In the below screenshot, using `docker ps` command, we can now see that the binding 

![image](https://user-images.githubusercontent.com/107522496/200612052-9f3c559a-fa65-4564-8582-9d643d360c4f.png)

This means the laptp's 6000 port is bound to the container's 6379 port. 

---

# `-d` - Running a Container in Detached mode 

To run a container in detached mode, use the option `-d`. For example:

![image](https://user-images.githubusercontent.com/107522496/201109302-f5877d83-b944-4b4f-a3bf-46058afd57f9.png)

The reason why we may run a container in detached mode is so that we can use the terminal again

---
# Error When Trying to Access the Aame Port on the Laptop as the Another Container

The following is an error which occurs when trying to run another container which is trying to access the same port on the laptop as the first container. 

![image](https://user-images.githubusercontent.com/107522496/201157060-99f9c5cd-9bb2-40a6-a479-de740a511d9d.png)

To solve this, we can change the number of the laptop port it is trying to access, such as:

![image](https://user-images.githubusercontent.com/107522496/201112550-d0d09b9a-a44f-42d1-832d-5e486bbe76f4.png)

From the above, we can see that we now have two different versions of redis running, both of which are bound to different port on the laptop but both listening to requests on the same port. 

---

# Debugging Containers - `docker logs` & `docker exec -it`

If sommething goes wrong and want to troubleshoot to see logs or get inside of a container.

So, for example, if our application is not able to connect to redis, so, want to see the logs which the redis container is producing, you would run `docker logs` followed by container ID or the name of the container

```yaml
$ docker logs <container_ID or name_of_container>  
```

![image](https://user-images.githubusercontent.com/107522496/201124594-ceb14f26-8aa1-403e-8bc6-7e97239db8cc.png)

---

# Renaming Containers to Your Choice 

This is useful when do not want to reember the container ID, and instead find it easier to remember name of the containers. To do this

For example, if we wanted to create a new container using the redis 4.0 image


```yaml
$ sudo docker run -d -p3002:6379 --name myredis redis:4.0
```
Here;

* `run` will start a new container 
*  `-d` option is used to run the container in detached mode
* `-p` option opens and binda a port of the host machine to the port of the container 
* `redis:4.0` need to specify the image  

And then we can do the same for the other container: 

![image](https://user-images.githubusercontent.com/107522496/201148194-2ebc4951-9b0e-4cb4-b9c7-1b91ed2399ae.png)

This means, if we wanted to run a command on a particular container, for example, because it has some issues, we can do so by typing in its name too, such as 

![image](https://user-images.githubusercontent.com/107522496/201156056-28e66cce-9ae9-4226-a43c-1a4a5dcfe245.png)

`docker logs` will display the logs

---

Another Useful commmand when it comes to debugging is:

`docker exec`

This will us to get the terminal of a running container. For example, here we can see that we have two containers running. Let's say that we have an issue with one of them, in this case, let's say the redis5 container: 

![image](https://user-images.githubusercontent.com/107522496/201354662-8e1bb538-b49e-42c3-907c-925d28103648.png)

And we want to bring up a termina for this container and navigate th a directory, or check a log, or print out some enviromental variables, we will use:

```yaml
$ docker exec -it <specify_name/ID_of_container> /bin/bash
```
`-it` - stands for interactive terminal 

![image](https://user-images.githubusercontent.com/107522496/201356221-b25e938d-b99f-4786-b7e3-f356d3161afc.png)

We can see that the cursor has changed. We are now in the redis5 container as a root user. 




