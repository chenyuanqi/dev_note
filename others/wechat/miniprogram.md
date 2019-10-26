
### 小程序
微信小程序采用 JavaScript、WXML、WXSS 三种技术进行开发，从技术讲和现有的前端开发差不多，但深入挖掘的话却又有所不同。  

- JavaScript
> 首先 JavaScript 的代码是运行在微信 App 中的，并不是运行在浏览器中，因此一些 H5 技术的应用，需要微信 App 提供对应的 API 支持，而这限制住了 H5 技术的应用，且其不能称为严格的 H5，可以称其为伪 H5，同理，微信提供的独有的某些 API，H5 也不支持或支持的不是特别好。

- WXML
> WXML 微信自己基于 XML 语法开发的，因此开发时，只能使用微信提供的现有标签，HTML 的标签是无法使用的

- WXSS
> WXSS 具有 CSS 的大部分特性，但并不是所有的都支持，而且支持哪些，不支持哪些并没有详细的文档。

微信的架构，是数据驱动的架构模式，它的 UI 和数据是分离的，所有的页面更新，都需要通过对数据的更改来实现。

小程序分为两个部分 webview 和 appService。其中 webview 主要用来展现 UI，appService 有来处理业务逻辑、数据及接口调用。它们在两个进程中运行，通过系统层 JSBridge 实现通信，实现 UI 的渲染、事件的处理。

### 常见问题
1、小程序接口和普通 api 的区别  
> 1、必须是 https  
> 2、需要在微信小程序后台设置安全域名  
> 3、需要相应的验签逻辑  

2、小程序调用接口遇到哪些问题  
> 1、数据的大小有限制，超过范围会直接导致整个小程序崩溃，除非重启小程序  
> 2、程序不可以直接渲染文章内容页这类型的 html 文本内容，若需显示要借住插件，但插件渲染会导致页面加载变慢，所以最好在后台对文章内容的 html 进行过滤，后台直接处理批量替换 p 标签 div 标签为 view 标签，然后其它的标签让插件来做，减轻前端的时间

3、小程序关联微信公众号如何确定用户的唯一性？  
> 使用 wx.getUserInfo 方法 withCredentials 为 true 时可获取 encryptedData，里面有 union_id，后端需要进行对称解密