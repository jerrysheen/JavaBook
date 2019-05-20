# 3.9 Big Number
如果基本的整数和浮点数数据类型不能满足需要，那么你需要```java.math```包中的```BigInteger```和```BigDecimal```来表示更大的数字。前者提供了任意精度的整数运算，后者提供了任意精度的小数运算。
1. 对于能用基本数据类型来表示的数字，使用```valueOf```来让他变为bigNumber：
```java
BigInteger a = BigInteger.valueOf(123);
```   
2. 对于不能用基本数据类型来表示的大叔，直接用构造函数加上string参数来写：
```java
Big Integer reallyBig = new BigInteger("22222222222222222222");
```  
3. 在BigNumber中，如果你要使用加减乘除算术，不能直接用符号，而是要使用方法：
```Java
BigInteger c = a.add(b);
BigInteger d = c.multiply(a);
```  
