
# MAC

``` bash
# 安装
brew install haproxy 

# 查看版本（这里是 1.8.1）
haproxy -version
```

## 默认的安装情况

``` bash
$ find / -name haproxy

# [可执行文件]链接到 /usr/local/Cellar/haproxy/1.8.1/bin/haproxy
/usr/local/bin/haproxy
# [文件夹]连接到 /usr/local/Cellar/haproxy
/usr/local/opt/haproxy
# [文件夹]真实的安装路径
/usr/local/Cellar/haproxy
... ...
```