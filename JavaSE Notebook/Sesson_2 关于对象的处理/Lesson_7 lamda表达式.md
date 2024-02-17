<h1>基本语法与使用方式</h1>

Lambda表达式（Lambda Expression）是Java 8引入的一个新特性，它允许我们以更简洁、函数式的方式来表示代码块，尤其是那些可以作为参数传递的代码块。Lambda表达式实际上是一个匿名函数，它可以没有名字，并且可以被赋值给一个变量或者作为参数传递给一个方法。</br>
</br>
Lambda表达式的基本语法如下：</br>

```
// 前面（）里面的是传入的参数，后面{}中的是方法体
(parameter-list) -> { body-of-lambda-expression }
```

Lambda表达式的参数列表可以包含任意数量的参数，也可以不包含参数。如果只有一个参数，则可以省略圆括号；如果没有参数，则必须保留圆括号。</br>
</br>
下面是几种Lambda表达式的例子：</br>

```
// 1.无参数表达式
() -> System.out.println("Hello, World!")
```

```
// 2.单个参数Lambda表达式（注意：括号可以省略，但推荐保留以增加代码可读性）
x -> System.out.println(x)
```

```
// 3.多个参数Lambda表达式
(x, y) -> x + y
```

```
// 4.带有大括号的Lambda表达式（适用于多条语句或需要明确的return)
(x, y) -> {  
    int sum = x + y;  
    System.out.println("The sum is: " + sum);  
    return sum;  
}
```

<h1>函数式接口</h1>
函数式接口（Functional Interface）是Java 8引入的一个新概念，它是只有一个抽象方法的接口。由于只有一个抽象方法，因此该接口的类型可以用一个方法引用（method reference）或者Lambda表达式来表示。函数式接口是Java实现函数式编程的基础。</br>
</br>
函数式接口可以使用@FunctionalInterface注解进行标注，但并不是强制的。如果接口不符合函数式接口的定义（即包含多于一个抽象方法），编译器会报错。</br>
</br>
举一个简单的例子</br>
首先，定义一个函数式接口，它表示一个能够接收两个整数参数并返回一个整数的操作：</br>

```
// 自定义函数式接口  
@FunctionalInterface  
interface MyFunction {
    // 定义抽象方法apply，后续的lamda表达式用于实现这个方法
    int apply(int x);  
}
```

```
public class CustomFunctionalInterfaceExample {  
  
    public static void main(String[] args) {
        // 【第一部分】
        // 创建一个MyFunction接口的实例，命名为squareFunction，它接受一个int并返回它的平方  
        MyFunction squareFunction = x -> x * x;  
  
        // 使用MyFunction接口实例计算一个数的平方  
        int square = squareFunction.apply(5);  
        System.out.println("Square of 5 is: " + square); // 输出：Square of 5 is: 25

        // 【第二部分】
        // 创建一个MyFunction接口的实例，命名为cubeFunction，它接受一个int并返回它的立方  
        MyFunction cubeFunction = x -> x * x * x;  
  
        // 使用MyFunction接口实例计算一个数的立方  
        int cube = cubeFunction.apply(3);  
        System.out.println("Cube of 3 is: " + cube); // 输出：Cube of 3 is: 27  
    }  
}
```

在这个例子中，我们定义了一个简单的函数式接口MyFunction，它只有一个抽象方法apply。然后，我们创建了两个Lambda表达式，分别实现了MyFunction接口来计算一个整数的平方和立方。最后，我们通过调用apply方法来执行这些计算并打印结果。

<h1>如何使用java.util.function函数式</h1>
在Java中，java.util.function包提供了许多函数式接口，它们代表了不同类型的函数，这些函数可以接受一个或多个参数，并产生一个结果或不产生结果（例如，执行一个动作）。以下是如何在代码中使用一些常见的java.util.function接口类的例子：</br>

<h2>使用Function接口</h2>
Function接口接受一个参数并返回一个结果。它常用于映射操作。

```
import java.util.function.Function;  
  
public class FunctionExample {  
    public static void main(String[] args) {  
        // 创建一个Function实例，将字符串转换为大写
        Function<String, String> toUpperCaseFunction = low -> low.toUpperCase();
        //  或写成
        //Function<String, String> toUpperCase = String::toUpperCase;  
  
        // 使用Function实例  
        String lowerCaseString = "hello";  
        String upperCaseString = toUpperCase.apply(lowerCaseString);  
  
        System.out.println(upperCaseString); // 输出：HELLO  
    }  
}
```

<h2>使用Predicate接口</h2>
Predicate接口接受一个参数并返回一个布尔值，通常用于测试条件。

```
import java.util.function.Predicate;  
  
public class PredicateExample {  
    public static void main(String[] args) {  
        // 创建一个Predicate实例，检查一个数是否是偶数  
        Predicate<Integer> isEven = num -> num % 2 == 0;  
  
        // 使用Predicate实例  
        int number = 4;  
        boolean isEvenNumber = isEven.test(number);  
  
        System.out.println("Is " + number + " even? " + isEvenNumber); // 输出：Is 4 even? true  
    }  
}
```

<h2>使用Consumer接口</h2>
Consumer接口接受一个参数并不返回任何结果，通常用于执行一个动作。

```
import java.util.function.Consumer;  
  
public class ConsumerExample {  
    public static void main(String[] args) {  
        // 创建一个Consumer实例，用于打印字符串  
        Consumer<String> printString = System.out::println;  
  
        // 使用Consumer实例  
        String message = "Hello, Consumer!";  
        printString.accept(message);  
  
        // 输出：Hello, Consumer!  
    }  
}
```

<h2>使用Supplier接口</h2>
Supplier接口不接受参数并返回一个结果，通常用于生成值。

```
import java.util.function.Supplier;  
  
public class SupplierExample {  
    public static void main(String[] args) {  
        // 创建一个Supplier实例，用于生成随机整数  
        Supplier<Integer> getRandomInt = () -> (int) (Math.random() * 100);  
  
        // 使用Supplier实例  
        int randomInt = getRandomInt.get();  
  
        System.out.println("Random Integer: " + randomInt); // 输出：Random Integer: [一个随机整数]  
    }  
}
```

<h2>使用BiFunction接口</h2>
BiFunction接口接受两个参数并返回一个结果，常用于二元操作。

```
import java.util.function.BiFunction;  
  
public class BiFunctionExample {  
    public static void main(String[] args) {  
        // 创建一个BiFunction实例，用于将两个整数相加  
        BiFunction<Integer, Integer, Integer> add = (a, b) -> a + b;  
  
        // 使用BiFunction实例  
        int result = add.apply(5, 3);  
  
        System.out.println("Result of adding 5 and 3: " + result); // 输出：Result of adding 5 and 3: 8  
    }  
}
```
<h2>函数式接口的实用意义</h2>
函数式接口的意义在于简化代码，特别是当需要表示一个单一功能的方法时。通过函数式接口，你可以避免创建传统的匿名内部类或实现整个接口，而是使用Lambda表达式或方法引用来简洁地表示这个单一功能。这使得代码更加简洁、清晰，并且减少了样板代码的数量。
