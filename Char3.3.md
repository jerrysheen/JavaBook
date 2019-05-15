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

1. Java程序码，不管运行在何种机器上，整数类型所表达的范围一定是上表所示，这使代码移动到另一个平台变得方便。  
2. **长整形**（Long）有一个后缀L/l（像是**400000L**），**16进制数字**以前缀0X/0x开头（像是**0XCAFE**），**8进制**以前缀0开头（像是**010**），8进制容易和正常的10进制混起来，所以一般**不推荐用8进制**。  
3. 从Java 7开始，Java可以表示**二进制数**，只要以前缀0b/0B开头就可以（像是**0b1001**）。另外从Java7开始，可以使用**_下划线**来标注数字，像是1_000_000和1000000是一样的道理，只是看起来比较方便一点。  



## Float-Point Types
Java中提供两种浮点数据类型的数：

|Type  | Storage Requirement | Range|
|:--:  |  :----:  | :----:|
|float  |  4 byte  |  大约 ±3.40282347E+38F  6-7位小数|
|double |  8 byte  |  大约 ±1.79769313486231570E+308   15位小数|

1. double比float多一倍的精度，日常也更多的被使用。Float一般只是在特定的库（library）要Float类型的时候才会使用。
2. 使用Float数据类型需要特别注明F/f（像是3.187F），而double类型以D/d标注，但是不需要特別写清楚。
3. 在double类型中，有三个特殊的值 ```Double.POSITIVE_INFINITY```,```Double.NEGATIVE_INFINITY```,```Double.NaN```，其中前两个就是正负无穷，并且是可以被拿来与别的数进行比较的。但是```Double.NaN```不能来进行（==）比较，```Double.NaN```就是表示一个数除以零之后的情况，或是负数的平方根所得值。如果要看一个变数是不是等于```Double.NaN```，则要使用以下语法：
```java
if(Double.isNaN(x)); // check whether x is "not a number"
```
4. 注意，尽量不要使用浮点数的加减法，例如（2.0-1.1），你最后得到的不会是0.9。而是一个近似的数字。原因是因为在Java中，浮点数以二进制来表示，而二进制无法精准表示像是1/10这样的数字，就像二进制无法精准表示1/3这样的数字。如果你真的需要用浮点数来计算，那么你需要```Bigdecimal```这个库，这将在之后提到。  

## Char Type:  
1. 在Java中，Char被单引号引起来，像是```'A'```就是一字符常量，将他转变成数值，他的值是65。注意，他和```"A"```是不一样的，后者是一个字符类型的字符串（String）。  
2. 字符常量的值会从```\u0000```到```\uFFFF```。其中**\u**是用来告诉Java这之后的两组十六进位数字是unicode。而**\u**叫做跳脱字元（escape character）。加上斜杠之后，**u**就不再是字符原来的意思，而是表达了一个新的意思。在Java中还有其他的跳脱字元：

|Escape Sequence  | Name | Unicode Value|
|:--:  |  :----:  | :----:|
|\b |  BackSpace  | \u0008 |
|\t |  Tab        | \u0009 |
|\n |  Linefeed   | \u000a |
|\r |  Carriage return  | \u0008d |
|\"	| Double quote|\u0022|
|\' | Single quote|\u0027|
|\\ | Backslash   |\u005c|

3. 上述跳脱字符在字符内容中使用的时候，相当于你在打字的时候按了一下那个键。另外也要主义的是，斜杠之后的意义就会改变，可能和原本想要表示的意思不一样。**特别的！**只有\u能够在字符串以外的地方使用，例如你完全可以输入以下的语句，用跳脱字元来代替```[]```:
```public static void main(String\u005B\005D args)```

### Unicode and the char Type
1. 这里再来重点讲一讲Unicode编码方式，在Unicode产生之前，有许多不同的编码法则，像是Ascii，BIG-5。这样子的不同的编码有两种问题，一是存储的长度不一样，二是同一个字符或许在不同的编码方式里有不同的数值。
2. 一开始的时候，unicode是以16-bit（4Hex）来保存一个字符的，但是随着中文，日文以及韩文的加入，2^16个字已经不能满足unicode了。JAVA利用以下方法来解决该问题：
	- 首先，每个字符都会有一个自己的Code point，就像自己的身份证一样，其范围为（U+0000 to U+10FFFF），其中（U+0000 to U+FFFF）为**基本字符**，而后的为**补充字符**（U+10000 to U+10FFFF）。有了身份证之后，每个人都有自己的住所，JAVA 提供了17个code planes，这些planes对应到了之前的所有身份证，像是第一个plane（basic multilingual plane）对应的就是基本字符，这些字符也被叫做**code unit**。而后的16个planes对应的就是补充字符。
	- 有了这些定义之后，我们要如何来表示那些补充字符呢？后面的字符就用两个code unit来组成。前一个code unit的范围在（0xD800和0xDBFF）之间，后一个code unit的范围在（0xDC00和0xDFFF）之间。这两个区域被叫做**surrogates area**。
	- 更加详细具体的解释可以[详见](https://tools.ietf.org/html/rfc2781)，作者提到最好不要使用char类型，而是使用String类型会比较好。