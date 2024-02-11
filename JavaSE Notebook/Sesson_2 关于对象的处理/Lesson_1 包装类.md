!!!【个人理解】包装类主要是在某些情况下将几个基本类型写成类的形式（几种基础数据类型比如int、short类的形式）！！！</br>
包装类（Wrapper Classes）是Java提供的一组类，用于将基本数据类型封装为对象。这样做的好处是可以将基本数据类型当作对象来处理，这样就可以调用对象的方法。Java为每一个基本数据类型都提供了一个对应的包装类。</br>

```
// 基本上都是基本数据类型的首字母大写
byte -> Byte
short -> Short
int -> Integer
long -> Long
float -> Float
double -> Double
char -> Character
boolean -> Boolean
```

使用包装类的实际场景：</br>

```
public class Recursive {
    public static void main(){
        // 把一个基础数据类型赋给Integet对象
        Integer inObj = 5;
        // 把一个基础数据类型赋给Objcet对象
        Object boolObj = true;

        // 把上述Integer对象再赋给int类型，无报错
        int it = inObj;
        // 把上述Objcet对象再赋给boolen类型，无报错
        //!!!在这里用到了包装类以及instanceof jdk17引入的新特性
        if(boolObj instanceof Boolean bool){
                boolean b = bool;
                System.out.println(b);
            }
        }
    }

```
