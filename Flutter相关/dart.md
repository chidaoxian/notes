# Flutter系列1-Dart基础笔记

## 1、变量声明及命名规则

### 1、简介

Dart的开始处，是因为我看见了flutter。其实对于一个会 javaScript 和 java 的来说这些都是理所当然的。我学习的时候比较喜欢记笔记所以我记录一些这些东西。

其实如果会一些语言，Dart根本不需要花时间。

### 2、声明

dart 是一个强大的脚本类语言，可以不预设先定义变量类型，自动会类型推倒

dart 中定义变量可以通过var关键字可以通过类型来申明变量

如： 

```dart
var str = 'this is var'；
String str = 'this is var';
int str = 123
```

```dart
void main() {
    var str = '你好dart';
    var numx = 1234;
    print(str);
    print(numx);
    
    String str1 = '你好dart';
    print(str);
    
    int numx1 = 123;
    print(numx1);
}
```

定义报错：

```dart
var str = '';
str = 1234; //报错 A value of type 'int' can't be assigned to a variable of type 'String'.
print(str)；
```



```dart
 String str = 12312;//报错 A value of type 'int' can't be assigned to a variable of type 'String'.
```

 ### 3、命名规则

一、Dart命名规则：

1、变量名称必须有数字、字母、下划线和美元符号（$）组成

2、注意：标识符开头不能是数字

3、标识符不能是保留字和关键字

4、变量的名字是区分大小写的如：age和Age是不同的变量。在实际的运用中也建议不要用一个

5、标识符（变量名称）一定要见名思意：变量名称建议用名词，方法名称建议用动词



二、Dart常量：final和const修饰符

const 值不变 一开始就得赋值

final 可以开始不赋值但是只能赋值一次；而final不仅仅有const的编译时常量的特性，最重要的它是运行时常量，并且final是惰性初始化，即在运行时第一次使用前才初始化。可以见下面定义时间的例子。

永远不变的量，例如 PI = 3.1415926，请使用final或const修饰它，而不是使用var或其他变量类型

```dart
 final name = "Bob";
 final String strname = "Bobby";

 const bar = 1000000;
 const double a = 1.123 * bar;

 final date1 = new DateTime.now();
 const date2 = new DateTime().now();//报错，New expression is not a constant expression.
```



## 2、Dart的数据类型

Dart中支持以下数据类型：

一、常用数据类型：

numbers（数值）：int、double

String（字符串）：String

Booleans（布尔）：bool

List（数组）：在Dart中，数组是列表对象，所以大多数人只是称它们为列表

Maps（字典）：通常来说，Map是一个键值对相关的对象。键和值可以是任何类型的对象。每个 **键**

1、number类型

int 必须时整型

double 既可以是整型也可以是浮点型

2、String类型

String 定义时 “”“  单引号定义会保持格式

```dart
  String str1 = '111';
  String str2 = "222";
  String str3 = ''' 111 
  111''';

  print(str1);
  print(str2);
  print(str3);
```

运行结果：

![1612704870053](D:\md图片\1612704870053.png)

String字符串的拼接

```dart
  String str1 = '你好';
  String str2 = "Dart";

  print("$str1 $str2");
  print(str1 + str2);
```

3、Boolean类型

```dart
  bool flag = true;
  print(flag);
```

4、List（数组/集合）

```dart
var l1 = ['aaa','bbb','ccc'];
print(l1);
print(l1.length);
print(l1[0]);
//输出：
//[aaa, bbb, ccc]
//3
//aaa

var l2 = new List();
l2.add("111");
l2.add("222");
l2.add("333");
print(l2);
//输出：[111, 222, 333]

//定义list指定类型
var l3  = List<String>();
l3.add("111");
l3.add(222);//报错，Error: The argument type 'int' can't be assigned to the parameter type 'String'.
print(l3);
```

5、Maps（字典）

```dart
//key必须加上 " 号
var person = {
  "name" : "张三",
  "age" : 20,
  "like" : ["111","222"]
};
print(person);
//输出：{name: 张三, age: 20, like: [111, 222]}
print(person["name"]);
//输出：张三

var p = new Map();

p["name"] = "张三";
p["age"] = 20;
p["like"] = ["111","222"];

print(p);
//输出：{name: 张三, age: 20, like: [111, 222]}
```

二、很少用的数据类型：

​	Runes：Rune是UTF-32编码的字符串。它可以通过文字转换成符号表情或者代表特定的文字。

```dart
  var clapping = '\u{1f44f}';
  print(clapping);
  print(clapping.codeUnits);
  print(clapping.runes.toList());

  Runes input = new Runes('\u2665 \u{1f605} \u{1f60e} \u{1f47b} \u{1f596} \u{1f44d}');

  print(new String.fromCharCodes(input));
```

​	Symbols：Symbol对象表示在Dart程序中声明的运算符或标识符。

三、判断数据类型

is  关键字判断数据类型

```dart
var str = '1234';

if(str is String){
  print('是String类型');
}else {
  print('其他');
}
//输出：是String类型
```

## 3、Dart算术运算符/条件表达式/类型转化

### 1、运算符

1、算术运算符

```
+  -  *  /  ~/(取整)  %
```

2、关系运算符

```
==  !=  >  <  >=  <=
```

3、逻辑运算符

```
!  &&  ||  
```

4、赋值运算符

```
基础赋值运算符 =  ??=
复合赋值运算符 +=  -=  *=  /=  %=  ~/=
```

```dart
int b =10;
b??= 23;
print(b);//输出：10

int b ;
b??= 23;
print(b);//输出：23

//上述  ??=  表示如果b为空的话，才进行赋值操作
```

### 2、条件表达式

1、if  else   switch  case

2、三目运算符

```dart
bool flag = true;
String c = flag? 'true':'false';
print(c);//输出true
```

3、??  运算符

```dart
var a ;
var b = a ?? 10;
print(b);//输出10

var a = 7 ;
var b = a ?? 10;
print(b);//输出7
```

### 3、类型转化

1、number与String类型之间的转换

number类型转换成String类型  toString()

String类型转换成number类型  parse

```dart
String str = '123';
var numx = int.parse(str);
print(numx is int);//输出true
```

2、其他类型转换成Booleans类型

## 4、Dart循环语句

1、for基本语法

```dart
for(int i = 1 ; i <= 100 ;i++){
  print(i);
}
```

2、while/do...while

```dart
int  i = 1;
while(i <= 10){
  print(i);
  i++;
}

do{
  print("总会执行一次");

}while(i < 2);
```

3、continue/break

continue：结束本次循环，但是还是会继续执行当前循环。

break：跳出当前循环体，结束当前循环，但是只能向外跳出一层。

## 5、Dart集合类型List/Set/Map

### 1、List

1、常用属性

length（长度）、reversed（翻转）、isEmpty（是否为空）、isNotEmpty（是否不为空）

2、常用方法

add（增加）、addAll（拼接数组）、indexOf（查找，需传入具体值）、remove（删除，需传入具体值）、removeAt（删除，传入索引值）、fillRange（修改）、insert(index,value)指定位置插入、insertAll(index,list)指定位置插入List、toList（其他类型转化成List）、join（List转换成字符串）、split（字符串转换成List）

### 2、Set

set是没有顺序且不能重复的集合。

### 3、Map

1、常用属性

keys：获取所有的key值，values：获取所有的values值，isEmpty：是否为空，isNotEmpty:是否不为空

2、常用方法

remove(key)：删除指定key的数据、addAll({...})：合并映射，给映射内增加属性、containsValues：查看映射内的值，返回true/false

### 4、循环语句 forEach map where any every

```dart
  List myList = ["111", "222", "333"];
  myList.forEach((value) {
    print(value);
  });
//输出：
//111
//222
//333
  List myListnumx = [1, 2, 3, 4];

  var newList = myListnumx.map((e) {
    return e * 2;
  });
  print(newList);//(2, 4, 6, 8)

  var newListWhere = myListnumx.where((e) {
    return e > 2;
  });
  print(newListWhere);//(3, 4)

  //只要有一个满足条件即返回true
  var f = newList.any((element) {
    return element > 2;
  });
  print(f);//true

  //全部满足返回true
  var d = newList.every((element) {
    return element > 2;
  });
  print(d);//false
```

## 6、Dart中的函数

### 1、函数的定义

```dart
void main(List<String> args) {
  var n = getnumx();
  print(n);//123
  printInfo();//自定义方法！
}

void printInfo() {
  print("自定义方法！");
}
int getnumx() {
  return 123;
}
```

```dart
void main(List<String> args) {
  print(sum(1,2));//3
  print(sumd(1,2));//3
}

int sum(int a,int b){
  return a+b;
}

int sumd(a,b){
  return a+b;
}
```

### 2、可选参数

```dart
void main(List<String> args) {
  print(getStr("xxx"));//xxx
  print(getStr("xxx",12));//xxx   12
}

String getStr(String name,[int age]){
  if(age != null){
    return "$name   $age";
  }else {
    return name;
  }
}
```

### 3、默认参数

```dart
void main(List<String> args) {
  print(getStr("xxx"));//xxx   男
  print(getStr("xxx","女",20));//xxx   20   女
 
}

String getStr(String name,[String sex = '男',int age]){
  if(age != null){
    return "$name   $age   $sex";
  }else {
    return "$name   $sex";
  }
}
```

### 4、命名参数

注意：传参和函数那边的{ }里面的key定义一致。

```dart
void main(List<String> args) {
  print(getStr("xxx"));//xxx   男
  print(getStr("xxx",sex:"女",age:20));//xxx   20   女
 
}

String getStr(String name,{String sex = '男',int age}){
  if(age != null){
    return "$name   $age   $sex";
  }else {
    return "$name   $sex";
  }
}
```

### 5、箭头函数

```dart
main(List<String> args) {
  List list = ["111","222","333"];

  list.forEach((element) => {
    print(element)  //这里面不打分号，只能写一行，注意啊
  });
}
```

### 6、匿名函数

```dart
main(List<String> args) {
   //fun是匿名函数
   var fun = (){
    print("xxxx");
  };
  fun(); 
}
```

### 7、自执行方法

```dart
main(List<String> args) {
  ((){
    print("自执行方法！");
  })();
}
```

### 8、方法的递归

```dart
main(List<String> args) {
  var sum =1;
  fn(n) {
    sum+=n;
    if(n==0){
      return;
    }
    fn(n-1);
  }
  fn(100);
  print(sum);
}
```

### 9、闭包

全局变量：全局变量常驻内存、全局变量污染全局

局部变量：不常驻内存会被垃圾回收机制回收、不会污染全局

闭包实现：常驻内存但是不污染全局

闭包通俗点讲就是函数嵌套函数，并且返回里面的函数。

```dart
main(List<String> args) {
  fn(){
    var a = 1;
    return (){
      a++;
      print(a);
    };
  }
  var b = fn();
  b();//2
  b();//3
  b();//4
}
```

## 7、Dart中的对象

### 1、面向对象简介

面向对象编程（OOP）的三个基本特征是：封装、继承、多态

封装：封装是对象和类概念的主要特征。封装，把客观事物封装成抽象的类，并且把自己的部分属性和方法提供给其他对象。

继承：面向对象编程语言的一个主要的功能就是”继承“。继承可以说是一种能力，继承实际上也是为了提高代码的复用性和可扩展性。继承是使用已存在的类的定义作为基础建立新类的技术，新类的定义可以增加新的数据或新的功能，也可以用父类的功能，但不能选择性地继承父类。

多态：允许将子类型的指针赋值给父类类型的指针，同一个函数调用会有不同的执行效果。

Dart也不例外，所有东西都是对象，所有的对象都继承自Object类。

Dart可以说是一门使用类和单继承的面向对象语言，所有的对象都是类的实例，并且所有的类都是Object的子类。一个类通常由属性和方法组成。

### 2、类的创建

```dart
class Person{
  String name = "cdx";
  int age = 23;

  void getInfo(){
    print("${this.name}  ${this.age}");
    print(this.name + "  "+ this.age.toString());
  }

  void setInfo(age){
    this.age = age;
  }
}

main(List<String> args) {
  var p1 = new Person();
  print(p1.age); //23
  p1.getInfo();//cdx  23    cdx  23
  p1.setInfo(18);
  print(p1.age);//18
}
```

### 3、构造函数

```dart
class Person{
  String name = "cdx";
  int age = 23;
  //默认构造函数
  Person(){
    print("构造函数");
  }

  void getInfo(){
    print("${this.name}  ${this.age}");
  }
}

main(List<String> args) {
  var p1 = new Person();
}
//输出：构造函数
```

```dart
class Person{
  String name = "cdx";
  int age = 23;

  Person(String name , int age){
    this.name = name;
    this.age = age;
  }
  //简写形式
  // Person(this.name,this.age);

  void getInfo(){
    print("${this.name}  ${this.age}");
  }
}

main(List<String> args) {
  var p1 = new Person("zs",12);
  p1.getInfo();//zs  12

  var p2 = new Person("ls",16);
  p2.getInfo();//ls  16
}
```

注意：默认的构造函数只能定义一个。

### 4、命名构造函数

默认构造函数只能定义一个但是命名构造函数可以定义多个。

```dart
class Person{
  String name = "cdx";
  int age = 23;
  //默认构造函数
  Person(this.name,this.age);
  Person.now(){
    print("命名构造函数");
  }

  void getInfo(){
    print("${this.name}  ${this.age}");
  }
}

main(List<String> args) {
  var p1 = new Person.now();//命名构造函数
}
```

### 5、私有属性/私有方法

Dart中是没有和java一样有public、private、protected这些访问修饰符的。

方法：将类抽离成一个文件，使用 “ _ ”  把一个方法或者属性变成私有的。

### 6、getter与setter修饰符

```dart
class Rect {
  num height;
  num width;
  Rect(this.height,this.width);
  get area{
    return this.height * this.width;
  }
  set areaHeight(value){
    this.height = value;
  }
}
main(List<String> args) {
  Rect r = new Rect(10, 2);
  print("面积为：${r.area}");//注意调用直接通过访问属性的方式访问area
  r.areaHeight = 6;
  print("面积为：${r.area}");
}
```

### 7、静态成员

1、使用static关键字来实现类级别的变量和函数。

2、静态方法不能访问非静态成员，非静态方法可以访问静态成员。

```dart
class Person {
  static String name = 'cdx';
  static void showName() {
    print(name);
  }
}

main(List<String> args) {
  print(Person.name);
  Person.showName();
}
```

```dart
class Person {
  static String name = 'cdx';
  int age = 23;
  static void showName() {
    print(name);
  }
  void printInfo(){ //非静态方法可以访问静态成员以及非静态成员
    print(name);//访问静态属性
    print(this.age);//访问非静态属性
  }
}
main(List<String> args) {
  Person p = new  Person();
  p.printInfo();
}
```

### 8、操作符

?：条件操作符    as：类型转换    is：类型判断    ..：级联操作

```dart
class Person {
  String name = 'cdx';
  int age = 23;
  void printInfo(){
    print("${this.name}  ${this.age}");
  }
}

main(List<String> args) {
  Person p1 = new  Person();
  p1.printInfo();//cdx  23
  Person p2;
  //p2.printInfo();//报错：The method 'printInfo' was called on null.
  p2?.printInfo();
}
```

```dart
p as Person  //类型转换
```

```dart
class Person {
  String name = 'cdx';
  int age = 23;
  void printInfo(){
    print("${this.name}  ${this.age}");
  }
}

main(List<String> args) {
  Person p1 = new  Person();
  p1.printInfo();//cdx  23
  p1..name='xxx'
    ..age =20
    ..printInfo();//xxx  20
}
```

### 9、继承

1、子类使用extends关键词来继承父类

2、子类会继承父类里面可见的属性和方法但是不会继承构造函数

3、子类能复写符类的方法 getter和setter

```dart
class Person {
  String name = 'cdx';
  int age = 23;
  Person(this.name,this.age);
  void printInfo(){
    print("${this.name}  ${this.age}");
  }
}

class Cdx extends Person{
  String sex;
  Cdx(String name, int age,String sex) : super(name, age){
    this.sex = sex;
  }

  void printCdx(){
    print("${this.name}  ${this.age}  ${this.sex} ");
  }

}
main(List<String> args) {
  Cdx c = new  Cdx('xxx',20,'男');
  c.printInfo();//xxx  20
  c.printCdx();//xxx  20  男 
}
```

### 10、抽象类

Dart中抽象类主要用于定义标准，子类可以继承抽象类，也可也实现抽象类接口。

1、抽象类通过abstract关键词来定义。

2、Dart中的抽象方法不能用abstract声明，Dart中没有方法体的方法称为抽象方法。

3、如果子类继承抽象类必须要实现里面的抽象方法。

4、如果把抽象类当作接口实现的话，必须要实现抽象类里面定义的所有属性和方法。

5、抽象类不能被实例化，但可以继承它的子类

extends抽象类和implements的区别：

1、如果要复用抽象类里面的方法，并且要用抽象方法约束子类的话我们就要用extends继承抽象类。

2、如果只是把抽象类当作标准的话我们就要用implement实现抽象类。

```dart
//定义一个Animal类必须要求它的子类包含eat方法
//解决方法：用到抽象类
abstract class Animal{
  eat();//抽象方法
}
class Dog extends Animal{
  @override
  eat() {
    print("eat");
  }
}

main(List<String> args) {
  Dog dog = new Dog();
  dog.eat();
}
```

### 11、多态

允许将子类类型的指针赋值给父类类型的指针，同一个函数调用会有不同的执行效果。

子类的实例赋值给父类的引用。

多态就是父类定义一个方法不去实现，让继承他的子类去实现，每个子类有不同的表现。

```dart
abstract class Animal{
  eat();//抽象方法
}
class Dog extends Animal{
  @override
  eat() {
    print("Dog eat");
  }
}

class Cat extends Animal{
  @override
  eat() {
    print("Cat eat");
  }
}

main(List<String> args) {
  Animal dog = new Dog();
  dog.eat();//Dog eat

  Animal cat = new Cat();
  cat.eat();//Cat eat
}
```

### 12、接口

和java一样Dart也是有接口的他们之间案对区别是

Dart的接口没有interface关键字定义接口，而是普通类或抽象类都可以作为接口被发现

但是Dart还是有不一样的地方，如果实现的类是普通类，会将普通类和抽象中的属性的方法全部需要覆盖写一遍。而因为抽象类可以定义抽象方法，普通类不可以，所有一般来说如果要实现java接口那样的方式，一般使用抽象类。当然也建议使用抽象类定义接口。

```dart
abstract class Db{
  String url;
  add();
  save();
  delete();
}
class Mysql implements Db{
  @override
  String url;
  Mysql(this.url);
  @override
  add() {
    print("Mysql add");
  }
  @override
  delete() {
    print("Mysql delete");
  }
  @override
  save() {
    print("Mysql save");
  }
}
main(List<String> args) {
  Mysql mysql = new Mysql("xxxxxxx");
}
```

### 13、mixins

中文的意思是混入，其实就是在类中混入其他功能。比如说使用它实现类似多继承的功能。

但是随着Dart版本的不断变化，下面讲一下Dart中2.x中使用mixins的条件

1、作为mixins的类只能继承自Object，不能继承其他类。

2、作为mixins的类不能有构造函数

3、一个类可以mixins多个mixins类

4、mixins绝不是继承，也不是接口，而是一一种全新的特性。

```dart
//A,B不能继承其他类，而且A,B不能有构造函数
class A{
  void printA(){
    print("A");
  }
}
class B{
  void printB(){
    print("B");
  }
}
class C with A,B {

}
main(List<String> args) {
  var  c = new C();
  c.printA();
  c.printB();
}
```

## 8、泛型

泛型就是解决，类、接口、方法的复用性，以及对不特定数据类型的支持（类型校验）。

```dart
T getData<T>(T value){
  return value;
}
main(List<String> args) {
  print(getData(21));
  print(getData<String>('xxxx'));
}
```

```dart
class PrClass<T> {
  List list = new List<T>();
  void add(T value) {
    this.list.add(value);
  }
  void printInfo() {
    for (var i = 0; i < this.list.length; i++) {
      print(this.list[i]);
    }
  }
}
main(List<String> args) {
  PrClass p = new PrClass<String>();
  p.add("111");
  //p.add(1);//type 'int' is not a subtype of type 'String' of 'value'
  p.printInfo();//输出：111
}
```

## 9、Dart中的库

在Dart中，库的使用是通过import关键字引入的。

library指令可以创建一个库，每个Dart文件都是一个库，即使没有使用library指令来指定。

Dart中的库主要分为三种：

1、我们自定义的库

```dart
import 'lib/xxx.dart'
```

2、系统内置库

```dart
import 'dart:math';
import 'dart:io';
import 'dart:convert';
//等等

```

3、第三方包管理系统中的库（一般pub中）。

有很多不一一举例了。

1、需要在自己项目根目录新建一个pubspec.yaml。

2、在pubspec.yaml文件中配置名称、描述、依赖信息。

3、运行pub get 获取包下载到本地。

4、项目中引入该库。

4、最后就是看文档使用它。

## 10、扩展一下async和await

async和await

这两个关键词的使用只需要记住：

1、只有async方法才能使用await关键字调用方法。

2、如果调用别的async方法必须使用await关键字。

async是让方法变成异步。

await是等待异步方法执行完成。

```dart
main(List<String> args) async{
  var result = await testAsync();
  print(result);
}

//异步方法
testAsync() async{
  return 'async';
}
```

