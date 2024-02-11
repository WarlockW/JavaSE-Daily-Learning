在Java中，==和equals()是两个用于比较对象或值是否相等的操作符和方法，但它们之间存在一些重要的区别。</br>
</br>
1.性质不同：</br>
==是一个比较运算符，用于比较两个基本数据类型或对象引用的值是否相等。而equals()是一个方法，用于比较两个对象的内容是否相等。</br>
```
int a = 10;  
int b = 20;
int c = 10;  
  
// 使用 == 比较基本数据类型  
System.out.println("a == b: " + (a == b)); // 输出 false
System.out.println("a == c: " + (a == c)); // 输出 true
// 使用 equals 比较基本数据类型
System.out.println("a equals b: " + (a.equals(b))); // 输出 false
System.out.println("a equals c: " + (a.equals(c))); // 输出 true
```

2.用途不同：</br>
==运算符：</br>
当用于比较基本数据类型时，它比较的是两个值是否相等。</br>
当用于比较对象时，它比较的是两个对象的引用是否相同，即是否指向内存中的同一个对象。</br>
</br>
equals()方法：</br>
equals()方法被重写后，通常用于比较两个对象的内容是否相等。如果不重写equals()方法，那么它的行为与==相同，即比较的是对象的引用。</br>
equals()方法不能用于基本数据类型的比较。</br>
</br>
3.默认行为：</br>
==的默认行为是比较两个变量的值或内存地址。</br>
equals()的默认行为依赖于类的实现。在Object类中，equals()的实现与==相同，但许多类（如String、Integer等）都重写了equals()方法以提供更有意义的比较。</br>
</br>
4.空值处理：</br>
使用==比较一个对象和一个null值时，结果总是false。</br>
使用equals()方法比较一个对象和一个null值时，会抛出NullPointerException，除非该方法被重写以处理这种情况。</br>
</br>
5.可重写性：</br>
==运算符不能被重写。</br>
equals()方法可以被重写以提供自定义的比较逻辑。</br>
在比较对象时，通常建议使用equals()方法而不是==运算符，除非你确定要比较的是对象的引用而不是内容。这是因为equals()方法提供了更灵活和有意义的比较方式，特别是在处理自定义对象时。</br>
