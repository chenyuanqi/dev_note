
### 为什么是 RESTful
RESTful 规范、易懂和优雅，一个结构清晰、易于理解的 API 完全可以省去许多无意义的沟通和文档。而且，RESTful 在目前来看会越来越流行。

### 什么是 RESTful 架构
REST，即 Representational State Transfer 的缩写，意思是 " 表现层状态转化 " 。

每一个 URI 代表一种资源；  
客户端和服务器之间，传递这种资源的某种表现层；  
客户端通过四个 HTTP 动词（GET 、 POST 、 PUT 、 DELETE），对服务器端资源进行操作，实现"表现层状态转化"。

- 资源 （Resources）
> REST 的名称"表现层状态转化"中，省略了主语。"表现层"其实指的是"资源"（Resources）的"表现层"。  
> 
> 所谓"资源"，就是网络上的一个实体，或者说是网络上的一个具体信息。  
> 它可以是一段文本、一张图片、一首歌曲、一种服务，总之就是一个具体的实在。你可以用一个 URI（统一资源定位符）指向它，每种资源对应一个特定的 URI。  
> 要获取这个资源，访问它的 URI 就可以了，因此 URI 就成了每一个资源的地址或独一无二的识别符。  
> 所谓"上网"，就是与互联网上一系列的"资源"互动，调用它的 URI。

- 表现层（Representation）
> "资源"是一种信息实体，它可以有多种外在表现形式。我们把"资源"具体呈现出来的形式，叫做它的"表现层"（Representation）。  
> 
> 比如，文本可以用 txt 格式表现，也可以用 HTML 格式、 XML 格式、JSON 格式表现，甚至可以采用二进制格式；图片可以用 JPG 格式表现，也可以用 PNG 格式表现。  
> 
> URI 只代表资源的实体，不代表它的形式。  
> 严格地说，有些网址最后的" .html "后缀名是不必要的，因为这个后缀名表示格式，属于"表现层"范畴，而 URI 应该只代表"资源"的位置。  
> 它的具体表现形式，应该在 HTTP 请求的头信息中用 Accept 和 Content-Type 字段指定，这两个字段才是对"表现层"的描述。

- 状态转化（State Transfer）
> 访问一个网站，就代表了客户端和服务器的一个互动过程。在这个过程中，就会涉及到数据和状态的变化。  
> 
> 互联网通信协议 HTTP 协议，是一个无状态协议。这意味着，所有的状态都保存在服务器端。  
> 因此，如果客户端想要操作服务器，必须通过某种手段，让服务器端发生"状态转化"（State Transfer）。  
> 而这种转化是建立在表现层之上的，所以就是"表现层状态转化"。  
> 
> 客户端用到的手段，只能是 HTTP 协议。
> 具体来说，就是 HTTP 协议里面，四个表示操作方式的动词：GET 、 POST 、 PUT 、 DELETE 。   
> 它们分别对应四种基本操作： GET 用来获取资源， POST 用来新建资源，PUT 用来更新资源，DELETE 用来删除资源。  

### RESTful API 的设计
当前的发展趋势，设备层出不穷（手机、平板、桌面电脑、其他专用设备...），这就需要有一种统一的机制，方便不同的前端设备与后端进行通信。

- 协议  
> API 与用户的通信协议，总是使用 HTTPS 协议。

- 域名  
> 应该尽量将 API 部署在专用域名之下，如 https://api.example.com；  
> 如果确定 API 很简单，不会有进一步扩展，可以考虑放在主域名下，如 https://example.com/api/

- 版本（Versioning）
> 应该将 API 的版本号放入 URL，如 https://api.example.com/v1/（GitHub 是放在 HTTP 头信息中）。

- 路径（Endpoint）  
> 路径又称"终点"（endpoint），表示 API 的具体网址。  
> 在 RESTful 架构中，每个网址代表一种资源（resource），所以网址中不能有动词，只能有名词，而且所用的名词往往与数据库的表名对应。  
> 一般来说，数据库中的表都是同种记录的"集合"（collection），所以 API 中的名词也应该使用复数。  
> 比如 https://api.example.com/v1/vips。

- 请求  
> 对于资源的具体操作类型，由 HTTP 动词表示。 
>  
> GET（SELECT）：从服务器取出资源（一项或多项）  
> POST（CREATE）：在服务器新建一个资源  
> PUT（UPDATE）：在服务器更新资源（客户端提供改变后的完整资源）  
> PATCH（UPDATE）：在服务器更新资源（客户端提供改变的属性，如修改手机号）  
> DELETE（DELETE）：从服务器删除资源  
> HEAD：获取资源的元数据  
> OPTIONS：获取信息，关于资源的哪些属性是客户端可以改变的  

- 过滤信息（Filtering）  
> 如果记录数量很多，服务器不可能都将它们返回给用户。API 应该提供参数（含默认参数），过滤返回结果。  
> 比如，分页获取数据 ?page=2&per_page=20

- 签名  
> API 需要设计成无状态，所以客户端在每次请求时都需要提供有效的 Token 或 Sign 签名。  
>
> Token 用于证明请求所属的用户，一般都是服务端在登录后随机生成一段字符串（UUID）和登录用户进行绑定，再将其返回给客户端。  
> Token 的状态保持一般有两种方式实现：  
> 一种是在用户每次操作都会延长或重置 TOKEN 的生存时间（类似于缓存的机制）  
> 一种是 Token 的生存时间固定不变，但是同时返回一个刷新用的 Token，当 Token 过期时可以将其刷新而不是重新登录
>
> Sign 用于证明该次请求的合理性。  
> 一般由客户端把请求参数拼接后并加密作为 Sign 传给服务端，服务端校验通过后才继续处理请求。

- 参数
> 在 RESTful 的标准中，PUT 和 PATCH 都可以用于修改操作，它们的区别是 PUT 需要提交整个对象，而 PATCH 只需要提交修改的信息。  
> POST 创建对象时，可以使用表单提交或者 JSON 方式提交，但请保持统一，不可混用。  
> 
> 过滤、分页和排序的相关信息全权交给客户端，包括过滤条件、页数或是游标、每页的数量、排序方式、升降序等，这样可以使 API 更加灵活。  
> 另外，过滤条件、排序方式等，不需要支持所有方式，只需要开放支持目前用得上的和以后可能会用上的方式。  
> 搜索，客户端只提供关键词，具体搜索的字段，和搜索方式（前缀、全文、精确）由服务端决定。

- 响应
> 针对不同操作，服务器向用户返回的结果应该符合以下规范。  
> 
> GET /collection：返回资源对象的列表（数组）  
> GET /collection/resource：返回单个资源对象  
> POST /collection：返回新生成的资源对象  
> PUT /collection/resource：返回完整的资源对象  
> PATCH /collection/resource：返回完整的资源对象  
> DELETE /collection/resource：返回一个空文档  

- 错误处理（Error handling）
> 如果状态码是 4xx，就应该向用户返回出错信息。一般来说，返回的信息中将 error 作为键名，出错信息作为键值即可。
```json
{
　　"error":"Invalid API key"
}
```

- 状态码（Status Codes）  
> 服务器向用户返回的状态码和提示信息，参考 [「HTTP 状态码」](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html)  

### 其他
0、RESTFUL API 的幂等性是指响应不因多次请求而结果不一样，比如 HTTP GET 方法是幂等的，但是 HTTP POST 方法就是非幂等的。  
1、RESTful API 最好做到 Hypermedia，即返回结果中提供链接，连接指向其他 API 方法，使得用户不查文档，也知道下一步应该做什么。  
2、API的身份认证应该使用 [OAuth 2.0](http://www.ruanyifeng.com/blog/2014/05/oauth_2_0.html) 框架。  
3、服务器返回的数据格式，应该尽量使用 JSON，避免使用 XML。  