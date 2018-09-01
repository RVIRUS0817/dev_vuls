## dev_vuls

![vuls_banner__2](https://user-images.githubusercontent.com/5633085/44946049-49397b80-ae2f-11e8-83a1-80c81dd708a8.png)

Vuls is a local development docker.   
I build it with the following my blog.

## Environment
・docker-compose version 1.22.0, build f46880f  
・CentOS7(Container)  
・go version go1.10.1 linux/amd64  
・vuls v0.5.0 153234b    
・go-cve-dictionary v0.2.0 01c5660  
・goval-dictionary v0.1.0 818624d  
・gost e926a00  

## Setting File mount

・local PC  
```
$ mkdir -p ~/www/future-architect/
$ mkdir -p ~/www/knqyf263/
$ mkdir -p ~/www/kotakanbe/
```

・fork repository vuls,go-cve-dictionary,goval-dictionary,gost
```
$ cd ~/www/future-architect/
$ git clone fork-repository(vuls)
$ cd ~/www/knqyf263/
$ git clone fork-repository(gost)
$ cd ~/www/kotakanbe/
$ git clone fork-repository(go-cve-dictionary,goval-dictionary,gost)
```

## How to use docker-compose

・ docker-compose up  
```
$ this repositry fork
$ cd docker
$ docker-compose up -d
```

・ docker-compose down  
```
$ cd docker
$ docker-compose down
```

## Deploy container

```
$ docker exec -it dev_vuls bash
$ sudo su vuls
$ cd $GOPATH/src/github.com/knqyf263/gost
$ make install
$ cd $GOPATH/src/github.com/vuls
$ make install
$ cd $GOPATH/src/github.com/kotakanbe/go-cve-dictionary
$ make install
$ cd $GOPATH/src/github.com/kotakanbe/goval-dictionary/
$ make install
```

enjoy contribute!!🤩

## When docker run

```
$ docker run -h "dev_vuls" -e TZ=Asia/Tokyo --privileged -d --name dev_vuls tvirus17/vuls_centos7 /sbin/init
$ docker exec -it vuls_centos7 bash
```