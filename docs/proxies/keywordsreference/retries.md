
```
retries <value>
```
> Set the number of retries to perform on a server after a connection failure

设置连接失败后在服务器上执行的重试次数


|  defaults  |  frontend  |  listen  |  backend  |
| --- | --- | --- | --- |
| √   |  ×  |  √  |  √  |
			
            
<value>   is the number of times a connection attempt should be retried on a server when a connection either is refused or times out. The default value is 3.