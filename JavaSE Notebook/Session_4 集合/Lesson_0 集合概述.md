<h1>集合的主要三种类型</h1>
List：一种有序列表的集合，例如，按索引排列的Student的List；<br>
Set：一种保证没有重复元素的集合，例如，所有无重复名称的Student的Set；<br>
Map：一种通过键值（key-value）查找的映射表集合，例如，根据Student的name查找对应Student的Map。<br>
<br>
如果是集合类型----<br>
有List和Set供我们选择。List的特点是插入有序的，元素是可重复的。Set的特点是插入无序的，元素不可重复的。至于选择哪个实现类来作为我们的存储容器，我们就得看具体的应用场景。是希望可重复的就得用List，选择List下常见的子类。是希望不可重复，选择Set下常见的子类。<br>
<br>
如果是Key-Value型----<br>
那我们会选择Map。如果要保持插入顺序的，我们可以选择LinkedHashMap(底层是链表，增减快查询慢)，如果不需要则选择HashMap，如果要排序则选择TreeMap（底层是红黑树）。<br>
<br>
补充内容----常见的数据结构<br>
数据结构指的是数据的组存储方式，不同的数据结构有不同的特点。<br>
数组结构（ArrayList底层结构）----查询快，增删慢<br>
链表结构（LinkedList底层结构）----查询慢，增删快<br>
栈和队列----栈：先进后出(子弹夹,杯子)；队列：先进先出(排队,管子)<br>

<h1>List类与Set类</h1>

![屏幕截图 2024-03-26 102524](https://github.com/WarlockW/JavaSE_Daily_Learning/assets/64346345/08b819cc-c2c7-4fc4-8c77-8279eb4601ab)

通常使用collection接口实现List和Set功能
对于List：<br>
1.ArrayList（最常用）：底层数据结构是数组，查询快，增删慢，线程不安全，效率高，可以存储重复元素。<br>
2.LinkedList 底层数据结构是链表，查询慢，增删快，线程不安全，效率高，可以存储重复元素。<br>
3.Vector:底层数据结构是数组，查询快，增删慢，线程安全，效率低，可以存储重复元素。<br>
<br>
对于Set：<br>

<h1>Map类</h1>

![屏幕截图 2024-03-26 103556](https://github.com/WarlockW/JavaSE_Daily_Learning/assets/64346345/a20ff237-b6ac-40c0-aafd-2f2ab38956c4)
