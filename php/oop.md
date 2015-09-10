###PHP的OOP（面向对象编程）

####什么是面向对象编程

>面向对象编程（Object Oriented Programming，OOP，面向对象程序设计）是一种计算机编程架构。OOP 的一条基本原则是计算机程序是由单个能够起到子程序作用的单元或对象组合而成。OOP 达到了软件工程的三个主要目标：重用性、灵活性和扩展性。为了实现整体运算，每个对象都能够接收信息、处理数据和向其它对象发送信息。--百度百科

我们可以先简单的理解就是把代码写到类里面。那么什么是类呢？

>类（Class）定义了一件事物的抽象特点。通常来说，类定义了事物的属性和它可以做到的（它的行为）。举例来说，“狗”这个类会包含狗的一切基础特征，例如它的毛皮颜色和吠叫的能力。类可以为程序提供模版和结构。一个类的方法和属性被称为“成员”。

下面看下php是如何定义类的

```php
class Dog {
  public $name;
  public $furColor;
  
  public function watchHouse() {
    //do somthing
  }
}  
```

那如何使用这个类呢？

```php
$myDog = new Dog();
$myDog->name = '旺财';
$myDog->watchHouse();
```

可能上面的例子很难与工作的代码相联系，下面举个工作中的例子。

工作中经常开发的功能是增删改查，比如单品的API，我们原先的代码通常是这样的结构：

* danpinList.php
* danpinAdd.php
* danpinEdit.php
* danpinDelete.php
