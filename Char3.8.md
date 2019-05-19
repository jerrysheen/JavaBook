# 控制流程Control Flow
Java和其他的语言一样，都支持条件叙述和循环。这一小节我们先从条件叙述开始讲起，接下去在讲循环。

## 3.81 块结构 Block scope
首先我们需要来了解一下什么是块，块是由一堆Java的程序组成，被包在一个大括号里面。块定义了变量的适用范围，一个块可以是巢状（nested）的，接下来就是一个例子:
```Java
public static void main(String[] args){
	int n;
	{
		int k;
	}// k is only defined here
}

```
1. 在nested block中，你不能重复定义外面已经定义过的变量

## 3.82 条件式叙述（Conditional Statements）
基本格式：
```Java
if (condition){
	statement1;
	statement2;
}
```
1. 大括号中的内容在condition为true的情况下执行。  

除此之外，可以使用多个判断，以及使用```else```来叙述如果condition为false会执行什么。
```Java
if (condition){
	statement1;
}else if (condition2){
	statement2;
}else{
	statement3;
}
```

## 3.83 循环Loops

### while loops
while loops在condition为true的情况下执行block里面的代码，基本的格式是：
```Java
while(condition){

}
```
1. 如果condition是false，那么loop一次都不会执行。  

**注意:**如果你想要block中的内容至少执行一次，那么你需要do/while循环，基本代码如下：
```Java
do{
	statement;
}while(condition)
```  

还有另外一种循环方式是根据计数器（counter）的数字变化来进行的，那就是```for循环```，基本格式如下:
```Java
for(int i =0; i<10; i++){
	System.out.println(i);
}
```
1. for循环中的三个位置分别是(起始值；条件判断；更新方式)，其中，在loop进行前，都会进行条件判断。
2. 正常情况下，loop最好是从小到大计算，当然更新方式也可以是```i--```
3. 当你在for循环中声明一个变量，他会存在到for循环结束。

## 3.85 多个选择项—— switch 语法
switch有的时候比if else语法更加简介，它可以从多个选择中选择一个，语法是：
```Java
int choice = 1;
switch(choice){
	case 1:
		...;
		break;
	case 2:
		...;
		break;
	default:
		...;
		break;
}
```  
1. 代码根据choice的值进行比对，满足哪个case值就是哪个，如果没有case满足，则为default值。
2. **注意**，因为如果不加break，很容易造成error，所以一般**不建议**在程序中用switch。
3. switch中可以使用多种数据类型，像是```char,byte,short,int,enumerated constant,string```。  

## 3.86 能够中断控制流程的语句 （Break、Label） 
尽管```goto```被Java作者定做保留字，他们打算不在java中使用它，因为他会把代码弄得一团糟。但是许多人认为，偶尔的跳出循环是一件不错的事情，因此他们设计了break这个语句。  
在循环中使用break，就会直接跳出这个循环。  
### Label：
这是一个我之前没有学过的概念，在Java中，循环之前可以用一个Label来命名，之后可以用Break Label来终止某个循环：
```Java
firstLabel:
while(){
	secondLabel:
	while(){
		...
		if(){
			break secondLabel;
		}
	}

	if(){
		break firstLabel;
	}
}
```
1. 注意，这里break的Label一定要在之前已经声明了，想要break哪个loop，就写在这个loop的外面。  

### Continue 
与break不同，Continue执行的时候，会跳过循环后面的内容，重新执行continue上面的内容：
```Java
Scanner in = new Scanner(System.in);
        Label1:
        while(true){
            int num = in.nextInt();
            if (num <0){
                continue Label1;
            }
            else{
                break Label1;
            }
        }

```  
1. continue 后面也可以接上Label，会直接跳到Label那边去。

