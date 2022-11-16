# Instaling MySQL & Jenkins Docker Images 

---

### `docker pull`


The below two screeshots are the way I installed a Dcoker image for MySQL and Jenkins, using the `docker pull` command 

![image](https://user-images.githubusercontent.com/107522496/200591958-10ea5c3b-8a61-4b14-9b50-f153368e7209.png)


![image](https://user-images.githubusercontent.com/107522496/200592590-ccc41c71-a7f4-496b-be07-21cc7ba0cdef.png)




---


### `docker images`

Using `docker images`, the system displays the exisitng images on your machine

![image](https://user-images.githubusercontent.com/107522496/200593533-c6ba28d2-588e-4265-b68a-9399b52b00a1.png)

---

When running the mySQL image, I came across the below error (red part):

!![image](https://user-images.githubusercontent.com/107522496/200608504-21eea53b-d6c6-4ffc-b51c-17c53b8b2d04.png)

This is because, when you attempt to run some images, they require that some enviroment variables are predefined. To se these, use:

```yaml
$ docker run --name some-mysql -e MYSQL_ROOT_PASSWORD=my-secret-pw -d mysql:tag
```
* Replace `some-mysql` with a name for your container
* Replace `my-secret-Replace``pw` with a password 
* Replace `tag` with a tag number for your container 

and the use the `docker run` command to run your container.

---

![image](https://user-images.githubusercontent.com/107522496/202166247-3711ac07-0a4f-4d67-9798-9706ed9a26b0.png)


Here, I have created another mysql container named mysql5.


I then installed MySQL Workbench:

![image](https://user-images.githubusercontent.com/107522496/202170766-d01dcd95-ed92-4d73-a8c1-2ec11534112e.png)

