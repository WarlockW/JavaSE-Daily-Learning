for each循环一般用于遍历数组、集合中的所有元素，类似于python中的for i in list <br/>

```
public class ForEachTest{
  public static void main(Sting[] args){
      String[] names = {
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
