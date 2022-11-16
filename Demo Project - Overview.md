# Demo Project - Overview

To see how Docker integrates the various steps of software development and deployment, continuous delivery and continuous integration    

In the software development workflow, we have the classical steps of development and continuous delivery and continuous integration, 
and then eventually, the software gets deployed on some type of environment, such as a test environment or a development environment. 

Here, we'll be looking at an overview of the workflow and look at then specific parts of the workflow and how Docker plays a role in all these steps.

![image](https://user-images.githubusercontent.com/107522496/202139418-b246e42d-4508-42b7-9885-b801a1147c53.png)

---

![image](https://user-images.githubusercontent.com/107522496/202152307-b659af10-111f-492f-8370-78d175e52ac3.png)

A simple scenario is where we are trying to develop a JavaScript  application which uses a Mongo Database. Instead of installing the Mongo Database,
we download a docker container from the docker hub. We then connect the JavaScript application to the Mongo DB and start development.

Once the first version is done locally, let's say we want to test it or deploy it in a development environment where someone else from the team 
is going to run and test it. 

To do this, let's say we then commit the application to Git or another version control system. This will trigger a continuous integration 
using a Jenkins build or whatever we have decided to configure. Jenkins' build will produce artifacts from your application

So first you will build your JavaScript application and then create a docker image out of that JavaScript artifact.

Question: what happens to this Docker image once it gets created by the Jenkins build?
Answer: it gets pushed to a private docker repository.

> Note: A company may use a private docker repository as it does not want external people to be able to access to its docker images. This is why companies may choose to push the docker image to a private docker repository.

The next step could be configured on Jenkins' or some other scripts or tools. That Docker image has to be deployed on a development server that pulls the image from the private repository, the JAvaScript application and Mongo DB which the JavaScript application depends on from Docker Hub.

Now, you will have two containers, one, your custom container and a publicly available Mongo DB container running on dev server. They talk and communicate to each other after configuration and run as an aplication.

This means, if a tester now logs into the dev server, they will be able to test the application. 

This was an example of how Docker will work in a real-life process of making an application. 

---

# Developing with Containers - TO BE COMPLETED 

![image](https://user-images.githubusercontent.com/107522496/202154710-835ed485-3dde-4bc3-8ebd-ee2d9ca15ec6.png)

Here, we will look at how to use docker in a local development process. 

Demo of a JavaScript and node JS application to simulate a local development process and then will connect it to a docker container with a Mongo DB in it. 

---

Here, we will look at how to work with docker containers when developing applications.


---


 

























 




























