Integer與int之間的區別
===
在JDK1.5之後引入了自動裝箱（autoboxing）與自動拆箱（unboxing），這讓很多對java的初學者感到很疑惑，我剛才也是其中一員。

首先，有一些基本的概念需要瞭解：

1. `Ingeter`是`int`的包裝類，`int`的初值為0，`Ingeter`的初值為`null`。

2. `Integer`是一個類，用`Integer`聲明一個變量是一個對象類型（或者說引用類型）；`int`是基本類型，用`int`聲明的變量是非對象類型，即不能在其上調用方法。

3. `==`作用於對象上的時候，其比較的是對象的引用本身的值（或者說對象的地址更容易理解），而作用於基本類型的時候比較的就是基本類型的值。

然後，我們需要明白兩個基本概念：自動裝箱與自動拆箱

```java
Integer a = 1;
```

這就是一個自動裝箱，如果沒有自動裝箱的話，需要這樣
```java
Integer a = new Integer(1) 
```
```java
int b = a;
```
這就是一個自動拆箱，如果沒有自動拆箱的話，需要這樣：
```java
int b = a.intValue 
```
這樣就能看出自動裝箱和自動拆箱是簡化了基本數據類型和相對應對象的轉化步驟。

接下來我們會用具體的代碼敘述`Integer`與`int`之間的區別：
1. **`Integer x = 10`與`Integer y = new Integer(10)`不會相等。**
   
   因為這兩者在比較的時候不會經歷拆箱過程，後者的引用指向堆，而前者指向專門存放他的內存（-128~127的常量池），他們的內存地址不一樣，所以為false。
    ```java
    public static void main(String args)
    { 
        Integer i = 10; 
        Integer j = new Integer(10); 
        System.out.println(i == j); //false
    }
    ```
2. **兩個都不是new出來的`Integer`，如果數在-128到127之間，則是true,否則為false。**

    ```java
    public static void main(String args) 
        { 
            Integer i = 10; 
            Integer j = 10; 
            System.out.println(i == j); //true 
        }
            
        public static void main(String args) 
        { 
            Integer i = 128; 
            Integer j = 128; 
            System.out.println(i == j); //false 
        }
    ```
    java在編譯`Integer i = 10`的時候,被翻譯成`Integer i = Integer.valueOf(10);`

    JDK源碼的valueOf函數式這樣的：

    ```java
    public static Integer valueOf(int i) 
    { 
        assert IntegerCache.high >= 127; 
        if (i >= IntegerCache.low && i <= IntegerCache.high) 
            return IntegerCache.cache[i + (-IntegerCache.low)]; 
        return new Integer(i); 
    }
    ```
    對於-128到127之間的數，會進行緩存，`Integer i = 10`時，會將10進行緩存，下次再寫`Integer j = 10`時，就會直接從緩存中取，就不會new了。
    所以第一段代碼的結果是true.

    反之，對於-128到127之外的數，參照`valueOf`函數的最後一行，會返回一個new(新的)`Integer`對象。

    當`Integer i = 128`的時候產生了第一個Integer對象，`當Integer j = 128`的時候產生了第二個Integer對象，兩個對象的地址不同。

3. **當兩者都是new Integer出來的時候，兩者肯定不相同。**
    ```java
    public static void main(String args) 
    {  
        Integer i = new Integer(10); 
        Integer j = new Integer(10); 
        System.out.println(i == j); //false 
    }
    ```
    這裡有個比較，就是`Integer i = 10` `Integer j = 10`是相同的，因為這時候i和j取得的都是緩存中值為10的地址（參照2）

4. **如果`Integer`類型與`int`類型比較，只要兩者的值相等，則`Integer`類型與`int`類型就相同。**
    ```java
    public static void main(String args) 
    { 
        Integer i = 128; 
        Integer j = new Integer(128); 
        int k =128; 
        System.out.println(i == j); //false
        System.out.println(i == k); //true
        System.out.println(j == k); //true 
    }
    ```
    因為當Integer類型與int類型比較的時候，java是**向下轉型**的，所以Integer類型會自動拆箱變成int類型，所以，兩者在比較的時候會是比較數值。