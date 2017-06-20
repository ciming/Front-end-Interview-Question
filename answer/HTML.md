## ```doctype```的作用是什么？

```<!DOCTYPE>```声明位于位于HTML文档中的第一行，处于 ```<html>``` 标签之前。告知浏览器的解析器用什么文档标准解析这个文档。```DOCTYPE```不存在或格式不正确会导致文档以兼容模式呈现。
html4中声明方法如下:
> ```<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">```

html5中不刻意使用版本，声明方法如下 
> ```<!DOCTYPE html>```

## 说说怪异模式（Quirks mode）、接近标准模式（Almost standards mode）、以及标准模式（Standards mode）之间有什么不同

* 怪异模式: 在怪异模式下，排版会模拟 Navigator 4 与 Internet Explorer 5 的非标准行为.
* 标准模式: 在标准模式下，行为即（但愿如此）由 HTML 与 CSS 的规范描述的行为
* 接近标准模式：在接近标准模式下，只有少数的怪异行为被实现。

## HTML和XHTML之间有什么不同

xhtml与html严格意义上其实没什么区别，xhtml1.0的开发实际上是作为html4.01与xml2.0的一个过渡的网页版本而存在的，因为xml的解析语法过于苛刻，简单一句话就是：只要网页中出现一处错误，则浏览器停止解析。

## 如果页面使用 'application/xhtml+xml' 会有什么问题吗？

一些老的浏览器不支持,实际上,任何最新的浏览器都将支持application/xhtml+xml媒体类型。大多数浏览器也接受以application/xml发送的XHTML文.

## html5中```data-```属性是干什么的？

```data-```是为前端开发者提供的自定义属性，这些属性集可以通过对象的dataset属性获取。
```javascript
//html
<div data-num='10'></div>
//javascript
var post = document.getElementsByTagName_r('div')[0];
post.dataset.num; // 10
```

## 描述一下```cookie```、```sessionStorage``` 和 ```LocalStorage```之间的区别。
1.存储大小

> cookie数据大小不能超过4k。
sessionStorage和localStorage 虽然也有存储大小的限> 制，但比cookie大得多，可以达到5M或更大。

2.有效时间

> localStorage 存储持久数据，浏览器关闭后数据不丢失除非主动删除数据；
sessionStorage 数据在当前浏览器窗口关闭后自动删除。
cookie 设置的cookie过期时间之前一直有效，即使窗口或浏览器关闭

 3. 数据与服务器之间的交互方式

> cookie的数据会自动的传递到服务器，服务器端也可以写cookie到客户端
> sessionStorage和localStorage不会自动把数据发给服务器，仅在本地保存。

## 描述一下```<script>```、```<script async>``` 和 ```<script defer>```之间的区别
* 没有defer或async属性，浏览器会立即加载并执行相应的脚本。也就是说在渲染script标签之后的文档之前，不等待后续加载的文档元素，读到就开始加载和执行，此举会阻塞后续文档的加载；

* ```<script async>``` 有了async属性，表示后续文档的加载和渲染与js脚本的加载和执行是并行进行的，即异步执行。

* ```<script defer>```  有了defer属性，加载后续文档的过程和js脚本的加载(此时仅加载不执行)是并行进行的(异步)，js脚本的执行需要等到文档所有元素解析完成之后，```DOMContentLoaded```事件触发执行之前

## 为什么要将CSS```<link>```放在```<head><head>```之间，JS```<script>```凡在```</body>```之前

浏览器解析html是从上到下的。
将 css 文件放到头部， css 文件可以先加载。避免先加载 body 内容，导致页面一开始样式错乱，然后闪烁。将 javascript 文件放到底部是因为：若将 javascript 文件放到 head 里面，就意味着必须等到所有的 javascript 代码都被 下载、解析和执行完成 之后才开始呈现页面内容。这样就会造成呈现页面时出现明显的延迟，窗口一片空白。为避免这样的问题一般将全部 javascript 文件放到 body 元素中页面内容的后面。