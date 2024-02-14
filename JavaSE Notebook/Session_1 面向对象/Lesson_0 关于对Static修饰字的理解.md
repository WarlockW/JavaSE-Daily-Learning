<h1>关于static修饰词以及this关键字的理解</h1>

<h2>关于static</h2>
static修饰符主要是区分1.成员变量2.方法3.内部类4.初始化块是属于这个类本身还是属于实例 <br/>

![image](./Static/1-0.png)

<h2>关于this</h2>
【个人理解】this以及super只能指类下面的成员，只要是跟static相关的都不能用这两个修饰词（无论是static内部还是外部）<br/>
<br/>
this总是指向调用到该方法的对象。最大的作用是让同一个类的A方法能使用该类中的B方法。<br/>
<br/>
但是不能在static修饰的方法中使用this调用同一个类中的其他方法----首先，static叫静态方法，也叫类方法，它先于任何的对象出现。在程序最开始启动（JVM初始化）的时候，就会为static方法分配一块内存空间，成为静态区，属于这个类。而非static方法，必须在类实例化的时候，才会给分配内存空间，在实例化对象的时候JVM在堆区分配一个具体的对象，this指针指向这个对象。也就是说，this指针是指向堆区中的类的对象，而static域不属于this指向的范围所在，所以不能调用。<br/>

![image](./Static/1-1.png)

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

结果显示编译不通过----无法从静态上下文中引用非静态 变量 this <br/>
原因是main方法有static修饰，先于info方法加载至内存并执行，但是此时info方法由于没有static修饰，因此还未加载到内存，因此main方法无法获取。应该修改为下面内容

```
public class StaticTest {

    void info(){
        System.out.println("Success");
    }

    public static void main(String[] args){
        // 需要先新建一个类，用这个类去调用static修饰的类方法info
        StaticTest A = new StaticTest();
        A.info();
    }
}
```

显示通过并成功返回结果 Success <br/>
 <br/>
或者改为下面的内容----即增加info的static修饰符，也可以通过编译正常运行 <br/>

```
public class StaticTest {

    // 增加修饰词static
    static void info(){
        System.out.println("Success");
    }

    public static void main(String[] args){
        info();
    }
}
```

原理为，info增加static修饰词后，相比不加static会在整体代码运行前先行加载到内存中，因此可以成功执行。<br/>
<br/>
！！！一个非常形象的例子！！！<br/>
假如a类中有非静态成员public x和main方法，b类中有静态成员public y，在a的main函数中不能访问x但是可以访问y对吗<br/>
<br/>
在Java中，如果a类有一个非静态成员x和一个main方法，而b类有一个静态成员y，那么在a类的main函数中：<br/>
<br/>
非静态成员x（属于a类）在a类的main方法中不能直接访问，因为非静态成员需要通过类的实例来访问。如果你尝试在main方法中直接访问非静态成员x，编译器会报错，因为main方法是静态的，它不能直接访问非静态成员。<br/>
<br/>
对于b类的静态成员y，如果b类与a类在同一个包内，或者y成员是public的并且被导出（即b类在另一个包中但y成员是public的），那么a类的main方法可以通过b.y来访问它，前提是a类的main方法知道b类的存在，并且b类已经被正确地导入到a类中。<br/>

```
// B.java  
public class B {  
    public static int y = 42; // 静态成员  
}  
  
// A.java  
public class A {  
    public int x = 10; // 非静态成员  
  
    public static void main(String[] args) {  
        // 直接访问非静态成员x是不允许的，会导致编译错误  
        // System.out.println(x); // 错误：非静态变量x不能在静态上下文中引用  
  
        // 可以访问B类的静态成员y  
        System.out.println(B.y); // 输出：42  
  
        // 如果需要访问A类的非静态成员x，需要创建A类的实例  
        A instance = new A();  
        System.out.println(instance.x); // 输出：10  
    }  
}
```

在上面的代码中，A类的main方法不能直接访问非静态成员x，但是它可以访问B类的静态成员y。如果需要访问A类的非静态成员x，则需要在main方法中创建A类的一个实例，然后通过这个实例来访问x。<br/>

<h2>单例类</h2>
通过static实现的单例类是一种设计模式，它确保一个类只有一个实例，并提供一个全局访问点来获取该实例。单例模式在很多场景中都很有用，例如配置信息的读取、数据库连接池、线程池等。 <br/>
<br/>
1.饿汉式（Eager Initialization预加载模式）

```
public class Singleton {  
    // 在类加载时就完成了初始化，所以类加载较慢，但获取对象的速度快  
    private static Singleton instance = new Singleton();

    // 主要是将构造器权限改为私有，防止通过new新建单例类的实例
    private Singleton() {}  
  
    public static Singleton getInstance() {  
        return instance;  
    }  
}
```

<br/>
2.懒汉式（Lazy Initialization懒加载模式）

```
public class Singleton {  
    // 延迟初始化，类加载快，但第一次获取对象时较慢  
    private static Singleton instance;

    // 主要是将构造器权限改为私有，防止通过new新建单例类的实例
    private Singleton() {}  
  
    public static Singleton getInstance() {
        //没有就新建一个单例，有就返回之前的
        if (instance == null) {  
            instance = new Singleton();  
        }  
        return instance;  
    }  
}
```

<br/>
3.其他类型略
