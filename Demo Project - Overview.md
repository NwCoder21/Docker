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

![image](https://user-images.githubusercontent.com/107522496/203026547-6c6c5b00-d59e-4ced-aaa0-7e99b69747c7.png)

Here, we will look at how to work with docker containers when developing applications.

First step will be is we going to develop a very simple UI backend application using JavaScript, very simple HTML structure and node JS in the backend. 

And in order to integrate all of this in the database, we are going to use a docker container of a MongoDB database and will allow working with the MongoDB much easier so we don't have to execute commands in the terminal.

We will deploy a Docker container of a Monga UI, which is called the Mongar Express, where we can see the database structure and all the updates that our application is making in the database.

**So, this development setup should give you an idea of how docker containers are actually used in the development process.**

---

![image](https://user-images.githubusercontent.com/107522496/203027439-4e705239-5eff-411a-bf98-707b35289970.png)

 ---
 
 ![image](https://user-images.githubusercontent.com/107522496/203028153-82dd64e5-5450-4530-8f6b-550c71424eb7.png)


Here, is some very simple JavaScript application. we have this index HTML with Javascript and using Node JS backend which serves the Index HTML file....

![image](https://user-images.githubusercontent.com/107522496/203028489-1b778757-cd21-4973-98bc-d91af9e6bcfd.png)

and listens on port 3000. SO, the server is running at the backend and the UI is at the frontend. 

---


So, if we make changes to the profile, such as:

![image](https://user-images.githubusercontent.com/107522496/203028771-388809e2-b1ac-4dbe-abc4-76ec52dccb1d.png)

the issue is that when we refresh the page, the changes are lost as there's no persistent component in this application.

To be able to save changes, we need to integrate the application with a database. This is how real-life applications work. 

Will demo how you can actually use the docker containers to make the development process easier by just pulling one of the databases and connecting it to the application.

So, for this demo, we will go with a MongoDB application and in addition to this MongoDB container, will also deploy a MongoDb UI, which will be in its own container, which is called Mongo Express where we can manage or see the database insights and updates from our application much easier.

---

![image](https://user-images.githubusercontent.com/107522496/203030178-81704900-9352-4cc1-be7e-da00082a12ab.png)

Go to Docker Hub and find the MongoDB Image. 

![image](https://user-images.githubusercontent.com/107522496/203031006-0c48e091-68ac-474d-b5a8-2729af9e0fdd.png)

First pull the MongoDB official image. doesn’t take as long here as it MongoDB Latest is already installed on this machine

> Mongo Express is what we will use for the UI.

---

![image](https://user-images.githubusercontent.com/107522496/203031190-2aa96df9-7e51-4c09-822f-7bd37e24b8c7.png)

Then pull the Mongo Express.

![image](https://user-images.githubusercontent.com/107522496/203031294-99f2c51f-bbe2-4357-82dd-1d59ea650d39.png)

As it is also already installed on this machine, won't take as long. 

---

![image](https://user-images.githubusercontent.com/107522496/203031451-f15c8852-a2d6-4152-ad40-e2a4499026f6.png)

Now if we check locally, we can see we now have them installed, MongoDb and Mongo Express.

---

Next step is to run both MongoDB and Mongo Express containers in order to make the MongoDB database available for application and also to connect the Mongo Express with the MongoDB container. 

Let's do the connection between those two (MongoDB and Mongo Express containers) first.

# Docker Network 

In order to do this, we need to understand another concept, Docker Network.

![image](https://user-images.githubusercontent.com/107522496/203033236-aa2ab7d5-e6a5-4df1-8cff-380f12421fa8.png)

Dockers creates its isolated Docker network in which the containers are running in. 

![image](https://user-images.githubusercontent.com/107522496/203033466-3a735b6f-94f3-44d5-b789-095301d7d2c5.png)

So, when we deploy two containers in the same  Docker network, in this case, MongoDB and Mongo Express, they can talk to each other using just the container name, without localhost port number etc, just the container name, as they are both in the same network.

![image](https://user-images.githubusercontent.com/107522496/203034050-e53a4792-4958-4a25-a480-ec730c9d8522.png)

And the applications that run outside of Docker like our Node JS, which just runs from node server, is going to connect to them from the outside/from the host using localhost and the port number.


![image](https://user-images.githubusercontent.com/107522496/203034890-4a43c828-dbc4-4248-9fb4-3495c78a1b3a.png)


So later when we package our application into its own Docker image, what we will have is, a Docker network a MongoDB container and a Mongo Express container. We will also have a Node Js application, which we wrote including the Index HTML and JavaScript for the frontend in its own Docker container and its going to connect to the MongoDB.

And the browser, which is running on the host but outside of the Docker network, will connect to our JavaScript application again using hostname and the port number. 
 
---

# `docker network` & `docker network create` Commands

Docker, by default, provides some networks.

![image](https://user-images.githubusercontent.com/107522496/203035133-8e9832fd-e6d7-428a-8404-2fba426b55e7.png)

Using the `docker network ls` command, we can see the auto generated Docker networks. Here, we have four of them with different names and the drivers.

---

What we will do is create our network for our MongoDB and Mongo Express containers and will call it Mongo Network. <br>

![image](https://user-images.githubusercontent.com/107522496/203040539-4a9917cb-4428-4ede-bb89-5e2cc2223bfa.png)

Now, our Docker network has been created using the `docker network create` command followed by the name we want to give to the network.

To make the MongoDB and Mongo Express containers run in this network, we need to provide this network option when we run the `docker run` command 

 ---
 
 Let's start with the MongoDB container. 
 
 
 
 
 
 

`docker run` is the command to use to start an container from an image. However we will also need to specify some more things in order to connect the container to the network:
* Will need to need to specify a port using `-p`. so, will need to open a port of MongoDB. The default port for MonogDB is 27017 so we'll use that one for both, host and container. 
* Will also run it in detached mode using `-d`

* Enviromental Variables of MongoDB. - in the official image description (where you download the image from on Docker Hub), you actually have a couple of documentation about how to use the image, which is very helpful to kind of understand what kind of configuration you can apply to it.

![image](https://user-images.githubusercontent.com/107522496/203048969-eb9ddabe-29dc-4bdb-96d0-9002771e8933.png)

Here you see some environmental variables. So basically, on start-up, you can define what the root username and the password will be. These will be important in order to connect the MongoDB to the Mongo Express. 

![image](https://user-images.githubusercontent.com/107522496/203049020-6cc14e7d-d0f2-4eb2-844c-187d08b465bb.png)

And you can also specify the INIT database. We're just going to provide the username and password because we can create the database from the Mongo Express UI later.


---

![image](https://user-images.githubusercontent.com/107522496/203050562-58c07456-173d-4969-b900-0a94bbf58496.png)

This shows us how to specify the environmental variables. One variable is USERNAME, which we have set to admin in the case above and another is PASSWORD, which we have set to password in the case above. This means the defualt username and password is overridden. 

`-e` stands for environmental variable

* Container name: we also need t0 specfiy a container name because we need this container name to connect to Mongo Express. In this case, we will name it `mongodb`
* Network: we also need to specify the network we created. In this case we created one called `mongo-network`.

So, the command will look like:

```yaml
$ docker run -p 27017:27017 -d -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=password --name mongo-db --net mongo-network 
```


In order to make this easier to read, will place this command on multiple lines. 


```yaml
$ docker run -d \
> -p 27017:27017 \
> -e MONGO_INITDB_ROOT_USERNAME=admin \
> -e MONGO_INITDB_ROOT_PASSWORD=password \ 
> --name mongo-db \ 
> --net mongo-network \
> mongo
```

`> mongo` - this is the name of the image. 


This should then start a container:

![image](https://user-images.githubusercontent.com/107522496/203267022-0f5044a5-e957-4924-8883-abaf90cf2780.png)

---

Now let's start Mongo Express. We want to connect Mongo Express to connect to the running MongoDB container on start-up.

![image](https://user-images.githubusercontent.com/107522496/203268240-d04680d3-961d-4716-89b8-da83052edc1d.png)

On the official Mongo Express Image page on Docker Hub, it shows us the enviromentel configuration options (yellow box) we can use and an example of how to run it (blue box).

![image](https://user-images.githubusercontent.com/107522496/203268699-404ad00b-a98d-4c3c-bf57-a6519af725db.png)

`ME_CONFIG_MONGODB_ADMINUSERNAME` and `ME_CONFIG_MONGODB_ADMINPASSWORD` 

We need the admin username and password of the MongoDB.  This is what we overwrote with `admin` and `password`. So we are going to use them because Mongo Express will need some username password to authenticate with the MongoDB.

The port, by default, is the correct one, so we don't need to change that.
 
 `ME_CONFIG_MONGODB_SERVER` - this is the MongoDB Server. This is the container name that Mongo Express will use to connect to Docker. Because they are running in the same network, this configuration and connection will work. If we did not specify the network, we could have specified the name of the containe, as in `ME_CONFIG_MONGODB_{NAME_OF_SERVER}` and it would not work. 
 
 We then create the dcoker run command for Mongo Express too...
 
 We can see the default Mongo Express runs on using the Docker Hub Documentation is 8081...
 
 ![image](https://user-images.githubusercontent.com/107522496/203275364-89c24804-969d-43e8-9594-31e20e5f1c0f.png)

  
 ```yaml
$ docker run -d \
> -p 8081:8081 \
> -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin \
> -e ME_CONFIG_MONGODB_ADMINPASSWORD=password \ 
> --name mongo-express \ 
> --net mongo-network \
> -e ME_CONFIG_MONGODB_SERVER=mongodb
> mongo-express
```
 
 `-e ME_CONFIG_MONGODB_SERVER=mongodb` the name we will put at the end is the name of the other container when we run `docker ps`

`> mongo-express` this is the name of the image. 

When we run this command, Mongo Express should be able to connect to the MongoDB container. 

![image](https://user-images.githubusercontent.com/107522496/203284593-701b8543-0c78-4676-b946-78df2e483e67.png)

From the above, we can see now it is connected. 

---

![image](https://user-images.githubusercontent.com/107522496/203285114-cca961bb-2907-4161-888a-f5382a501224.png)

Now let's check Mongo Express at port 8081. Go to a browswer on local machine, and type in `localhost:8081`

![image](https://user-images.githubusercontent.com/107522496/203285248-74b70dc8-6a4b-4ded-b943-82bda20e105e.png)

We should be able to see the Mongo Express.

![image](https://user-images.githubusercontent.com/107522496/203285696-451796cf-eb28-4185-ae96-4d8ce3fd72c1.png)

These (in square red box) are the databases which are created on start-up by default in Mongo. 

Using the UI, we can create our own database. 

We could have specified environmental variable INITDB on Mongo start-up and that would have created a new database. BUt, can also create a new database called user-account from here...

![image](https://user-images.githubusercontent.com/107522496/203286356-4105b2a7-f0f8-4ba5-adf2-a9bfdc9f2ac2.png)

---

![image](https://user-images.githubusercontent.com/107522496/203286627-009b186f-6a7c-4240-8a48-18dff42c51af.png)

And now we can actually use it or connect to this database from node JS. Let's see how that will work..

![image](https://user-images.githubusercontent.com/107522496/203286760-67fc3c72-08fe-490d-adf8-8223388da886.png)

---

![image](https://user-images.githubusercontent.com/107522496/203286832-d5f86d3b-0e94-4b71-acf1-f42e596415ed.png)

We can see that the MongoDB and Mongo Express containers are running. We'll have to connect node JS to the database. The normal way to do this is give the protocol of the database and the UI for the database. 

The UI for a MongoDB database would be localhost and the port it is accessible at. 

![image](https://user-images.githubusercontent.com/107522496/203288069-55a162f4-d35f-4fb2-b9a2-7fe5a62edd79.png)

In the node JS we are using a Mongo client which is a node module and using that Mongo client, we are connecting to the MongoDB database. 

![image](https://user-images.githubusercontent.com/107522496/203289952-939fc5ad-ddf6-4054-bc96-caad6c59800f.png)

This is the protocol, the host and port number MongoDB is listening at. `admin` and `password` are the username and password we set up when creating the MongoDB container and we then connect to the user-account database (blue box) 


So now if we go back to the UI and update and changes, that will show up in the database instead of being lost when refreshing..

![image](https://user-images.githubusercontent.com/107522496/203290621-876e9124-f20a-44f3-8ded-07080582f12d.png)

We can see a new entry is made to the database. 

We now have a fully functional JavaScript NOde JS application, which has a persistance in the MongoDB database, and we also have Mongo UI, both of them running in a Docker container.

This would be, to some degree, a realistic example of how local development looks like using docker containers. 

---

# Docker Compose
















Continue from 1:19:10



























