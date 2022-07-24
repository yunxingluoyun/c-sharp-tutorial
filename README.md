[toc]

### C#基础入门

#### 基本用法（理解面向对象编程）

C# 是一种面向对象的编程语言。在面向对象的程序设计方法中，程序由各种相互交互的对象组成。如果没有面向对象的基础，请先了解一下面向对象。

学习资料参考：[C# 中的类、结构和记录 | Microsoft Docs](https://docs.microsoft.com/zh-cn/dotnet/csharp/fundamentals/object-oriented/)

##### 示例1：创建线类

```c#
using System; // 导入命名空间，类似python的导入库

namespace BasicTutorials // 声明命名空间
{
    /// <summary>
    /// 创建形状
    /// </summary>
    class Shape
    {
        //打印输出形状信息
        public virtual void Display(){ }// 虚函数用于继承
    }
    
    /// <summary>
    /// 创建点类
    /// </summary>
    class Point:Shape
    {
        double x;
        double y;

        public double getX()
        {
            return this.x;
        }
        public void setX(double x)
        {
            this.x = x;
        }
        public double getY()
        {
            return this.y;
        }
        public void setY(double y)
        {
            this.y = y;
        }

        public override void Display() // 重写Display函数
        {
            //Console.WriteLine("Point:");
            Console.WriteLine("x:{0} y:{1}", x, y);
        }
    }

    /// <summary>
    /// 创建线类
    /// </summary>
    class Line: Shape
    {
        Point p1;
        Point p2;
        double distance;

        // 构造函数
        public Line() { }
        public Line(Point p1, Point p2)
        {
            this.p1 = p1;
            this.p2 = p2;
        }
        // 设置点坐标
        public void setPoints(Point p1, Point p2)
        {
            this.p1 = p1;
            this.p2 = p2;
        }
        // 计算距离
        public void calDistance()
        {
            this.distance = Math.Pow((p1.getX() - p2.getX()), 2) + Math.Pow((p1.getY() - p2.getY()), 2); // Math.Pow源自于System 命名空间
            
        }
        public override void Display()
        {
            Console.WriteLine("Line:"); 
            Console.WriteLine("p1:" );
            p1.Display();
            Console.WriteLine("p2:");
            p2.Display();
            Console.WriteLine("Distance:{0}", this.distance);
        }

    }

    class main // 类
    {
        static void Main(string[] args) // C#的程序入口
        {
            // Console.WriteLine("Hello World!");// 输出Hello World

            // 创建一个Point1对象
            Point point1 = new Point();
            point1.setX(3.0);// 设置x
            point1.setY(4.0);// 设置y
            point1.Display();// 显示点坐标

            // 创建一个Point2对象
            Point point2 = new Point();
            point2.setX(6.0);// 设置x
            point2.setY(8.0);// 设置y
            point2.Display();// 显示点坐标

            // 创建一个线对象
            Line line = new Line(point1, point2);
            line.calDistance(); // 计算线的长度
            line.Display();// 输出线的信息

            // Console.ReadLine(); // 输入内容，也可以用于防止控制台窗口快速关闭
            Console.ReadKey(); // 防止控制台窗口快速关闭
        }

    }
}

```

#### 关键字

关键字是 C# 编译器预定义的保留字。这些关键字不能用作标识符，但是，如果您想使用这些关键字作为标识符，可以在关键字前面加上 @ 字符作为前缀。

在 C# 中，有些关键字在代码的上下文中有特殊的意义，如 get 和 set，这些被称为上下文关键字（contextual keywords）。

下表列出了 C# 中的保留关键字（Reserved Keywords）和上下文关键字（Contextual Keywords）：

| **保留关键字**                                               |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| [abstract](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/abstract) | [as](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/type-testing-and-cast#as-operator) | [base](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/base) | [bool](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/bool) | [break](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/jump-statements#the-break-statement) | [byte](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/integral-numeric-types) | [case](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/selection-statements#the-switch-statement) |
| [catch](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/try-catch) | [char](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/char) | [checked](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/checked) | [class](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/class) | [const](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/const) | [continue](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/jump-statements#the-continue-statement) | [decimal](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/floating-point-numeric-types) |
| [default](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/default) | [delegate](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/reference-types) | [do](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/iteration-statements#the-do-statement) | [double](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/floating-point-numeric-types) | [else](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/selection-statements#the-if-statement) | [enum](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/enum) | [event](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/event) |
| [explicit](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/user-defined-conversion-operators) | [extern](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/extern) | [false](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/bool) | [finally](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/try-finally) | [fixed](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/fixed-statement) | [float](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/floating-point-numeric-types) | [for](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/iteration-statements#the-for-statement) |
| [foreach](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/iteration-statements#the-foreach-statement) | [goto](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/jump-statements#the-goto-statement) | [if](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/selection-statements#the-if-statement) | [implicit](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/user-defined-conversion-operators) | [in](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/in) | [int](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/integral-numeric-types) | [interface](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/interface) |
| [internal](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/internal) | [is](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/is) | [lock](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/lock) | [long](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/integral-numeric-types) | [namespace](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/namespace) | [new](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/new-operator) | [null](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/null) |
| [object](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/reference-types) | [operator](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/operator-overloading) | [out](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/out) | [override](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/override) | [params](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/params) | [private](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/private) | [protected](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/protected) |
| [public](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/public) | [readonly](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/readonly) | [ref](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/ref) | [return](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/jump-statements#the-return-statement) | [sbyte](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/integral-numeric-types) | [sealed](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/sealed) | [short](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/integral-numeric-types) |
| [sizeof](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/sizeof) | [stackalloc](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/stackalloc) | [static](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/static) | [string](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/reference-types) | [struct](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/struct) | [switch](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/switch-expression) | [this](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/this) |
| [throw](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/throw) | [true](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/bool) | [try](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/try-catch) | [typeof](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/type-testing-and-cast#typeof-operator) | [uint](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/integral-numeric-types) | [ulong](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/integral-numeric-types) | [unchecked](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/unchecked) |
| [unsafe](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/unsafe) | [ushort](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/integral-numeric-types) | [using](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/using) | [virtual](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/virtual) | [void](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/void) | [volatile](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/volatile) | [while](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/iteration-statements#the-while-statement) |
| **上下文关键字**                                             |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |
| [add](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/add) | [and](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/patterns#logical-patterns) | [alias](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/extern-alias) | [ascending](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/ascending) | [args](https://docs.microsoft.com/zh-cn/dotnet/csharp/fundamentals/program-structure/top-level-statements#args) | [async](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/async) | [await](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/await) |
| [by](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/by) | [descending](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/descending) | [dynamic](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/reference-types) | [equals](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/equals) | [from](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/from-clause) | [get](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/get) | [global](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/namespace-alias-qualifier) |
| [group](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/group-clause) | [init](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/init) | [into](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/into) | [join](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/join-clause) | [let](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/let-clause) | [托管（函数指针调用约定）](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/unsafe-code#function-pointers) | [nameof](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/nameof) |
| [nint](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/integral-numeric-types) | [not](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/patterns#logical-patterns) | [notnull](https://docs.microsoft.com/zh-cn/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters#notnull-constraint) | [nuint](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/builtin-types/integral-numeric-types) | [on](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/on) | [or](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/patterns#logical-patterns) | [orderby](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/orderby-clause) |
| [partial（类型）](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/partial-type) | [partial（方法）](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/partial-method) | [record](https://docs.microsoft.com/zh-cn/dotnet/csharp/fundamentals/types/records) | [remove](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/remove) | [select](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/select-clause) | [set](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/set) | [非托管（函数指针调用约定）](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/unsafe-code#function-pointers) |
| [unmanaged（泛型类型约束）](https://docs.microsoft.com/zh-cn/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters#unmanaged-constraint) | [value](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/value) | [var](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/var) | [when（筛选条件）](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/when) | [where（泛型类型约束）](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/where-generic-type-constraint) | [where（查询子句）](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/where-clause) | [with](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/with-expression) |
| [yield](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/yield) |                                                              |                                                              |                                                              |                                                              |                                                              |                                                              |

#### 数据类型

在 C# 中，变量分为以下几种类型：

- 数值类型
- 布尔与文本类型
- 引用类型
- 指针类型

##### 数值类型

| 类型    | 描述                                 | 默认值 |
| :------ | :----------------------------------- | :----- |
| sbyte   | 8 位有符号整数类型                   | 0      |
| byte    | 8 位无符号整数                       | 0      |
| short   | 16 位有符号整数类型                  | 0      |
| ushort  | 16 位无符号整数类型                  | 0      |
| int     | 32 位有符号整数类型                  | 0      |
| uint    | 32 位无符号整数类型                  | 0      |
| long    | 64 位有符号整数类型                  | 0L     |
| ulong   | 64 位无符号整数类型                  | 0      |
| float   | 32 位单精度浮点型                    | 0.0F   |
| double  | 64 位双精度浮点型                    | 0.0D   |
| decimal | 128 位精确的十进制值，28-29 有效位数 | 0.0M   |

##### 布尔与文本类型

| 类型   | 描述              | 范围          | 默认值 |
| ------ | ----------------- | ------------- | ------ |
| bool   | 布尔值            | True 或 False | False  |
| char   | 6 位 Unicode 字符 | 0 到 65535    | '\0'   |
| string | 字符串            | 一组字符      |        |

##### 引用类型

其实，string 字符串既属于文本类型属于引用类型。

| 类型    | 描述                                                         |
| ------- | ------------------------------------------------------------ |
| string  | 允许您给变量分配任何字符串值。字符串（String）类型是 System.String 类的别名。它是从对象（Object）类型派生的。字符串（String）类型的值可以通过两种形式进行分配：引号和 @引号。 |
| Object  | 对象（Object）类型 是 C# 通用类型系统（Common Type System - CTS）中所有数据类型的终极基类。Object 是 System.Object 类的别名。所以对象（Object）类型可以被分配任何其他类型（值类型、引用类型、预定义类型或用户自定义类型）的值。但是，在分配值之前，需要先进行类型转换。 |
| Dynamic | 动态（Dynamic）类型可以存储任何类型的值在动态数据类型变量中。这些变量的类型检查是在运行时发生的。 |

##### 指针类型

和 C/C++中的指针一样

例如:

```c#
double* x;
string* pStr;
```

##### 示例2：数值类型

```c#
using System; // 导入命名空间，类似python的导入库


namespace BasicTutorials // 声明命名空间
{
    class main // 类
    {
        static void Main(string[] args) // C#的程序入口
        {
            byte a = 255;
            int b = 10;
            float c = -13.04F;
            double d = 3.1415926;

            Console.WriteLine(a + 1);// 0
            Console.WriteLine(Math.Pow(b, 2));//100
            Console.WriteLine(Math.Abs(c));// 13.04
            Console.WriteLine(Math.Sin(d));// 接近0
            Console.WriteLine(Math.Min(Math.PI, d));// 判断PI与d谁小，输出小的值
            Console.ReadKey(); // 防止控制台窗口快速关闭
        }

    }
}

```

##### 示例3：文本类型

```c#
using System; // 导入命名空间，类似python的导入库

namespace BasicTutorials // 声明命名空间
{

    class main // 类
    {
        static void Main(string[] args) // C#的程序入口
        {
            char s1 = 'm';
            char[] s2 = { 'H','e' ,'l','l','o'};
            string s3 = "你 好";
            string s4 = @"D:\PIESat\PIESDK\Document";// 使用@将转义字符（\）当作普通字符对待
            string s5 = "暮境难禁日月催，腊醅初见拆泥开。压车麦穗黄云卷，食叶蚕声白雨来。";
            string s6 = @"暮境难禁日月催，腊醅初见拆泥开。
                            压车麦穗黄云卷，食叶蚕声白雨来。";// 使用@可以换行添加字符串

            Console.WriteLine(s1);
            Console.WriteLine("类型：{0}",s1.GetType());

            Console.WriteLine(s2);
            Console.WriteLine("类型：{0}",s2.GetType());

            Console.WriteLine(s3);
            Console.WriteLine("类型：{0}",s3.GetType());
            Console.WriteLine("统计s3字符数：{0}", s3.Length);

            Console.WriteLine(s4);
            string[] temp1 = s4.Split('\\'); // 拆分字符串
            // 显示拆分的字符串
            for(int i=0; i<temp1.Length;++i)
            {
                Console.WriteLine(temp1[i]);
            }

            Console.WriteLine(s5);
            string temp = "薄饭蕨薇端可饱，短衫纻葛亦新裁。宦涂自古多忧畏，白首为农信乐哉！";
            Console.WriteLine(s5.Insert(s5.Length - 1, temp)); // 增
            Console.WriteLine(s5.Remove(0, s5.Length));// 删
            Console.WriteLine(s5.Replace("食叶蚕声白雨来","1234567"));// 替换
            Console.WriteLine(s5.IndexOf("日月"));// 查找索引位置
            
            Console.ReadKey(); // 防止控制台窗口快速关闭
        }

    }
}

```

结果：

```c#
m
类型：System.Char
Hello
类型：System.Char[]
你 好
类型：System.String
统计s3字符数：3
D:\PIESat\PIESDK\Document
D:
PIESat
PIESDK
Document
暮境难禁日月催，腊醅初见拆泥开。压车麦穗黄云卷，食叶蚕声白雨来。
暮境难禁日月催，腊醅初见拆泥开。压车麦穗黄云卷，食叶蚕声白雨来薄饭蕨薇端可饱，短衫纻葛亦新裁。宦涂自古多忧畏，白首为农信乐哉！。

暮境难禁日月催，腊醅初见拆泥开。压车麦穗黄云卷，1234567。
```

##### 示例4：Object

```c#
using System; // 导入命名空间，类似python的导入库

namespace BasicTutorials // 声明命名空间
{

    class main // 类
    {
        static void Main(string[] args) // C#的程序入口
        {
            bool isTrue = false;
            int x = 10;
            double[] y = { 1.2, 1.3, 12.4 };
            string str = "暮境难禁日月催，腊醅初见拆泥开。压车麦穗黄云卷，食叶蚕声白雨来。";

            object[] obj = new object[5]; // 创建对象,指定了obj数组的大小

            obj[0] = isTrue;
            obj[1] = x;
            obj[2] = y;
            obj[3] = str;
            obj[4] = y;

            // 输出所有内容
            for (int i=0; i<obj.Length;++i)
            {
                if(y.GetType() == obj[i].GetType()) // 判断obj[i]是否为double型数组
                {
                    double[] temp = (double[])obj[i];// 显示转换
                    for(int j=0;j< temp.Length;j++)
                    {
                        Console.WriteLine(temp[j]);// 输出内容
                    }
                    
                    Console.WriteLine(obj[i].GetType()); //输出类型
                }
                else
                {
                    Console.WriteLine(obj[i]);// 输出内容
                    Console.WriteLine(obj[i].GetType()); //输出类型
                }
            }
            
            Console.ReadKey(); // 防止控制台窗口快速关闭
        }

    }
}

```

结果：

```c#
False
System.Boolean
10
System.Int32
1.2
1.3
12.4
System.Double[]
暮境难禁日月催，腊醅初见拆泥开。压车麦穗黄云卷，食叶蚕声白雨来。
System.String
1.2
1.3
12.4
System.Double[]
```

##### 示例5：Dynamic

与object作用类似。

```C#
using System; // 导入命名空间，类似python的导入库


namespace BasicTutorials // 声明命名空间
{

    class main // 类
    {
        static void Main(string[] args) // C#的程序入口
        {
            bool isTrue = false;
            int x = 10;
            double[] y = { 1.2, 1.3, 12.4 };
            string str = "暮境难禁日月催，腊醅初见拆泥开。压车麦穗黄云卷，食叶蚕声白雨来。";
            dynamic[] d = new object[5]; // 创建对象,指定了obj数组的大小
            d[0] = isTrue;
            d[1] = x;
            d[2] = y;
            d[3] = str;
            d[4] = y;

            // 输出所有内容
            for (int i=0; i<d.Length;++i)
            {
                if(y.GetType() == d[i].GetType()) // 判断obj[i]是否为double型数组
                {
                    double[] temp = (double[])d[i];// 显示转换
                    for(int j=0;j< temp.Length;j++)
                    {
                        Console.WriteLine(temp[j]);// 输出内容
                    }
                    
                    Console.WriteLine(d[i].GetType()); //输出类型
                }
                else
                {
                    Console.WriteLine(d[i]);// 输出内容
                    Console.WriteLine(d[i].GetType()); //输出类型
                }
            }

            Console.ReadKey(); // 防止控制台窗口快速关闭
        }

    }
}

```

**区别**：动态类型与对象类型相似，但是对象类型变量的类型检查是在编译时发生的，而动态类型变量的类型检查是在运行时发生的

#### 类型转换

类型转换从根本上说是把数据从一种类型转换为另一种类型。在 C# 中，类型转换有两种形式：

- **隐式类型转换** - 这些转换是 C# 默认的以安全方式进行的转换, 不会导致数据丢失。例如，从小的整数类型转换为大的整数类型，从派生类转换为基类。

- **显式类型转换** - 显式类型转换，即强制类型转换。显式转换需要强制转换运算符，而且强制转换会造成数据丢失。

- **字符串转数值**- 以int为例，其他类似。

  - int.Parse()是一种类容转换；表示将数字内容的字符串转为int类型。  

    ​		如果字符串为空，则抛出`ArgumentNullException`异常； 

    　　如果字符串内容不是数字，则抛出`FormatException`异常；  

    　　如果字符串内容所表示数字超出int类型可表示的范围，则抛出`OverflowException`异常；

  - `Convert.ToInt32()`是一种类容转换；但它不限于将字符串转为int类型，还可以是其它类型的参数；`Convert.ToInt32` 与 `int.Parse` 较为类似，实际上 `Convert.ToInt32` 内部调用了 `int.Parse`。

  - `int.TryParse (String s,out int num)`与 `int.Parse(string s)`又较为类似，但它不会产生异常，最后一个参数为输出值,如果转换失败，输出值为 0，如果转换成功，输出值为转换后的int值。

##### 在Convert中常见内置类型转换方法：

| 序号 | 方法 & 描述                                                  |
| :--- | :----------------------------------------------------------- |
| 1    | **ToBoolean** 如果可能的话，把类型转换为布尔型。             |
| 2    | **ToByte** 把类型转换为字节类型。                            |
| 3    | **ToChar** 如果可能的话，把类型转换为单个 Unicode 字符类型。 |
| 4    | **ToDateTime** 把类型（整数或字符串类型）转换为 日期-时间 结构。 |
| 5    | **ToDecimal** 把浮点型或整数类型转换为十进制类型。           |
| 6    | **ToDouble** 把类型转换为双精度浮点型。                      |
| 7    | **ToInt16** 把类型转换为 16 位整数类型。                     |
| 8    | **ToInt32** 把类型转换为 32 位整数类型。                     |
| 9    | **ToInt64** 把类型转换为 64 位整数类型。                     |
| 10   | **ToSbyte** 把类型转换为有符号字节类型。                     |
| 11   | **ToSingle** 把类型转换为小浮点数类型。                      |
| 12   | **ToString** 把类型转换为字符串类型。                        |
| 13   | **ToType** 把类型转换为指定类型。                            |
| 14   | **ToUInt16** 把类型转换为 16 位无符号整数类型。              |
| 15   | **ToUInt32** 把类型转换为 32 位无符号整数类型。              |
| 16   | **ToUInt64** 把类型转换为 64 位无符号整数类型。              |

更多内容可参考：[强制转换和类型转换 - C# 编程指南 | Microsoft Docs](https://docs.microsoft.com/zh-cn/dotnet/csharp/programming-guide/types/casting-and-type-conversions)

##### 示例6：类型转换

```c#
using System; // 导入命名空间，类似python的导入库

namespace BasicTutorials // 声明命名空间
{
    class Base
    {
    }

    class Derived : Base
    {
    }

    class main // 类
    {
        static void Main(string[] args) // C#的程序入口
        {
            int a = 10;
            float b = 10.2F;
            object c = "123";
            Derived d = new Derived();

            // 隐式转换
            double temp = b;
            object temp1 = a;
            Base temp2 = d;// 派生类转基类

            // 显式转换
            int temp3 = (int)b;
            Derived temp4 = (Derived)temp2;// 基类转派生类

            // 内置类型转换
            char[] temp5 = c.ToString().ToCharArray();

            Console.WriteLine("temp:{0}",temp);
            Console.WriteLine("temp1:{0}", temp1);
            Console.WriteLine("temp2:{0}", temp2);
            Console.WriteLine("temp3:{0}", temp3);
            Console.WriteLine("temp4:{0}", temp4);
            Console.WriteLine("temp5:{0}", temp5);
            Console.ReadKey(); // 防止控制台窗口快速关闭
        }

    }
}

```

输出：

```
temp:10.1999998092651
temp1:10
temp2:BasicTutorials.Derived
temp3:10
temp4:BasicTutorials.Derived
temp5:System.Char[]
```

##### 示例7：字符串转数值

```c#
using System; // 导入命名空间，类似python的导入库

namespace BasicTutorials // 声明命名空间
{
    class main // 类
    {
        static void Main(string[] args) // C#的程序入口
        {
            string str1 = "12";
            string str2 = "12.34";
            string str3 = "abc";

            //int temp = (int)str1; // 常见错误
            int temp1 = int.Parse(str1);// 12
            // int temp2 = int.Parse(str3); // 异常：System.FormatException:“输入字符串的格式不正确。”
            double temp3 = Convert.ToDouble(str2);// 12.34
            double.TryParse(str2, out double temp4);// 12.34
            double.TryParse(str3, out double temp5);// 0

            Console.WriteLine("temp1:{0}",temp1);
            Console.WriteLine("temp3:{0}", temp3);
            Console.WriteLine("temp4:{0}", temp4);
            Console.WriteLine("temp5:{0}", temp5);
            Console.ReadKey(); // 防止控制台窗口快速关闭
        }
    }
}
```

输出：

```
temp1:12
temp3:12.34
temp4:12.34
temp5:0
```

#### 运算符优先级

下表按最高优先级到最低优先级的顺序列出 C# 运算符。 每行中运算符的优先级相同。

| 运算符                                                       | 类别或名称                                                   |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [x.y](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/member-access-operators#member-access-expression-)、[f(x)](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/member-access-operators#invocation-expression-)、[a[i\]](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/member-access-operators#indexer-operator-)、[`x?.y`](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/member-access-operators#null-conditional-operators--and-)、[`x?[y\]`](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/member-access-operators#null-conditional-operators--and-)、[x++](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/arithmetic-operators#increment-operator-)、[x--](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/arithmetic-operators#decrement-operator---)、[x!](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/null-forgiving)、[new](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/new-operator)、[typeof](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/type-testing-and-cast#typeof-operator)、[checked](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/checked)、[unchecked](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/unchecked)、[default](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/default)、[nameof](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/nameof)、[delegate](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/delegate-operator)、[sizeof](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/sizeof)、[stackalloc](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/stackalloc)、[x->y](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/pointer-related-operators#pointer-member-access-operator--) | 主要                                                         |
| [+x](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/arithmetic-operators#unary-plus-and-minus-operators)、[-x](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/arithmetic-operators#unary-plus-and-minus-operators)、x[、](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/bitwise-and-shift-operators#bitwise-complement-operator-)~x[、](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/arithmetic-operators#increment-operator-)++x[、](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/arithmetic-operators#decrement-operator---)--x[、](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/member-access-operators#index-from-end-operator-)^x[、](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/type-testing-and-cast#cast-expression)(T)x[、](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/await)await[、&&x](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/pointer-related-operators#address-of-operator-)、[*x](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/pointer-related-operators#pointer-indirection-operator-)、[true 和 false](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/true-false-operators) | 一元                                                         |
| [x..y](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/member-access-operators#range-operator-) | 范围                                                         |
| [switch](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/switch-expression)、[with](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/with-expression) | `switch` 和 `with` 表达式                                    |
| [x * y](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/arithmetic-operators#multiplication-operator-)、[x / y](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/arithmetic-operators#division-operator-)、[x % y](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/arithmetic-operators#remainder-operator-) | 乘法                                                         |
| [x + y](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/arithmetic-operators#addition-operator-)、[x – y](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/arithmetic-operators#subtraction-operator--) | 加法                                                         |
| [x << y](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/bitwise-and-shift-operators#left-shift-operator-)、[x >> y](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/bitwise-and-shift-operators#right-shift-operator-) | 移位                                                         |
| [x < y](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/comparison-operators#less-than-operator-)、[x > y](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/comparison-operators#greater-than-operator-)、[x <= y](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/comparison-operators#less-than-or-equal-operator-)、[x >= y](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/comparison-operators#greater-than-or-equal-operator-)、[is](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/type-testing-and-cast#is-operator)、[as](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/type-testing-and-cast#as-operator) | 关系和类型测试                                               |
| [x == y](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/equality-operators#equality-operator-)、[x != y](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/equality-operators#inequality-operator-) | 相等                                                         |
| `x & y`                                                      | [布尔逻辑 AND](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/boolean-logical-operators#logical-and-operator-) 或[按位逻辑 AND](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/bitwise-and-shift-operators#logical-and-operator-) |
| `x ^ y`                                                      | [布尔逻辑 XOR](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/boolean-logical-operators#logical-exclusive-or-operator-) 或[按位逻辑 XOR](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/bitwise-and-shift-operators#logical-exclusive-or-operator-) |
| `x | y`                                                      | [布尔逻辑 OR](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/boolean-logical-operators#logical-or-operator-) 或[按位逻辑 OR](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/bitwise-and-shift-operators#logical-or-operator-) |
| [x && y](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/boolean-logical-operators#conditional-logical-and-operator-) | 条件“与”                                                     |
| [x \|\| y](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/boolean-logical-operators#conditional-logical-or-operator-) | 条件“或”                                                     |
| [x ?? y](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/null-coalescing-operator) | Null 合并运算符                                              |
| [c ? t : f](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/conditional-operator) | 条件运算符                                                   |
| [x = y](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/assignment-operator)、[x += y](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/arithmetic-operators#compound-assignment)、[x -= y](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/arithmetic-operators#compound-assignment)、[x *= y](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/arithmetic-operators#compound-assignment)、[x /= y](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/arithmetic-operators#compound-assignment)、[x %= y](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/arithmetic-operators#compound-assignment)、[x &= y](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/boolean-logical-operators#compound-assignment)、[x \|= y](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/boolean-logical-operators#compound-assignment)、[x ^= y](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/boolean-logical-operators#compound-assignment)、[x <<= y](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/bitwise-and-shift-operators#compound-assignment)、[x >>= y](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/bitwise-and-shift-operators#compound-assignment)、[x ??= y](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/null-coalescing-operator)、[=>](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/lambda-operator) |                                                              |

#### 语句

下表列出了 C# 中的各种语句类型及其关联的关键字，并提供指向包含详细信息的主题的链接：

| 类别                                                         | C# 关键字/说明                                               |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| [声明语句](https://docs.microsoft.com/zh-cn/dotnet/csharp/programming-guide/statements-expressions-operators/statements#declaration-statements) | 声明语句引入新的变量或常量。 变量声明可以选择为变量赋值。 在常量声明中必须赋值。 |
| [表达式语句](https://docs.microsoft.com/zh-cn/dotnet/csharp/programming-guide/statements-expressions-operators/statements#expression-statements) | 用于计算值的表达式语句必须在变量中存储该值。                 |
| 选择语句                                                     | 选择语句用于根据一个或多个指定条件分支到不同的代码段。 有关详细信息，请参阅下列主题：[if](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/selection-statements#the-if-statement)[switch](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/selection-statements#the-switch-statement) |
| 循环语句                                                     | 循环语句用于遍历集合（如数组），或重复执行同一组语句直到满足指定的条件。 有关详细信息，请参阅下列主题：[do](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/iteration-statements#the-do-statement)[for](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/iteration-statements#the-for-statement)[foreach](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/iteration-statements#the-foreach-statement)[while](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/iteration-statements#the-while-statement) |
| 跳转语句                                                     | 跳转语句将控制转移给另一代码段。 有关详细信息，请参阅下列主题：[break](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/jump-statements#the-break-statement)[continue](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/jump-statements#the-continue-statement)[goto](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/jump-statements#the-goto-statement)[return](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/jump-statements#the-return-statement)[yield](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/yield) |
| 异常处理语句                                                 | 异常处理语句用于从运行时发生的异常情况正常恢复。 有关详细信息，请参阅下列主题：[throw](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/throw)[try-catch](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/try-catch)[try-finally](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/try-finally)[try-catch-finally](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/try-catch-finally) |
| [Checked 和 unchecked](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/checked-and-unchecked) | Checked 和 unchecked 语句用于指定将结果存储在变量中、但该变量过小而不能容纳结果值时，是否允许数值运算导致溢出。 有关详细信息，请参阅 [checked](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/checked) 和 [unchecked](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/unchecked)。 |
| `await` 语句                                                 | 如果用 [async](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/async) 修饰符标记方法，则可以使用该方法中的 [await](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/operators/await) 运算符。 在控制到达异步方法的 `await` 表达式时，控制将返回到调用方，该方法中的进程将挂起，直到等待的任务完成为止。 任务完成后，可以在方法中恢复执行。  有关简单示例，请参阅[方法](https://docs.microsoft.com/zh-cn/dotnet/csharp/programming-guide/classes-and-structs/methods)的“异步方法”一节。 有关详细信息，请参阅 [async 和 await 的异步编程](https://docs.microsoft.com/zh-cn/dotnet/csharp/programming-guide/concepts/async/)。 |
| `yield return` 语句                                          | 迭代器对集合执行自定义迭代，如列表或数组。 迭代器使用 [yield return](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/yield) 语句返回元素，每次返回一个。 到达 `yield return` 语句时，会记住当前在代码中的位置。 下次调用迭代器时，将从该位置重新开始执行。  有关更多信息，请参见 [迭代器](https://docs.microsoft.com/zh-cn/dotnet/csharp/programming-guide/concepts/iterators)。 |
| `fixed` 语句                                                 | fixed 语句禁止垃圾回收器重定位可移动的变量。 有关详细信息，请参阅 [fixed](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/keywords/fixed-statement)。 |
| `lock` 语句                                                  | lock 语句用于限制一次仅允许一个线程访问代码块。 有关详细信息，请参阅 [lock](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/lock)。 |
| 带标签的语句                                                 | 可以为语句指定一个标签，然后使用 [goto](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/jump-statements#the-goto-statement) 关键字跳转到该带标签的语句。 （参见下一行中的示例。） |
| [空语句](https://docs.microsoft.com/zh-cn/dotnet/csharp/programming-guide/statements-expressions-operators/statements#the-empty-statement) | 空语句只含一个分号。 不执行任何操作，可以在需要语句但不需要执行任何操作的地方使用。 |

语句主要介绍常用的4类：选择语句、循环语句、跳转语句和lock语句。

##### 选择语句

以下语句根据表达式的值从多个可能的语句选择要执行的语句：

- [`if` 语句](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/selection-statements#the-if-statement)：根据布尔表达式的值来选择要执行的语句。
- [`switch` 语句](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/selection-statements#the-switch-statement)：根据与表达式匹配的模式来选择要执行的语句列表。（不推荐，可能有功能“关系模式”在 C# 7.3 中不可用的问题）

##### 示例8：if else

```c#
using System; // 导入命名空间，类似python的导入库

namespace BasicTutorials // 声明命名空间
{
    class main // 类
    {
        static void Main(string[] args) // C#的程序入口
        {
            Console.WriteLine("请输入成绩：");
            double.TryParse(Console.ReadLine(),out double score);// 将字符串转换double
            
            if(score>=0 && score<=100 )
            {
                if (score < 60)
                {
                    Console.WriteLine("差");
                }
                else if (score < 90)
                {
                    Console.WriteLine("良");
                }
                else
                {
                    Console.WriteLine("优");
                }
            }
            else
            {
                Console.WriteLine("输入的成绩有误！");
            }
            
            Console.ReadKey(); // 防止控制台窗口快速关闭
        }
    }
}
```

输出：

```
请输入成绩：
88
良
```

##### 循环语句

以下语句重复执行语句或语句块：

- [`for` 语句](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/iteration-statements#the-for-statement)：在指定的布尔表达式的计算结果为 `true` 时会执行其主体。
- [`foreach` 语句](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/iteration-statements#the-foreach-statement)：枚举集合元素并对集合中的每个元素执行其主体。
- [`do` 语句](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/iteration-statements#the-do-statement)：有条件地执行其主体一次或多次。
- [`while` 语句](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/iteration-statements#the-while-statement)：有条件地执行其主体零次或多次。

##### 示例9：for

```c#
using System; // 导入命名空间，类似python的导入库

namespace BasicTutorials // 声明命名空间
{
    class main // 类
    {
        static void Main(string[] args) // C#的程序入口
        {
            int n = 100;
            int total = 0;
            for(int i=0;i<=n; i++)
            {
                total += i;
            }
            Console.WriteLine(total);
            Console.ReadKey(); // 防止控制台窗口快速关闭
        }
    }
}
```

##### 示例10：foreach

`foreach` 语句为类型实例中实现 [System.Collections.IEnumerable](https://docs.microsoft.com/zh-cn/dotnet/api/system.collections.ienumerable) 或 [System.Collections.Generic.IEnumerable](https://docs.microsoft.com/zh-cn/dotnet/api/system.collections.generic.ienumerable-1) 接口的每个元素执行语句或语句块。

```c#
using System; // 导入命名空间，类似python的导入库
using System.Collections.Generic;

namespace BasicTutorials // 声明命名空间
{
    class main // 类
    {
        static void Main(string[] args) // C#的程序入口
        {
            var fibNumbers = new List<int> { 0, 1, 1, 2, 3, 5, 8, 13 };
            foreach (int element in fibNumbers)
            {
                Console.Write($"{element} ");
            }
            Console.ReadKey(); // 防止控制台窗口快速关闭
        }
    }
}
```

输出：

```
0 1 1 2 3 5 8 13
```

##### 示例11：while

```c#
using System; // 导入命名空间，类似python的导入库

namespace BasicTutorials // 声明命名空间
{
    class main // 类
    {
        static void Main(string[] args) // C#的程序入口
        {
            int n = 0;
            while (n < 5)
            {
                Console.Write(n);// 打印输出，但不换行
                Console.Write(" ");
                n++;
            }
            Console.ReadKey(); // 防止控制台窗口快速关闭
        }
    }
}
```

输出：

```
0 1 2 3 4
```

##### 示例12：do ... while

```c#
using System; // 导入命名空间，类似python的导入库

namespace BasicTutorials // 声明命名空间
{
    class main // 类
    {
        static void Main(string[] args) // C#的程序入口
        {
            int n = 0;
            do
            {
                Console.Write(n);
                Console.Write(" ");
                n++;
            } while (n < 5);
            Console.ReadKey(); // 防止控制台窗口快速关闭
        }
    }
}
```

##### 跳转语句

以下语句无条件转移控制：

- [`break` 语句](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/jump-statements#the-break-statement)：将终止最接近的封闭[循环语句](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/iteration-statements)或 [`switch` 语句](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/selection-statements#the-switch-statement)。
- [`continue` 语句](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/jump-statements#the-continue-statement)：启动最接近的封闭[循环语句](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/iteration-statements)的新迭代。
- [`return` 语句](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/jump-statements#the-return-statement)：可终止它所在的函数的执行，并将控制权返回给调用方。
- [`goto` 语句](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/jump-statements#the-goto-statement)：将控制权转交给带有标签的语句。

##### 示例13：break

例：检测5天内是否做核酸

```c#
using System; // 导入命名空间，类似python的导入库

namespace BasicTutorials // 声明命名空间
{
    class main // 类
    {
        static void Main(string[] args) // C#的程序入口
        {
            int[] numbers = { 24, 72, 120, 24, 112, 150, 33 };
            foreach (int number in numbers)
            {
                if (number >120)
                {
                    Console.WriteLine();
                    Console.WriteLine("5天未做核酸，无法乘坐交通工具，请您先做核酸！！！");
                    break;
                }
                Console.Write($"{number} ");
            }
            Console.WriteLine();
            Console.WriteLine("结束示例");
            Console.ReadKey(); // 防止控制台窗口快速关闭
        }
    }
}
```

##### 示例14：continue

`continue` 语句启动最接近的封闭[循环语句](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/iteration-statements)（即 `for`、`foreach`、`while` 或 `do` 循环）的新迭代。

```c#
using System; // 导入命名空间，类似python的导入库

namespace BasicTutorials // 声明命名空间
{
    class main // 类
    {
        static void Main(string[] args) // C#的程序入口
        {
            int[] numbers = { 24, 72, 120, 24, 112, 150, 33 };
            foreach (int number in numbers)
            {
                if (number >120)
                {
                    Console.Write($"{number} ");
                    Console.WriteLine("5天未做核酸，无法乘坐交通工具，请您先做核酸！！！");
                    continue;
                }
                
                Console.Write($"{number} ");
                Console.WriteLine("已通过");
            }
            Console.WriteLine();
            Console.WriteLine("结束示例");
            Console.ReadKey(); // 防止控制台窗口快速关闭
        }
    }
}
```

输出：

```
24 已通过
72 已通过
120 已通过
24 已通过
112 已通过
150 5天未做核酸，无法乘坐交通工具，请您先做核酸！！！
33 已通过

结束示例
```

##### 示例15：goto

`goto` 语句将控制权转交给带有标签的语句，改进示例8。

```c#
using System; // 导入命名空间，类似python的导入库

namespace BasicTutorials // 声明命名空间
{
    class main // 类
    {
        static void Main(string[] args) // C#的程序入口
        {
            Next:
                Console.WriteLine("请输入成绩：");
                double.TryParse(Console.ReadLine(), out double score);// 将字符串转换double

            if (score >= 0 && score <= 100)
            {
                if (score < 60)
                {
                    Console.WriteLine("差");
                }
                else if (score < 90)
                {
                    Console.WriteLine("良");
                }
                else
                {
                    Console.WriteLine("优");
                }
            }
            else
            {
                Console.WriteLine("输入的成绩有误！");
                goto Next;
            }

            Console.ReadKey(); // 防止控制台窗口快速关闭
        }
    }
}
```

输出：

```
请输入成绩：
120
输入的成绩有误！
请输入成绩：
100
优
```

##### lock语句

`lock` 语句获取给定对象的互斥 lock，执行语句块，然后释放 lock。 持有 lock 时，持有 lock 的线程可以再次获取并释放 lock。 阻止任何其他线程获取 lock 并等待释放 lock。

##### 示例16：lock

以下示例定义了一个 `Account` 类，该类通过锁定专用的 `balanceLock` 实例来同步对其专用 `balance` 字段的访问。 使用相同的实例进行锁定可确保尝试同时调用 `Debit` 或 `Credit` 方法的两个线程无法同时更新 `balance` 字段。

示例来自于：[lock 语句 - C# 参考 | Microsoft Docs](https://docs.microsoft.com/zh-cn/dotnet/csharp/language-reference/statements/lock)

```c#
using System; // 导入命名空间，类似python的导入库
using System.Threading.Tasks;

namespace BasicTutorials // 声明命名空间
{
    public class Account
    {
        private readonly object balanceLock = new object();
        private decimal balance;

        public Account(decimal initialBalance) => balance = initialBalance;

        public decimal Debit(decimal amount)
        {
            if (amount < 0)
            {
                throw new ArgumentOutOfRangeException(nameof(amount), "The debit amount cannot be negative.");
            }

            decimal appliedAmount = 0;
            lock (balanceLock)
            {
                if (balance >= amount)
                {
                    balance -= amount;
                    appliedAmount = amount;
                }
            }
            return appliedAmount;
        }

        public void Credit(decimal amount)
        {
            if (amount < 0)
            {
                throw new ArgumentOutOfRangeException(nameof(amount), "The credit amount cannot be negative.");
            }

            lock (balanceLock)
            {
                balance += amount;
            }
        }

        public decimal GetBalance()
        {
            lock (balanceLock)
            {
                return balance;
            }
        }
    }

    class AccountTest
    {
        static async Task Main()// 主程序
        {
            var account = new Account(1000);
            var tasks = new Task[100];
            for (int i = 0; i < tasks.Length; i++)
            {
                tasks[i] = Task.Run(() => Update(account));
            }
            await Task.WhenAll(tasks);
            Console.WriteLine($"Account's balance is {account.GetBalance()}");
            Console.ReadKey();
            // Output:
            // Account's balance is 2000
        }

        static void Update(Account account)
        {
            decimal[] amounts = { 0, 2, -3, 6, -2, -1, 8, -5, 11, -6 };
            foreach (var amount in amounts)
            {
                if (amount >= 0)
                {
                    account.Credit(amount);
                }
                else
                {
                    account.Debit(Math.Abs(amount));
                }
            }
        }
    }
}
```

#### 常用命名空间

选通过这些表格锁定命名空间名称，再到下面这个链接里查具体的功能。

查询命名空间具体内容网址：[System 命名空间 | Microsoft Docs](https://docs.microsoft.com/zh-cn/dotnet/api/system?view=netframework-4.0)

##### 一、基础命名空间

| 基础命名空间                                                 | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [System](https://docs.microsoft.com/zh-cn/dotnet/api/system?view=netframework-4.0) | 处理内建数据、数学计算、随机数的产生、环境变量、垃圾回收器及一些常见的异常和特征. |
| System.Collections                                           | 包含了一些与集合相关的类型，比如列表、队列、位数组、哈希表和字典等. |
| System.Collections.Generic                                   | 定义泛型集合的接口和类，泛型集合允许用户创建强类型集合，它能提供更好的类型安全性和性能. |
| System.IO                                                    | 包含了一些数据流类型并提供了文件和目录同步异步读写.          |
| System.IO.Comoression                                        | 提供基本的流压缩和解压缩服务的类.                            |
| System.IO.Ports                                              | 控制串行端口的类.                                            |
| System.Text                                                  | 包含了一些表示字符编码的类型并提供了字符串的操作和格式化.    |
| System.Reflection                                            | 包括了一些提供加载类型,方法和字段的托管视图以及动态创建和调用类型功能的类型. |
| System.Threading                                             | 提供启用多线程的类和接口.                                    |
| System.Runtime.InteropServices                               | 使得.NET类型可以与非托管代码交互.                            |

##### 二、图形命名空间

| 图形命名空间            | 描述                                                         |
| ----------------------- | ------------------------------------------------------------ |
| System.Drawing          | 这个主要的GDI＋命名空间定义了许多类型，实现基本的绘图类型（字体，钢笔，基本画笔等）和无所不能的Graphics对象． |
| System.Drawing2D        | 这个命名空间提供高级的二维和失量图像功能．                   |
| System.Drawing.Imaging  | 这个命名空间定义了一些类型实现图形图像的操作．               |
| System.Drawing.Text     | 这个命名空间提供了操作字体集合的功能．                       |
| System.Drawing.Printing | 这个命名空间定义了一些类型实现在打印纸上绘制图像，和打印机交互以及格式化某个打印任务的总体外观等功能． |

##### 三、数据命名空间

| 数据命名空间             | 描述                                                         |
| ------------------------ | ------------------------------------------------------------ |
| System.Data              | 包含了数据访问使用的一些主要类型．                           |
| System.Data.Common       | 包含了各种数据库访问共享的一些类型．                         |
| System.XML               | 包含了根据标准来支持XML处理的类．                            |
| System.Data.OleDb        | 包含了一些操作OLEDB数据源的类型．                            |
| System.Data.Sql          | 能使你枚举安装在当前本地网络的SQLServer实例．                |
| System.Data.SqlClient    | 包含了一些操作MSSQLServer数据库的类型，提供了和System.Data.OleDb相似的功能，但是针对SQL做了优化． |
| System.Data.SqlTypes     | 提供了一些表示SQL数据类型的类．                              |
| System.Data.Odbc         | 包含了操作Odbc数据源的类型．                                 |
| System.Data.OracleClient | 包含了操作Odbc数据库的类型．                                 |
| System.Transactions      | 这个命名空间提供了编写事务性应用程序和资源管理器的一些类．   |

##### 四、语言集成查询

| 语言集成查询     |                                                        |
| ---------------- | ------------------------------------------------------ |
| System.Linq      | 支持使用语言集成查询的查询.                            |
| System.Xml.Linq  | 包含LINQtoXML的类.                                     |
| System.Data.Linq | 包含支持与LINQtoSQL应用程序中的关系数据库进行交互的类. |

##### 五、Windows窗体应用程序

| Windows窗体应用程序      |                                                          |
| ------------------------ | -------------------------------------------------------- |
| System.Windows.Froms     | 创建WinForm应用程序.                                     |
| System.Windows           | 提供支持WPF属性系统和事件逻辑的一些基元素类以及其他类型. |
| System.Windows.Controlls | 创建WPF控件元素，使用户与应用程序进行交互.               |
| System.Windows.Shapes    | 提供对WPFXAML或代码中使用的形状库的访问.                 |

##### 六、WEB命名空间

| WEB命名空间                  |                                                              |
| ---------------------------- | ------------------------------------------------------------ |
| System.Web                   | 这个命名空间包含启用浏览器/服务器通信的类和接口.这些命名空间类用于管理到客户端的HTTP输出和读取HTTP请求.附加的类则提供了一些功能,用于服务器端的应用程序以及进程,Cookie管理,文件传输,异常信息和输出缓存的控制. |
| System.Web.UI                | 这个命名空间包含Web窗体的类,包括Page类和用于创建Web用户界面的其他标准类. |
| System.Web.UI.HtmlControls   | 这个命名空间包含用于HTML特定控件的类,这些控件可以添加到Web窗体中以创建Web用户界面. |
| System.Web.UI.WebControls    | 包含创建ASP.NET服务器控件的类,当添加到窗体时,这些控件将呈现浏览器特定的HTML和脚本,用于创建和设备无关的Web用户界面. |
| System.Web.Mobile            | 包含生成ASP.NET移动应用程序所需要的核心功能,包括身份验证和错误处理. |
| System.Web.UI.MobileControls | 包括一组ASP.NET服务器控件,这些控件可以针对不同的移动设备呈现应用程序. |
| System.Web.Services          | 包含能使你使用和生成XMLWebService的类,这些服务是驻留在服务器中的可编程实体,并通过标准Internet协议公开. |

##### 七、框架服务命名空间

| 框架服务命名空间         |                                                              |
| ------------------------ | ------------------------------------------------------------ |
| System.Diagnostics       | 这个命名空间所提供的类允许你启动系统进程,读取和写入事件日志以及使用性能计数器监视系统性能. |
| System.DirectoryServices | 这个命名空间所提供的类可便于从托管代码中访问ActiveDirectory.此命名空间中的类可以与任何ActiveDirectory服务提供程序一起使用. |
| System.Management        | 这个命名空间提供的类用于管理一些信息和事件,它们关系到系统,设备和WMI基础结构所使用的应用程序. |
| System.Messaging         | 这个命名空间提供的类用于连接到网络上的消息队列,向队列发送消息,从队列接收或查看消息. |
| System.ServiceProcess    | 这个命名空间提供的类用于安装和运行服务,服务是长期运行的可执行文件,它们不通过用户界面来运行. |
| System.Timers            | 这个命名空间提供基于服务器的计时器组件,用以按指定的间隔引发事件. |

##### 八、安全性命名空间

| 安全性命名空间      |                                                           |
| ------------------- | --------------------------------------------------------- |
| System.Security     | 这个命名空间提供公共语言运行库安全性系统的基础结构.       |
| System.Net.Security | 这个命名空间提供用于主机间安全通信的网络流.               |
| System.Web.Security | 这个命名空间包含的类用于在Web应用程序中实现ASP.NET安全性. |

##### 九、网络命名空间

| 网络命名空间                  |                                                              |
| ----------------------------- | ------------------------------------------------------------ |
| System.Net                    | 包含的类可为当前网络上的多种协议提供简单的编程接口.          |
| System.Net.Cache              | 这个命名空间定义了一些类和枚举,用于为使用WebRequest和HttpWebRequest类获取的资源定义缓存策略. |
| System.Net.Configuration      | 这个命名空间包含了以编程方式访问和更新System.Net命名空间的配置设置的类. |
| System.Net.Mime               | 这个命名空间包含了用于将电子邮件发送到SMTP服务器进行传送的类. |
| System.Net.Networkinformation | 这个命名空间提供对网络流量数据,网络地址信息和本地计算机的地址更改通知的访问,还包含实现Ping实用工具的类.你可以使用Ping和相关的类来检查是否可通过网络访问某台计算机. |
| System.Net.Sockets            | 这个命名空间为严格控制网络访问的开发人员提供Windows套接字接口的托管实现. |

##### 十、配置命名空间

| 配置命名空间                    |                                                              |
| ------------------------------- | ------------------------------------------------------------ |
| System.Configuration            | 这个命名空间包含用于以编程方式访问.NetFramework配置设置并处理配置文件中错误的类. |
| System.Configuration.Assemblies | 这个命名空间包含用于配置程序集的类.                          |
| System.Configuration.Provider   | 这个命名空间包含由服务器和客户端应用程序共享,以支持可插接式模型轻松添加或移除功能的基类. |

##### 十一、本地化命名空间

| 本地化命名空间         |                                                              |
| ---------------------- | ------------------------------------------------------------ |
| System.Globalization   | 包含的类定义与区域性相关的信息,其中包括语言,国家\地区,所使用的日历,日期格式的模式,货币与数字以及字符串的排序顺序. |
| System.Resources       | 这个命名空间提供一些类和接口,它们使开发人员得以创建,存储并管理应用程序中使用的各种区域性特定资源. |
| System.Resources.Tools | 这个命名空间包含StronglyTypedResourceBuilder类,该类提供对强类型资源的支持.这个编译时功能通过创建包含一组静态只读属性的类封装对资源的访问,从而使得使用资源变得更加容易. |

##### 十二、其他命名空间

| 其他命名空间        |                                               |
| ------------------- | --------------------------------------------- |
| System.ServiceModel | 包含生成WCF服务和客户端应用程序所需要的类型.  |
| System.Workflow     | 开发工作流应用程序.                           |
| System.Media        | 包含用于播放声音文件和访问系统提供的声音的类. |

该文档就写这么多吧，如果还想深入学习的见参考网址吧。

参考网址：

[C# 文档 - 入门、教程、参考。 | Microsoft Docs](https://docs.microsoft.com/zh-cn/dotnet/csharp/)

[C# 教程 | 菜鸟教程 (runoob.com)](https://www.runoob.com/csharp/csharp-tutorial.html)

[ C# String转int主要有四种方法_※※冰馨※※的博客-CSDN博客_c将string转换成int](https://blog.csdn.net/Pei_hua100/article/details/111220308)

[C#常用命名空间 - 天琊蓝 - 博客园 (cnblogs.com)](https://www.cnblogs.com/makesense/p/4500955.html)

