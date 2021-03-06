#4.1 介绍面向对象的程序
面向对象编程（Object Oriented Programming）或者OOP是目前非常流行的编程方式。面向对象的程序由对象构成，每个对象都有特定的对用户公开的部分，和隐藏起来，用户看不到的实现的部分。对象可以是从标准库中获得，也可以是从自己写的类里获得。  
在传统的structured programming中，标准的格式是```Algotithm + data```,意味着要先考虑操作data的步骤，再来考虑采取怎么样结构的资料会使这种操作比较简单。OOP语言反转了这个过程，把资料放在首位，之后再考虑要对这个Data做什么。  
对于小的程序来说，将其分解成不同的procedure来做是非常顺利的，但是面对大的问题，面向对象的程序更加适合。  

## 4.11 类
- 类是一个产生对象的模板，当你从类中产生了一个他的对象，我们称这种行为为创造了一个类的实例。  
- Java中所有的代码都是写在类当中的，Java标准库中有各种各样的类。像是日历类，网络编程类。你也可以根据自己的需要去写自己的类来解决问题。  

### 封装 Encapsulation
1. 封装是一个面向对象思想的关键概念。封装就是将data和行为结合在一个包裹中，并且把如何实现内部行为的代码都隐藏起来，使使用者不必去了解。对象中的数据被叫做实例域（instance field），能够对数据进行操作的叫做方法。每个对象都会有自己特定的实例域值，这些值被叫做对象目前的状态（state），当你呼叫方法的时候，这些值就可能会改变。  
2. 封装一个主要的idea就是对象中的instance field最好要用**对象的方法**来访问，而不是直接访问，这就像是一个黑盒的概念。  

### 继承 inheritance 
1. Java中另外一个重要的思想就是继承，类可以靠“继承其他的类”来建造。在Java中，其实所有的类都由一个叫"Object"的父类继承而来。
2. 当你继承一个已经存在的类之后，你会继承下来其所有的属性和方法，并且可以添加自己的方法。  

## 4.1.2 Objects对象 
- 对象具有三个特性你需要去认识：
 1. 对象的行为——你可以对这个对象做什么，你可以用哪些方法和对象进行交互?
 2. 对象的状态——当你使用方法的时候，对象的会发生什么反应。
 3. 对象的identity——如何将这个对象和其他对象进行区别。
- 同属于同一个类的对象具有相似性，因为他们能够做相同的行为，而这种因为是由你呼叫方法来实现的。
- 每一个对象都会存储他当前内容的资讯，这就是对象的状态，一个对象的状态可以随着时间改变，但是必须通过一系列方法的调用，并非自发性的。
- 但是需要注意，上述的状态并不能完全来描述一个对象，最主要来区别两个对象的还是identity这个属性。不管状态是否相同，只要是不同的对象，其identity一定会不同。

## 4.1.3 识别一个类。
在设计一个传统程序的时候，人们往往会从main开始设计，但是在设计OOP的时候，我们从定义每一个类，并且往其中加上方法来开始。  
定义其中类的一个简单的规则就是分析问题中的名词和动词，将名词作为类，将动词作为方法。  
举例来说，为了建立一个订单系统，其中一部分的名词如下：
```
· 商品     ———— Item
· 订单     ———— Order
· 购买地址
· 付款
· 账户
```
1. 这里就会产生后面所示的这些类。
2. 接下来，寻找动词，与此相关的动词有```add```,```delete```，```ship```,```cancel```。你需要理清楚其中的关系，例如```add```就要属于```Order```，并且需要一个Item作为参数。  

## 4.1.4 类之间的关系 
类与类之间最常见的关系是：
- Dependence -- use a
- Aggregation -- has a
- Inheritance  -- is a
1. **Dependence**关系，是最常见的关系，比方说，订单类就会uses账号类，因为订单对象需要去访问账号类，看账号的信誉值再决定是否建立这笔订单。但是物品类并不依赖于账号类，因为订单对象不需要去担心顾客账号。因此总的来说，如果一个类需要对另一个类的对象进行操作，那他们就是依赖关系。
2. 尽量**最小化**这些依赖关系，因为如果A类和B类没关系，那么B类的改变一定不会引入bug到A类，这如果用软件工程的术语来讲叫做**coupling 耦合**。
3. **The Aggregation**：聚合关系，表示的是如下关系：例如```订单```的对象中，会有```Item```对象。
4. **The inheritance**:继承关系是对象之间另外一种关系。举例说：```紧急订单```是从```订单```类中继承下来的。他可能会有特殊的方法和参数，例如有计算需要增加多少运费的方法，但是其他的方法，从原来的订单类里面继承下来，所以保持不变。总的来说：类A```extends class```类B,类A```inherits```方法from类B，但是类A也可以有自己的方法。

![](https://raw.githubusercontent.com/jerrysheen/JavaBook/master/img/Char3/char3.53.png)
1. 上图所示的叫做```UML```（Unified Modeling Language）来制作类的图，并且用来描述类之间的关系。例如下图就是一个简单的例子，其中类用长方形来表示，箭头用来表示类与类之间的关系:
![](https://raw.githubusercontent.com/jerrysheen/JavaBook/master/img/Char3/char3.53.png)