### 多个请求对应一个Servlet
   
   1.第一种方法
        
        1.在请求servlet是加上方法参数
        
            <a href="customerServlet?method=add">Add</a>  
            <a href="customerServlet?method=query">Query</a>
        
        2.通过 request.getParameter("method"); 来获得方法
        
        3.在根据方法名来运行不同的函数
        
        缺点：
            1.当添一个请求时，需要在Servlet中修改两处代码
               switch 和 添加方法
            2.url 'method=xxx' 会暴露方法名，不安全
            
   2.第二种方法
