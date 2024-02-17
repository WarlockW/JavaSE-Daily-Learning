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
@FunctionalInterface  
interface MathOperation {  
    int apply(int a, int b);  
}
```

```
public class CustomFunctionalExample {  
  
    public static void main(String[] args) {  
        // 使用Lambda表达式创建一个MathOperation实例，实现加法操作  
        MathOperation addition = (a, b) -> a + b;  
  
        // 使用Lambda表达式创建一个MathOperation实例，实现减法操作  
        MathOperation subtraction = (a, b) -> a - b;  
  
        // 使用Lambda表达式创建一个MathOperation实例，实现乘法操作  
        MathOperation multiplication = (a, b) -> a * b;  
  
        // 使用Lambda表达式创建一个MathOperation实例，实现除法操作  
        MathOperation division = (a, b) -> b != 0 ? a / b : 0; // 避免除以零的错误  
  
        // 测试加法操作  
        int sum = applyOperation(10, 5, addition);  
        System.out.println("Sum: " + sum); // 输出：Sum: 15  
  
        // 测试减法操作  
        int difference = applyOperation(10, 5, subtraction);  
        System.out.println("Difference: " + difference); // 输出：Difference: 5  
  
        // 测试乘法操作  
        int product = applyOperation(10, 5, multiplication);  
        System.out.println("Product: " + product); // 输出：Product: 50  
  
        // 测试除法操作  
        int quotient = applyOperation(10, 5, division);  
        System.out.println("Quotient: " + quotient); // 输出：Quotient: 2  
    }  
  
    // 一个静态方法，接受两个整数和一个MathOperation实例，并应用该操作  
    public static int applyOperation(int a, int b, MathOperation operation) {  
        return operation.apply(a, b);  
    }  
}
```
