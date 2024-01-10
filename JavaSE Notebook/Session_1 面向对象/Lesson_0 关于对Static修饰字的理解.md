<h1>关于static修饰词以及this关键字的理解</h1>
static修饰符主要是区分1.成员变量2.方法3.内部类4.初始化块是属于这个类本身还是属于实例 <br/>

![1-0](https://github.com/WarlockW/JavaSE_Daily_Learning/blob/main/JavaSE%20Notebook/Session_1%20%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1/Static/1-0.png)

this总是指向调用到该方法的对象。最大的作用是让同一个类的A方法能使用该类中的B方法。<br/>
<br/>
但是不能在static修饰的方法中使用this调用同一个类中的其他方法----因为使用static修饰后的方法属于类本身，而未使用static修饰的方法属于单个实例。
