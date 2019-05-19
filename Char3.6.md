# 3.6 字串Strings
Java没有内建的string类型，而是在Java的标准库中加入了一个事先定义的类String，每一个在程序中出现的字串，都是这个String类的实例。例如：
```Java
String e =""; // an empty string
String greeting = "Hello";
```

## 3.61 Substrings:
通过```substring```这个方法，你可以从一个String中抽取出一个子字串。例如：
```Java
String e = "Hello";
String s = s.substring(0,3)  // s = "Hel"
```
1. 这里第一个参数表示开始的地方，第二个参数减第一个参数为字符串的长度。 

## 3.62 字符串的连接Concatenation：
1. Java可以用```+```来连接两个字符串，产生一个新的字符串。
2. 当你将一个字符串和一个不是字符串的变量结合在一起的时候，整个输出的结果会变成字符串。例如：
```Java
int age = 13;
String tomAge = "Tom"+age   //tomAge = "Tom13"
``` 
在java中，你想将多个字符连接在一起，并且中间用符号区别开，你会用到join方法：
```Java
String all = String.join("/","S","M","L","XL");
// all is the String "S/M/L/XL"
```

## 3.63 字串的不可变性（！！重要）String Are Immutable
对于已经生成的字串，String类没有提供方法来让你改变字符串内容，如果你要改变某个字符串变量a的值，你可以有几种不同的方法：
1. 通过concatenation和substring两个来进行删减和增加达到change的目的。
2. 直接将a指向别的字符串，等于直接更改a指向的地址。

## 3.65 空字串和Null
空字串```""```的长度为0，空字串是一个有着字符串长度（0），并且没有内容的Java对象。String对象还可以有一个特殊的值，叫做```null```，这表示当前没有任何一个对象指向现在的变数。在Java中，在你测试是不是空字串的时候，你需要以下的程式码：
```Java
if (str != null && str.length() != 0)
```
1. 要注意，这个顺序不可以换，必须先测试这个string是不是null的，因为null.lenghth()会报错。

## 3.69 StringBuilder
除了concatenation这个方法，Java还有append方法来合并两个字串。
在将多个string结合在一起的时候，如果使用concatenation这个方法，每一次相加就会产生一个新的String，非常的麻烦。为此，Java用stringbuilder来解决这个问题，利用```builder.appened()```这个方法，这样不会每次拼接都产生新的string，而是会保存在一个缓存区里面。

```Java
String str = builder.toString();
```
1. 当你确定已经结束拼接之后，可以将其变回string：