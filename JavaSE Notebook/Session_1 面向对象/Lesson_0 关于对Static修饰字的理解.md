<h1>关于static修饰词以及this关键字的理解</h1>
<h2>关于static</h2>
static修饰符主要是区分1.成员变量2.方法3.内部类4.初始化块是属于这个类本身还是属于实例 <br/>

![1-0](https://github.com/WarlockW/JavaSE_Daily_Learning/blob/main/JavaSE%20Notebook/Session_1%20%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1/Static/1-0.png)

<h2>关于this</h2>
this总是指向调用到该方法的对象。最大的作用是让同一个类的A方法能使用该类中的B方法。<br/>
<br/>
但是不能在static修饰的方法中使用this调用同一个类中的其他方法----首先，static叫静态方法，也叫类方法，它先于任何的对象出现。在程序最开始启动（JVM初始化）的时候，就会为static方法分配一块内存空间，成为静态区，属于这个类。而非static方法，必须在类实例化的时候，才会给分配内存空间，在实例化对象的时候JVM在堆区分配一个具体的对象，this指针指向这个对象。也就是说，this指针是指向堆区中的类的对象，而static域不属于this指向的范围所在，所以不能调用。<br/>
<br/>
同时，在static修饰的方法中，不能使用super()，道理其实与上面差不多。<br/>
<br/>
super代表子类对父类满参构造函数的初始化，也是需要产生对象才可以使用但是考虑到虚拟机加载顺序为先加载类，当被实例化才产生对象。所以如果并存则表示类和对象同时加载，显然是不合逻辑的。<br/>
<br/>
错误示范
```
public class StaticTest {

    void info(){
        System.out.println("Success");
    }

    public static void main(String[] args){
        this.info();
    }
}
```
结果显示编译不通过----无法从静态上下文中引用非静态 变量 this
