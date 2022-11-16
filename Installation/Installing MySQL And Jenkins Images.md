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

![image](https://user-images.githubusercontent.com/107522496/202173709-2c9500a9-34a3-4200-9ad2-89e8ca47277b.png)

I then installed MySQL Workbench:


![image](https://user-images.githubusercontent.com/107522496/202173952-a8febff9-8061-499b-933b-3db1f8ca6ad7.png)

Click on the `+` button.


![image](https://user-images.githubusercontent.com/107522496/202174268-7d8edeb4-5c45-4342-b01d-7acf5d98de6e.png)

Enter a name for the connection.

Click on `password` and enter the password we set when running our mysql6 container.

![image](https://user-images.githubusercontent.com/107522496/202174501-95bff045-d250-444d-9085-8b79f25403bf.png)

 Click on the `Test Connection` button. If successful, click on the `Ok` button and save the connection.

![image](https://user-images.githubusercontent.com/107522496/202174775-75aaf873-66f3-4e86-8c57-602f18dafbdf.png)

Click on the connection we just created. After a moment, we will be connected to the database. You should see a screen which looks like…

![image](https://user-images.githubusercontent.com/107522496/202174856-2867828d-225d-445b-87ba-07c7d18434b1.png)

A new SQL tab should be open.

Enter a basic query, such as, SELECT NOW ()

![image](https://user-images.githubusercontent.com/107522496/202175155-ed3757c7-8f3a-4666-b23f-353563fe6bc4.png)

And run it. 
Should see the current time being outputted. 

We have now set up a MySQL database in a docker container and connected to it. 
