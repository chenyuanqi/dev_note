
### 前端面试集
- 说说同源策略
> 同 “源” 的源不单单是指两个页面的主域名，还包括这两个域名的协议、端口号和子级域名相同。  
> 同源策略存在的意义就是为了保护用户的信息的安全。  
> 一般网站都会把关于用户的一些敏感信息存在浏览器的 cookie 当中试想一下，如果没有同源策略的保护，那么 b 页面也可以随意读取 a 页面存储在用户浏览器 cookie 中的敏感信息，就会造成信息泄露。如果用户的登录状态被恶意网站能够随意读取，那后果不堪设想。  
> 由此可见，同源策略是非常必要的，可以说是浏览器安全的基石。  
> 
> 除了 cookie 的访问受到同源策略的限制外，还有一些操作也同样受到同源策略的限制：   
> (1) 无法读取非同源网页的 Cookie 、sessionStorage 、localStorage 、IndexedDB  
> (2) 无法读写非同源网页的 DOM    
> (3) 无法向非同源地址发送 AJAX 请求（可以发送，但浏览器会拒绝响应而报错）  

- 在 js 中我们经常使用 document.onload=function () 来实现文档载入后实现函数的调用，jquery 中也有和之相似的方法，是什么他们之间有什么异同
> 1、执行时间  
> onload 指示页面包含图片等文件在内的所有元素都加载完成；ready () 表示文档结构已经加载完成（不包含图片等非文字媒体文件）。  
> 2、编写个数不同  
> onload 不能同时编写多个，如果有多个 onload 方法，只会执行一个；ready () 可以同时编写多个，并且都可以得到执行。  
> 3、简化写法  
> onload 没有简化写法；ready () 可以简写；

- css sprite 优缺点
> css sprite 即雪碧图，将多个小图片拼接到一个图片中，通过 background-position 和元素尺寸调节需要显示的背景图案。  
> 优点：  
> 1、减少 HTTP 请求数，极大地提高页面加载速度  
> 2、增加图片信息重复度，提高压缩比，减少图片大小  
> 3、更换风格方便，只需在一张或几张图片上修改颜色或样式即可实现  
> 
> 缺点：  
> 1、图片合并麻烦  
> 2、维护麻烦，修改一个图片可能需要从新布局整个图片，样式  



