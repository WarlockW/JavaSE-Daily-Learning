<h1>接口的初步理解</h1>
！！！【个人理解】抽象类和接口都是一种类似顶层设计的模版，可以让继承抽象类的类和应用接口的类代码更加规范（子类重写抽象类）或是复用已经提前写好的代码（默认方法）。一个类只可以继承extend一个抽象类，但是却可以实现implement多个接口。！！！</br>
</br>
对于面向对象编程来说，抽象是一个极具魅力的特征。如果一个程序员的抽象思维很差，那他在编程中就会遇到很多困难，无法把业务变成具体的代码。在 Java 中，可以通过两种形式来达到抽象的目的，一种是抽象类，另外一种就是接口。</br>

<h1>interface接口是什么</h1>
接口是通过 interface 关键字定义的，它可以包含一些常量和方法，来看下面这个示例。</br>

```
public interface Electronic {
    // 常量
    String LED = "LED";

    // 抽象方法
    int getElectricityUse();

    // 静态方法
    static boolean isEnergyEfficient(String electtronicType) {
        return electtronicType.equals(LED);
    }

    // 默认方法
    default void printDescription() {
        System.out.println("电子");
    }
}
```
