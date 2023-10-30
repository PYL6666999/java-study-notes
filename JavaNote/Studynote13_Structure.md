# 类的结构

## 对象和成员变量

类的引入：对于需要表示的数据，采用简单的数据结构无法储存足够的信息

* 单独变量 =>不利于数据管理
* 数组 =>无法体现数据类型；只能通过[下标]获取信息，造成变量名字和内容的对应关系不明确

类与对象

* 类是抽象、概念的数据类型，包含属性、行为
* 对象是类的个体，一个具体的实例，创建/实例化对象（数组也是对象：一个数组名只能指向一个具体数组，但是一个具体的数组可将地址赋给多个数组名；名字不包含具体数据，只有地址才能访问数据）

| Java内存结构 | 存放内容                                       | 对象实例的存在形式             |
| ------------ | ---------------------------------------------- | ------------------------------ |
| 栈           | 基本数据类型（局部变量）                       | 名称/对象名/对象引用           |
| 堆           | 对象（类实例，数组等)                          | 数据空间（属性、基本数据类型） |
| 方法区       | 常量池（储存引用类型，例如String），类加载信息 | 类的信息（属性、行为）         |



### 成员变量

1. 从概念或叫法上看：成员变量=属性=fied（字段）（即成员变量用来表示属性）

2. 属性Properties是类的一个组成部分，一般是基本数据类型，也可是引用类型(对象，数组)。

   * 属性的定义语法同变量

     ```java
     访问修饰符 属性类型 属性名;
     //访问修饰符：控制属性的访问范围
     //有四种访问修饰符：public,proctected,默认，private
     ```

   * 属性的定义类型可以为任意类型，包含基本类型或引用类型

   * 属性如果不赋值，有默认值，规则和数组一致。



## 成员方法

1. 定义格式

   ```java
   访问修饰符 返回数据类型 方法名(形参列表..){//方法体
   	语句;
   	return 返回值;
   }
   ```
   
2. 使用细节

   * 访问修饰符：作用是控制方法使用的范围。如果不写默认访问，[有四种：public, protected, 默认, private]
   * 返回数据类型
     * 一个方法最多有一个返回值[使用数组可返回多个结果]
     * 返回类型可以为任意类型，包含基本类型或引用类型(数组，对象)
     * 如果方法要求有返回数据类型，则方法体中最后的执行语句必须为return值，而且要求返回值类型必须和return的值类型一致或兼容
     * 如果方法是void,则方法体中可以没有return语句，或者只写return;
   * 方法名：在实际工作中，我们的方法都是为了完成某个功能，所以方法名要有一定含义，遵循驼峰命名法。最好见名知义，表达出该功能的意思即可，比如得到两个数的和getSum,开发中按照规范
   * 形参列表
     * 一个方法可以有0个参数，也可以有多个参数，中间用逗号隔开，比如`getSum(int n1,int n2)`
     * 参数类型可以为任意类型，包含基本类型或引用类型，比如`printArr(int[][] map)`
     * 调用带参数的方法时，一定对应着参数列表传入相同类型或兼容类型的参数
     * 方法定义时的参数称为形式参数，简称形参；方法调用时的参数称为实际参数，简称实参，实参和形参的类型要一致或兼容、个数、顺序必须一致！
   * 方法体：里面写完成功能的具体的语句，可以为输入、输出、变量、运算、分支、循环、方法调用，但里面不能再定义方法！即：方法不能嵌套定义，

3. 使用方式
   * 同一个类中的方法调用:直接调用即可。
   * 跨类中的方法A类调用B类方法：需要通过对象名调用。比如 `对象名.方法名(参数)）`
   * 特别说明：跨类的方法调用和方法的访问修饰符相关

### 作用域Scope

1. 在java编程中，主要的变量就是属性（成员变量）和局部变量，
2. 我们说的局部变量一般是指在成员方法中定义的变量。
3. java中作用域的分类
   * 全局变量：也就是属性，作用域为整个类体。定义时可直接赋值
   * 局部变量：也就是除了属性之外的其他变量，作用域为定义它的代码块中
4. 全局变量（属性）可以不赋值，直接使用，因为有默认值，局部变量必须赋值后才能使用，因为没有默认值。

注意事项

1. 属性和局部变量可以重名，访问时遵循就近原则。
2. 在同一个作用域中，比如在同一个成员方法中，两个局部变量，不能重名。
3. 生命周期不同
   * 属性生命周期较长，伴随着对象的创建而创建，伴随着对象的销毁而销毁
   * 局部变量，生命周期较短，伴随着它的代码块的执行而创建，伴随着代码块的结束而销毁。即在一次方法调用过程中。
4. 作用域范围不同
   * 全局变量/属性：可以被本类使用，或其他类使用（通过对象调用）
   * 局部变量：只能在本类中对应的方法中使用
5. 修饰符不同
   * 全局变量/属性可以加修饰符
   * 局部变量不可以加修饰符

方法中的同名变量的声明会使得同名的成员变量在该方法中被屏蔽



## 相关代码实现

### 创建对象实例

```java
//1.先声明再创建
Cat cat;//声明Cat类的对象cat
cat = new Cat();创建

//2.直接创建
Cat cat = new Cat()
```

若两个名称指向同一对象，再对其中一个名称赋值null，则仅会给其中一个空指针异常，不会导致对象的消失



### Java代码的执行流程简单分析

创建对象实例

```java
Person p = new Person();
p.name = "jack”;
p.age = 10;
```

1. 先加载Person类信息（属性和方法信息，只会加载一次）
2. 在堆中分配空间，进行默认初始化
3. 把地址赋给p，p就指向对象
4. 进行指定初始化，完成变量赋值



调用对象方法

```java
Person p1 = new Person();
int returnRes = p1.getSum(10, 20);
System.out.println("getSum方法返回的值="+returnRes);
```

执行原理：--其方法调用对应的代码为
```java
	public int getSum(int num1, int num2) {
		int res = num1 + num2;
		return res;
	}
```

1. 在栈中创建数据空间"main栈"
2. 在栈中创建独立的数据空间"getSum栈"
3. 将int值num1和num2拷贝到getSum栈中，运行得到res
4. 结果返回到main栈中，getSum栈销毁