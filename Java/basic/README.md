# 基础

### 1、基础数据类型

### 2、基础数据类型和包装类型的区别

Java中的基础类型和基础类型的包装类的主要区别在于两方面：

1. 数据类型：基础类型是Java语言中最基本的数据类型，包括byte、short、int、long、float、double、boolean和char。基础类型的包装类则是为每个基础类型提供的一个对应的类，例如Integer对应int，Float对应float，Boolean对应boolean等。
2. 特性：基础类型的包装类具有一些特殊的功能，例如提供了转换为字符串、转换为其他进制、常量值等。此外，基础类型的包装类还可以作为Java集合框架中的元素类型，以及作为泛型类型参数等。

基础类型的包装类通常用于实现需要操作基础类型的方法，例如实现泛型算法、在集合中存储基础类型等。在Java中，基础类型的包装类也提供了许多便捷的方法，例如在字符串和基础类型之间进行转换，或者将基础类型转换为其他进制等。

3、Integer a = 125会发生什么

被编译器转换为Integer a = Integer.valueOf(125),125处于默认的常量池内，所以会引用常量池中的对象。

### 3、异常体系

![Java异常体系](https://pdai.tech/images/java/java-basic-exception-1.png)



### 4、Java的HashMap为什么使用红黑树的数据结构？

红黑树是一种自平衡的二叉搜索树，相比链表，可以在O(logN)的时间复杂度内进行插入、删除、查找等操作，因此能够在保证HashMap操作的时间复杂度不变的前提下，提高HashMap的查询性能。

### 5、HashMap的容量为什么要采用2的幂次方？

在 HashMap 中，使用长度为 n 的数组来存储数据，当存储数据的个数超过了数组长度时，需要对数组进行扩容，一般情况下将数组长度扩充为原来的两倍。这个做法是为了提高 HashMap 的存取效率，同时也是为了让哈希值均匀分布在数组中。

由于哈希函数的存在，元素的键（key）被映射到数组下标（index），为了使元素分布均匀，数组的长度需要是 2 的幂次方。这是因为，当数组长度为 2 的幂次方时，元素的哈希值和数组下标的关系可以用位运算来表示，而位运算比除法和取模运算更快，从而提高了 HashMap 的性能。同时，当数组长度为 2 的幂次方时，数组的容量减 1 的二进制表示每一位都是 1，这样在进行哈希函数计算时，可以通过位运算取代取模运算，进一步提高了性能。

### 6、HashMap的底层原理

Java中的HashMap是一种哈希表数据结构，其底层是由一个数组和链表/红黑树（JDK1.8之后）组成。其中数组中的每个元素都是一个链表/红黑树的头结点，每个节点保存着一个键值对（key-value）。

当需要添加键值对时，首先会通过key的哈希值和一个位运算得到该元素在数组中的索引，然后在对应的链表/红黑树中查找key是否已经存在，如果存在则替换该节点的value，如果不存在则在链表/红黑树的尾部添加一个新节点。当链表长度达到一定阈值时（默认为8），该链表就会转化为红黑树，以加快查找效率。

在查询时，首先会根据key的哈希值和位运算得到数组中对应的索引，然后在链表/红黑树中查找是否存在该key，如果存在则返回相应的value，否则返回null。

需要注意的是，当哈希冲突时（即不同的key具有相同的哈希值），会通过链表/红黑树来解决冲突，但如果哈希冲突过于频繁，会导致链表/红黑树过长，从而降低了哈希表的效率。因此，为了保证哈希表的性能，需要通过调整哈希表的容量（即数组大小）和扩容机制来减少哈希冲突的发生。

### 7、为什么选择红黑树而不是平衡查找树

红黑树和平衡查找树都是为了解决在树形结构中的节点长度不平衡的问题，但它们之间还是有区别的。

平衡查找树是指保持左右子树高度差不超过1的树形结构，比如AVL树、红黑树等。平衡查找树的优点是查找、插入、删除操作的时间复杂度都可以做到O(log n)，但缺点是需要频繁调整节点，导致插入和删除的时间复杂度比较高。

红黑树是一种近似平衡的二叉查找树，它的高度近似log2(n)，但是它比平衡查找树的调整要简单，所以在实际应用中，红黑树比平衡查找树使用更广泛。

另外，相比于平衡查找树，红黑树的节点结构更加简单，实现起来也更加容易。而且，红黑树的高度比较矮，可以更好地利用CPU缓存，提高查找的效率。因此，在Java中，HashMap中采用了红黑树来优化查找效率。

### 8、什么是Java中的多态？它的实现方式是什么？

多态是指在Java中，子类可以重写父类的方法，调用这个方法时会根据实际的对象类型来执行不同的实现代码，从而实现不同对象的多种形态展现。这种机制使得程序具有更强的灵活性和可扩展性，提高了代码的重用性和维护性。在Java中，多态的实现主要是通过继承和接口来实现的。

### 9、什么是Java中的注解？它的作用是什么？

Java中注解（Annotation）是一种元数据，用于为代码元素（如类、方法、字段、参数等）添加标记和信息。注解通过元数据的方式为Java源代码提供了额外的信息，但并不直接影响程序的执行。注解可以用于生成文档、编译时检查、运行时的动态处理等场景。

注解的作用主要有以下几个方面：

提供元数据信息，用于编写文档或代码分析。
编译时检查，用于检查代码的正确性，如@SuppressWarnings注解可以用于关闭编译器的警告。
运行时动态处理，用于在程序运行时动态生成代码或进行特殊处理。
配合其他框架使用，如Spring框架中的@Service、@Autowired、@RequestMapping等注解用于定义服务、自动注入、请求映射等功能。

### 10、什么是泛型？

泛型是Java中的一种编程机制，它可以让代码更加通用、灵活、安全。通过使用泛型，我们可以在编译时检查数据类型的正确性，从而在运行时避免了类型转换异常和其他类型相关的运行时错误。同时，泛型还可以提高代码的可读性和可维护性，使得代码更加简洁。在使用泛型时，我们可以使用类型参数来指定数据类型，使得代码可以处理各种类型的数据，而无需针对每种数据类型都编写一份代码。

### 11、字节流和字符流

字节流和字符流是Java中的I/O操作中的两种不同的流。主要区别如下：

- 数据类型不同：字节流以字节为单位进行输入输出，而字符流则以字符为单位进行输入输出；
- 字符编码不同：字节流可以接受所有类型的二进制数据，包括图像、音频、视频等等，而字符流只能处理字符数据，会对其进行编码转换；
- 缓冲方式不同：字节流可以使用字节缓冲区，字符流可以使用字符缓冲区，不同类型的缓冲区底层的实现不同，字符缓冲区可以减少I/O操作的次数；
- 读写单位不同：字节流每次读写一个字节或者一个字节数组，字符流每次读写一个字符或者一个字符数组。

### 12、多态的常见形式

多态在面向对象编程中是一种重要的概念，常见的多态形式包括：

1. 方法重写（Override）：子类可以重写父类的方法，提供自己的实现。在程序运行时，根据对象的实际类型来调用相应的方法。

2. 方法重载（Overload）：同一个类中可以定义多个同名方法，但参数列表不同。在程序编译时，根据方法的参数类型和数量来确定调用哪个方法。

3. 接口实现（Interface Implementation）：一个类实现了一个或多个接口，可以根据接口类型引用对象，调用接口中定义的方法。

4. 抽象类继承（Abstract Class Inheritance）：子类可以继承抽象类，并实现抽象类中的抽象方法。在程序中可以使用抽象类类型引用对象，并调用子类实现的方法。

这些形式都体现了多态的概念，即同一类型的对象在不同的上下文中表现出不同的行为。多态使得代码更加灵活、可扩展，并提高了代码的可读性和可维护性。