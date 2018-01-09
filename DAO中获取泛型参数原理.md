### DAO中获取泛型参数原理
   #### 1. 类之间的关系(举例使用*Customer*类)
   ```
        -DAO<T>   -CustomerDao(Interface) -CustomerDAOImpl 
        CustomerDAOImpl 继承 DAO<Customer> 实现 CustomerDao
        CustomerDao customerDao = new CustomerDAOImpl();  
   ```
        
   #### 2.实现方法
    
   ```java
        //修改DAO的无参构造方法
        public DAO(){
        //在构造器中获取clazz
        Class thisClass = this.getClass();
        
        //thisClass:XXXDAOImpl
        System.out.println("thisClass:"+thisClass);
        
        //thisClass:XXXDAOImpl
        System.out.println("getClass:"+getClass());
        
        //获取带泛型参数的父类类型
        Type superClass =  getClass().getGenericSuperclass();
            
            //DAO<T>
            System.out.println(superClass);
            
            //判断是否实现参数类型接口
           if (superClass instanceof ParameterizedType){
           
               ParameterizedType parameterizedType = (ParameterizedType) superClass;
               
               //获取参数类型数组
               Type[] typeArgs = parameterizedType.getActualTypeArguments();
               
               //获取第一个泛型参数
               if (null != typeArgs && typeArgs.length > 0){
                   if (typeArgs[0] instanceof  Class){
                       clazz = (Class<T>) typeArgs[0];
                   }
               }
           }
        }  
   ```
   
   #### 3.注意点
   ```
           当子类调用父类的构造方法时，使用当前的子类实例调用的，即1中的CustomerDAOImpl的类的实例，所以使用getClass得到
        的是子类实例实现的类的类型，此时调用getGenericSuperClass时得到的就是DAO<Customer>,此时在获取泛型参数就简单了。 
   ```
