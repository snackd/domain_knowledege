# Domain Knowledege Record
###### tags: `CS`

[知識記錄](https://hackmd.io/@zz8yeJXcQYOjqL6CsPNdlg/HkwOZHUk3)

[TOC]

### Compilation vs. Translaction

References:[編譯 vs. 直譯](https://ithelp.ithome.com.tw/articles/10214510)

#### 編譯語言(Compilation)

1. 在程序執行時先會透過編譯器將你的程序編譯成電腦看得懂的機器碼。
![程序轉成機器碼](https://i.imgur.com/zujWV2J.png)
2. 預先定義變數類別和類別檢查等等。
3. 編譯語言多數是靜態語言，比如：C, C++, Swift。
> 程序一次性全部編譯完再執行

#### 直譯語言(Translaction)

1. 直譯語言的運行器會將一行一行的程式碼先後編譯成機器碼，讓程序的類別檢測更靈活。
2. 比起編譯語言更為彈性、較「符合人性」，但缺點是較為緩慢的運行速度。
3. 直譯語言的模塊甚至都以編譯語言所寫成以加快速度。比如：Javascript 、Python、Shellscript、PHP，被認為是Scripting Language。
> 程序一行一行執行

#### 彼此差異：優缺比較
> 編譯語言
優點：執行速度較為快速
缺點：除錯較為緩慢、不易開發

編譯語言的可執行檔是可以獨立運行的

比如：C++ 雖然只能在新電腦中編譯，但他的可執行檔甚至連不支援C++的電腦，都可以運行

> 直譯語言
優點：容易除錯、開發較為快速
缺點：執行速度較為緩慢

直譯語言需要有適合的執行環境，或是虛擬環境(VM)才可以執行
比如：Python3 程式碼便需要有在有安裝 Python3 的電腦中才可以運行

### Statically Typed vs. Dynamically Typed

References:[動態 vs. 靜態](https://growingdna.com/language-type-compiler/)

#### 靜態語言(Statically Typed Languages)

靜態代表程式語言：Java, C#

1. 撰寫時必須使用明確的型別宣告
2. 一旦宣告型態後，在執行時期時無法任意更換型別，否則會發生錯誤
3. 編譯時期(Compile Time)確認與檢查型別，一旦有變數誤用或資料型態上的 Bug，在編譯時期就能發現，降低執行時期的風險。

> 以 Java 示範錯誤案例(Error Case)：
```=Java
# Java
int x;
x = "Hello"
```
> 型別宣告為整數，卻塞了個非整數的值
當輸出Output 會報錯如下：
```=Java
HelloWorld.java:5: error: incompatible types: String cannot be converted to int
```

靜態語言又可細分：
1. 顯性型別(explicitly typed)：型別是語法宣告的一部份，從語法就能得知，比如：Java, C
2. 隱性型別(implicity typed)：型別是透過編譯過程的推導得知，比如：Ocaml、Haskell


#### 動態語言(Dynamically Typed Languages)

動態代表程式語言：Python、PHP、Ruby

1. 撰寫時不用明確的型別宣告
2. 執行時，變數能任意更換型別
3. 與靜態語言相反，是在執行時期(Runtime)確認與檢查型別

> 以 PHP 示範更改型態案例：
```=PHP
$a = 123;
echo $a;  // print: 123
$a = "Hello";
echo $a;  // print: Hello
```

### Strongly Typed vs. Weakly Typed

Refernces: [強型別 vs. 弱型別](https://ithelp.ithome.com.tw/articles/10202260)

#### 強型別(Strongly Typed)
偏向不容忍隱性的型別轉換，型別檢查上較為嚴格。

> 以 Java 示範錯誤案例(Error Case)：
```=Java
# Java
int x = 123 + "456";
System.out.println(x);
```
> Output:
```=Java
HelloWorld.java:4: error: incompatible types: String cannot be converted to int
```

> 你必須用 Java 能接受的方式，明確表明型態：
```=Java
# Java
int x = 123 + Integer.parseInt("456");
System.out.println(x);
```
＞ Output:
```=Java
579
```


#### 弱型別(Weakly Typed)
偏向容忍隱性的型別轉換，型別檢查上較為寬鬆
> 以 PHP 示範更改型態案例：
```=PHP
# PHP
$x = 123 + "456";
echo $x;
```
> Output:
```=PHP
579
```

弱型別最常導致 Bug 的情境，除了混用不同型別去數學運算或字串串接，另一個就是允許不同型別之間的比對。

以 PHP 為例，要比對兩個值，提供了兩種運算子：
1. ==：寬鬆比對，只比對兩值的內容。
2. ===：嚴謹比對，比對兩值的型別和內容。
```=PHP
echo ("111" == 111) ? "Yes" : "No";     // "Yes"
echo ("111" === 111) ? "Yes" : "No";    // "No"
```

### 程式語言型態比較
程式語言強/弱型別列表：
| 靜態/動態語言 | 強型別/弱型別 | 程式語言 |
| -------- | -------- | -------- |
| 靜態     | 強     | Java, C#     |
| 靜態     | 弱     | C/C++     |
| 靜態     | 強     | Python, Ruby     |
| 靜態     | 弱     | Perl, PHP, JavaScript     |

程式語言強/弱型別象限分佈圖：
![](https://i.imgur.com/bWp3oql.jpg)


### 靜態變數 (Static Variable)

Refernces: [靜態變數，為何宣告 static?](https://ithelp.ithome.com.tw/articles/10184803)

#### 原理

程式被組譯後都可以得到程式/物件的大小，當作業系統(OS)啟動該程式的時候，就會將程式掛載在記憶體中，並且賦予一個記憶體位置，並跳躍至該程式的啟動區域執行。

當程式中出現new的時候，會跟記憶體申請記憶體空間，當記憶體擁有對應的大小的記憶時就會將其提供給該程式使用，而該程式也能針對該區域的記憶體進行讀寫。

static變數就是在載入程式後會主動配給記憶體給程式(僅一次)，後續無論實例化多少次，記憶體位置都一樣。

#### 使用方法
使用static關鍵字可以讓程式被OS載入時就被儲存於記憶體中，直到Application結束為止。如下：
```=Java
# Java
private static float PI = 0.0f;  //靜態變數
private float radius = 0.0f;     //一般變數
```
> 靜態建構函式只會執行一次

#### 優、缺點
實務上將公共變數全部設定為靜態變數，例如上述物件中含有一個PI的定義。

優點：共享記憶體，相對較節省記憶體
缺點：須注意存取權限、存取時機，避免其他程序誤取。

### 全域變數 & 區域變數
References: [全域變數 & 區域變數](https://ithelp.ithome.com.tw/articles/10206034)

#### 全域變數

定義在函式外的變數，其有效範圍是整個程序。

所有函式外定義的變數為全域變數，可以用在主程式中，也能在各函式中作使用。

> 範例：
```=python
# Python

x = 5         #全域變數
def f1():
    y = 6         
    print(x+y)
def f2():
    y = 1
    print(x+y)    

f1() // print: 11
f2() // print: 6
```

#### 區域變數

定義在一個函式中的變數，其有效範圍是該涵式內。

在一個函式中所使用的變數稱為區域變數，它的作用範圍只有在該函式內部，所以不同的涵式中可以有相同名稱的變數，它們在各自的涵式中互不干擾。

當函式執行完畢，區域變數所占有的記憶體空間也會被釋放。

> 範例：
```=python
# Python
def f1():
    x = 5         #區域變數
    y = 6         #f1()中的y跟f2()的y不相干
    print(x+y)
def f2():
    y = 1
    print(x+y)    #錯誤! 不能取到x值(區域)

f1()
f2()
```

> 如果函式中定義的區域變數與全域變數名稱相同，則區域變數會隱藏全域變數。
```=python
x = 'outside'       #全域變數
y = 'global'
def f():
    x = 'inside'    #覆蓋掉
    print(x)
    print(y)

f() 
print(x)

>>>
inside
global
outside
>>>
```

在函式中對全域變數進行設定值運算，或改變全域變數值，皆會發生錯誤，如：
```=python
a = 'abc'
def d():
    b = a
    a = 10         #改變全域變數，錯誤
   
    a = a+'inside' #右方a不存在，錯誤    
    print(a)
    
d()
print(a)
```

為了告知函式某變數為全域變數，請使用「global」敘述：
```
a = 'abc'
def d():
    global a        #宣告a為全域變數
    a = a+'inside'
    print(a)
    
d()

>>> 
abc inside
>>> 
```
