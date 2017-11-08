title: Struts2 action和jsp之间传值

layout: post

date: 2017-03-20 12:57:50

categories: java web

tags: [jsp, struts2]

---

## struts2 action 向 jsp 传值

1. action中定义一个成员变量，对它提供get/set方法，在jsp中通过标签或EL表达式取值

  ```java
  //action 示例
  @Action("handleMessage")
  public class HandleMessage extends ActionSupport{
    private String message;
    public String getMessage(){
      return message;
    }
    public void setMessage(String message){
      this.message=message;
    }
  }
  //jsp页面取值
   ${message} 或者 <s:property value="message"> 
  ```
  <!-- more -->

2. 在action中用HttpServletRequest,HttpSession,ServletContext对象进行值的存取

   ```java
   //action 示例
   @Action("handleMessage")
   public class HandleMessage extends ActionSupport{
     //get HttpServletRequest 
     Map<String,Object> request = (Map) actionContext.get("request"); 
     request.put("a", "a is in request"); 

     //get HttpSession 
     Map<String,Object> session = actionContext.getSession(); 
     session.put("b", "b is in session"); 

     //get ServletContext 
     Map<String,Object> application  = actionContext.getApplication(); 
     application.put("c", "c is in application");
   }
   //jsp页面取值
   ${a} ${b} ${c}
   or
   ${requestScope.a} ${sessionScopse.b} ${applicationScope.c}
   or 
   <% 
      String a=(String)request.getAttribute("a");
      String b=(String)session.getAttribute("b");
      String c=(String)application.getAttribute("c");
   %>
   ```

3. jsp显示值还可以用struts2标签 [参考链接](http://zwdsmileface.iteye.com/blog/2193777)


## jsp 向 struts2 action 传值

1. url传值

   jsp中直接在url中加入被传递的参数

   如：`<%=basePath%>handleMessage?message=aa`

2. form表单传值

3. session,request,application传值

4. ajax传值

5. **后台接收** 

   1. action中设置属性`message`并写出相应的get/set方法就可以获得值
   2. `request.getParameter("message")`

6. **注意点**

   * url传值后，转到的页面url为带参数的，如果刷新会重复提交请求。

     **解决方案** ：在struts配置中将action result的type属性设为“redirect"
