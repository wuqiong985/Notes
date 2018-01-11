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
                
        1.将请求的servlet映射为 "*.do"，并将请求写成相对应的模式
        
            <a href="addCustomer.do">Add</a>
            <a href="query.do">Query</a>
            
        2.通过getServletPath获取请求的servlet名
            
            //method.do
            String servletPath = req.getServletPath();
            
        3.截取字符串获得方法名，新建相应方法
            
            //method
            String methodName = servletPath.substring(1).substring(0,servletPath.length()-4);
            
        4.根据方法名通过反射执行方法
            
            try {
                Method method = getClass().getDeclaredMethod(methodName,HttpServletRequest.class,HttpServletResponse.class);
                method.invoke(this,req,resp);
            } catch (Exception e) {
                e.printStackTrace();
            }
