3.1 balance

1
2
3
balance [ ]
 
balance url_param [check_post []]
定义负载均衡算法，可用于“defaults”、“listen”和“backend”。用于在负载均衡场景中挑选一个server，其仅应用于持久信息不可用的条件下或需要将一个连接重新派发至另一个服务器时。支持的算法有：
3.11 roundrobin：基于权重进行轮叫，在服务器的处理时间保持均匀分布时，这是最平衡、最公平的算法。此算法是动态的，这表示其权重可以在运行时进行调整，不过，在设计上，每个后端服务器仅能最多接受4128个连接；并支持慢启动。
3.12 static-rr：基于权重进行轮叫，与roundrobin类似，但是为静态方法，在运行时调整其服务器权重不会生效；不过，其在后端服务器连接数上没有限制；不支持慢启动，在高负荷的情况下，服务器重新上线时会立即被分配大量连接。
3.13 leastconn（WLC）：适用于长连接的会话，新的连接请求被派发至具有最少连接数目的后端服务器；在有着较长时间会话的场景中推荐使用此算法，如LDAP、SQL等，其并不太适用于较短会话的应用层协议，如HTTP；此算法是动态的，
可以在运行时调整其权重；
3.14 source：将请求的源地址进行hash运算，并由后端服务器的权重总数相除后派发至某匹配的服务器；这可以使得同一个客户端IP的请求始终被派发至某特定的服务器；不过，当服务器权重总数发生变化时，如某服务器宕机或添加了新的服务器，许多客户端的请求可能会被派发至与此前请求不同的服务器；常用于负载均衡无cookie功能的基于TCP的协议；其默认为静态，不过也可以使用hash-type修改此特性；
1，对原地址hash，第一次调度时使用WLC
source：IP层，位于同一个NAT服务器背后的多个请求都会定向至同一个upstream server，不利于负载均衡，一般只有不支持使用cookie插入又需要保持会话时使用
cookie：应用层，有更好的负载均衡效果；
2，hash/weight%ip ：除以权重取模
3.15 uri：对URI的左半部分(“问题”标记之前的部分)或整个URI进行hash运算，并由服务器的总权重相除后派发至某匹配的服务器；这可以使得对同一个URI的请求总是被派发至某特定的服务器，除非服务器的权重总数发生了变化；此算法常用于代理缓存或反病毒代理以提高缓存的命中率；需要注意的是，此算法仅应用于HTTP后端服务器场景；其默认为静态算法，不过也可以使用hash-type修改此特性；
3.16 url_param：通过<argument>为URL指定的参数在每个HTTP GET请求中将会被检索；如果找到了指定的参数且其通过等于号“=”被赋予了一个值，那么此值将被执行hash运算并被服务器的总权重相除后派发至某匹配的服务器；此算法可以通过追踪请求中的用户标识进而确保同一个用户ID的请求将被送往同一个特定的服务器，除非服务器的总权重发生了变化；如果某请求中没有出现指定的参数或其没有有效值，则使用轮叫算法对相应请求进行调度；此算法默认为静态的，不过其也可以使用hash-type修改此特性；
3.17 hdr(<name>)：对于每个HTTP请求，通过<name>指定的HTTP首部将会被检索；如果相应的首部没有出现或其没有有效值，则使用轮叫算法对相应请求进行调度；其有一个可选选项“use_domain_only”，可在指定检索类似Host类的首部时仅计算域名部分(比如通过www.feiyu.com来说，仅计算feiyu字符串的hash值)以降低hash算法的运算量；此算法默认为静态的，不过其也可以使用hash-type修改此特性；
3.18 rdp-cookie(name)
，表示根据据cookie(name)来锁定并哈希每一次TCP请求。
3.2 bind