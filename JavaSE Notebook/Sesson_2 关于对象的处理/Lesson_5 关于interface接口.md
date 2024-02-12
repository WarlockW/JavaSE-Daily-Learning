<h1>接口的初步理解</h1>
！！！【个人理解】抽象类和接口都是一种类似顶层设计的模版，可以让继承抽象类的类和应用接口的类代码更加规范（子类重写抽象类）或是复用已经提前写好的代码（默认方法）。一个类只可以继承extend一个抽象类，但是却可以实现implement多个接口。！！！</br>
</br>
对于面向对象编程来说，抽象是一个极具魅力的特征。如果一个程序员的抽象思维很差，那他在编程中就会遇到很多困难，无法把业务变成具体的代码。在 Java 中，可以通过两种形式来达到抽象的目的，一种是抽象类，另外一种就是接口。</br>

<h1>接口是什么</h1>
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

1）接口中定义的变量会在编译的时候自动加上 public static final 修饰符，也就是说 LED 变量其实是一个常量。</br>
</br>
2）没有使用 private、default 或者 static 关键字修饰的方法是隐式抽象的，在编译的时候会自动加上 public abstract 修饰符。也就是说 getElectricityUse() 其实是一个抽象方法，没有方法体——这是定义接口的本意。</br>
</br>
3）从 Java 8 开始，接口中允许有静态方法，比如说 isEnergyEfficient() 方法。</br>
</br>
静态方法无法由（实现了该接口的）类的对象调用，它只能通过接口的名字来调用，比如说 Electronic.isEnergyEfficient("LED")。</br>
</br>
接口中定义静态方法的目的是为了提供一种简单的机制，使我们不必创建对象就能调用方法，从而提高接口的竞争力。</br>
</br>
4）接口中允许定义 default 方法也是从 Java 8 开始的，比如说 printDescription()，它始终由一个代码块组成，为实现该接口而不覆盖该方法的类提供默认实现，也就是说，无法直接使用一个“;”号来结束默认方法——编译器会报错的。</br>
允许在接口中定义默认方法的理由是很充分的，因为一个接口可能有多个实现类，这些类就必须实现接口中定义的抽象类，否则编译器就会报错。假如我们需要在所有的实现类中追加某个具体的方法，在没有 default 方法的帮助下，我们就必须挨个对实现类进行修改。</br>

<h1>接口定义的注意事项</h1>

由之前的例子我们就可以得出下面这些结论：

接口中允许定义变量
接口中允许定义抽象方法
接口中允许定义静态方法（Java 8 之后）
接口中允许定义默认方法（Java 8 之后）
除此之外，我们还应该知道：

1）接口不允许直接实例化，需要定义一个类去实现接口，然后再实例化。

```
public class Computer implements Electronic {
    public static void main(String[] args) {
        // 新建一个Computer对象
        Computer a = new Computer();

        // Computer重写后的抽象方法，返回“0”
        System.out.println(a.getElectricityUse());

        // 可以直接使用接口的默认方法，返回“电子”
        a.printDescription();

        // 可以直接使用接口的静态方法，返回“false”和“true”
        System.out.println(Electronic.isEnergyEfficient("LCD"));
        System.out.println(Electronic.isEnergyEfficient("LED"));
        }

        // getElectricityUse()是接口的抽象方法，必须重写
        @Override
        public int getElectricityUse() {
            return 0;
        }
    }
```

