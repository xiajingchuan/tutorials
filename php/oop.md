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

* danpinList.php  --查询数据将数据以列表显示出来
* danpinAdd.php   --往数据库中添加数据
* danpinEdit.php
* danpinDelete.php

那写到类里面是什么样呢？我们只要定义一个类文件 Danpin.class.php

```php
class Danpin {
  public function list() {
    //do somthing
  }
  
  public function add() {
    //do somthing
  }
  
  public function edit() {
    //do somthing
  }
  
  public function delete() {
    //do somthing
  }
}
```

只用一个文件，很不错吧！但问题来了，所有方法都在一个文件里，怎么分别调用每个方法呢？
我们用类似这样的链接来进行访问`http://www.linktech.cn/index.php?m=danpin&a=list`

说了这么多感觉面向对象也没啥啊，下面说下面向对象的高级特性
* 封装
* 继承
* 多态

>封装性：封装是一种信息隐蔽技术，它体现于类的说明，是对象的重要特性。封装使数据和加工该数据的方法（函数）封装为一个整体，以实现独立性很强的模块，使得用户只能见到对象的外特性（对象能接受哪些消息，具有那些处理能力），而对象的内特性（保存内部状态的私有数据和实现加工能力的算法）对用户是隐蔽的。封装的目的在于把对象的设计者和对象的使用者分开，使用者不必知晓行为实现的细节，只须用设计者提供的消息来访问该对象。

>继承性：继承性是子类自动共享父类之间数据和方法的机制。它由类的派生功能体现。一个类直接继承其它类的全部描述，同时可修改和扩充。继承具有传递性。继承分为单继承（一个子类只有一父类）和多重继承（一个类有多个父类）。类的对象是各自封闭的，如果没继承性机制，则类对象中数据、方法就会出现大量重复。继承不仅支持系统的可重用性，而且还促进系统的可扩充性。

>多态性：对象根据所接收的消息而做出动作。同一消息为不同的对象接受时可产生完全不同的行动，这种现象称为多态性。利用多态性用户可发送一个通用的信息，而将所有的实现细节都留给接受消息的对象自行决定，如是，同一消息即可调用不同的方法。例如：Print消息被发送给一图或表时调用的打印方法与将同样的Print消息发送给一正文文件而调用的打印方法会完全不同。多态性的实现受到继承性的支持，利用类继承的层次关系，把具有通用功能的协议存放在类层次中尽可能高的地方，而将实现这一功能的不同方法置于较低层次，这样，在这些低层次上生成的对象就能给通用消息以不同的响应。在OOPL中可通过在派生类中重定义基类函数（定义为重载函数或虚函数）来实现多态性。（对方法的覆写）

####抽象类####
包含抽象方法的类叫做抽象类

我们在类里面定义的没有方法体的方法就是抽象方法，所谓没有方法体就是在方法声明的时候没有大括号以及其中的内容，而是直接声明时在方法名后加上分号结束，另外在声明抽象方法时还要加一个关键字"abstract"来修饰：
>abstract function fun1();

####接口####


---------
综合例子：
> api.class.php

```php
abstract class API{
  protected $db;
  function __constract() {
    //链接数据库
    $this->db = $PDO;
  }
  
  abstract function list();
  abstract function add();
  abstract function edit();
  abstract function delete();
}
```

> danpin.class.php

```php
class Danpin extends API {
  public function list() {
    //do somthing
  }
  
  public function add() {
    //do somthing
  }
  
  public function edit() {
    //do somthing
  }
  
  public function delete() {
    // do somthing
  }
}
```

> product.class.php

```php
class Product extends API {
  public function list() {
    //do somthing
  }
  
  public function add() {
    //do somthing
  }
  
  public function edit() {
    //do somthing
  }
  
  public function delete() {
    // do somthing
  }
}
```
