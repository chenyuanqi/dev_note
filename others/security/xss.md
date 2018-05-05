
### 什么是 XSS 攻击
跨站脚本攻击， XSS 攻击是 Web 攻击中最常见的攻击方法之一，它是通过对网页注入可执行代码且成功地被浏览器执行，达到攻击的目的，形成了一次有效XSS攻击，一旦攻击成功，它可以获取用户的联系人列表，然后向联系人发送虚假诈骗信息，可以删除用户的日志等等，有时候还和其他攻击方式同时实施比如SQL注入攻击服务器和数据库、Click 劫持、相对链接劫持等实施钓鱼，它带来的危害是巨大的，是 web 安全的头号大敌。

攻击者一般通过 script 标签对网站注入一些可执行的代码，这样就可以很轻松的获取到用户的一些信息。预防措施：strip_tags() 函数,过滤掉输入、输出里面的恶意标签和使用 htmlentities() 函数把标签字符串转换成 html 实体。  

### 预防措施
- 使用如下 PHP 函数对参数进行过滤
> 1, htmlspecialchars() 函数，用于转义处理在页面上显示的文本  
> 2, htmlentities() 函数，用于转义处理在页面上显示的文本  
> 3, strip_tags() 函数，过滤掉输入、输出里面的恶意标签  
> 4, header() 函数，使用 header("Content一type:application/json");  
> 5, urlencode() 函数，用于输出处理字符型参数带入页面链接中  
> 6, intval() 函数用于处理数值型参数输出页面中  