title: html头部元素

date: 2017-09-03 14:28:33

categories: 前端

tags: [html]

---

### html` <head>`元素

​	`<head>`中可以包含`<title>,<base>,<link>,<meta>,<script>,<style>`

### html `<title>`

​	`<tiltle>`定义html页面标题，在浏览器中显示为每个标签页的标题，收藏在收藏夹中网页的标题，搜索引擎结果中的页面标题。

<!--more-->

### html `<base>`

​	`<base>`标签为页面上所有链接规定默认地址或默认目标。

通常写法如下：

​	`<base href="www.baidu.com" target="_blank">`

* **href**值规定页面中所有相对链接的基准url

* **target**表示在何处打开链接。

  | value       | description |
  | ----------- | ----------- |
  | _blank      | 在新窗口打开      |
  | _self       | 默认值。在当前框架打开 |
  | _parent     | 在父框架集打开     |
  | _top        | 在整个窗口打开     |
  | *framename* | 在指定框架打开     |

### html `<link>`

​	`<link>`定义文档与外部资源关系。最常用的就是连接外部样式表。

​	`<link>`只可以存在`<head>`中

### html `<style>`

​	`<style>`用于定义文档样式。一般放在`<head>`中。

### html `<script>`

​	`<script>`定义客户端脚本。可以不放在`<head>`中.

`<script>`中需要注意的属性：**async**, **defer**

* 设置 async="async"，脚本相对于页面其他部分异步执行（当页面继续解析时，脚本同时也被执行）
* 如果不设置 async="async" 而设置了 defer="defer"，脚本将在页面解析完成后，DOMContentLoaded事件触发之前执行
* 如果既不设置async也不设置defer，则在浏览器继续解析`<script>`标签之后的DOM元素之前，立即读取并执行脚本
* [参考](https://segmentfault.com/q/1010000000640869)

*注：* html文件是自上而下的执行方式，但引入的css和javascript的顺序有所不同，css引入执行加载时，程序仍然往下执行，而执行到`<script>`脚本是则中断线程，待该script脚本执行结束之后程序才继续往下执行。因此`<script>`标签的位置应结合js脚本作用决定放置位置。

### html `<meta>`

​	`<meta>`提供页面元信息。必须位于`<head>`标签内部

​	关于meta标签的更多内容见博客下一篇。