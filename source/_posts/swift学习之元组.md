---
title: swift学习之元组
date: 2017-11-04 01:53:54
tags:
- swift学习
---

### Swift 元组(Tuples)介绍

## 元组的定义

元组是Objective-C中没有的数据类型，与数组类似，都是表示一组数据的集合，但与数组不同，它的特点是：

<!-- more -->

1>元组的长度任意

2>元组中的数据可以是不同的数据类型

元组的定义很简单，用小括号括起来，以逗号隔开就可以了，如：

```bash
var userInfo = ("Tuski" ,true, 19)  
```

元组内的值可以使任意类型,并不要求是相同类型。

```bash
let http404Error = (404, "Not Found")
// http404Error 的类型是 (Int, String),值是 (404, "Not Found")
```

另外，在创建元组时你还可以给元组中的元素命名：

```bash
 let secondHighScore = (name: "James", score: 4096)
```

###以上就是创建元组的方法

**从元组中读元素**

如果我们没有给元组的元素命名，我们可以用点语法，通过定义好的元组变量或常量获取它的第1个到第n个元素：

```bash
let firstHighScore = ("Mary", 9001)
println(firstHighScore.0) // Mary
println(firstHighScore.1) // 9001
```

若你觉得上述这种方法会造成语义的不明确，我们还可以将元组赋值给一个带有元素名称的元组（元素名称个数要对应）:

```bash
let (firstName, firstScore) = firstHighScore
println(firstName) // Mary
println(firstScore) // 9001
```

如果你只需要一部分元组值，分解的时候可以把要忽略的部分用下划线（_）标记：

```bash
let (_, firstScore) = firstHighScore
println(firstScore) // 9001
```

如果我们已经给元组中的元素命名了名称，那么我们可以这样写：

```bash
let secondHighScore = (name: "James", score: 4096)
println(secondHighScore.name) // James
println(secondHighScore.score) // 4096
```

**将元组作为函数返回值**

当你想让一个函数能够返回多种类型时，这是元组的最佳使用场景。

我们可以将元组作为函数的返回值，下面这个函数的返回值就是我们之前定义过的secondHighScore元组：

```bash
func getAHighScore() -> (name: String, score: Int) {
 let theName = "Patricia"
 let theScore = 3894
 return (theName, theScore)
 }
```

为什么说上述函数的返回值是secondHighScore元组呢？因为getAHighScore函数返回的元组元素个数、元素名称、元素类型均和secondHighScore相同。



其实将元组作为函数的返回值时也可以不必对元素进行命名，只要你明白每个元素代表的含义即可：

```bash
func getAHighScore() -> (String, Int) {
 let theName = "Patricia"
 let theScore = 3894
 return (theName, theScore)
 }
```

如果你不确定返回的元组一定不为nil，那么你可以返回一个可选的元组类型：

```bash
func maybeGetHighScore() -> (String, Int)? {
 return nil
}
```

因为是可选的元组类型，所以当返回的元组不为nil时，你需要对元组进行解包：

```bash
if let possibleScore = maybeGetHighScore() {
 possibleScore.0
 possibleScore.1
} else {
 println("Nothing Here")
}
```

###**注意：**当你定义了一个没有返回值的函数时，其实该函数是返回一个空的元组()



**元组的访问级别**

元组的访问级别取决于它包含的元素。比如元组里的元素都是private级别的，那么该元组也是private级别的。但这里有一个遵循最小的原则，也就是说如果一个元组中有两个元素，一个为private级别，另一个为public级别，那么该元组遵循最小原则，它的访问级别为private。



**元组是值类型**

关于值类型和引用类型的知识这里不再累赘，我们通过一个代码示例来看看元组是哪种类型：

```bash
var someScore = ("John", 55)
var anotherScore = someScore
anotherScore.0 = "Robert"
println(anotherScore.0) //Outputs: "Robert"
println(someScore.0)  //Outputs: "John"
```

通过上述的代码示例可以看出，我把someScore元组赋值给了anotherScore，然后修改了anotherScore的第1个元素的值，最后分别打印了someScore和anotherScore第1个元素的值。someScore元组第一个元素的值为Robert，而anotherScore元组第一个元素的值仍然为John。由此可见元组是值类型。

**总结**

元组（Tuple）的概念对于没有接触过脚本语言的同学来说，是比较新的概念。但是元组既不复杂也不神秘，很多时候用Struct结构体或者类都可以解决。可以把元组理解为一种只能存放数据，却没有定义方法的轻量级数据结构。