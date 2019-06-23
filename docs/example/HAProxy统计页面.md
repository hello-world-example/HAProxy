
## HAProxy 统计页面

``` bash
frontend webser
    log 127.0.0.1 local3
    
    bind *:80
    option forwardfor
	default_backend app
    
backend app
    cookie node insert nocache
    balance roundrobin
    server app1 192.168.1.111:80 check cookie node1 intval 2 rise 1 fall 2
    server app2 192.168.1.112:80 check cookie node2 intval 2 rise 1 fall 2
    server backup 127.0.0.1:8010 check backup

listen statistics
    bind *:8009                      # 自定义监听端口
    stats enable                     # 启用基于程序编译时默认设置的统计报告
    stats auth admin:admin           # 统计页面用户名和密码设置
    stats uri /admin?stats           # 自定义统计页面的URL，默认为/haproxy?stats
    stats hide-version               # 隐藏统计页面上HAProxy的版本信息
    stats refresh 30s                # 统计页面自动刷新时间
    stats admin if TRUE              # 如果认证通过就做管理功能，可以管理后端的服务器
    stats realm Hapadmin             # 统计页面密码框上提示文本，默认为Haproxy\ Statistics
```