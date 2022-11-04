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

 















