for each循环一般用于遍历数组、集合中的所有元素，类似于python中的for i in list <br/>

```
public class ForEachTest{
  public static void main(Sting[] args){
      String[] names = new String[]{
      "张三",
      "李四",
      "王五",
    };

    // 使用for each结构遍历数组中所有元素
    for(String name:names){
      System.out.println(name);
    }
  }
}
```

可变形参的格式为 【数据类型】...【形参名称】，比如 String...names。可变形参传入方法后，可以视为数组进行处理，也可以跟上文提到的for each循环一起使用 <br/>

```
public class VariableVarsTest {
    static void printnames(String...names){
        for(String name:names){
            System.out.println(name);
        }
    }

    public static void main(String[] args){
        printnames("张三","李四","王五");
    }
}
```
