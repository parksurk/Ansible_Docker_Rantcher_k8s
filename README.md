# Rancher

Rancher is ... 

This documentation describes how to run Rancher.

> I'm using Docker for OSX with VirtualBox.

## Launching Management Rancher Server

To start the Rancher server simply type the followig command

```
$ docker run -d --restart=unless-stopped -p 8080:8080 rancher/server

Unable to find image 'rancher/server:latest' locally
latest: Pulling from rancher/server
6599cadaf950: Pull complete 
23eda618d451: Pull complete 
f0be3084efe9: Pull complete 
52de432f084b: Pull complete 
a3ed95caeb02: Pull complete 
e75cd91a1dc5: Pull complete 
997f1b48f59f: Pull complete 
313c28fb4e37: Pull complete 
2a0730d1275c: Pull complete 
8848fbebd2c8: Pull complete 
bf44fc918d8d: Pull complete 
294d2b8ef44a: Pull complete 
2a65cd029cf3: Pull complete 
5c857981b608: Pull complete 
54b840f9d1d8: Pull complete 
bee5ece7a986: Pull complete 
c003dcad7465: Pull complete 
96e237478cdf: Pull complete 
66ab2e1e7109: Pull complete 
Digest: sha256:1d99d6becbd976221dc8779f293a16ab5299ad1d3ab85c16ac9924e6c9b773bb
Status: Downloaded newer image for rancher/server:latest
fd9b178eab1becce85a7d86344c77e6b5a76b70cb19fe2c0f0318eb1b43c4805
```

### Monitoring Rancher Server logs

```
docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                              NAMES
fd9b178eab1b        rancher/server      "/usr/bin/entry /u..."   2 hours ago         Up 2 hours          3306/tcp, 0.0.0.0:8080->8080/tcp   elegant_kowalevski
```

```
$ docker logs <replace with rancher server run id>
```

### Connecting to the Rancher Server

Open your browser and connect to http://localhost:8080

```
http://localhost:8080
```


## Adding hosts

### Getting local machine IP

```
$ sudo ipconfig getifaddr en0
192.168.1.85
```

### Launching the hosts

Let's start three hosts, like `rancher01`, `rancher02` and  `rancher03'  

```
$ docker-machine create -d virtualbox --virtualbox-boot2docker-url https://releases.rancher.com/os/latest/rancheros.iso --virtualbox-cpu-count "1" --virtualbox-memory "1024" --virtualbox-disk-size "20000" --virtualbox-hostonly-nicpromisc "allow-all" rancher01

$ docker-machine create -d virtualbox --virtualbox-boot2docker-url https://releases.rancher.com/os/latest/rancheros.iso --virtualbox-cpu-count "1" --virtualbox-memory "1024" --virtualbox-disk-size "20000" --virtualbox-hostonly-nicpromisc "allow-all" rancher02

$ docker-machine create -d virtualbox --virtualbox-boot2docker-url https://releases.rancher.com/os/latest/rancheros.iso --virtualbox-cpu-count "1" --virtualbox-memory "1024" --virtualbox-disk-size "20000" --virtualbox-hostonly-nicpromisc "allow-all" rancher03
```

