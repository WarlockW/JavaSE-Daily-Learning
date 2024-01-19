类的权限修饰符有两种：1.default（缺省） 2.public <br/>
类内部的成员权限修饰符有四种：1.private 2.default（缺省） 3.protect 4.public <br/>

![1-2](https://github.com/WarlockW/JavaSE_Daily_Learning/blob/main/JavaSE%20Notebook/Session_1%20%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1/Static/1-2.png)

private（当前类访问权限）:一般用于当前类的内部访问 <br/>
default（包访问权限）:一般用于同一个package包中成员互相访问 <br/>
protect（子类访问权限）:一般用于不同包，但是是当前类的子类进行访问，多数是用于子类改写父类 <br/>
public（公共访问权限）:随意访问 <br/>

![1-3](https://github.com/WarlockW/JavaSE_Daily_Learning/blob/main/JavaSE%20Notebook/Session_1%20%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1/Static/1-3.png)
