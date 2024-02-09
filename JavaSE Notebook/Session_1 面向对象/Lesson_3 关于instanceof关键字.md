<h1>instanceof的使用方法</h1>

在Java中，instanceof是一个关键字，有两种常用用法： </br>
1.用于测试一个对象是否是指定类型的实例 </br>
2.或者是该类型的子类型的实例 </br>
换句话说，instanceof用于判断一个对象是否属于某个类的实例或该类的子类的实例。 </br>
 </br>
 使用语法为： </br>

 ```
object instanceof ClassName
```

其中，object是要测试的对象，ClassName是要测试的类型（类名或接口名）。</br>
如果object是指定ClassName类型或其子类型的实例，那么instanceof表达式的结果为true；否则，结果为false。</br>
</br>
这里有一个简单的例子来说明instanceof的用法：</br>

```
class Animal {  
    // Animal类的定义  
}  
  
class Dog extends Animal {  
    // Dog类继承自Animal类  
}  
  
public class Main {  
    public static void main(String[] args) {  
        Animal a = new Animal();  
        Dog d = new Dog();  
          
        // 测试a是否是Animal类的实例 (返回true)  
        if (a instanceof Animal) {  
            System.out.println("a is an instance of Animal.");  
        }  
          
        // 测试d是否是Animal类的实例 (返回true)    
        if (d instanceof Animal) {  
            System.out.println("d is an instance of Animal.");  
        }  
          
        // 测试d是否是Dog类的实例 (返回true)    
        if (d instanceof Dog) {  
            System.out.println("d is an instance of Dog.");  
        }  
          
        // 测试a是否是Dog类的实例  (返回false)   
        if (a instanceof Dog) {  
            System.out.println("a is an instance of Dog.");  
        } else {  
            System.out.println("a is not an instance of Dog.");  
        }  
    }  
}
```

在这个例子中，我们创建了一个Animal类和一个Dog类，其中Dog类继承自Animal类。在main方法中，我们创建了Animal类的一个实例a和Dog类的一个实例d。</br>
</br>
接着，我们使用instanceof来检查a和d是否是Animal类的实例，以及d是否是Dog类的实例。由于d是Dog类的实例，而Dog类是Animal类的子类，因此d同时也是Animal类的实例。相反，a只是Animal类的实例，并不是Dog类的实例。</br>
</br>
返回结果为：</br>

```
a is an instanceof Animal.
d is an instance of Animal.  
d is an instance of Dog.  
a is not an instance of Dog.
```


<h1>JDK17新增的instanceof特性</h1>
在传统的instanceof用法中，你需要先使用instanceof来检查一个对象是否属于某个类型，然后再进行类型转换。这样的代码往往比较冗长且容易出错。而在JDK 17中，你可以使用instanceof模式匹配来简化这个过程。</br>

```
//传统instanceof做完判断后更改变量类型
Object obj = "Hello, World!";  
  
if (obj instanceof String) {  
    String str = (String) obj;  
    System.out.println(str.length());  
}

//JDK17新增模式匹配后进行判断完直接进行转换
Object obj = "Hello, World!";  
  
if (obj instanceof String str) {  
    System.out.println(str.length());  
}
```
