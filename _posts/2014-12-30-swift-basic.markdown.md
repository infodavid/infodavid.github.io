---
layout: post
title:  "高逼格设计师系列之 Swift 基础"
date:   2014-12-30 17:20:46
author: 大蔚陈
categories: 
- Tutorials
img: swift-icon.png
thumb: swift-icon.png
---

# 高逼格设计师系列之 Swift 基础

## Swift 基础

这一节将会介绍 Swift 的基础知识，尽是大白话，没有高深内容，即便是没有任何编程经验，也可以快速理解。

### 变量

`变量`，英文为 `Variables`。顾名思义，`变量`就是可以变化的信息。每一种编程语言中，都有`变量`，它允许你储存数据。<!--more-->



#### 声明变量和常量

在 Swift 中，你必须通过使用关键词`var`来声明变量。


```
var greeting: String = "Hello World" 
```

上面的代码的意思是你创建了个一个名叫`greeting`的变量，这个变量的类型是`字符串`，同时它包含了一个文本, "Hello World"。

##### 类型标注

你声明常量或者变量的时候可以加上**类型标注**(type annotation)，说明常量或者变量中要存储的值的类型。如果要添加类型标注，需要在常量或者变量名后面加上一个冒号和空格，然后加上类型名称。

这个例子给`greeting`变量添加了类型标注，表示这个变量可以存储 `String`类型的值。

#### 可变变量

变量一旦创建了，就可以更改。我们试着增加一行代码，把变量`greeting`变成其他东西。


```
var greeting: String = "Hello World" 

greeting = "Hello Swift"
```

简单说地说，我们可以把变量看做一个篮子，我们可以在篮子中放置一个物品，再倒出来，放入一个其他的东西。然后，即便可以改变篮子里的内容，它仍是同一个篮子。

但是在写程序的时候，有很多的情况下是你初始化创建后不想修改变量。创建一个不可变的变量，你需要使用关键词`let`。

#### 不可变变量--常量

我们试着把上面的例子修改一下，用`let`替代`var`。取代之后，因为`常量`是不能吸怪的，所以第二行代码就报错`Compiler error`。

```
let greeting: String = "Hello World" 

greeting = "Hello Swift" // Compiler error

```

注：注释里的文本不会被执行，可以输入一些提示或者方便以后阅读的笔记。

为更好的理解为什么以及何时使用`let`，让我们再看看另一个例子。

```
let languageName: String = "Swift"
var version: Double = 1.0
let introduced: Int = 2014
let isAwesome: Bool = true
```

上面的例子不仅展现了 Swift 中的多种类型都是允许的，也同时展现了使用`let`的原因。除了 Swift 语言的版本号，其他都是保持不变的。（当然你可能对`isAwesome`持怀疑态度，但是当你学完这个系列，你会同意的）

```
let languageName: String = "Swift" // 被指定为字符串
var version: Double = 1.0 // 被指定为64位浮点数
let introduced: Int = 2014 // 被指定为整型
let isAwesome: Bool = true // 被指定为布尔值
```

注：`浮点数`指的是有小数部分的数字。 Swift 提供了两种浮点数类型。`Double`表示64位浮点数，当需要存储很大或者很高精度的浮点数时请使用此类型。`Float`表示32位浮点数，精度要求不要的的话可以使用此类型。

### 字符串

在上面的例子中，我们已经写过`String`类型了，让我们看看两个字符串是怎么通过`+`运算符连结起来的。

```
let title = "高逼格设计师系列之 Swift"
let review = "屌炸天"
let description = title + "--" + review
// description = "高逼格设计师系列之 Swift--屌炸天"
```

字符串有一个强大的字符串**插值**功能，可以让你便捷地用变量创建一个字符串。

```
let datePublished = "11 月 9 日，2014"
let postMeta = "博客发表于：\(datePublished)"
// postMeta = "博客发表于：11 月 9 日，2014"
```

在上面这些例子里，我用的都是`let`关键词，这意味着这些字符串一旦创建了之后，就无法修改了。如果你需要能够修改这些字符串的话，用`var`关键词就可以了。

### 集合类型

#### 数组

集合有两种类型。`数组`是一个数据的集合，可以通过一个从0开始的索引进行存取。

```
var cardNames: [String] = ["Jack", "Queen", "King"]

// Swift 会指定[String]，所以我们也可以写成下面这样：

var cardNames = ["Jack", "Queen", "King"]
```

你可以创建两种类型的数组。一个单一类型的数组，或者一个拥有多个类型的数组。上面的例子就是一个字符串的数组，意味着那是一个单一类型数组。

要从数组中存取项目的话，你需要使用下标：

```
println(cardNames[0])
```

> 注：我们在上面使用了一个叫`prinln`的方法，这个方法将输出"Jack"这个值到控制台，然后添加一个新的行。

#### 修改数组

让我们创建一个新的包含了代办列表的数组。

```
var todo = ["写一篇博客","回电话给大蔚"]
```
确保使用的是关键词`var`，这样我们才能修改数组。

要新增一条事项到`todo`数组的话，我们使用`+=`操作符。

```
todo += ["取快递"]
```
要增加多条事项到我们的`todo`数组的话，我们只需要增加一个数组：

```
todo += ["发邮件", "逛街", "约饭"]
```

要替换一个在数组中已存在的事项，只需要下标出此事项，同时提供一个新值：

```
println(todo[0]) // 先查看已存在的事项是什么，得到的是："写一篇博客"

todo[0] = "乖乖上班吧" // 用新内容替换已存在事项

println(todo[0]) // 最后输出为："乖乖上班吧"
```

要替换一定范围的事项的话，看下面的例子：

```
todo[2..<5] = ["双11抢购","吃方便面", "还信用卡"]
```

### 字典

另一种集合类型交货`Dictionary`，字典。和其他编程语言的哈希表类似。字典可以让你存储**键值对**，并通过提供**键**存取**值**。

举个例子，我们可以指定卡片，通过提供它们的**键**和后面的**值**

```
var cards = ["Jack" : 11, "Queen" : 12, "King" : 13]
```

在这个例子里，我们指定卡片名字为**键**，以及它们对应的数字值。**键**（key）并非限制只能是`字符串`类型，它们可以是任何类型，**值**也一样。

#### 修改字典

如果我们想添加一个“ace”(A)到我们的字典里,该怎么做呢？我们要做的就是把**键**作为下标，同时赋予它一个值。注：`card`是用关键词`var`定义的，这表示可以修改。

```
cards["ace"] = 15
```

要是输错了，就再赋予一个新值就行了。

```
cards["ace"] = 1
```

从字典中取回一个值：

```
println(cards["ace"]) = 1
```

### 控制流

#### 循环

要是不能循环遍历的话，集合也就没有啥好的了。Swift 提供了`while`, `do-while`, `for` and `for-in`循环。让我们一次来看看。

里面最简单的是`while`循环。如果条件为真，会重复运行一系列语句，直到条件变为`false`。

```
while !complete {
	println("Downloading...")
}
```

> 注： 在变量`complete`前的感叹号表示未完成，读作“未完成”。

同样的，你可以用`do-while`循环可以确保你的代码块可以至少执行一次。

```
var message = "Starting to download"
do {
	println(message)
	message = "Downloading.."
} while !complete 
```

后面调用的 `println` 声明将会输出"Downloading..."

你可以指定一个数字，并将此数字增量至一个特定值，获得一个循环。

```
for var i = 1; i < cardNames.count; ++i {
	println(cardNames[i])
}
```

或者你可以使用另一种形式，`for-in`，他创建了一个临时变量，并在遍历数组时，赋予它一个值。


```
for cardName in cardNames {
	println(cardName)
}
```

以上的代码将会输出数组里所有的卡片名称。我们页可以使用一个范围域。一个值的范围域用两个点`(..)`或者三个点`(...)`表示。

举个例子：

- 1...10 -- 表示从1到10的数字范围。3个点代表是的是一个闭合范围，因为包括了最大的范围。
- 1..<10 -- 表示从1到9的数字范围。2个点加上一个小于号代表的是一个版闭合范围，因为最大范围没包括在内。

我们使用`for-in`循环，加上一个范围，输出双倍的表格：

```
for number in 1...10 {
	println("\(number) times 2 is \(number*2)")
}
```

我们页可以遍历`cards`字典，同时输出**键**和**值**：

```
for (cardName, cardValue) in cards {
	println("\(cardName) = \(cardValue)")
}
```

#### if 条件语句

根据特定的条件执行特定的代码是非常有必要的，要实现这些，就需要使用条件语句。

```
if cardValue == 11 {
	println("Jack")
} else if cardValue == 12 {
	println("Queen")
} else {
	println("Not found")
}
```
> if 条件语法语法可以包含圆括号，但圆括号`()`是可选的。但是和其他语言有些不一样的是，花括号`{}`是强制需要的。

#### switch 条件语句

当条件较为简单且可能的情况很少时，使用`if`语句。而`switch`语句更适用于条件比较复杂，可能情况较多，且需要用到模式匹配（pattern-matching）的情景。

以下是一些`switch`声明的基础规则：

- 在每个 case 声明后，不需要一个 `break` 语句
- `switch`语句不仅限于整型值。你可以匹配任何值为：`String`, `Int`, `Double`，或者任何对象。
- `switch`语句必须尽可能地和每一个值进行匹配，如果没有的话，你必须有一个默认的 `case`，这样可以让你的代码更安全。如果你没有提供一个`case`给每一个值或者没有默认情况，你会受到编译错误的提示：switch must be exhaustive

```
switch cardValue {
	case 11:
		println("Jack")
	case 12: 
		println("Queen")
	default:
		println("Not found")
}
```

如果你有一个叫 distance 变量的话，你像在 distance 输出一个信息。你可以对每个 case 声明使用多个值：

```
switch distance {
	case 0:
		println("not a valid distance")
	case 1,2,3,4,5:
		println("near")
	case 6,7,8,9,10:
		println("far")
	default:
		println("too far")
}
```

有很多情况是，多个值被限制了。对于这些实例，你可以使用范围域。举个例子，如果距离大于10小于100是什么样的？


```
switch distance {
	case 0:
		println("not a valid distance")

	case 1..10:
		println("near")

	case 10..100 :
		println("far")

	default:
		println("too far")

}
```

你猜上面的代码会输出什么？

## 函数

函数是在脚本的开始处设置的一系列的编程步骤，等效于为助手提供的详细指示。比如说你让助手小虎帮你去买瓶饮料，第一次你需要告诉他，出门右拐，直走50米到小卖部，选好「海之言」。买瓶饮料这系列的步骤就可以变成一个函数，但是下一次，你直接告诉他去买瓶饮料就可以了（相当于调用函数）。

最后，我们在很多例子中都使用了`println`函数，但是你怎么创建函数呢？

很简单，你必须使用关键词`func`并提供给它一个名字。

```
func printCard() {
	println("Queen")
}
```

What good is a function if it always going to just print “Queen” as the card name. What if we want to pass it a parameter so it can print any card name?

如果想要它一直输出`Queen`作为卡片名，也没什么好的。如果我们想传一个参数，这样它可以输出任何卡片名称，该怎么做呢？


```
func printCard(cardName: String) {
	println(cardName)
}
```

当然，我们并不是只能限制为一个参数。我们也可以传递多个参数：

```
func printCard(cardName: String, cardValue: Int) {
	println("\(cardName) = \(cardValue)")
}
```

如果我们只想函数可以建立一个字符串并返回值，而不是输出呢？那我们可以指定一个返回，在函数声明的最后加上一个数组 ->


```
func buildCard(cardName: String, cardValue: Int) -> String {
	return "\(cardName) = \(cardValue)"
}
```

上面说的是创建了一个名叫`buildCard`的函数，它带入了2个参数，并返回了一个字符串。



> 参考链接：[http://blog.teamtreehouse.com/an-absolute-beginners-guide-to-swift](http://blog.teamtreehouse.com/an-absolute-beginners-guide-to-swift)



















