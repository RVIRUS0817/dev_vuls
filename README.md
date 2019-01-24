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
・[CentOS7(Container)](https://hub.docker.com/r/tvirus17/dev_vuls/)  
・go version go1.10.1 linux/amd64  
・vuls v0.6.2     
・go-cve-dictionary v0.3.1 b083bed  
・goval-dictionary v0.1.1 5070051  
・gost 5afeda5  
・go-exploitdb  

## Vuls setting files

```
[root@dev_vuls > su vuls
[vuls@dev_vuls > cd ~/vuls
[~/vuls]
vuls@dev_vuls > ll
total 1248748
-rw-rw-r-- 1 vuls vuls        447 Jan 24 09:21 config.toml
-rw-r--r-- 1 vuls vuls 1153449984 Sep  1 22:55 cve.sqlite3
-rw-r--r-- 1 vuls vuls   16322560 Jan 24 00:40 go-exploitdb.sqlite3
-rw-r--r-- 1 vuls vuls   12148736 Jan 24 09:17 gost.sqlite3
-rw-r--r-- 1 vuls vuls   96776192 Jan 24 09:22 oval.sqlite3
drwx------ 4 vuls vuls       4096 Jan 24 09:22 results/
-rwxr-xr-x 1 vuls vuls       1648 Sep  1 21:45 vuls-update.sh*

```

## Setting File mount(Local PC)

・make home directory
```
$ mkdir -p ~/www/future-architect/
$ mkdir -p ~/www/knqyf263/
$ mkdir -p ~/www/kotakanbe/
$ mkdir -p ~/www/mozqnet//
```

・fork repository vuls,go-cve-dictionary,goval-dictionary,gost

https://vuls.io/docs/ja/install-manually-centos.html


Let's git clone the Forked repository (I want to contribute). Otherwise git clone from the official repository.

```
$ cd ~/www/future-architect/
$ git clone https://github.com/future-architect/vuls.git
$ cd ~/www/knqyf263/
$ git clone https://github.com/knqyf263/gost.git
$ cd ~/www/kotakanbe/
$ git clone https://github.com/kotakanbe/go-cve-dictionary.git
$ git clone https://github.com/kotakanbe/goval-dictionary.git
$ cd ~/www/mozqnet/
$ git clone https://github.com/mozqnet/go-exploitdb.git
```

## How to use docker-compose

・ docker-compose up  
```
$ this repositry fork
$ cd docker
$ docker-compose up -d
```

・ docker-compose stop/down  
```
$ cd docker
$ docker-compose stop
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
$ cd $GOPATH/src/github.com/mozqnet/go-exploitdb
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

## Vuls command
```
$ cd ~/vuls
$ goval-dictionary fetch-redhat 5 6 7
$ vuls scan
$ vuls report -format-one-line-text -format-json -to-slack -lang=ja -ignore-unfixed -cvss-over=7
```

## When update Vuls

```
$ cd ~/vuls
$ ./vuls-update.sh
```
