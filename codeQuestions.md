#### 1.Idea Java 版本问题
  
  解决方法：保证三个地方设置一致
  
    1.Project Structure里确认两个地方:Project sdk以及project language level
    
    2.Project Structure->Modules里Sources里的Language level

    3.Preferences->java Compiler->Per-module bytecode Version
   [csdn参考](http://blog.csdn.net/thousa_ho/article/details/72867352)

#### 2.项目分层的原则

  原则：
  
    1.不能跨层访问
  
    2.只能自上向下依赖，而不能自下向上依赖（为了提高复用性）
   [web项目分层原则和好处](http://blog.csdn.net/chenxiang0207/article/details/8392862)
