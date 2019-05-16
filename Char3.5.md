# 3.5运算子(Operators)
运算子是用来combine value的，在这一章节中，我们将会介绍**算数运算子**和**逻辑运算子**以及算数方程（mathematical function）。

## 3.51算数运算子
最常用的运算子有四个```+ , - , * , /```，其中```/```比较特殊，在整数和浮点数时运算不同：
1. 整数：整数的时候```/```代表整除，另外一个符号```%```代表取余数。
2. 浮点数：浮点数的时候，就是正常的除法。
3. ```stricfp```关键词用来解决浮点数除法相关的议题，因为不同的机器处理的精度可能不同，而Java虚拟机又想要将所有的计算精度统一起来，这造成了运算时间的问题，所以用了stricfp来让大家选择是否要进行严格的运算。

## 3.52 数学方程(mathematical function)和常量  

 ```Math``` 类中包含了许多常用的计算，例如平方根运算：

```Java
double x = 4;
double y = Math.sqrt(x);
System.out.println(y);
```

1. 注意到，```.sqrt()```和```println();```还是有一些差距的，后者执行在System.out对象上，而前者是直接执行在一个类里，这样子的方法被叫做类的**静态方法**(static method)，之后会讲到。

2. 另外还有一些常用的方法以及里面的参数：  

```java
Math.pow(x,a);  //x^a
Math.sin()
Math.cos()
Math.tan()
Math.atan()
Math.exp()
Math.log()
Math.log10()
Math.PI
Math.E
```

1. **TIP**:如果你每一次使用之前不想加Math，可以选择在开头导入包```import static java.lang.Math.*;```,这样你可以直接写Math里面的方法名称或者常量名称就可以，之后会在第四章中讨论这种static import.
2. Math中的浮点数运算是跟着计算机来的（而不是随着虚拟机而统一），这样能够保证运行的速度，如果要用严格统一的浮点数运算，则用StricMath方法。
3. Math计算的时候，用了许多的方法来保证计算的安全，如果计算结果超出数据类型的长度，就会报出异常。 

## 3.53 数字类型之间的转换。

![](https://raw.githubusercontent.com/jerrysheen/JavaBook/master/img/char3.53.png)
