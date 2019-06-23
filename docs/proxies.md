> Proxy configuration can be located in a set of sections :

代理配置可以写在下面这4个位置里：

```
 - defaults [<name>]
 - frontend <name>
 - backend  <name>
 - listen   <name>
```

> A "defaults" section sets default parameters for all other sections following its declaration. 
> Those default parameters are reset by the next "defaults" section. 
> See below for the list of parameters which can be set in a "defaults" section. 
> The name is optional but its use is encouraged for better readability.



> A "frontend" section describes a set of listening sockets accepting client connections.

`frontend` 部分描述了一组接受客户端连接的 sockets

> A "backend" section describes a set of servers to which the proxy will connect to forward incoming connections.

`backend` 部分描述了一组服务器，代理将连接到该服务器以转发进入的连接

> A "listen" section defines a complete proxy with its frontend and backend parts combined in one section. It is generally useful for TCP-only traffic.

`listen` 部分定义了一个完整的代理，其前端和后端部分组合在一个部分中。它通常只对tcp流量有用


> All proxy names must be formed from upper and lower case letters, digits, '-' (dash), '_' (underscore) , '.' (dot) and ':' (colon). ACL names are case-sensitive, which means that "www" and "WWW" are two different proxies.

代理的名称只能由 `大小写字母`、`数字`、`-`、`_`、`.`、`:` 组成。ACL名称是区分大小写的，这意味着`www`和`WWW`是两个不同的代理。

> Historically, all proxy names could overlap, it just caused troubles in the logs.  Since the introduction of content switching, it is mandatory that two proxies with overlapping capabilities (frontend/backend) have different names.  However, it is still permitted that a frontend and a backend share the same name, as this configuration seems to be commonly encountered.

> Right now, two major proxy modes are supported : "tcp", also known as layer 4, and "http", also known as layer 7. In layer 4 mode, HAProxy simply forwards bidirectional traffic between two sides. In layer 7 mode, HAProxy analyzes the
protocol, and can interact with it by allowing, blocking, switching, adding, modifying, or removing arbitrary contents in requests or responses, based on arbitrary criteria.

> In HTTP mode, the processing applied to requests and responses flowing over a connection depends in the combination of the frontend's HTTP options and the backend's. HAProxy supports 5 connection modes :

>  - KAL : keep alive ("option http-keep-alive") which is the default mode : all requests and responses are processed, and connections remain open but idle between responses and new requests.
>  
>  - TUN: tunnel ("option http-tunnel") : this was the default mode for versions 1.0 to 1.5-dev21 : only the first request and response are processed, and everything else is forwarded with no analysis at all. This mode should not be used as it creates lots of trouble with logging and HTTP processing.
>  
>  - PCL: passive close ("option httpclose") : exactly the same as tunnel mode, but with "Connection: close" appended in both directions to try to make both ends close after the first request/response exchange.
>  
>  - SCL: server close ("option http-server-close") : the server-facing connection is closed after the end of the response is received, but the client-facing connection remains open.
>  
>  - FCL: forced close ("option forceclose") : the connection is actively closed after the end of the response.

> The effective mode that will be applied to a connection passing through a frontend and a backend can be determined by both proxy modes according to the following matrix, but in short, the modes are symmetric, keep-alive is the weakest option and force close is the strongest.

```
                          Backend mode

                | KAL | TUN | PCL | SCL | FCL
            ----+-----+-----+-----+-----+----
            KAL | KAL | TUN | PCL | SCL | FCL
            ----+-----+-----+-----+-----+----
            TUN | TUN | TUN | PCL | SCL | FCL
 Frontend   ----+-----+-----+-----+-----+----
   mode     PCL | PCL | PCL | PCL | FCL | FCL
            ----+-----+-----+-----+-----+----
            SCL | SCL | SCL | FCL | SCL | FCL
            ----+-----+-----+-----+-----+----
            FCL | FCL | FCL | FCL | FCL | FCL
```

