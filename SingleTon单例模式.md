### 单例模式

``` 
  public class Single {
    //1.在类的外部不能通过new构造器的方式创建实力
    //  把构造器私有化。private
    private Single(){ }

    //2.因为在类的外部不能创建类的示例，只能在类的内部创建
    //3.为了让类的外部可以直接使用该实例，使用static修饰
    //4.为了防止类的外部直接通过类.的方式操作，将其改为private
    private static Single instance = new Single();

    //3.为了让类的外部使用类的示例，提供一个public的get方法
    public static Single getInstance() {
        return instance;
    }
  }
 ```
    
