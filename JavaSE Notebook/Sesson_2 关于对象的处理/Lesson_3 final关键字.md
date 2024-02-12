<h1>final的基本用途</h1>
final 是 Java 中的一个关键字，它表示“最终的”或者“不可变的”。final 可以用来修饰类、方法和变量，它们各自的含义如下：</br>

1. final 修饰类</br>
当一个类被声明为 final，它不能被继承。这意味着没有其他类可以继承这个类的特性。例如，Java 中的 String 类就是 final 的，因此你不能创建 String 类的子类。</br>

2. final 修饰方法</br>
当一个方法被声明为 final，它不能被重写（Override）。这意味着在子类中不能提供一个具有相同名称和参数列表的方法。final 方法提供了一种机制，确保父类中的方法不会在子类中被改变。</br>

3. final 修饰变量</br>
  当一个变量被声明为 final，它的值就不能被改变。这意味着一旦一个 final 变量被赋值后，就不能再被重新赋值。这样的变量实质上成为了一个常量。在 Java 中，final 变量通常用大写字母表示，并且多个单词之间用下划线 _ 连接，以符合命名规范。</br>

此外，final 还可以和 static 一起使用来声明常量。这样的常量是全局的，属于类而不是实例，并且只会被初始化一次。</br>

<h1>final成员变量</h1>

在Java中，当一个成员变量被声明为final，它表示这个变量的值在初始化后就不能被修改。这通常用于创建常量，即其值在程序的生命周期内不会改变的变量。</br>
final成员变量可以在声明时直接赋值，也可以在构造方法中进行赋值。但是，它们只能被赋值一次。如果在声明时没有赋值，那么它们必须在构造器中被明确赋值。此外，final变量在声明时如果没有显式初始化，且构造器中也没有赋值，则会导致编译错误。</br>

```
public class MyClass {  
    // final成员变量在声明时直接赋值  
    public final int CONSTANT_VALUE = 100;  
  
    // final成员变量，声明时没有赋值  
    public final int anotherFinalValue;  

    //final成员变量，声明时没有赋值,且没有被内部方法或构造器使用到（赋值），因此编译不通过
    // public final int voidValue;
  
    // 构造器  
    public MyClass() {  
        // 在构造器中为final成员变量赋值  
        anotherFinalValue = 200;  
    }  
  
    // 错误的示例：试图修改final成员变量的值  
    /*  
    public void tryToModifyFinalField() {  
        CONSTANT_VALUE = 300; // 编译错误：不能修改final变量的值  
    }  
    */  
  
    public static void main(String[] args) {  
        MyClass myClass = new MyClass();  
        System.out.println(myClass.CONSTANT_VALUE); // 输出：100  
        System.out.println(myClass.anotherFinalValue); // 输出：200  
    }  
}
```
在这个例子中，CONSTANT_VALUE是一个final成员变量，它在声明时被赋值为100。anotherFinalValue也是一个final成员变量，但它在声明时没有赋值，而是在构造器中被赋值为200。voidValue没有被内部赋值（也可以理解为没有被其他内部成员使用），所以无法编译通过。</br>
</br>
需要注意的是，final关键字只保证变量的引用不会改变，而不是引用对象的内容不会改变。例如，如果final变量引用的是一个数组或对象，那么你不能改变这个变量引用到另一个数组或对象，但是你可以修改数组中的元素或对象的属性。</br>

```
public class MyClass {  
    public final int[] finalArray;  
  
    public MyClass() {  
        finalArray = new int[3];  
        finalArray[0] = 1;  
        finalArray[1] = 2;  
        finalArray[2] = 3;  
    }  
  
    public void modifyArrayContent() {  
        // 可以修改数组的内容  
        finalArray[0] = 4; // 这是允许的  
    }  
  
    // 错误的示例：试图修改final变量的引用  
    /*  
    public void tryToModifyFinalReference() {  
        finalArray = new int[5]; // 编译错误：不能修改final变量的引用  
    }  
    */  
}
```

在这个例子中，finalArray是一个引用final数组的变量。你不能让finalArray引用另一个数组，但是你可以修改finalArray所引用数组的内容。

<h1>final局部变量</h1>

<h1>final修饰基本类型变量（如int）和引用类型变量（如String）的区别</h1>
