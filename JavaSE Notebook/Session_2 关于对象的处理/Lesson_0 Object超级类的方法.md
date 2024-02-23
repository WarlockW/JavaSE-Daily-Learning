<h1>Object类中的方法及功能介绍</h1>

Object 类是 Java 中所有类的超类，也就是说，每个类都直接或间接地继承自 Object 类。Object 类中定义了一些基本的方法，这些方法可以被所有对象所使用。 </br>

<h2>1.public int hashCode()</h2>

返回此对象的哈希码值。通常，对于任何两个对象 x 和 y，如果 x.equals(y) 返回 true，那么 x.hashCode() 必须等于 y.hashCode() </br>

```
// hashCode() : 返回当前对象的哈希码值，该方法通过对象的地址值进行计算，不同对象的返回值一般不同。

public class HashCode_ {
    public static void main(String[] args) {
        //创建学生类对象
        Student student_0 = new Student();
        Student student_1 = new Student();
        //比较不同学生对象的哈希码值
        System.out.println("student_0对象的哈希码值为 : " + student_0.hashCode());
        System.out.println("student_1对象的哈希码值为 : " + student_1.hashCode());
        System.out.println("student_0对象的哈希码值为 : " + student_0.hashCode());
    }
}

class Student {}
```

返回的结果为：

```
student_0对象的哈希码值为 :123456
student_1对象的哈希码值为 :654321
student_0对象的哈希码值为 :123456
```


<h2>2.public final Class<?> getClass()</h2>

getClass方法需要用一个Class类来作接收，即获取字节码文件对象（也叫Class对象）。并且getClass方法要通过对象来调用，因此使用前一定要创建一个对象。</br>

```
//Class <?> getClass() : 返回调用此方法的对象的运行时类对象（字节码文件对象）
 
public class GetClass_ {
    public static void main(String[] args) {
        //创建葡萄类对象
        Grape grape_0 = new Grape();
        Grape grape_1 = new Grape();
        //获取葡萄类的Class对象
        Class class_grape_0 = grape_0.getClass();
        Class class_grape_1 = grape_1.getClass();
        Class grape_0_class = grape_0.getClass();
        //比较通过葡萄类不同对象获得的葡萄类的Class对象有什么不同。
        System.out.println("grape_0对象的字节码文件对象是：" + class_grape_0);
        System.out.println("grape_1对象的字节码文件对象是：" + class_grape_1);
        System.out.println("grape_0对象的字节码文件对象是：" + grape_0_class);
        System.out.println("--------------------------------------------------");
        
        //创建苹果类对象
        Apple apple_0 = new Apple();
        Apple apple_1 = new Apple();
        //获取苹果类的Class对象
        Class apple_0_class = apple_0.getClass();
        Class apple_1_class = apple_1.getClass();
        //比较通过苹果类不同对象获得的苹果类的Class文件有什么不同
        System.out.println("apple_0对象的字节码文件对象是：" + apple_0_class);
        System.out.println("apple_1对象的字节码文件对象是：" + apple_1_class);
    }
}

class Grape {}
class Apple {}
```

返回的结果为：

```
grape_0对象的字节码文件对象是：Class Grape
grape_1对象的字节码文件对象是：Class Grape
grape_0对象的字节码文件对象是：Class Grape
--------------------------------------------------
apple_0对象的字节码文件对象是：Class Apple
apple_1对象的字节码文件对象是：Class Apple
```

<h2>3.public String toString()</h2>
关于toString方法要注意一点 : 当我们直接输出一个对象时，默认调用toString方法。比如方法println一个实例对象instance，默认输出instance.toString()。有必要时可以重写该方法。 </br>

```
// toString() : 返回该对象的字符串表示（默认打印的是"全类名 + @ + 哈希码值的十六进制"）

public class toString_ {
    public static void main(String[] args) {
        //创建Animal类对象
        Animal animal_0 = new Animal();
        Animal animal_1 = new Animal();
        Animal animal_2 = new Animal();
        //toString() 方法的返回值类型为String类型（也可不做接收）
        String animal_0_string = animal_0.toString();
        System.out.println("animal_0对象的字符串表示是：" + animal_0_string);
        System.out.println(animal_0);
        System.out.println("------------------------------------------------");
        System.out.println("animal_1对象的字符串表示是：" + animal_1.toString());
        System.out.println("animal_2对象的字符串表示是：" + animal_2.toString());
    }
}

class Animal {}
```

返回的结果为：

```
animal_0对象的字符串表示是：Animal@4eec7777
Animal@4eec7777
------------------------------------------------
animal_1对象的字符串表示是：Animal@682a02eb
animal_2对象的字符串表示是：Animal@3d045e70
```

<h2>4.public boolean equals(Object obj)</h2>

Object类中的equals()方法默认比较的是两个对象的引用。有必要时可以重写该方法。

```
// equals() : 返回其他某个对象是否与此对象“相等”（默认情况下比较的是两个对象的引用）
 
public class Equals_ {
    public static void main(String[] args) {
        //创建教师类对象
        Teacher teacher_0 = new Teacher();
        Teacher teacher_1 = new Teacher();
        //通过对象调用equals() 方法
        System.out.println("teacher_0和teacher_1是一个对象吗？" + teacher_0.equals(teacher_1));
        System.out.println("teacher_0和teacher_0是一个对象吗？" + teacher_0.equals(teacher_0));
    }
}

class Teacher {}
```
输出结果：

```
teacher_0和teacher_1是一个对象吗？ false
teacher_0和teacher_0是一个对象吗？ true
```

<h2>其余方法待补充，基础阶段暂时不会用到</h2>
