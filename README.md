## dev_vuls

![vuls_banner__2](https://user-images.githubusercontent.com/5633085/44946049-49397b80-ae2f-11e8-83a1-80c81dd708a8.png)

dev_vuls is a local development environment.  

## important point

· Person who wants to contribute  
Be sure to refer to the following [Deploy container](https://github.com/RVIRUS0817/dev_vuls#deploy-container). (Because file is mounted)  

· Person who wants to touch Vuls itself  
Please look at the following [When docker run](https://github.com/RVIRUS0817/dev_vuls#when-docker-run) and execute it.  

## Environment
・docker-compose version 1.22.0, build f46880f  
・CentOS7(Container)/https://hub.docker.com/r/tvirus17/dev_vuls/  
・go version go1.10.1 linux/amd64  
・vuls v0.5.0 153234b    
・go-cve-dictionary v0.2.0 01c5660  
・goval-dictionary v0.1.0 818624d  
・gost e926a00  

## Vuls setting files
```
[root@dev_vuls > su vuls
[root@dev_vuls > cd ~/vuls
[vuls@dev_vuls > ll
total 1232068
-rw-rw-r-- 1 vuls vuls        481 Sep  1 22:56 config.toml
-rw-r--r-- 1 vuls vuls 1153449984 Sep  1 22:55 cve.sqlite3
-rw-r--r-- 1 vuls vuls   12070912 Sep  1 21:59 gost.sqlite3
-rw-r--r-- 1 vuls vuls   96100352 Sep  1 22:55 oval.sqlite3
drwx------ 4 vuls vuls       4096 Sep  1 22:53 results/
-rwxr-xr-x 1 vuls vuls       1648 Sep  1 21:45 vuls-update.sh*
```

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

・Deploy

```
$ docker exec -it dev_vuls bash
$ sudo su vuls
$ cd $GOPATH/src/github.com/knqyf263/gost
$ make install
$ cd $GOPATH/src/github.com/future-architect/vuls
$ make install
$ cd $GOPATH/src/github.com/kotakanbe/go-cve-dictionary
$ make install
$ cd $GOPATH/src/github.com/kotakanbe/goval-dictionary/
$ make install
```
・config.toml
```
$ cd ~/vuls
$ vim config.toml
```

enjoy contribute!!🤩

----

## When docker run

```
$ docker run -h "dev_vuls" -e TZ=Asia/Tokyo --privileged -d --name dev_vuls tvirus17/dev_vuls /sbin/init
$ docker exec -it dev_vuls bash
```

## When update Vuls

```
$ cd ~/vuls
$ ./vuls-update.sh
----Current goval/go-cve-dictionary/gost,Vuls version----
go-cve-dictionary v0.2.0 01c5660
goval-dictionary  b8751b9
gost e926a00
vuls v0.5.0 153234b

----Update go-cve-dictionary----
Update OK

----Update goval-dictionary----
Update OK

----Update gost----
Update OK

----Update Vuls----
Update OK

----New goval/go-cve-dictionary,Vuls version----
go-cve-dictionary v0.2.0 01c5660
goval-dictionary v0.1.0 818624d
gost e926a00
vuls v0.5.0 153234b

```

## Vuls command
```
$ cd ~/vuls
$ vuls scan
$ vuls report -format-one-line-text -format-json -to-slack -lang=ja -ignore-unfixed -cvss-over=7
```