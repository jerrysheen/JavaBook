#3.3 资料类型（Data Types）

Java是一个strongly typed language，这意味着每一个变量（variable）都要有具体的数据类型。Java有8个基本数据类型（primitive types），其中有四种整数（Integer）数据类型，两种浮点数（Floating-point）数据类型,一种字符（char）数据类型，以及一种布尔（Boolean）型。

##Integer：
在Java中，负整数是可以存在的，Java一共提供了四种整数类型：

|Type  | Storage Requirement | Range|
|:--:  |  :----:  | :----:|
|byte  |  1 byte  |  -128 to 127|
|short |  2 byte  |  -32768 to 32768|
|int   |  4 byte  |  -2,147,483,648 to 2,147,483,647|
|long  |  8 byte  |  -9,223,372,026,854,775,808  to 9,223,372,026,854,775,807|

- Java程序码，不管运行在何种机器上，整数类型所表达的范围一定是上表所示，这使代码移动到另一个平台变得方便。  
- **长整形**（Long）有一个后缀L/l（像是**400000L**），**16进制数字**以前缀0X/0x开头（像是**0XCAFE**），**8进制**以前缀0开头（像是**010**），8进制容易和正常的10进制混起来，所以一般**不推荐用8进制**。  
- 从Java 7开始，Java可以表示**二进制数**，只要以前缀0b/0B开头就可以（像是**0b1001**）。另外从Java7开始，可以使用**_下划线**来标注数字，像是1_000_000和1000000是一样的道理，只是看起来比较方便一点。  



## Float-Point Types
Java中提供两种浮点数据类型的数：

|Type  | Storage Requirement | Range|
|:--:  |  :----:  | :----:|
|float  |  4 byte  |  大约 ±3.40282347E+38F  6-7位小数|
|double |  8 byte  |  大约 ±1.79769313486231570E+308   15位小数|

- double比float多一倍的精度，日常也更多的被使用。Float一般只是在特定的库（library）要Float类型的时候才会使用。
- 使用Float数据类型需要特别注明F/f（像是3.187F），而double类型以D/d标注，但是不需要特別写清楚。
- 在double类型中，有三个特殊的值 ```Double.POSITIVE_INFINITY```,```Double.NEGATIVE_INFINITY```,```Double.NaN```，其中前两个就是正负无穷，并且是可以被拿来与别的数进行比较的。但是```Double.NaN```不能来进行（==）比较，```Double.NaN```就是表示一个数除以零之后的情况，或是负数的平方根所得值。如果要看一个变数是不是等于```Double.NaN```，则要使用以下语法：
```java
if(Double.isNaN(x)); // check whether x is "not a number"
```