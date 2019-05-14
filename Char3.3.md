#3.3 资料类型（Data Types）
Java是一个strongly typed language

Java中的注释，不会出现在可执行文件中。因此，你可以在程序档中大肆的添加注释，Java有三种方式来添加注释：
1. 第一种最常用的方法就是添加符号```//```，使用这个符号可以在本行注释符号之后添加注释。
```Java
System.out.println("Hello World");  // this line will print "Hello World". 
```
2. 使用```/* aaa  */```来产生一段比较长的注释
```java
/*
在这个block中的都是注释
在这个block中的都是注释
*/
```
3. 还有一种注释，用来自动产生代码的说明文件，格式为```/**    */```，这种注释将会在第四章中重点说明。
```java
/**
*This is the first sample program in Core Java Chapter3
*@version 1.01 1997-3-22
*@author Gary Cornell 
*/
```