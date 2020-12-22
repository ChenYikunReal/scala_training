# Scala学习记录

![](images/scala.jpg)

## 安装配置
- [Scala安装教程](https://www.runoob.com/scala/scala-install.html)
- [Scala下载地址](https://www.scala-lang.org/download/)
- [Scala之IDEA配置方法](https://blog.csdn.net/qq_35826412/article/details/82187881)
- [IDEA官网Scala插件下载地址](https://plugins.jetbrains.com/plugin/1347-scala/versions/stable)

## 文件夹说明
- images<br/>
项目涉及到的图片集合
- out<br/>
存放Scala源码编译生成的文件[已设置被Git忽略]
- `scala-intellij-bin-2019.2.40`<br/>
这本来是`scala-intellij-bin-2019.2.40.zip`，即`IntelliJ IDEA`的Scala插件，但是这个压缩包大小>50MB，交不上去，所以干脆选择展开提交。
- `scala-intellij-bin-2020.2.17`<br/>
同上`scala-intellij-bin-2019.2.40`，我的`IDEA`从`2019.2`版本升级到`2020.2`版本，所以也重新从官网下载了插件(使用原来的会报错)。
- src<br/>
存放Scala源码

## Scala关键词
- abstract
- case
- catch
- class
- def
- do
- else
- extends
- false
- final
- finally
- for
- forSome
- if
- implicit
- import
- lazy
- match
- new
- null
- object
- override
- package
- private
- protected
- return
- sealed
- super
- this
- throw
- trait
- try
- true
- type
- val
- var
- while
- with
- yield
- \-
- :
- =
- =\>
- \<-
- \<:
- \<%
- \>:
- \#
- @

## Scala数据类型
|数据类型 | 描述|
|:---:|:---:|
|Byte | 8位有符号补码整数。数值区间为 -128 到 127
|Short | 16位有符号补码整数。数值区间为 -32768 到 32767
|Int | 32位有符号补码整数。数值区间为 -2147483648 到 2147483647
|Long | 64位有符号补码整数。数值区间为 -9223372036854775808 到 9223372036854775807
|Float | 32 位, IEEE 754 标准的单精度浮点数
|Double | 64 位 IEEE 754 标准的双精度浮点数
|Char | 16位无符号Unicode字符, 区间值为 U+0000 到 U+FFFF
|String | 字符序列
|Boolean | true或false
|Unit | 表示无值，和其他语言中void等同，用作不返回任何结果的方法的结果类型<br/>Unit只有一个实例值，写成()
|Null | null 或空引用
|Nothing | Nothing类型在Scala的类层级的最底端；它是任何其他类型的子类型。
|Any | Any是所有其他类的超类
|AnyRef | AnyRef类是Scala里所有引用类(reference class)的基类

## Scala访问控制符
- private
- protected（包权限+子类继承可得）
- public（默认）

## Scala运算符
Scala的逻辑运算符没有\&和\|

## Scala方法和函数
- Scala有方法与函数，二者在语义上的区别很小。Scala方法是类的一部分，而函数是一个对象可以赋值给一个变量。换句话来说在类中定义的函数即是方法。
- Scala中的方法跟Java的类似，方法是组成类的一部分。
- Scala中的函数则是一个完整的对象，Scala中的函数其实就是继承了Trait的类的对象。
- Scala中使用val语句可以定义函数，def语句定义方法。


- 方法是一个以def开头的带有参数列表（可以无参数列表）的一个逻辑操作块，这正如object或者class中的成员方法一样。
- 函数是一个赋值给一个变量（或者常量）的匿名方法（带或者不带参数列表），并且通过=>转换符号跟上逻辑代码块的一个表达式。=>转换符号后面的逻辑代码块的写法与method的body部分相同。


- 函数可作为一个参数传入到方法中，而方法不行。
- 在Scala中无法直接操作方法，如果要操作方法，必须先将其转换成函数。有两种方法可以将方法转换成函数：`val f1 = m _`、`val f1: (Int) => Int = m`。
- 函数必须要有参数列表，而方法可以没有参数列表。
- 在函数出现的地方我们可以提供一个方法
    - 在需要函数的地方，如果传递一个方法，会自动进行ETA展开（把方法转换为函数）
    - 如果我们直接把一个方法赋值给变量会报错。如果我们指定变量的类型就是函数，那么就可以通过编译
    - 当然我们也可以强制把一个方法转换给函数，这就用到了Scala中的部分应用函数

## Scala字符串函数
![](images/scala-string-functions.png)

## Scala数组函数
![](images/scala-array-functions.png)

## Scala迭代器函数
![](images/scala-iterator-functions.png)

## Scala集合
[Scala集合](https://www.runoob.com/scala/scala-collections.html)

## Scala特征构造器的顺序
特征也可以有构造器，由字段的初始化和其他特征体中的语句构成。这些语句在任何混入该特征的对象在构造时都会被执行。

构造器的执行顺序：
1. 调用超类的构造器
2. 特征构造器在超类构造器之后、类构造器之前执行
3. 特征由左到右被构造
4. 每个特征当中，父特征先被构造
5. 如果多个特征共有一个父特征，父特征不会被重复构造
6. 所有特征被构造完毕，子类被构造

构造器的顺序是类的线性化的反向。线性化是描述某个类型的所有超类型的一种技术规格。 

## Scala正则表达式

正则表达式规则：<br/><br/>
![](images/regex-rules.png)
<br/>
正则表达式实例：<br/><br/>
![](images/regex-examples.png)

## Scala样例类声明的过程
此过程自动进行了以下行为：
- 构造器的每个参数都成为val，除非显式被声明为var，但是并不推荐这么做
- 在伴生对象中提供了apply方法，所以可以不使用new关键字就可构建对象
- 提供unapply方法使模式匹配可以工作
- 生成toString、equals、hashCode和copy方法，除非显示给出这些方法的定义
