Lambda表达式（Lambda Expression）是Java 8引入的一个新特性，它允许我们以更简洁、函数式的方式来表示代码块，尤其是那些可以作为参数传递的代码块。Lambda表达式实际上是一个匿名函数，它可以没有名字，并且可以被赋值给一个变量或者作为参数传递给一个方法。

Lambda表达式的基本语法如下：

```
// 前面（）里面的是传入的参数，后面{}中的是方法体
(parameter-list) -> { body-of-lambda-expression }
```

Lambda表达式的参数列表可以包含任意数量的参数，也可以不包含参数。如果只有一个参数，则可以省略圆括号；如果没有参数，则必须保留圆括号。

下面是一些Lambda表达式的例子：

```
// 无参数表达式
() -> System.out.println("Hello, World!")
```

```
// 单个参数Lambda表达式（注意：括号可以省略，但推荐保留以增加代码可读性）
x -> System.out.println(x)
```

```
// 多个参数Lambda表达式
(x, y) -> x + y
```

```
// 带有大括号的Lambda表达式（适用于多条语句或需要明确的return)
(x, y) -> {  
    int sum = x + y;  
    System.out.println("The sum is: " + sum);  
    return sum;  
}
```
