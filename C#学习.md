**封装** 被定义为"把一个或多个项目封闭在一个物理的或者逻辑的包中"。在面向对象程序设计方法论中，封装是为了防止对实现细节的访问。

抽象和封装是面向对象程序设计的相关特性。抽象允许相关信息可视化，封装则使程序员***实现所需级别的抽象**。*

封装使用 **访问修饰符** 来实现。一个 **访问修饰符** 定义了一个类成员的范围和可见性。C# 支持的访问修饰符如下所示：

- Public
- Private
- Protected
- Internal
- Protected internal



**可空类型（Nullable）**

**语法：**<data_type> ? <variable_name> = null;

作用：

1、无“魔数”。 <data_type> ? <variable_name> = null;

2、安全访问只

3、提供默认值。  ??



**数组 Array**

数组是引用类型

五种数组类型：

1、多维数组（矩形数组）。类似二维平面图形，三维空间图形。

```C#
int[,] a = new int[2,2]{
{1,2},
{3,4}
}
```

2、交错数组,类似多维数组？

```C#
int [][] a = new int[][];
int[][] a= new int[][]
{
new int{1,2},new int{4,5,7},new int{5,1}
}
int[0][1]=1,int[0][2]=2;
int[1][1]=4,int[1][2]=5,int[1][3]=7
int[2][1]=5,int[2][2]=1;
```

3、传递数组给函数 ,一个存在的数组传递给函数

将数组作为参数传递到函数中做处理

4、参数数组 

是函数定义方法，允许函数接受不定数量的参数，这些参数会被当做数组处理

```c#
public 返回类型 方法名称( params 类型名称[] 数组名称 )
```

5、Array 类，是数组的基类

数组的使用

1、数组长度修改

```C#
int[] numbers = { 1, 2, 3 };

// "增加"元素（实际是创建新数组）
int[] newArray = new int[numbers.Length + 1];
Array.Copy(numbers, newArray, numbers.Length);//复制一个数组的元素到新的数组，（旧，新，复制的元素个数）
newArray[^1] = 4; // 添加新元素到末尾，^1 表示倒一 ，^表示倒二，依次类推

// "减少"元素（删除最后一个元素）
int[] smallerArray = new int[numbers.Length - 1];
Array.Copy(numbers, smallerArray, smallerArray.Length);
```

2、Array.Resize方法

```c#
// 扩展数组
Array.Resize(ref numbers, numbers.Length + 1);
numbers[^1] = 4; // 添加新元素

// 缩小数组
Array.Resize(ref numbers, numbers.Length - 1);
```

3、动态集合 List<>

```c#
// 创建列表（相当于可变长数组）
List<int> list = new List<int> { 1, 2, 3 };

// 增加元素
list.Add(4);       // 末尾添加
list.Insert(1, 5); // 在索引1处插入

// 减少元素
list.Remove(2);    // 删除值为2的元素
list.RemoveAt(0);  // 删除索引0的元素

// 转回数组（如果需要）
int[] array = list.ToArray();
```

4、数组常用操作

```c#
int[] arr = { 1, 2, 3, 4, 5 };

// 查找元素
int index = Array.IndexOf(arr, 3); // 返回值2（索引位置）

// 排序
Array.Sort(arr); // 升序排列

// 反转
Array.Reverse(arr);

// 清空部分内容
Array.Clear(arr, 0, 2); // 清空前2个元素（设为0）
```

**建议**

- 当元素数量**固定不变**时使用数组 `int[]`
- 当需要**动态增减**元素时使用 `List`
- 两者可通过 `.ToArray()` 和 `.ToList()` 相互转换



**结构体 Struct**

单一类型可以存储各种类型的相关数据、

```c#
struct Books{
   public string title;
   public string author;
   public string subject;
   public int book_id;
};  
```

- 结构可带有方法、字段、索引、属性、运算符方法和事件。
- 结构可定义构造函数，但不能定义析构函数。但是，您不能为结构定义默认的构造函数。默认的构造函数是自动定义的，且不能被改变。
- 与类不同，结构不能继承其他的结构或类。
- 结构不能作为其他结构或类的基础结构。
- 结构可实现一个或多个接口。
- 结构成员不能指定为 abstract、virtual 或 protected。
- 当您使用 **New** 操作符创建一个结构对象时，会调用适当的构造函数来创建结构。与类不同，结构可以不使用 New 操作符即可被实例化。
- 如果不使用 New 操作符，只有在所有的字段都被初始化之后，字段才被赋值，对象才被使用。



**枚举Enum**

```c#
Enum enum_name {enum_list};
enum Days { Sun, Mon, tue, Wed, thu, Fri, Sat };
```



**构造函数**

创建类的对象时调用。构造函数与类的名称一致，且没有返回类型。--> 参数化构造函数



**析构函数 ** 释放非托管资源（文件/网络/数据库句柄等）

类的 **析构函数** 是类的一个特殊的成员函数，当类的对象超出范围时执行。

析构函数的名称是在类的名称前加上一个波浪形（~）作为前缀，它不返回值，也不带任何参数。

析构函数用于在结束程序（比如关闭文件、释放内存等）之前释放资源。析构函数不能继承或重载。



**字典 Dictionary<TKey, TValue>**

需引入System.Collections.Generic 

作用：1、数据索引

​            2、统计频次

​            3、缓存数据

**链表 ListNode**

链表指针移动

```c#
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     public int val;
 *     public ListNode next;
 *     public ListNode(int val=0, ListNode next=null) {
 *         this.val = val;
 *         this.next = next;
 *     }
 * }
 */
public class Solution {
    public ListNode AddTwoNumbers(ListNode l1, ListNode l2) {
        ListNode ResultNode = new   ListNode(0); //哑点
        ListNode Current = ResultNode;
        int carry = 0;
        //同时遍历两张链表
        while(l1  != null || l2 != null || carry !=0)
        {
            int x = (l1 != null) ? l1.val : 0;
            int y = (l2 != null) ? l2.val : 0;
            int sum = x + y +carry;
            carry = sum /10;
            Current.next = new ListNode (sum%10);
            Current = Current.next;
            if(l1 != null) l1 = l1.next; 
            if(l2 != null) l2 = l2.next; 
        }
        return ResultNode.next;
    }
}
```

