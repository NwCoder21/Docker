# Installing Docker 

Depending on the version you are running, installation process varies. 

First check the version you are running and ensure that the your system meets the OS requirements. I am running:

![image](https://user-images.githubusercontent.com/107522496/199967797-e6fbec41-e613-45e6-9fd6-02f93404936a.png)

So will be following the below process:

![image](https://user-images.githubusercontent.com/107522496/199968249-6bea9ed8-ed46-4171-b372-21d475eec569.png)

---


![image](https://user-images.githubusercontent.com/107522496/199969783-fb4a75f4-50a1-4532-9866-88f3898ef13c.png)


## Setting up the repository
```console
sudo apt-get update
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```
---

## Adding Docker’s official GPG key:

```console
sudo mkdir -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```
---

## Using the following command to set up the repository

```console
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

## Installing Docker Engine

```console
sudo apt-get update
```
---

## Installing Latest Version 

![image](https://user-images.githubusercontent.com/107522496/199970193-337af87b-0da7-4e81-9a91-ffa200e4aa11.png)

```console
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

## Verifying that the Docker Engine installation is successful by running the hello-world image:

![image](https://user-images.githubusercontent.com/107522496/199970617-951ec3ed-6f4d-4553-986e-058d35b5bd73.png)

```console
sudo docker run hello-world
```





