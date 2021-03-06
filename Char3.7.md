# 3.7 输入和输出 (Input and Output)

## 3.7.1 读取一个输入
和在console里打印一样东西不同，输入一个东西相对来讲复杂一点。
1. 首先，需要创建一个连接System.in的```Scanner```：
```Java
Scanner in = new Scanner(System.in);
``` 
之后你可以用好几种方法来读取输入，像是：
```Java
in.nextLine();   //读取一整行输入，以String保存
in.next();       //读取下一个单词，以空格作为分割
in.nextInt();    //读取输入的int，必须是第一个字就是int，不然会报错。
in.nextDouble(); //读取double类型、
```

## 3.72 格式化的输出
有的时候我们希望输出能够按照我们规定的形式进行打印，在Java中，格式化输出的样式是和C差不多的，例如：
```Java
System.out.printf("%8.2f", x);
```
1. 注意这里用的是```printf```，他是不会换行的。
2. 在Java中，如果不限制输出几位小数，那么会打印6位小数。
3. 加上的```8```在这里是用来控制总共输出多少数，例如我这边要求8个，但是你只有输出了7个（包括小数点），那么我左边会自动空一个来补充，你可以理解为右对齐。要**注意**的是,如果没有限制小数位数，那么会默认打印6位小数，此时计算控制了几位数就需要加上输出的小数那个部分。举例来说：
```Java
double x = 8888.88
System.out.printf("%8f",x) //8888.880000
```
1. 可以看到这个时候，控制位数就无效了。
2. 加上.2表示精确到第二位，这里都是包括四舍五入的。  
你也可以在多个地方插入格式，并且可以使用不同的参数：
```Java
System.out.printf("I am %s ,and I am %d years old",name ,age);
```
1. 格式化输出就是在字符串中加入```%```以及一个固定的字母。在Java中，后面分别有这几个字母：

|Conversion character  | Type | Example|
|:--:  |  :----:  | :----:|
|d  |  十进制整数 |  159|
|x |  十六进制整数  |  9f|
|o   |  八进制整数  | 237|
|f  |  浮点数  |  15.900000|
|e  |  以指数形式来表示的浮点数  |  1.590000e+01|
|g |  浮点数，显示的小数位数比较少  | 15.9000|
|a   |  十六进制浮点数(???)  |  0x1.fcccccccccccdp3 (15.9)|
|s  |  字符串  |  Hello|
|c  |  字串  |  H|
|b |  布尔数  |  true|
|h   |  hash code  | 42528b2|
|tx or Tx  |  日期和时间  |  详见char6|
|%  |  百分号  | %(%%会打印出一个%)|
|n |  空行  |  空行|  

### Flag for printf
除了这些之外，printf还有一些flag来控制输出的样子，就像我们之前看到的```8.2f```都是样式:

|flag | purpose | Example|
|:--:  |  :----:  | :----:|
|+|打印出正负号（主要为正数服务）|+159|
|space|打印出一个空格|[ 928]|
|0|前面需要多少个零补足（正式使用的时候要变成正整数）|0033.222222|
|-|左对齐，需要配合数字使用||
|(|括号，但是会消除负号|(15.9)|
|,|每三位加上逗号|10,000|
|#|在浮点数中使用表示每次都留一个.在最后|15.|
|#|给x或者0用，每次在前面加上0x或者0|0xcafe|
|$|还不是很懂||
|<|还不是很懂| | 

此外，还有和日期有关的输出型，这里不做过多的学习了，虽然有两页。  
  
![](https://raw.githubusercontent.com/jerrysheen/JavaBook/master/img/Char3/char3.73.png)  
- **注意！！！**：所有的这些符号的输出是有顺序的，下面是整个输出的顺序，顺序不对是会报错的，按照错误提示其实也可以改正：    

### 文件的输入和输出 
这里读取一个文件的操作，我没有按照书中的来，因为貌似在我这个JDK9中，实现方式不太一样。
```Java
File file = new File("C:\\....\\test.txt");
String encoding = "utf-8";
Scanner in = new Scanner(file,String.valueOf(StandardCharsets.UTF_8));  //or encoding
System.out.println(in.next());
``` 
1. 这样可以读取txt中的一行。
2. 后面一个参数是以什么编码方式读取文件，你可以自己写一个string，也可以找StandardCharsets里面的，但是要注意转换。
3. File的地址需要是绝对路径，并且要用双反斜杠来区隔。
输出的部分等之后整理了再来完成。


