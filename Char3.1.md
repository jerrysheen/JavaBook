#3.1 一个简单的Java程序

在学习所有语言的时候，第一个要尝试的就是打印"Hello World"：
```java
public class HelloWorld{
	public static void main(String[] args){
		System.out.println("Hello World");
	}
}
```
这段代码会重复的出现，其中有一些点需要强调的东西：

1. Java是**Case Sensitive**的语言，也就是说这些关键词如果大小写打错了，就会报错。
2. 接下来看到**public**，他是一个访问修饰符(access modifier)，它用来控制其他程序短语这段代码的访问权限。详情在第五章中会重点介绍。
3. **class**关键词表明在Java程序中，**所有的**code都是在class中的，你可以把class想象为一个容器，它里面装了很多的代码，这些代码是用来描述一个应用（application）会做哪些事情的。
4. 接下来是class的名称，names开头必须要是**英文字母**，并且不可以将保留字（reserved word）作为程序的名称。在Java中，class name往往有一套固定的命名格式，它要求是以大写字母开始的名词，每一个word的首字母用大写。注意，类名称要和你保存的**.java档**一样。
5. 当你写完了.java档之后，编译会产生bytecode,系统会自己将这个文件命名为.class。
6. 每次执行的时候，虚拟机都会从main方法中开始执行，所以main方法是必须要有的。你也可以在main方法中呼叫自己的方法来执行。
7. 用**"{"**(opening brace),**"}"**(closing brace)包起来的内容在Java中被叫做块(block)，java中所有的方法都要用{}包起来。
8. 现在我们还不用关心```static void```是干嘛的，就把它当作写程序执行时需要的，我们不能忘记的是程序一定要有main方法。
9. 再来看大括号的内部，可以看到每一句statement都是以“；”结尾的，在Java中，回车并不代表一句话的结束。
10. 再来看```System.out.println("Hello World");```这语句，这里，**System.out**对象呼叫了**println**方法，并且传入了字符串参数"Hello World"。用双引号引起来的内容在Java中都为字符串。
