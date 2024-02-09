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
