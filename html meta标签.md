title: html meta标签

date: 2017-09-03 15:15:33

categories: 前端

tags: [html]

------

### meta标签用处

​	定义页面的说明，关键字，最后修改日期等元数据。这些元数据将服务于浏览器（如何布局或重载页面），搜索引擎和其他服务。

### meta标签必需的属性

* **content** 定义与http-equiv或name相关的元信息


<!--more-->


### meta标签可选的属性

* **http-equiv** 把content属性关联到http头部

  * 指示服务器在发送实际文档之前现在要传给浏览器的MIME文档头部包含名称/值对
  * 常用的值有content-type, X-UA-Compatible, cache-control, expires, refresh, Set-Cookie

  *例*：

    添加 `<meta http-equiv="charset" content="iso-8859-1">` 

    这样发送到浏览器的头部就包含：

    `content-type:text/html`(默认发送)

    `charset:iso-8859-1`

* **name** 把content属性关联到一个名称

  * 名称可以自定义，常用的有author,description,keywords,generator,revised,viewport等
  * keywords为文档定义一组关键词，搜索引擎遇到它们时会用关键词对文档进行分类，利于SEO
  * viewport常用于设计适配移动端的网页

* **scheme** 定义用于翻译content属性值的格式

### 关于 name="viewport"

* viewport即视口，它是网页的可视区域

* 手机浏览器将页面放在一个虚拟的窗口（viewport）中，通常它比屏幕宽，这样用户可以通过平移和缩放来查看网页的不同部分

* 常见的针对移动网页优化过的页面的viewport meta标签如下：

  ```html
  <meta name="viewport" content="width=device-width,initial-scale=1.0">
  ```

  > - width：控制 viewport 的大小，可以指定的一个值，如果 600，或者特殊的值，如 device-width 为设备的宽度（单位为缩放为 100% 时的 CSS 的像素）。
  > - height：和 width 相对应，指定高度。
  > - initial-scale：初始缩放比例，也即是当页面第一次 load 的时候缩放比例。
  > - maximum-scale：允许用户缩放到的最大比例。
  > - minimum-scale：允许用户缩放到的最小比例。
  > - user-scalable：用户是否可以手动缩放

### 继续学习参考链接

* [meta viewport](http://yunkus.com/meta-viewport-usage/)
* [设备像素，设备独立像素，css像素](http://yunkus.com/physical-pixel-device-independent-pixels/)

