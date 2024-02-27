<h1>Scanner类</h1>
Scanner 主要提供了两个方法来扫描输入 。

```
hasNextXxx(): 
是否还有下一个输入项， 其中 Xxx可以是 Int、 Long等代表基本数据类型的字符串。
如果只是判断是否包含下一个字符串 ，则直接使用 hasNext()。
```

```
nextXxx():
获取下一个输入工页。 Xxx的含义与前一个方法中的Xxx相同。
在默认情况下， Scanner 使用空白(包括空格、 Tab 空白、回车)作为多个输入项之间的分隔符。
```

Scanner不仅能读取用户的键盘输入，还可以读取文件输入。只要在创建 Scanner对象时传入一个 File对象作为参数，就可以让 Scanner读取该文件的内容。
```
import java.io.File;
import java.util.Scanner;

public class ScannerTest{
    public static void main(String[] args)throws Exception{
        Scanner sc = new Scanner(new File("/Users/warlockw/Desktop/L4jTest/src/main/java/1.txt"));
        while (sc.hasNextLine()){
            System.out.println(sc.nextLine());
        }
    }
}
```
