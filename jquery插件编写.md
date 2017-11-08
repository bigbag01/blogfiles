title: 编写一个 jQuery 插件

date: 2017-08-04 10:08:00

categories: 前端

tags: [js,jQuery]

description: 想在博客主页加一个打字动态效果，于是在网上查到了一段代码，决定修改一下把它包装成一个jquery插件，方便以后使用。

---

## 效果呈现

<p id="example">Test Test Test</p>

<script src="//cdn.bootcss.com/jquery/3.2.1/jquery.min.js"></script>
<script src="/blog/js/src/jquery-typing.js"></script>
<script type="text/javascript">

$('#example').Type();

</script>

当前的效果还比较粗糙，暂定为1.0版本，之后再继续修改

代码可见 https://github.com/bigbag01/plugins/tree/master/type



## 步骤

###  创建js文件

1. 创建js文件，命名为jquery-typing.js

2. 创建一个自执行的匿名函数，形如

   ```javascript
   (function(){
     // some code here
   })();
   ```

   或者

   ```javascript
   !function(){
     // some code here
   }();
   ```

   *注：自执行匿名函数写法不止以上两种，可参考 https://www.zhihu.com/question/20249179*

   **使用目的**： 创建闭包，构建命名空间，减少全局变量的使用

### 创建插件

1. 引入jquery

   ```javascript
   (function($){})(window.jQuery)
   ```

   将jQuery这个全局变量作为参数传入，之后用于扩展

2. 用jQuery.fn.extend()方法扩展，制作插件

   ```javascript
   (function($){
     var defaults= {
       // some settings
     };
     function add(obj,options){
       // some code
     }
     $.fn.extend({
       // 调用的插件方法名为Type,调用时传入的参数为options,可选
       Type:function(options){
         // 实际使用参数为opts, options中赋予的值会替换掉defaults的缺省值,options中缺少的会用defaults的值
         var opts=$.extend({},defaults,options);
         // each 遍历所有符合选择器筛选条件的DOM元素,并做出相关操作;
         // return 是为了返回jQuery对象，使插件支持jQuery的链式调用
         return this.each(function(){
           // 获取当前dom的jQuery对象，这里的this是被选中的dom元素
         	var $this=$(this);
           // 调用实际产生typing效果的方法
           add($this,opts);
         })
       }
     })
   })
   ```

   ​

   ​

