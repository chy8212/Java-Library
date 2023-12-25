#### 简介


>了解常见操作的本质，这些顶层接口对应的数据结构，有哪些抽象的特点，每个接口有哪些实现，类，a实现和b实现有什么区别，每个实现有什么区别。底层结构，方法操作怎么实现，能说出来；put的的时候怎么扩容；某个具体的函数或方法怎么实现的。
google Guava

JDK：Java Development Kit
JRE：Java Runtime Environment
JDK除了包含JRE，还提供了编译器、调试器等开发工具。
一个Java源码只能定义一个`public`类型的class，并且class名称和文件名要完全一致；

编译成字节码文件的命令：javac Hello.java ——Hello.class  文件
运行  java Hello(Hello.java)

并非纯粹的面向对象，还有静态变量和方法针对类的；
四个特性
封装：模块、类、方法、权限修饰、内部类

IDE
- IDE是集成开发环境：Integrated Development Environment
- 好处在于，可以把编写代码、组织项目、编译、运行、调试等放到一个环境中运行，能极大地提高开发效率。
	- 自动提示
	- 自动重新编译和重新运行；
	- 方便断点调试

### 程序基础
- 程序基本结构
	- 类以大写字母开头大驼峰；方法以小写字母开头小驼峰，属性名用蛇形，例如x_1；
	- Java入口程序规定的方法必须是静态方法，方法名必须为`main`，括号内的参数必须是String数组。
	- 注释：
		单行、多行、特殊多行（/\*\*.....\*/，中间每行以星号开头，写在类和方法的定义处，可以用于自动创建文档。）
	- 变量与数据类型
		- Java提供了两种变量类型：基本类型和引用类型（对象在内存的地址，）
		- 基本数据类型
			整形：byte，short，int，long(8字节)
			浮点数类型：float（需加后缀f，最大表示3.4x10^38），double(8字节)
			字符类型：char(2字节，每个保存一个Unicode字符，也可用\\u+编码表示字符)；
			布尔类型：boolean(4字节)
		- var关键字：创建变量时，用于在简写替代较长的变量类型，自动识别；
		- 常量名通常全部大写。变量小驼峰；
		- final关键字：变量或方法只可赋值一次，不可重写；类不可继承
		- 引用类型
			- 判断方法用equals（）；
			- 字符串
				- 引用类型；
				- 字符串连接：+；
			- 数组类型
				- 定义：
					- Type[]  Variable = new  Type[长度]； 
					- Type[]  Variable = new  Type[]{ ,,,};
					- type[] variable={ ,,,}
	- 运算
		- 除得整余；
		- 超出范围溢出；
		- 移位等于乘除；
		- 与或非异或 & | ~ ^
		- 整数运算：结果永远是精确的、除数为0会报错；
		- 浮点数运算
			- 浮点数常常无法精确表示易产生误差（换算二进制是无限循环小数）；
			- 大小比较方法：差值小于极小数；
			- 除数为0不报错返回特殊值；NaN、+-Infinity；
			- 转整形溢出时结果为整形最大值；
			- 需四舍五入：浮点数+0.5，再强转；
	- 类型自动提升与强制转型
		- 参与运算的两个数类型不一致，那么计算结果为较大类型
		- 超出范围的强制转型会直接丢弃高位；


- 数组操作
	- foreach：for(int n: arr){function(n)}  n直接拿到元素；
	- 打印数组：
		- foreach挨个输出；
		- 直接输出Arrays.toString(arr)；
		- 多维数组打印：Arrays.deepToString()；
	- 命令行参数
		- Java程序的入口是main方法，main接受一个命令行参数，String[]数组；命令行参数由JVM接收用户输入并传给main方法
		- 前提该程序必须在命令行执行；java Main -version；
- 流程控制
	- 输入输出
		- System.out.println()，输出并换行；System.out.print() 仅输出；
		- 格式化输出：System.out.printf()；使用通配符将参数格式化结果；
		- 输入：
			- 导入java.util.Scanner类；
			- 创建Scanner对象并传入System.in；直接用System.in(标准输入流)读取输入代码复杂；
			- Scanner scanner = new Scanner(System.in)；
			- scanner对象读取。  
				- scanner.nextLine()读取整数；
				- scanner.nextLine()读取这一行为字符串；

### 面向对象基础
- 方法
	- 类class的字段需私有，用public修饰的set和get方法操作字段；
	- this变量：始终指向当前实例；
	- 方法参数
		- 可变参数 String... names：表示输入的参数看做字符串数组；
- 构造方法
	- 无返回值，public，类名  public Person(){}
	- 调用构造要用new；
	- 多构造方法
	- 默认构造方法
- 方法重载
	- 同名不同参数
- 继承
	- class 子 extends 父 { } 
	- 父类=超类=基类=super关键字；子类=扩展类；
	- 不能访问父类的private；可访问protected；
	- 如果父类没有默认的构造方法（即有自定义构造），子类就必须显式调用super()并给出参数以便让编译器定位到父类的一个合适的构造方法。
	- 子类_不会继承_任何父类的构造方法。子类默认的构造方法是编译器自动生成的，不是继承的。
	- 阻止继承
		- java 15 可用sealed修饰class，并通过permits明确写出能够从该class继承的子类名称。public sealed class Shape permits Rect, Circle, Triangle {}
	- 向上转型
		- 一个子类类型安全地变为父类类型的赋值，被称为向上转型；
		- 引用类型为父类的变量，指向子类的实例；Person p1 = new Student(); 
	- 向下转型
		- 把一个父类类型强制转型为子类类型：Student s1 = (Student) p1; 
		- 可能会失败；可预先判断 类型；
		- 用instanceof判断是否是：p instanceof Person；
	- 区分继承和组合
- 多态
	- 指，针对某个类型的方法调用，其真正执行的方法取决于运行时期实际类型的方法；
	- 覆写：子类定义了父类的同名方法；
	- 加上@Override可以让编译器帮助检查是否进行了正确的覆写；
	- 多态即：实例方法调用是基于运行时的实际类型的动态调用，而非变量的声明类型。即实际类型为Student，引用类型为Person的变量，会调用实际类型Student的同名方法；
	- 强大的功能，就是允许添加更多类型的子类实现功能扩展，却不需要修改基于父类的代码；
	- 子类中重写的方法里可以用super来代替父类名称来调用；
	- 如果一个父类不允许子类对它的某个方法进行覆写，可以把该方法标记为`final`；
	- 用`final`修饰的类不能被继承；
	- 用`final`修饰的字段在初始化后不能被修改；否则报错；
	- 可以在构造方法中初始化final字段；
- 抽象类
	- 抽象方法，本身没有实现任何方法语句。因为这个抽象方法本身是无法执行的；无法实例化一个抽象类；具有抽象方法的类无法实例化；
	- 本身被设计成只能用于被继承；强迫子类实现其定义的抽象方法；相当于定义了“规范”。
	- 如果父类的方法本身不需要实现任何功能，仅仅是为了定义方法签名，目的是让子类去覆写它，那么，可以把父类的方法声明为抽象方法
	- 抽象方法本质上是定义接口规范：即规定高层类的接口，从而保证所有子类都有相同的接口实现，这样，多态就能发挥出威力。
	- 抽象类的普通方法可以访问实例字段；
	- 面向抽象编程
		-  指尽量引用高层类型，避免引用实际子类型的方式，Person s = new Student();
		- 本质：
			- 上层代码只定义规范
			- 不需要子类就可以实现业务逻辑（正常编译）；
			- 具体的业务逻辑由不同的子类实现，调用者并不关心。
- 接口
	- 无字段，只有抽象方法的类，可以有default方法；可以有静态字段且必为public static final；
	- 当一个具体的`class`去实现一个接口时，需要使用`implements`关键字；
	- 一个类可以实现多个接口；
	- java的接口特指一个定义，表示一个接口类型和一组方法签名；编程接口泛指接口规范，如方法签名，数据格式，网络协议等；
	- 接口可以继承接口，用extends
	- 继承关系
		- 公共逻辑适合放在abstract class中；
		- 具体逻辑放到各个子类，而接口层次代表抽象程度；
	- default方法
		- 实现类可以不必覆写default方法。
		- 目的：需要给接口新增一个方法时，避免修改全部子类，只有需要重写的重写；
- 静态字段和静态方法
	- 静态字段：
		- 所有实例都会共享该字段；实例对象并没有静态字段，要用类名来访问；
		- 接口的静态字段
	- 静态方法：
		- 属于class，无法访问this变量，也无法访问实例字段，它只能访问静态字段；
		- 静态方法经常用于工具类，如Arrays.sort()；
		- 也经常用于辅助方法
- 包
	- 不用public、protected、private修饰的字段和方法就是包作用域
	- 导入
		- import static很少使用。导入一个类的静态字段和静态方法；
- 作用域
	- public：所有可见
	- private：类内部可见，包括内嵌类；
	- protect ：作用于继承，子类可见；
- 内部类
	- Inner Class定义在另一个类的内部；
		- 该内部类的实例不能单独存在，必须依附一个外部类的实例；
		- 可以访问外部类的private；
	- Anonymous Class匿名类
		- 在另一个类的方法中定义；
		- 可以访问外部类的private；
		- 隐含地持有Outer.this实例；
	- 静态内部类
		- 一个完全独立的类，不再依附；
		- 可以访问外部类的private；
- classpath和jar
	- classpath
		- 是JVM用到的一个环境变量，它用来指示JVM如何搜索class。指示去哪搜索对应的Hello.class文件；
		- 一组目录的集合，设置的搜索路径与操作系统相关。
		- classpath的设定方法有两种：
			- 在系统环境变量中设置classpath环境变量，不推荐；——污染整个系统环境
			- 在系统环境变量中设置classpath环境变量，不推荐；
- class版本
	- Java 8：指JDK的版本，也就是JVM的版本；
	- 每个版本的JVM，它能执行的class文件版本也不同
	- 高版本的JDK可编译输出低版本兼容的class文件，但低版本的JDK可能不存在高版本JDK添加的类和方法，导致运行时报错。
	- 运行时使用哪个JDK版本，编译时就尽量使用同一版本编译源码。
- 模块
	- jar文件就是class文件的容器。
	- 模块的重要作用就是声明依赖关系，进行管理；
	- 使用模块可以按需打包JRE；
	- 使用模块对类的访问权限有了进一步限制。

### java核心类
- 字符串和编码
	- String
		- 本质是类，是一个引用类型，内部是字符数组；
		- 搜索子串：
			- "Hello".indexOf("l"); // 2
			- "Hello".lastIndexOf("l"); // 3
			- "Hello".startsWith("He"); // true
			- "Hello".endsWith("lo"); // true
		- 提取子串
			- "Hello".substring(2); // "llo"
			- "Hello".substring(2, 4); "ll"
		- 比较：
			- equals()，
			- equalsIgnoreCase忽略大小写
		- 去除首尾空白字符：
			- trim()
			- strip()：类似中文的空格字符`\u3000`也会被移除；
		- 为空和空白字符串
			- "".isEmpty(); // true，因为字符串长度为0
			- "  ".isEmpty(); // false，因为字符串长度不为0
			- "  \n".isBlank(); // true，因为只包含空白字符
			- " Hello ".isBlank(); // false，因为包含非空白字符
		- 替换子串
			- replace
			- 正则替换
		- 分割字符串
			- split()
		- 拼接字符串
			- join()
		- 格式化字符串
			- formatted()
			- format()
		- 类型转换
			- valueOf()
			- parseInt
			- parseBoolean
			- getInteger(String)
		- 转换为char[]
			- toCharArray()
	- 编码
		- Java使用Unicode编码表示String和char；
		- 转换编码就是将String和byte[]转换，需要指定编码；
		- 转换为byte[]时，始终优先考虑UTF-8编码。
- StringBuilder
	- 拼接字符串时都会不断创建新对象，会浪费内存影响GC效率；
	- 为了能高效拼接字符串，可用StringBuilder，
	- 是一个可变对象，可以预分配缓冲区，这样，往StringBuilder中新增字符时，不会创建新的临时对象：
	- 可以支持链式操作，实现链式操作的关键是返回实例本身；
	- StringBuffer是StringBuilder的线程安全版本，但现在很少使用；
- 包装类型
	- 引用类型可以赋值为null，基本类型不能赋值为null
	- Integer类，只包含一个实例字段int
	- int和Integer可以互相转换
		- 自动装箱：int变为Integer，只发生在编译阶段，目的是为了少写代码。
		- 自动拆箱：只发生在编译阶段，目的是为了少写代码。
	- 所有的包装类型都是不变类，内部final修饰；
	- 能创建“新”对象的静态方法称为静态工厂方法。Integer.valueOf()就是静态工厂方法，它尽可能地返回缓存的实例以节省内存。
	- 进制转换：
	- 处理无符号整型：
- 枚举类
	- 通过关键字enum实现的，我们只需依次列出枚举的常量名
	- 被编译器编译为final class Xxx extends Enum { … }；
	- enum的比较：可以用==
	- 枚举类：没有任何区别，特点：
		- 定义的enum类型总是继承自java.lang.Enum，且无法被继承；
		- 只能定义出enum的实例，而无法通过new操作符创建enum的实例；
		- 定义的每个实例都是引用类型的唯一实例；
		- 可以将enum类型用于switch语句。
	- 通过name()获取常量定义的字符串，注意不要使用toString()；
	- 通过ordinal()返回常量定义的顺序（无实质意义）；
	- 可以为enum编写构造方法、字段和方法
	- enum的构造方法要声明为private，字段强烈建议声明为final；
	- enum适合用在switch语句中。

### 集合
- 也叫容器，主要由两大接口派生
	- java.util包中Collection接口，放单一元素；包含3个子接口List、Set 和 Queue；
	- Map接口
- 集合类Collection，包含3个子接口List、Set 和 Queue，定义在java.util包中，支持泛型，
- 主要提供了3种集合类，包括List，Set和Map。
- Java集合使用统一的Iterator遍历，尽量不要使用遗留接口。

##### 使用List
- 元素是有序的、可重复的。
- 一种有序列表，是接口。
- 实现类：
	- ArrayList（内部是动态数组实现），`Object[]` 数组
	- LinkedList（内部是链表实现），双向链表；
	- Vector（内部实现类似于ArrayList）；`Object[]` 数组
- 主要接口方法
	- 在末尾添加一个元素：       add(item)
	- 在指定索引添加一个元素：add(i, item)
	- 删除指定索引的元素：       item remove(i)
	- 删除某个元素：                  remove(item)
	- 获取指定索引的元素：       get(i)
	- 获取链表大小（包含元素的个数）： size()
	- 是否包含元素： contains（item）
	- 返回索引：indexOf（item）
- 常见操作
	- 创建：List< type> list =【List.of(1, 2, 5);不接受null值】【new  ArrayList<>(); 】
	- 遍历
		- for循环配合 get (index) 方法，不推荐代码复杂且速度慢；
		- 用迭代器Iterator对象遍历数组，对不同的List实现也不一样；Iterator对象是由List的实例调用iterator()方法时创建的；
			- for (Iterator< String> it = list.iterator(); it.hasNext(); ) {
					String s = it.next();
					System.out.println(s);
				}
				- for (String s : list) {            // foreach方式；
					System.out.println(s);
			}
	- List和Array转换
		- LIst变数组：toArray()方法，返回设定类型的数组；  Integer[]  arr = list.toArray( new Integer[n] )  泛型参数`<T>`可与List类型不同；
		- 进化为：
			- Integer[] array = list.toArray(new Integer[list.size()]);
			- 或Integer[] array = list.toArray(Integer[]::new);
		- 数组变List：List< Integer > list = List.of(array);


- 编写equals方法
	- 在List中查找元素时，List的实现类通过元素的equals()方法比较两个元素是否相等，因此，放入的元素必须正确覆写equals()方法；
	- String、Integer等已经覆写了equals()方法；
	- 如果不在List中查找元素，就不必覆写equals()方法。
	- 正确编写方法：
		先确定实例“相等”的逻辑，即哪些字段相等，就认为实例相等；
		用instanceof判断传入的待比较的Object是不是当前类型，如果是，继续比较，否则，返回false；
		对引用类型用Objects.equals()比较，对基本类型直接用== 比较。

##### 使用Map
- key-value键值对的一种集合，key无序不重复，value无序可重复；
- 常用方法：
	- Map<String, Integer> map = new HashMap<>();
	- get (key)
	- put (key value) 
	- 遍历
		- for (String key : map.keySet())； foreach遍历keySet中key的不重复集合；
		- for (  Map.Entry<String, Integer>   entry : map.entrySet()   )   entrySet()集合是键值对集合；
- 实现类
	- HashMap常用
		- jdk1.8之前是数组+链表；jdk1.8之后链表长度大于阈值时会转化成红黑树，可减少搜索时间；
		- 内部用key的值计算哈希值，即索引，再根据索引插入或找到value；
	- LinkedHashMap子类
		- 继承自HashMap；
		- 数组+链表或红黑树，额外增加一条双向链表，保持键值对的插入顺序以及一些操作；
	- Hashtable类
		- 数组+链表组成的、基本不用；
	- TreeMap类
		- 是SortedMap子接口的实现类，是有序的，底层是红黑树（自平衡的排序二叉树）；
		- 在内部会对Key进行排序；保证遍历时以Key的顺序来进行排序；
		- key必须实现 Comparable 比较接口或者传入Comparator。若未实现则在创建TreeMap时需指定自定义排序算法。String、Integer已实现；Value没有要求；
		- 要严格按照compare()规范实现比较逻辑，否则，TreeMap将不能正常工作。
	- ConcurrentHashMap类
		- 保证线程安全；
	- 使用EnumMap
		- key的对象是enum类型；
		- 内部是数组，根据enum类型的key直接定位到内部数组的索引，并不需要计算hashCode()；
		- Map<DayOfWeek, String> map = new EnumMap<>(DayOfWeek.class);
		- 
	
	


-  编写equals和hashCode
	- 注意Map中作比较是用equals实现的，如两个相同的key看起来一样但实际是两个对象；
	- 正确使用Map必须保证：
		- 作为key的对象必须正确覆写equals()方法；
		- 作为key的对象还必须正确覆写hashCode()方法；，即key是调用该方法来找到value，所以实际相同的key对象的hashCode需相同；
	- 实现hashCode()方法可以通过Objects.hashCode()辅助方法实现。




- 使用Properties
	- Properties表示一组配置，本质是Hashtable，用于读取配置文件；
	- 配置文件：Key-Valu形式一般为String-String类型，可以用Map<String, String>表示；
	- 用Properties读取配置文件，一共有三步：
		- 创建Properties实例；Properties props = new Properties();
		- 调用load()读取文件；props.load(new java.io.FileInputStream(f)); 或props.load(getClass().getResourceAsStream("/common/setting.properties"));
		- 调用getProperty()获取具体配置。String filepath = props.getProperty("last_open_file");


##### 使用Set接口
- 元素唯一不重复的集合；
- 放入的元素都要正确实现equals()和hashCode()方法，否则该元素无法正确地放入Set；
- Set接口提供的方法：  （都返回boolean）
	- add (item)
	- remove (item)
	- contains (item)
- 实现类
	- HashSet
		- 常用实现类，无序的；
		- 基于 HashMap 包装后实现的，底层采用 HashMap 来保存元素；
	- TreeSet实现类；实现的是SortedSet子接口；
		- 有序的；
		- 红黑树(自平衡的排序二叉树)；
		- 和使用TreeMap的要求一样，添加的元素必须正确实现Comparable接口，如果没有实现Comparable接口，那么创建TreeSet时必须传入一个Comparator对象。
	- LinkedHashSet
		- HashSet的子类，内部是通过 LinkedHashMap 来实现的。


#### 使用Queue接口
- 元素有序的可重复的、按照特定的规则确定先后顺序的；
- 不要把null添加到队列中
- 接口提供的方法：
	- size()，队列长度
	- add&offer (item)，添加到队尾；
	- remove&poll ()，获取队首并删除；
	- element&peek ()，获取队首但不删除；
##### 使用PriorityQueue
- 优先队列，出队顺序总是获取优先级最高的元素；
- Object[] 数组来实现小顶堆基于堆实现的；
- 放入优先队列的元素，必须实现Comparable接口，PriorityQueue会根据元素的排序顺序决定出队的优先级。未实现需提供Comparator对象；
- 默认按元素比较的顺序排序，也可以通过Comparator自定义排序算法。
##### 使用Deque接口
- 双端队列；允许两头进两头出；
- 本质扩展自Queue
- 方法：
	- addLast(item) / offerLast(item)，添加到队尾；
	- addFirst(item)/ offerFirst(item)，添加到队首；
	- removeFirst()/pollFirst()  ,  队首取出删除；
	- getFirst()/peekFirst(),  队首取出不删除；
	- removeLast()/pollLast(), 队尾取出删除
	- getLast()/peekLast()，队尾取出不删除；
- 实现类有ArrayDeque和LinkedList。
	- LinkedList
		- Deque< String> d2 = new LinkedList<>();
		- 即是List，又是Queue，还是Deque，用特定的接口来引用；
#### 使用Stack接口
- 由于遗留类问题不能创建Stack接口，只能用Deque接口来“模拟”一个Stack；
- 不要使用遗留类Stack；
- Deque< Integer> stack = new LinkedList<>();
- 方法
	- 把元素压栈：push(E)；
	- 把栈顶的元素“弹出”：pop()；
	- 取栈顶元素但不弹出：peek()。
- 用Deque可以实现Stack的功能：
	- 把元素压栈：`push(E)`/`addFirst(E)`；
	- 把栈顶的元素“弹出”：`pop()`/`removeFirst()`；
	- 取栈顶元素但不弹出：`peek()`/`peekFirst()`
- Stack的常见用途
	- 方法调用栈，
		- 维护方法调用的层次，参数压栈——执行方法——返回值圧栈——出栈获得返回值；
		- 调用栈存在容量限制容易栈溢出，引发StackOverflowError
	- 对整数进行进制的转换就可以利用栈。
	- 计算中缀表达式
#### 使用Iterator
- 集合类都可以使用for each循环；
- 迭代器：通过Iterator对象遍历集合的模式；
- 好处：调用方总是以统一的方式遍历各种集合类型，而不必关心它们内部的存储结构。集合类返回的Iterator对象知道如何迭代。
- 自己编写的集合类使用for each需满足：
	- 集合类实现`Iterable`接口，该接口要求返回一个`Iterator`对象；
	- 用`Iterator`对象迭代集合内部数据。
	- 关键在于，集合类通过调用iterator()方法，返回一个Iterator对象，这个对象必须自己知道如何遍历该集合。
- Java提供了标准的迭代器模型，即集合类实现java.util.Iterable接口，返回java.util.Iterator实例；
#### 使用Collections
- JDK提供的工具类，位于java.util包中。它提供了一系列静态方法，能更方便地操作各种集合；
- 创建空集合；比返回null更好；不容易报错，面向对象设计的一个思路；返回空集合更合适；
- 创建单元素集合；当另一个接口只接受list，元素不可变在多线程情况下线程安全，两个线程可以同时修改造不会引发并发问题；程序更健壮；容易被别人改变；只希望给别人查找；
- 创建不可变集合；
- 排序／洗牌等操作。
- 排序

### 泛型
- 背景：当使用任何一种集合时，如ArrayList类，当存入不同类型的元素，都需要为每一种类型创建特定的ArrayList，对此制定了一个模板ArrayList< T>；实现编写一次模版，可以创建任意类型的`ArrayList`；
	- ArrayList< String> strList = new ArrayList< String>();
- 概念
	- 泛型就是定义的一种模板；
	- 向上转型：可以把ArrayList< Integer>向上转型为List< Integer>（T不能变！）

### Object类中的方法
- Class、hashcode、equals、clone、toString(哈希码)、notifyAll、wait
### String


### 常见问题

- 过程和对象的区别？
	- 问题拆解成方法；性能更好
	- 问题抽出对象，对象执行方法、复用扩展；性能上需要实例化等；
- 创建一个对象用什么运算符?对象实体与对象引用有何不同?
	- new，在内存中，引用指向实体，1~n；
- 对象的相等和引用相等的区别
	- 内存存放的内容和在内存中的地址
- 类没有声明构造方法，该程序能正确执行吗
	- 构造方法完成对象的初始化；
	- 会有默认不带参的构造；
	- 若重载了有参构造也需要额外写无参构造；
- 构造方法特点
	- 无void，同类名，实例化时自动执行；不能重写可重载；
- 三大特征
	- 封装
	- 继承，private只是拥有但无法访问；
	- 多态：父类的引用指向子类的实例。并在方法调用时取决于运行时的实际类型所属的方法；
- 接口和抽象类有什么共同点和区别？
	- 实例化、包含抽象、可以有默认default实现的方法；
	- 接口约束行为、实现多个接口、成员变量只能是 public static final有初始值；
	- 抽象代码复用、继承一个类；成员变量默认default子类可重新定义赋值；
- 深拷贝和浅拷贝
	- 创建新对象，完整复制整个对象所有内容，包括内部的对象；
	- 将原对象的引用复制，共享同一块内存空间；
	- 引用拷贝呢？引用拷贝就是两个不同的引用指向同一个对象。
- Object
	- 所有类的父类
- == 和 equals() 的区别
	- == 值比较，如内存地址等；
	- equals，只用于比较对象的属性内容；object类中的equals内部为== ，所以需要子类重写；string常量池的问题，创建字符串时存在则赋引用；
- hashCode() 有什么用？
	- 哈希码的作用是确定该对象在哈希表中的索引位置。
	- 其实， hashCode() 和 equals()都是用于比较两个对象是否相等。
	- 如把对象加入 HashSet 时；用hashcode判断是否存在重复的hashcode值相同的对象，有同code则再equals；
- 为什么两者同时都要
	- hashCode 帮助我们大大缩小了查找成本。
	- 两个对象的hashCode 值相等并不代表两个对象就相等。因此还需要equals；
	- 同code对象不同：因为哈希算法也许刚好会让多个对象传回相同的哈希值；
- 为什么重写 equals() 时必须重写 hashCode() 方法？
	- 因为当如果 `equals` 方法判断两个对象是相等的，那这两个对象的 `hashCode` 值也要相等。
	- 重写 equals() 时没有重写 hashCode()——判断两对象时导致equals相同hash值可不同

#### string
- String、StringBuffer、StringBuilder 的区别
	- 可变性：1不可变、23都继承AbstractStringBuilder，无final 和 private，还都提供方法修改
	- 线程安全：常量安全、加锁安全、无锁不安全
	- 性能：1改变就创新对象、2对自身进行修改、性能有提升但不安全；
	- 使用：数量少时、多线程大数据量、单线程大数据量
- String 为什么是不可变的
	- 使用 final 关键字不是原因，因为本质是数组，只是引用不变；
	- 数组是fianl且私有、无暴露操作修改；
	- string是fianl的不能继承进一步不可改变；
- 字符串拼接用“+” 还是 StringBuilder
	- + 本质上通过 StringBuilder 调用 append() 方法实现的，拼接完成之后调用 toString() 得到一个 String 对象 。
- 字符串常量池的作用
	- 避免字符串的重复创建：提升性能减少内存消耗；
- String s1 = new String("abc");这句话创建了几个字符串对象
	- 1或2；存在或不存在；分别常量池和堆；
- String#intern 方法有什么作用
	- 作用是将指定的字符串对象的引用保存在字符串常量池中
		- 
#### 集合
- 为什么使用集合
	- 支持不同类型和数量的对象+多样化的操作方式；
	- 相对于数组大小可变、支持泛型、内建算法；
	- 提高数据的存储和处理的灵活性；
- ArrayLIst与array区别
	- 动态大小；创建时不需要指定大小；
	- 支持泛型
	- 只能存储对象；基本数据类型也要用包装类；
	- 支持一些常见的操作插入删除遍历等；
- ArrayList 和 Vector 的区别
	- 主要与古老，线程不安全与安全；
- Vector 和 Stack 的区别?
	- 并发编程中都淘汰、都线程安全；用别的并发集合类代替了；
- ArrayList 可以添加 null 值吗？
	- 可以但不建议，难以维护，忘记判空处理会空指针异常；
- ArrayList 插入和删除元素的时间复杂度？
	- 分头插尾插指定位置扩容等；n,1,n
- LinkedList 插入和删除元素的时间复杂度？
	- 1，1，n；
- ArrayList 与 LinkedList 区别?
	- 线程不安全，没有采用加锁机制；
	- 底层；
	- 插入和删除时对应的位置和复杂度；
	- 快速随机访问？RandomAccess接口
	- 内存空间的占用区别数据结构角度；
	- LinkedList几乎不咋用；
- LinkedList 为什么不能实现 RandomAccess 接口？
	- 链表，内存地址不连续，不能随机快速访问；
- ArrayList 的扩容机制
- Comparable 和 Comparator 的区别？
- HashSet、LinkedHashSet 和 TreeSet 三者的异同
	- 实现类，元素唯一、非线程安全；
	- 区别底层结构
- Queue 与 Deque 的区别
	- 单端双端、操作失败的处理方式不同可分类；
	- Queue 扩展了 Collection
	- Deque 扩展了 Queue
- ArrayDeque 与 LinkedList 的区别
	- 数组、链表、null、引入时间、




### 项目
job平台、注解JObhandle
接口名——方法名——cron表达式设定执行周期；

java http请求数据 存入自己的实体类，再把实体类，通过mybatis存入mysql

mybatis插入数据；接受实体类，
数据库同样设计数据模型’，
xml真正执行的sql；

usermapper与数据库相关，与表user的映射关系；依赖了框架mybatis（是对jdbc的封装，对数据库的操作，公用的操作封装了，写一个接口可以用sql放入注解中，提供了用户的模板语言）
	uermapper.xml配置的方式：在mapper中定义需要操作数据库的相关接口，接口的实现可以通过xml配置文件或注解的方式，包含各种操作数据库add。。mybatis包含数据库的操作sql；resource文件夹-id绑定对应具体的实现，取入参；结果集返回到一个对象里，service中会调用该结果集对象，在进行操作；
一般在mapper的接口上使用注解@mapper标明这是一个注解，让其按照对应的逻辑去处理；也可在mybatis配置文件中配置，账号和密码，标明mapper在哪个包里；可以使用公司中间件标明appid和对应的token，可以返回对应的source，也可声明mapper的地址mapper.xml
	注解
userserfvice，业务逻辑，
userconttroller，负责与前端的的请求；返回给前端数据；
DTO：两个系统传输的类
service中请求别人的接口，把结果转化成DTO，（为什么不直接转化为数据库的中实体类entity，两边倒 数据也许不太一致；DTO中有getset方法，set到数据库对应的entity类中，vo是controller获取到结果）获取到的对象，new DTO容器，再进行转换为


http请求谛听的需要的DTO对象，将其读写转化成entity实体类模型、调用mapper的方法去插入，具体实现SQL语句在xml文件中；加上jobhandle注解再在job平台中，

通过jobhandel注解告知了要掉的接口和方法是什么名称，再平台上注册了定时调度的周期，中间件可以通过远程rpc的方式按照规则调用该接口；autopulldatafromditing，，，只要写到service层；
设计表

定义模型类user，里面定义对应的各个字段，以及方法；





廖雪峰-jdbc
mybatis的原理；
springboot-mvc



个人介绍；
项目收货
面试常问的问题；
模拟面试——先自我介绍、做了几个项目；
脑海里回忆；