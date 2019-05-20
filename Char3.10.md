# 3.10 Arrays

## 3.10.1 声明一个Arrays
阵列是一种用来储存一群相同类型的资料的数据结构。通过每一个值的```index```来访问他们的值。例如，如果a是一个整数类型的阵列，那么```a[i]```就是其中第i个整数。  
1. 声明一个array，利用结构：```数据类型[] 变量名称 = new 数据类型[需存储数个数];```，例如：
```Java
int[] a = new int[100] ;
```
1. 这里int[100]，表示初始化这个阵列。
2. 这里声明了里面的数据类型，和里面要存储多少数据（阵列的长度）。当你固定了这个长度以后，就不能改变了。如果你需要长度可以变的阵列，那么你可以用arrayList，详见charpter5.   

```Java
int[] b ={ 2, 3, 5, 6,};
```
1. 这边用四个数字直接初始化了阵列，顺便规定了长度。
2. 最后这个逗号是允许的，加和不加都可以  

```Java
int[] c = new int[0];
```
1. 定义一个长度为0的数列也是可以的，这叫做空阵列，但是要注意和```null```不同。  


## 3.10.2 访问Array中的元素 
- 以上面```a```array为例，其中的元素从0~99，阵列创建以后，你可以访问每个值来给他们赋值。
- 当你初始化一个阵列之后，里面的初始值是主要注意的，int的数列，初始值为0；boolean的数列，初始值为false；如果是对象数列，则初始值为null。例如String，需要**注意**的是，对象阵列声明了之后，最好进行初始化，不然不小心用了对象的方法（nullPointerException），就会报错。  
```Java
for(i = 0; i<String.length(); i++){
	names[i] = "";
}
```

## 3.10.3 The "for each" Loop 
在Java中，可以用一种特殊的for循环来避免普通for循环中，一直要重复考虑index的问题。其结构为
```Java
for (variable variableName : collection) {
	statement;
}

for (int i : b){
	System.out.println(i);
}
```  
当然，打印也可以不用这种方法，直接调用```System.out.println(Arrays.toString(b));```就可以打印出来  

## 3,10.4 Array的复制：
1. 如果你通过简单的```=```来赋值，那么这两个value是连在一起的，改变其中一个，另外一个也会改变，因为他们指向的是同一个内存地址：
```Java
int[] aArray = {1,2,3,4,5};
int[] bArray = aArray;
bArray[1] = 5;  // aArray[1]也会变成五
```  
如果你要赋值数列，并且新的数列不会干扰旧的数列，那么需要用以下方法:
```Java
bArray = aArray.copyOf(aArray, length);
bArray = aArray.copyOfRange(aArray, int start , int end);
```  
第二个参数是用来扩大数列的长度，以帮助你增加数值，如果你需要的话。  

## 3.10.5 Command-Line Parameters 
回过头来看main函数：
```Java
public static void main(String[] args){
	if(args[0].equals("-g")){
		statementl;
	}
}
```
1. 这里的args表示接收一系列的字符串，并且这个内容可以在main中被使用,例如如上面这个程序，假设叫做Message，那么当我用编译器运行```Java Message -g```的时候，系统会自动运行```-g```对应的指令。这个有点像linux中各种不同的-符号可以进行不同操作一样。  

## 3.10.6 数列排序  
要排序一个数列，直接用Arrays中的sort方法即可。在Java中，排序使用```QuickSort```这一演算法实现。  
  
## 3.10.7 多维数列
多维阵列具有多个index，他们是提供给像是Table这样的数据集用的，定义方法如下：
```Java
double[][] balances = new double[NYEARS][NRATES]; //10，6
int[][] magicSquare = {
	{16,3,2,13},
	{5,10,11,8},
	{9,6,7,12},
	{4,15,14,1},
};
```
1. 注意，for each循环在二维数组中的使用有点不一样，要使用巢状的写法。  
  
要打印2维阵列，使用方法：
```Java
System.out.println(Arrays.deepToString(a));
```  
1. **注意：**这里需要注意，其实Java并没有所谓的多维阵列，例如上面的```balances[][]```,其实就可以看作是不同的两组阵列，第一个阵列中存储着10个元素，每个元素存储着六个浮点数，如下图：

![多维矩阵](https://raw.githubusercontent.com/jerrysheen/JavaBook/master/img/Char3/char3.10.8.PNG)

## 3.10.8 Ragged Arrays（不规则阵列）
承接上一部分内容，将二位矩阵拆分成这样的结构后，我们来看一看```balances[i]```是什么？其实他就是一个table中的第ith row，知道了这个以后，我们可以来做row与row之间的互换：
```Java
double[] temp = balances[i];
balances[i] = balances[i+1];
balances[i+1] = temp;
``` 
甚至通过这一个思想，我们还可以来做一个不规则的矩阵，像是：
```Java
// 1
// 2 2 
// 3 5 6
// 4 3 5 6
// 5 2 7 7 8
int[][] tables = new int[ROWS][];
for (int i=0 ; i<ROWS; i++){
	tables[i] = new int[i+1];
}
```
1. 由上述代码即可完成一个三角矩阵的初始化。