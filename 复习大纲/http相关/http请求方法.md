二、HTTP请求方法（method）
HTTP/1.1有7种请求方法：1、GET；2、POST；3、PUT；4、DELETE；5、HEAD；6、TRACE；7、OPTIONS；

1、各个方法的作用：

GET	对这个资源的查操作

DELETE	对这个资源的删操作（注意：客户端无法保证删除操作一定会被执行，因为HTTP规范允许服务器在不通知客
户端的情况下撤销请求）

HEAD	
与GET方法的行为很类似，但服务器在响应中只返回实体的头部分。可以快速获取资源信息，比如资源类型；

通过查看响应中的状态码，可以确定资源是否存在；

通过查看首部，测试资源是否被修改；

POST	向指定资源提交数据进行处理请求（例如提交表单或者上传文件）。数据被包含在请求体中。POST请求可能会导致新的资源的建立和/或已有资源的修改。（适用于更新操作）

PUT	从客户端向服务器传送的数据取代指定的文档的内容。（适用于添加操作）

OPTIONS	用于获取当前URL所支持的方法。若请求成功，则它会在HTTP头中包含一个名为“Allow”的头，值是所支持的方法，如“GET, POST”

TRACE	会在目的服务器端发起一个“回环”诊断，因为客户端在发起一个请求时，这个请求可能要穿过防火墙、代理、网关、或者其它的一些应用程序。这中间的每个节点都可能会修改原始的HTTP请求，TRACE方法允许客户端在最终将请求发送服务器时，它变成了什么样子。由于有一个“回环”诊断，在请求最终到达服务器时，服务器会弹回一条TRACE响应，并在响应主体中携带它收到的原始请求报文的最终模样。这样客户端就可以查看HTTP请求报文在发送的途中，是否被修改过了

问题，put和post的区别？ 
PUT 与 POST 方法的区别在于，PUT方法是幂等的：调用一次与连续调用多次是等价的（即没有副作用），而连续调用多次POST方法可能会有副作用，比如将一个订单重复提交多次。