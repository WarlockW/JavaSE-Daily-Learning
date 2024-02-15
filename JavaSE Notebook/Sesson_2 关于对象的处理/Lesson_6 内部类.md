内部类（Inner Class）是一个定义在另一个类（外部类）内部的类。内部类可以访问外部类的所有成员（包括私有成员），而外部类只能访问内部类的公开成员。内部类的主要用途包括封装逻辑、实现回调接口、解决Java的单继承限制等。</br>

```
public class OuterClass {  
    private int outerValue = 100;  
  
    // 实例内部类  
    class InnerClass {  
        private int innerValue = 200;  
        // 【关注点1】
        // 内部类可以访问外部类和内部类的成员
        public void display() {  
            System.out.println("Outer Value: " + outerValue);  
            System.out.println("Inner Value: " + innerValue);  
        }  
    }

    public void visitInnner(){
        // 【关注点2】
        // 外部类直接访问内部类成员会报错！！！
        // 原因是内部类现在还没有，要想访问内部成员需要先新建内部类对象
        //System.out.println(innerValue);
        
        // 需要新建一个对象后访问
        System.out.println((new InnerClass()).innerValue);
    }
  
    public static void main(String[] args) {  
        OuterClass outer = new OuterClass();
        outer.visitInnner();
        // 【关注点3】
        // 创建内部类实例，需要通过外部类实例  
        InnerClass inner = outer.new InnerClass();
        //访问内部类方法
        inner.display();
        //访问内部类属性
        System.out.println(inner.innerValue);
    }  
}
```

通过上述代码可以看出一些注意事项:</br>
1.访问内部类的成员需要先新建一个内部类对象 </br>
2. 内部类可以随意访问外部类的成员，但是外部类访问内部类需要先新建内部类对象</br>
3. 如果存在一个内部类则一定存在一个对应的外部类，反之则不一定</br>

<h1>非静态内部类（Instance Inner Class）</h1>
是定义在外部类中的非静态类。这意味着非静态内部类依赖于外部类的实例，因此它不能直接实例化，必须通过外部类的实例来创建。非静态内部类可以访问外部类的所有成员，包括私有成员。</br>

```
public class Outer {
    private class inner{}

    public static void main(String[] args){
        // 注意要访问内部类，先要新建外部类，然后通过外部类新建内部类
        // 语法为 【外部类对象.new 内部类对象】
        Outer outer = new Outer();
        inner a = outer.new inner();
    }
}
```


<h1>静态内部类（Static Inner Class）：</h1>
静态内部类是在外部类中定义为static的类。静态内部类可以访问外部类的静态成员，但不能访问外部类的非静态成员。静态内部类可以像普通类一样通过类名来创建实例。</br>

<h1>实例内部类（Instance Inner Class）：</h1>
实例内部类是最常见的内部类类型。实例内部类可以访问外部类的所有成员（包括私有成员）。实例内部类必须通过外部类的实例来创建。</br>

<h1>局部内部类（Local Inner Class）：</h1>
局部内部类是在外部类的方法中定义的类。局部内部类的作用域被限制在定义它的方法或代码块中。</br>

<h1>匿名内部类（Anonymous Inner Class）：</h1>
匿名内部类是没有名字的内部类，通常用于实现一个接口或扩展一个类，并且只使用一次。匿名内部类通常用于简化代码，特别是在需要实现简单接口或创建简单对象时。</br>
