# javascript学习笔记

### 1.JS的编写位置

##### 1.写在script标签内

```html
<script type="text/javascript">
    alert(123);
</script>
```

##### 2.写在标签内部,结构和行为耦合，不推荐使用

```html
<button onclick="alert(123)">456</button>
<a href="javascript:alert(789)">456</a>
```

##### 3.写在外部文件，通过script标签引入，写到外部的文件中，可以在不同的页面同时使用，推荐使用，script标签一旦用于引入外部文件，就不能再编写代码了，即使编写了，浏览器也会忽略，如果有需要，可以再新建一个script标签

```html
<script src="文件地址"></script>
```



### 2.注释

##### 1.单行注释

```html
//alert(123)
```

##### 2.多行注释

```
/*
	alert(123);
	alert(456);
*/
```



### 3.JS语法规则

##### 1.严格区分大小写

##### 2.每一条语句以分号结尾

##### 3.JS会忽略多个空格和换行，可以通过空格和换行对代码格式化,""必须写在一行，否则需要使用+号进行拼接



### 4.字面量和变量

##### 1.字面量是不可以改变的，例如1，2，3，4，5

##### 2.变量可以用来保存字面量，变量的值是可以随意改变的，js中通过var来声明一个变量并同时给它附上初始值，变量可以对字面量进行描述

```html
var a=123;
var age=20;
```

##### 3.在JS中，未声明的变量直接使用会报错，变量必须先声明后使用，声明过但是未赋值的变量默认为undefined



### 5.标识符

##### 1.在JS中所有的可以由我们自主命名的都可以称为标识符，例如变量名，函数名，属性名

##### 2.标识名中可以包含字母，数字，_，$，标识符不能以数字开头，标识符不能是ES中的关键字或者保留字

##### 3.标识符一般采用驼峰命名法



### 6.数据类型

##### 1.基本数据类型

###### （1）.字符串类型(String)

```html
1.在JS中字符串需要用引号引起来,即可以用单引号也可以用双引号,但不能混合着用
var str="hello world";
2.引号不能嵌套使用，嵌套使用需要使用转义符\对"进行转义
var str="我说:\"今天天气真不错\"";
3.可以在单引号里面嵌套双引号
var str='我说:"今天天气真不错"';
4.\n表示换行,\t表示制表符，\\表示\

```

###### （2）.数值类型(Number)

```
1.在JS中所有的数值类型都是Number类型的数据,包含整数，浮点数
2.使用typeof运算符可以检查一个变脸的类型,使用方式typeof 变量名
var a=10;
alert(typeof a);
3.infinity表示正无穷,-infinity表示负无穷,使用typeof infinity也会返回Number
4.NaN表示一个特殊的数字，表示Not a Number,使用typeof NaN也会返回Number
5.在JS中进行整数计算基本能保证精确,进行浮点数计算可能得到一个不精确的结果,所以千万不要使用JS进行精确度比较高的计算
var c=0.1+0.2; c的结果为0.3000000000004
```



###### （3）.布尔值(Boolean)

```
布尔值只有两个,true表示逻辑上的真,false表示逻辑上的假,用于逻辑判断
使用typeof检查一个布尔值的时候,会返回一个boolean
```



###### （4）.空值(Null)

```
Null类型的值就只有一个null
var a=null;
null这个值专门用来表示一个为空的对象
使用typeof null返回的是Object
```



###### （5）.未定义(Undefine)

```
Undefined类型的值只有一个undefined
只声明未定义的变量就是undefined类型的
var a;
console.log(typeof a)返回的结果就是undefined
使用typeof检查一个undefined时也会返回一个undefined
```



### 7.强制类型准换

##### 指将一个数据类型强制转换为其他的数据类型

##### 类型转换指:将其他的数据类型转换为String，Number，Boolean

##### 1.将其他数据类型转换为String

```html
方式一:调用被转换数据类型的toString方法
var a=123;
a=a.toString();
注意null和undefined没有方法可以调用,如果调用他们的方法会报错

方式二:调用String函数,并将转换的数据作为参数传递
var a=123;
a=String(a);
String()方法可以将null和undefined转换为对应的字符串
使用String()做强制类型转换时实际上还是调用的toString()，对于null和undefined,会将null和undefined直接转换为"null"和“undefined”


```

##### 2.将其他数据类型转换为Number

```
方式一:
使用Number函数

1.字符串转为Number
var a=“123”;
a=Number(a);
如果是纯数字类型的字符串,则直接转换为数字,如果字符串中有非字符串的内容,则转换为NaN,空字符串或全是空格转换为0

2.布尔值转为Number
var a=true;
a=Number(a); true转换为1
var a=false;
a=Number(a); false转换为0

3.null转为Number为0

4.undefined转为Number为NaN


方式二:
专门用来将字符串转换为Number
1.parseInt()把一个字符串转换为一个整数
var a="12a3px";
a=parseInt(a); 返回结果为12，parseInt()将字符串从左到右开始截取数字,当遇到第一个不为数字类型的字符时,停止截取,并将截取到的字符转换为数值

2.parseFloat()把一个字符串转换为一个浮点数
var a="12.3px";
a=parseFloat(a);返回结果为12.3,和parseInt()效果类似
如果对非String类型使用parseInt()和parseFloat,会将其转换为String,然后在操作
```

##### 3.将其他数据类型转换为Boolean

```
调用Boolean()方法将其他类型的数据转换为布尔值
1.数值转为布尔值,除了0和NaN会转为false,其余都转为true
2.字符串转换为布尔值,除了空串为false,其余的都为true
3.null转为布尔值为false
4.undefined转为布尔值为false
5.对象也会转换为true
```

### 8.运算符(操作符)

##### 1.数学运算符

```html
+:可以对两个值对加法运算,并将结果返回,当对非Number类型的值进行运算的时候,会将这些值转换为Number在计算,+还可以作为字符串拼接,任何值和NaN做运算结果都为NaN,任何值和字符串做+运算,都会转换为字符串,再进行运算,因此可以将一个变量转换为字符串的时候可以+上一个空串。

-:可以对两个变量做减法运算

*:可以对两个变量做乘法运算

/:可以对两个变量做除法运算

%:取模(取余数),9%2=1
任何值做- * /运算都会转换为Number进行运算,我们可以利用这一点做一些隐式的类型转换
```

##### 2.一元运算符(只需要一个参数)

```html
typeof:取变量类型
+:正号,可以运用正号将变量转换为Number类型
-:负号,可以运用负号将变量转换为Number类型
```

##### 3.自增和自减

```html
++:a++,可以使变量a自增1,++a也是自增1,a++先使用变量a,再自增1,++a使a先自增1,再使用变量a
--:a--,可以使变量a自减1,--a也是自减1,a--先使用变量a,再自减1,--a使a先自减1,再使用变量a
```

##### 4.逻辑运算符

```html
&&：逻辑与,当表达式都为真的时候,结果才为真
||：逻辑或,当表达式有一个为真的时候,结构就为真
！:逻辑非,对表达式取反,真取反为假,假取反为真,对一个值两次取反,不会改变原值,对非布尔值取反,先将值转换为Boolean类型,可以多任意类型的值取两次反,将其转换为Boolean类型
```

##### 5.赋值运算符

```html
=:var a=10;将字面量10赋值给变量a
```

##### 6.关系运算符

```
>:判断左侧是否大于右侧,成立返回true,不成立返回false
<:判断左侧是否小于右侧,成立返回true,不成立返回false
>=：判断左侧是否大于或等于右侧,成立返回true,不成立返回false
<=：判断左侧是否小于或等于右侧,成立返回true,不成立返回false
==: 判断左侧是否等于右侧，只判断转换后的类型是否相等,如123=="123"返回true
===：判断左侧是否等于右侧,既判断左侧是否等于右侧,也判断运算符左右两侧的数据类型是否一致,两者都满足才返回true
                                    
如果两个字符串进行比较，比较的是两个字符串的Unicode编码,比较字符编码的时候是一位一位的比较
```

7.条件运算符(三元运算符)

```html
表达式1?表达式2:表达式3 如果表达式1的值为真,则执行表达式2,否则执行表达式3
```

### 9.语句块

##### 1.我们的代码是一条一条语句从上到下依次执行的,在JS中可以使用{}对语句进行分组,同一个{}中的语句可以称为是一组语句,他们要么都执行,要么都不执行.

```javascript
{
	alert(1);
	var a=3;
	document.write(456);
}
```



### 10.流程控制语句

##### 1.条件判断语句

```javascript
if(表达式){
	代码块;
}
if语句会对表达式进行判断，如果表达式的值为真,则执行代码块,如果为假,则不执行代码块
```

##### 2.条件分支语句

```javascript
1.if条件分支
if(表达式1){
	代码块1;
}else if(表达式2){
    代码块2;
}else{
    代码块3;
}
分别判断表达式1、表达式2、表达式3的值是否为真,如果某一个为真,则执行对应的代码块,并不再对其他的表达式进行判断了

2.switch()条件分支
switch(num)
    case a:
    		表达式1;
    		break;
    case b:
    		表达式2;
    		break;
    case c:
    		表达式3;
    		break;
    ...
    default 表达式n
    
判断num的值和后面case里面哪一个的值相等,则执行对应的表达式
    
总结:一般来说,if的分支语句和switch分支语句的效果类似,但是如果分支条件大于或等于4个,则倾向于使用switch格式来写条件分支语句
```

##### 3.循环语句

```javascript
1.for循环
for(循环变量初始化;循环条件;循环变量改变){
	代码块;
}

2.while循环
while(循环条件){
	代码块;
	循环变量改变;
}

3.do...while()循环
do{
	代码块;
	循环变量改变;
}while(循环条件)

总结:三种循环的作用都是类似的,for循环和while循环中的代码块可能一次都不会执行,do..while()的循环则至少会执行一遍
```



### 11.对象

##### 1.简介:

##### 基本数据类型都是都是单一的数值，数值和数值之间没有任何联系，但是如果需要表达一个复合的数据类型，如表示一个人，人的属性包含身高，姓名，体重，则需要使用一种新的数据类型(对象)，对象中可以包含多个不同基本数据类型的属性.

##### 2.对象的类型

###### （1）.内建对象，由ES标准中定义的对象，再任何的ES实现中都可以使用，如Boolean，String，Number。

###### （2）.宿主对象，由JS得运行环境提供的对象，目前来讲主要指浏览器提供的对象。

###### （3）.自建对象，由开发人员自己创建的对象。

##### 3.对象的创建

```javascript
1.使用new创建对象
var obj=new Object();

2.使用对象字面量的方式创建对象
var obj={name:"猪八戒"};

3.使用工厂方法创建对象
function createPerson(age,name,sex){
    var obj=new Object();
    obj.name=name;
    obj.age=age;
    obj.sex=sex;
    return obj;
}

4.使用构造函数创建对象,构造函数和普通函数的创建方式没有区别,构造函数需要使用关键字new来调用,表明该函数是用来创建对象
Person(age,name,sex){
    this.age=age;
    this.name=name;
    this.sex=sex;
}
var person=new Person(20,"zhangsan","man");
构造函数的执行流程
1.新建一个对象
2.将新建的对象设置为函数中的this
3.逐行执行函数中的代码
4.将新建的对象作为返回值返回

使用构造函数创建的对象成为类的实例,使用instanceof可以检查一个对象是否是某个类的实例,任何的对象和Object做instanceof检查的时候都会返回true
```

##### 4.给对象的属性赋值

```javascript
var obj=new Object();
obj.name="zhangsan";
```

##### 5.读取对象的属性值

```javascript
var obj = new Object();
obj.name = "zhangsan";
var name = obj.name;
var name = obj["name"];  更加灵活,[]中可以直接传递一个变量
这两种方式都可以取出对象的属性值,如果读取对象中不存在的属性,不会报错,读出来的结果为Undefine
```

##### 6.修改对象的属性值

```javascript
var obj = new Object();
obj.name = "zhangsan";
Console.log(obj.name);
obj.name = "lisi";
Console.log(obj.name);
```

##### 7.删除对象的属性

```javascript
var obj = new Object();
obj.name = "zhangsan";
Console.log(obj.name);
delete obj.name;
Console.log(obj.name);
```

##### 8.使用in检查对象中是否包含某个属性

```javascript
var obj = new Object();
obj.name = "zhangsan";
Console.log("name" in obj);
如果对象中包含name属性,则返回true,否则返回false
```

### 12.函数

##### 1.函数的简介:函数也是对象，封装了一段代码的逻辑，用来实现某一功能，函数能实现代码的复用

##### 2.函数的创建

```javascript
函数声明
function test(param1,param2){
	函数体;
}

函数表达式
var test=function(param1,param2){
	函数体;
};
JS属于弱类型语言,参数没有类型,当实参的个数大于形参,多余的参数不会被赋值,当实参个数小于形参,多余的形参为undefined
```

##### 3.立即执行函数

```javascript
立即执行函数只会执行一次,
将函数使用()括起来,后面再加上一个()
(function(param1,param2){
	console.log(param1+param2);
})(1,2)

(function(param1,param2){
	console.log(param1+param2);
}(1,2))
```

### 13.this

##### 1.简介:函数每次调用的时候都会隐式的参数this,用于指向函数执行的上下文对象。

##### 2.以函数的方式调用,指向的永远是window对象

```javascript
fun test(){
	console.log(this);
}
test();直接调用相当于调用window对象的test方法,此时输出的是window对象
```

##### 3.以对象的方法调用,指向的是调用者本身

```javascript
var obj={
    name="zhangsan";
    sayName=function(){
        console.log(this.name);
    }
}
```

### 14.原型

##### 1.简介:我们创建的每一个函数，解析器都会在函数中添加一个熟悉propotype，这个属性对应着一个对象，这个对象就是所谓的原型，如果函数作为普通函数调用这个propotype没有任何作用，当作为构造函数调用时，它所创建的对象中都会有一个隐含的属性，指向该构造函数的原型对象，我们可以通过——proto—来访问该属性

##### 2.原型对象就相当于一个公共的区域，所有同一个类的实例都可以访问到原型对象，我们可以将对象中共有的内容，统一设置到原型对象中

##### 3.当我们访问对象的属性或者方法时，会现在对象自身中寻找，如果有，则直接使用，如果没有，则会去原型对象中寻找

##### 4.以后我们创建构造函数时，可以将对象共有的属性和方法，统一添加到构造函数的原型中，这样不用为每一个对象添加，也不会影响到全局作用域，就可以使对象都拥有这些属性和方法



### 15.数组

##### 1.数组的创建

```javascript
var arr=new Array();
```

##### 2.数组的方法

```JavaScript

```

### 16.call和apply

##### 1.调用函数对象的call和apply方法，函数体内的this会指向传入的第一个参数对象

```javascript
function test(){
	方法体;
}
var obj={}
test.call(obj)
```

##### 2.区别:call传参是一个一个传的，apply传参需要封装到一个数组里面

```
1.使用call调用
function test(a,b){
	方法体;
}
var obj={}
test.call(obj,1,2)

2.使用apply调用
function test(a,b){
	方法体;
}
var obj={}
var param=[obj,1,2];
test.call(param)
```

### 17.arguments

##### 1.简介:在函数调用的时候，会隐式的传递一个封装的对象arguments，arguments是一个类数组对象,它也可以通过索引操作数据，也可以获取长度，在调用函数时，我们所传递的实参都会在arguments中保存

##### 2.arguments对象中有一个属性callee，对应的就是当前正在执行的函数对象





### 18.正则表达式

##### 1.简介：定义字符串的规则，或者将字符串中符合规则的内容提取出来

##### 2.创建正则表达式对象

```javascript
var reg=new RegExp(正则表达式，匹配规则);
RegExp.test(str) 判断str是否满足正则，满足返回true，不满足返回false

var reg=new RegExp('a'); 用来判断字符串中是否包含a，区分大小写

使用字面量创建正则表达式,更加简单,但是使用构造函数更加灵活,构造函数可以传递变量
var reg=/正则表达式/匹配规则;

```

##### 3.匹配规则参数

###### i:忽略大小写

g:全局匹配

可以为一个正则表达式设置多个匹配模式，顺序无所谓

##### 4.正则表达式书写

```javascript
/a|b/   匹配字符串中是否包含a或者b
/[ab]/  匹配字符串中是否包含a或者b
/[a-z]/ 匹配字符串中是否包含任意小写字母  /[A-Z]/ 匹配字符串中是否包含任意大写字母
/[A-z]/ 匹配字符串中是否包含任意字母
/a[bcd]e/ 匹配abe或者ace或者ade
/[^ab]/ 如果字符串中除了a和b之外还有别的字符，返回true
/[^0-9]/ 除了数字之外是否含有别的字符
/ba{3}/ 匹配字符转是否包含baaa,量词只对前面的一个字符起作用
/ba{1,3}/ 匹配ba或者baa或者baaa
/ba{1,}/ 匹配ba(aaaaa...)
/ba+/ 匹配ba(aaaaa...)  +至少一个
/ba*/ 匹配b(aaaaa...)   *0个或多个
/ba?/ 匹配b或者ba        ？代表一个或者0个
/^a/  匹配以a开头
/a$/  匹配以a结尾
/^a$/ 完全匹配a,如果正则表达式以^开头$结尾，则必须完全匹配

```



### 19.DOM(Document Object Model)

##### 1.简介：通过JavaScript可以操作网页

##### 2.节点(Node),是构成我们网页最基本的组成部分，网页中的每一个部分都可以成为是一个节点，不如Html标签，属性，文本，注释，整个文档都是一个节点，节点分为四种，文档节点，元素节点，属性节点，文本节点![image-20200814225313553](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20200814225313553.png)

##### 3.事件：用户和浏览器的交互行为，我们可以在事件的对应的实践中设置一些Js代码，当事件被触发时，这些代码被执行

