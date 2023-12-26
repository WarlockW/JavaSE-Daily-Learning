<h1>关于java文件名称以及对应public修饰类的理解</h1>
JAVA是强类型语言，也就是说一些代码都需要封装在类中，这一点跟python不同 <br/>
一个JAVA文件只能有一个类被public修饰，被public修饰的类会对外暴露，因此该java文件的名称与该被public修饰的类同名<br/>
JAVA代码必须要有主函数才能正常执行，且主函数必须由public static void main修饰 <br/>

```
// 源代码
public class HelloWorld {
    public static void main(String[] args){
        System.out.println("First Program -- Hello World！");
    }
}
```

```
// 返回内容
First Program -- Hello World！
```
