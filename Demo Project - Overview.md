# Demo Project - Overview

To see how Docker integrates the various steps of software development and deployment, continuous delivery and continuous integration    

In the software development workflow, we have the classical steps of development and continuous delivery and continuous integration, 
and then eventually, the software gets deployed on some type of environment, such as a test environment or a development environment. 

Here, we'll be looking at an overview of the workflow and look at then specific parts of the workflow and how Docker plays a role in all these steps.

![image](https://user-images.githubusercontent.com/107522496/202139418-b246e42d-4508-42b7-9885-b801a1147c53.png)

---

A simple scenario is where we are trying to develop a JavaScript  application which uses a Mongo Database. Instead of installing the Mongo Database,
we download a docker container from the docker hub. We then connect the JavaScript application to the Mongo DB and start development.

Once the first version is done locally, let's say we want to test it or deploy it in a development environment where someone else from the team 
is going to run and test it. 

To do this, let's say we then commit the application to Git or another version control system. This will trigger a continuous integration 
using a Jenkins build or whatever we have decided to configure. Jenkins' build will produce artifacts from your application

So first you will build your JavaScript application and then create a docker image out of that JavaScript artifact.































