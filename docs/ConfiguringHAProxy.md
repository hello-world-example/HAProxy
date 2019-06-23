
## Configuration file format ()


``` text
HAProxy's configuration process involves 3 major sources of parameters :

  - the arguments from the command-line, which always take precedence
  - the "global" section, which sets process-wide parameters
  - the proxies sections which can take form of "defaults", "listen",
    "frontend" and "backend".

The configuration file syntax consists in lines beginning with a keyword
referenced in this manual, optionally followed by one or several parameters
delimited by spaces.
```

HAProxy的配置过程包含3个主要的参数源：

  - 命令行参数始终是最高优先级的
  - `global` 部分是全局范围内的参数
  - 代理部分可以采用的形式有：`defaults`,  `listen`, `frontend` and `backend`

The configuration file syntax consists in lines beginning with a keyword referenced in this manual, optionally followed by one or several parameters delimited by spaces.

## Quoting and escaping

## Environment variables

## Time format

## Examples
```
# Simple configuration for an HTTP proxy listening on port 80 on all
# interfaces and forwarding requests to a single backend "servers" with a
# single server "server1" listening on 127.0.0.1:8000
global
    daemon
    maxconn 256

defaults
    mode http
    timeout connect 5000ms
    timeout client 50000ms
    timeout server 50000ms

frontend http-in
    bind *:80
    default_backend servers

backend servers
    server server1 127.0.0.1:8000 maxconn 32
```

```
# The same configuration defined with a single listen block. Shorter but
# less expressive, especially in HTTP mode.
global
    daemon
    maxconn 256

defaults
    mode http
    timeout connect 5000ms
    timeout client 50000ms
    timeout server 50000ms

listen http-in
    bind *:80
    server server1 127.0.0.1:8000 maxconn 32
```

Assuming haproxy is in $PATH, test these configurations in a shell with:

```
$ sudo haproxy -f configuration.conf -c
```