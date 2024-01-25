<h1>jar包相关内容</h1>
<h2>包名的命名规范</h2>
<h2>jar包的理解</h2>
Java生成的JAR文件（Java Archive）通常包含编译后的.class文件。这些.class文件是Java源代码经过编译后的字节码文件。<br/>
当在Java项目中编译源代码时，编译器（例如javac）将源代码转换为字节码，并保存在.class文件中。然后，可以将这些.class文件打包到一个或多个JAR文件中。<br/>
一个JAR文件本质上是一个ZIP文件，它使用特定的目录结构来组织内部的文件。在一个标准的JAR文件中，通常会找到一个META-INF目录，其中包含有关JAR文件的元数据（例如MANIFEST.MF文件），以及一个或多个包含.class文件的目录。<br/>
要创建JAR文件，可以使用jar命令行工具，该工具是Java Development Kit (JDK) 的一部分。例如，要创建一个名为myapp.jar的JAR文件，你可以使用以下命令：<br/>
<h2>.MF文件的说明</h2>

<h1>package关键字相关内容</h1>
包与包下面的子包----

<h1>import关键字相关内容</h1>
import语句非必需，也可以写全路径
不能用import的情况----两个子包中有名字相同的类
import static的用处----import引入的是“类名”，在代码中引用时写的是【类名.类成员名称】；import static引入的是“类的静态成员名”，在代码中引用时可以直接写【静态成员名称】。总的来说两种引入都是为了减少代码量
