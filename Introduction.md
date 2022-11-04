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





























