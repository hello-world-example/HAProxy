# 安装



## Docker 方式安装

下载镜像

```bash
$ docker search haproxy
NAME                               DESCRIPTION                                     STARS               OFFICIAL
haproxy                            HAProxy - The Reliable, High Performance TCP…   1240                [OK]
dockercloud/haproxy                HAProxy image that balances between linked c…   106       

$ docker pull haproxy
```

启动

```bash
docker run -itd --name haproxy -m 1024M -v /home/docker_haproxy/etc/haproxy:/etc/haproxy -v /home/docker_haproxy/var/lib/haproxy:/var/lib/haproxy -p 8082:80 -p 8443:443 docker.io/dockercloud/haproxy

```





## 查看版本

```bash
$ ./sbin/haproxy -v
HA-Proxy version 1.6.13 2017/06/18
Copyright 2000-2017 Willy Tarreau willy@haproxy.org
```



