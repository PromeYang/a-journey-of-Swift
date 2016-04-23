# a-journey-of-Swift
一个前端的Swift之旅

```
![GitHub set up](https://raw.githubusercontent.com/PromeYang/a-journey-of-Swift/master/image/Default.png)
```

## 前夜

`Swift` , 我们这趟奇妙代码旅程的目的地

* 苹果创造, 代码开源
* 用于搭建苹果平台的应用程序, 可与Objective-C*共同运行于Mac OS和iOS
* 第一套具有与脚本语言同样的表现力和趣味性的系统编程语言

## 起航

这是一段走向 `Swift` 的旅程, 坐上前端友谊的小船, 我们粗发~

### 第一站 -  初见

代码的世界, 我们总是以 `"Hello World"` 来表达降临新世界的喜悦

在 `Swift` 中, 我们也用同样的方式表明: 我来了!

```
print("Hello, world!")
```

在 `JavaScript` 中, 就像我们曾经敲下的第一句代码

```
alert('Hello, world!');
```

没有 `main()` 入口函数, 不用引入库, 只用一行代码就可以实现

### 第二站 - 发现

有了对比, 就会有所发现.

#### 变量和常量

在 `Swift` 中, 用 `var` 来声明一个变量, 而用 `let` 来声明一个常量

```
var myVariable = 42    // 42, 声明一个变量
myVariable = 50        // 50, 重新赋值
let myConstant = 42    // 42, 声明一个常量
myConstant = 50        // error, 不能给一个常量重新赋值
```

在 `JavaScript` 中, 也总是用 `var` 来声明变量, 直到 `ES6` 的出现, 可以使用 `let` 来声明<块级作用域>变量, 用 `const` 来声明常量

```
let myConstant = 42;   // 42, 声明<块级作用域>变量
myConstant = 50;       // 50, 重新赋值
const PI = 30;         // 30, 声明一个常量
const PI;              // error, 声明常量必须初始化
```

#### 类型和转换

在 `Swift` 中, 声明变量或者常量的时候可以不显式指定类型, 但是必须在声明的同时赋值, 否则必须显式声明类型, 用冒号分割. 值永远不会被隐式转换为其他类型, 只能通过显式转换.

```
var aInt = 123         // 推断出整数类型
var aString = "123"    // 推断出字符串类型
var aBool: Bool        // 指定了类型
var aAny               // error, 没有显式指定类型
var bString = aString + String(aInt)    // 显式转换类型
var cString = aString + aInt            // error, 不会隐式转换
```

在 `JavaScript` 中, 声明变量或者常量不需要关注要指定什么类型, 在运算的时候会自动隐式转换成对应的类型

```
var aInt = 123;
var aString = '123';
var bString = aString + String(aInt);   // "123123", 显式转换类型
var cString = aString + aInt;           // "123123", 隐式转换类型
```

#### 数组和字典

在 `Swift` 中, 数组和字典都是通过 `"方括号[ ]"` 来定义, 字典没有点语法

```
var aArray = [AnyObject]()
aArray.append("1")
aArray.count
var aDictionary = [String : AnyObject]()
aDictionary["key"] = "value"
aDictionary["key"]
```

在 `JavaScript` 中, 数组用 `"方括号[ ]"` 表示, 对象用 `"花括号 { }"` 表示

```
var aArray = [];
aArray.push('1');
aArray.length;
var aObject = {};
aObject.key = 'value';
aObject.key;
```

#### 分支和循环

在 `Swift` 中,

`if` 语句的条件必须是一个布尔表达式, 不会隐式和`0`做对比. 即时执行语句只有一行代码, 也不可以省略 `"花括号{ }"` .

`switch` 语句匹配到子句之后会退出, 所以不需要在每个子句结尾写 `break` ,但是结束必须写 `default` 子句.

`for` 循环中可以使用 `..<` 或者 `...` 来表示范围.

`while` 循环中用 `repeat while` 来保证循环体至少执行一次

```
var aValue: String? = "value"
if 0 { print(aValue) }    // error, 判断条件不是布尔表达式
if let aValue = aValue {
    switch aValue {
    case "1" : print("1")
    case "2" : print("2")
    default : print("default")
    }
}
for i in 0..<2 {
    print(i)
}
repeat {
    print(1)
} while false
```

在 `JavaScript` 中,

`if` 语句的条件会隐式转换之后做对比. 

`switch` 需要在每个子句结尾写 `break` , `default` 子句不是必须的.

`while` 循环中用 `do while` 来保证循环体至少执行一次.

语句的条件表达式需要用 `"圆括号( )"` 包裹.

```
if(0) alert(0)            // 执行语句只有一行, 可以省略{}
switch(1) {
	case 1: alert(1); break;
}
do {
    alert(1)
} while (false)
```

#### 函数和闭包

在 `Swift` 中, 

使用 `func` 来声明一个函数, 使用 `->` 来指定函数返回值的类型, 如果返回类型为空, 可以省略 `->`。

使用元组来让一个函数返回多个值.

函数可以带有可变个数的参数,这些参数在函数内表现为数组的形式.

函数可以作为另外一个函数的返回值.

函数可以作为参数传入另外一个函数.

函数的参数名可以设置 `内部参数名` 和 `外部参数名`, `内部参数名` 主要是在函数体内部使用, `外部参数名` 用于说明该参数的作用, 由于兼容 `Objective-C` 语法, 第一个参数的 `外部参数名` 可以不传. 

函数的参数在声明的时候可以给定默认值.

```
// 声明函数
func afunc(callback: String -> Void) {
    // TODO
}
// 返回多个值
func bfunc() -> (a: Int, b: String) {
    // TODO
    return (a, b)
}
// 可变个数的参数
func cfunc(numbers: Int...) -> Void {
    for number in numbers {
    	// TODO
    }
}
// 作为返回值
func dfunc() -> (() -> Void) {
    func backFunc() {}
    return backFunc
}
// 作为参数
func callback(nickname name: String = "1") { print(1) } // 外参:nickname 内参:name 给定默认值 "1"
afunc(callback) // 省略第一个参数的外参
```

函数实际上是一种特殊的闭包: 它是一段能之后被调取的代码, 作用域是词法作用域.

闭包中的代码能访问闭包所建作用域中能得到的变量和函数,即使闭包是在一个不同的作用域被执行的.

可以使用 `{}` 来创建一个匿名闭包. 使用 `in` 将参数和返回值类型声明与闭包函数体进行分离.

```
// 传入一个匿名闭包
afunc({ (name) in
	// TODO
})
```

在 `JavaScript` 中, 

使用 `function` 声明函数 , 直到 `ES6` 支持箭头语法 `=>` 来声明函数. 箭头的左边是指定参数, 右边是指定返回值或者函数体, 虽然指定了返回值, 但是返回值并没有强制要求, 如果没有返回值默认返回 `undefined`

函数返回值永远只有一个, 如果要返回多个值信息, 只能返回数组或者对象

函数可以带有可变个数的参数, 用 `...` 语法可以让将一个数组转为用逗号分隔的参数序列, 在函数内调用该参数会遍历执行.

函数的参数在声明的时候可以给定默认值. 给定默认值之后函数的 `length` 属性会失真, `length` 属性的返回值，等于函数的参数个数减去指定了默认值的参数个数. 同理，`rest` 参数也不会计入length属性.
 
```
var f = () => 5;                           // ES6, 等同于下面语句
var f = function (){ return 5 };           // ES5以下, 使用 function 声明函数
var f = function (){ return {a:1, b:2} };  //返回对象
// 可变个数的参数
function push(array, ...items) {
  array.push(...items);
}
var f = function (name = 1){ };            // 声明参数并给定默认值
f.length                                   // 0, 失真
```

闭包就是定义在一个函数内部, 并能读取其函数内部变量的函数.

闭包的两个作用, 一个是可以读取函数的内部变量，另一个是让这些变量的值始终保持在内存中。

```
function f1(){
	var n=999;
	// 这里f2函数就是一个闭包
	function f2(){
		console.log(n++);
	}
	return f2;
}
var result=f1();     // result就是闭包函数f2
result();            // 999
result();            // 1000
```

#### 类和对象

在 `Swift` 中, 

使用 `class` 和 `类名` 来声明一个类, 类中的所有 `属性` 需要通过声明或者构造器的方式来赋值.

类中用 `self` 来识别类的实例对象本身.

继承父类, 用冒号分割, 多个继承用逗号分割.

要创建一个类的实例对象, 在类名后面加上 `括号()`, 使用点语法来访问实例的属性和方法.

```
// 声明一个类
class SuperClass {
    // 存储属性
    var aValue: Int = 0
    // 计算属性
    var bValue: String {
        // getter
        get {
            return "123"
        }
        // setter
        set {
            self.bValue = newValue
        }
    }
    // 构造器
    init (aValue: Int) {
        // 计算属性不直接存储值
        self.aValue = aValue
    }
}
// 继承父类, 用冒号分割, 多个继承用逗号分割
class SubClass: SuperClass {
    // 重写父类的方法
    override init(aValue: Int) {
        super.init(aValue: aValue)
    }
    // 析构函数
    deinit {
        // TODO
    }
}
// 创建类的实例对象
var subClass = SubClass(aValue: 1)
// 点语法访问成员属性
subClass.bValue
```

在 `JavaScript` 中, 

是没有真正的类的实现, 尽管在 `ES6` 引入了类的概念, 但也仅仅是一个语法糖, 都是通过构造函数定义一个 "类".

ES6的类,完全可以看作构造函数的另一种写法. 唯一的不同是, 类的内部所有定义的方法，都是不可枚举的.

ES6的类, 可以通过extends关键字实现继承, 这比ES5的通过修改原型链实现继承, 要清晰和方便很多。

ES5之后, 可以用使用 `get` 和 `set` 关键字来拦截存取行为.

```
// 定义构造函数
function Point(x,y){
	this.x = x;
	this.y = y;
}
// 类的方法都是定义在 prototype 属性上
Point.prototype.toString = function () {
	return '(' + this.x + ', ' + this.y + ')';
}
// 创建类的实例对象, 必须使用 new 命令
var point = new Point(1,10);
// 定义类
class Point {
	// 构造方法
	constructor(x, y) {
		this.x = x;
		this.y = y;
	}
	// 类的成员方法
	toString() {
		return '(' + this.x + ', ' + this.y + ')';
	}
}
// 继承
class ColorPoint extends Point {
	constructor(x, y, color) {
		// 调用父类的constructor(x, y)
		super(x, y);
		this.color = color;
	}
	// getter
	get color() {
		return 'getter';
	}
	// setter
	set color(value) {
		console.log('setter: '+value);
	}
	toString() {
		// 调用父类的toString()
		return this.color + ' ' + super.toString();
	}
}
```

### 第三站 - 探险

前路荆棘, 我们尝试着摸索前行.

#### 把函数作为参数传递

在 `JavaScript` 中, 

不需要考虑函数声明的参数, 也不需要考虑函数的返回值, 只需要把函数名作为参数传递.

```
var random = Math.round( Math.random() * 2 ) + 1 
var needTodo = (callback) => { callback(random); };
var fn1 = (Int) => { console.log(Int) }
var fn2 = (String) => { console.log(String) }
var fn3 = (Bool) => { console.log(Bool) }
switch(random) {
	case 1: needTodo(fn1); break;
	case 2: needTodo(fn2); break;
	case 3: needTodo(fn3); break;
}
```

在 `Swift` 中, 

要考虑函数声明的参数类型, 以及返回值类型

```
var random = arc4random() % 3 + 1
func needTodo(callback: () -> AnyObject) -> Void {
    callback()
}
func fn1(int: Int) -> Int {
    print(int)
    return int
}
func fn2(string: String) -> String {
    print(string)
    return string
}
func fn3(bool: Bool) -> Bool {
    print(bool)
    return bool
}
switch random {
case 1:
    needTodo({ () -> AnyObject in
        return fn1(1)
    })
case 2:
    needTodo({ () -> AnyObject in
        return fn2("2")
    })
case 3:
    needTodo({ () -> AnyObject in
        return fn3(false)
    })
default: break
}
```

#### 正则匹配

在 `JavaScript` 中, 

获取匹配模式中的子表达式匹配的字符串是一件很方便的事情

```
var regex = /\[(.*?)\]/;
var aString = 'name[3-5]';
var need;
aString.replace(regex, function(match, $1){
	need = $1;
});
```

在 `Swift` 中, 

要进行很多字符串的操作才能获取到想要的值

```
// 正则表达式字符串, 转义符需要两次
let pattern = "\\[.*\\]"
let aString = "name[3-5]"
// 尝试创建正则表达式执行语句
let regex = try? NSRegularExpression(pattern: pattern, options: NSRegularExpressionOptions.CaseInsensitive)
if let regex = regex {
    if let res = regex.firstMatchInString(aString, options: [], range: NSMakeRange(0, aString.characters.count)){
        // 获取到的是匹配结果对象, 还不是想要的字符串值
        let match = (aString as NSString).substringWithRange(res.range)
        let key = (aString as NSString).substringWithRange(NSMakeRange(0, res.range.location))
        let rule = (match as NSString).substringWithRange(NSMakeRange(1, match.characters.count-2))
    }
}
```

#### JSON数据

在 `JavaScript` 中, 

操作JSON数据是一件非常轻松的事情

```
var data = {
	"a": 1,
	"b": {
		"c": 2
	}
};
data.b.c
```

在 `Swift` 中, 

出于安全性的考虑, `JSON` 数据的传输都是序列化之后通过 NSData 来通讯的,

在解序列化的时候, 为了能把 `JSON` 数据的各种可能值解出来, 返回的结果都是 `AnyObject` 类型的,

在使用的时候, 各种判断和解包就不用说了, 连点语法都不支持, 只能通过自己封装或者使用第三方的库来让这个事情变得相对没那么繁琐.

```
// 定义一个字典
var data = [
    "a": 1,
    "b": [
        "c": 2
    ]
]
// 序列化成为NSData
var jsonData = try? NSJSONSerialization.dataWithJSONObject(data, options: [])
// 模拟获取到API接口数据, 解开NSData
var json = try? NSJSONSerialization.JSONObjectWithData(jsonData!, options: NSJSONReadingOptions.AllowFragments)
// 判断是否拿到json数据
if let json = json {
    // 判断是不是字典对象, 层级越深, 结构越复杂, 简直不忍直视
    if let b = json["b"] as? NSDictionary {
        b["c"]
    }
}
//============//
// 可以使用第三方库 SwiftyJSON 简化操作
if let c = json["b"]["c"].string{
	// Now you got your value
}
```

#### 时间格式化

在 `JavaScript` 中, 

原生是不支持时间格式化功能的, 需要额外实现

```
// 对Date的扩展，将 Date 转化为指定格式的String   
// 月(M)、日(d)、小时(h)、分(m)、秒(s)、季度(q) 可以用 1-2 个占位符，   
// 年(y)可以用 1-4 个占位符，毫秒(S)只能用 1 个占位符(是 1-3 位的数字)   
Date.prototype.Format = function(fmt) {
    var o = {
        "M+": this.getMonth() + 1, //月份   
        "d+": this.getDate(), //日   
        "h+": this.getHours(), //小时   
        "m+": this.getMinutes(), //分   
        "s+": this.getSeconds(), //秒   
        "q+": Math.floor((this.getMonth() + 3) / 3), //季度   
        "S": this.getMilliseconds() //毫秒   
    };
    if (/(y+)/.test(fmt))
        fmt = fmt.replace(RegExp.$1, (this.getFullYear() + "").substr(4 - RegExp.$1.length));
    for (var k in o)
        if (new RegExp("(" + k + ")").test(fmt))
            fmt = fmt.replace(RegExp.$1, (RegExp.$1.length == 1) ? (o[k]) : (("00" + o[k]).substr(("" + o[k]).length)));
    return fmt;
}
// 例子：   
(new Date()).Format("yyyy-MM-dd hh:mm:ss.S") // ==> 2016-07-02 08:09:04.423   
(new Date()).Format("yyyy-M-d h:m:s.S")      // ==> 2016-7-2 8:9:4.18
```

在 `Swift` 中, 

系统封装了格式化工具类, 使用非常方便

```
let formatter = NSDateFormatter()
formatter.dateFormat = "YYYY-MM-dd HH:mm"
formatter.stringFromDate(NSDate())
```

#### 自执行函数 - IIFE

在 `JavaScript` 中, 

```
var aModule = (function (name) {  
	function sayHi(name){
		console.log('Hello ' + name);
	}
	return {
		sayHi: sayHi
	};
})();
aModule.sayHi('Swift');
```

在 `Swift` 中, 

```
let aModule: [String : String -> Void] = {
    func sayHi(name: String) -> Void {
        print("Hello \(name)")
    }
    return [
        "sayHi" : sayHi
    ]
}()
aModule["sayHi"]!("Swift")
```

#### 模式匹配

在 `JavaScript` 中, 

只有简单的解构, 只能根据结构来拆分或合并, 而不能根据类型、值及自定义条件.

```
var {x, y} = { x:0, y:0 }
if (x === 0 && y === 0) console.log('(0, 0) is at origin.')
else if(x !== 0 && y === 0) console.log('('+ x +', 0) is at x axis.')
...
```

在 `Swift` 中, 

支持完整的模式匹配

```
var point = (0, 0)
switch point {
case (0, 0):
    print("(0, 0) is at origin.")
case let (x, 0):
    print("(\(x), 0) is at x axis.")
case let (0, y):
    print("(0, \(y)) is at y axis.")
case let (x, y) where x == y:
    print("(\(x), \(y)) is at line x == y.")
case let (x, y) where x == -y:
    print("(\(x), \(y)) is at line x == -y.")
case let (x, y):
    print("(\(x), \(y)) is just a point.")
}
```

#### 扩展方法

在 `JavaScript` 中, 

可以通过对 `prototype` 进行扩展

```
Object.prototype.mockData = function(){
	console.log('mockData');
}
```

在 `Swift` 中, 

可以通过 `extension` 进行扩展

```
extension NSObject {
    func mockData() {
        print("mockData")
    }
}
```

### 第四站 - 深入

曲径通幽, 拨开云雾见青天.

#### 协议

在 `Swift` 中, 

协议(Protocol)用于统一方法和属性的名称，而不实现任何功能。跟JAVA中的接口类似.

协议能够被类，枚举，结构体实现，满足协议要求的类，枚举，结构体被称为协议的遵循者。

遵循者需要提供协议指定的成员，如属性，方法，操作符，下标等。

```
// 定义一个协议
protocol SomeProtocol {
    // 规定一个变量
    var aValue: String { get }
    // 规定变量的读写属性
    var bValue: Int { get set }
    // 规定一个函数
    func someTypeMethod()
}
// 必须实现协议指定的所有要求, 否则编译不通过
struct Person: SomeProtocol{
    var aValue: String
    var bValue: Int {
        get {
            return 0
        }
        set {
            self.bValue = newValue
        }
    }
    func someTypeMethod() {
        print("someTypeMethod")
    }
}
```

#### 泛型

在 `Swift` 中, 

泛型（generic）可以使我们在程序代码中定义一些可变的部分，在运行的时候指定。

使用泛型可以最大限度地重用代码、保护类型的安全以及提高性能。

在Swift集合类中，已经采用了泛型。

```
// 定义一个函数对比两个整型参数的值是否相等
func isEqualsInt(a:Int, b:Int) -> Bool {
    return (a == b)
}
// 定义一个函数对比两个字符串类型参数的值是否相等
func isEqualsString(a:String, b:String) -> Bool {
    return (a == b)
}
// 定义一个泛型函数来对比两个参数是否相等
func isEquals<T: Comparable>(a: T, b: T) -> Bool {
    // Comparable协议表示类型是可比较的
    return (a == b)
}
var v1 = 0
var v2 = 1
isEquals(v1, b: v2)    // false 
var s1 = "1"
var s2 = "1"
isEquals(s1, b: s2)    // true
```

#### 内存管理

在 `JavaScript` 中, 

内存管理是基于 `GC` 的（Garbage Collection，垃圾收集）. 

`GC` 采用“标记－整理”＋“分代收集”的策略来进行自动内存管理的。

标记算法一般是从全局对象图的“根”出发进行可达性分析，对象的生死会被批量地标记出来，之后再在某个时间批量地释放死对象。

这是一种“全局＋延时”的管理策略, 这样不会因为循环引用而导致内存泄露 , 因为哪怕两个对象相互引用，但只要它们和“根”对象失去了联系，照样会被标记为死对象，然后在合适的时间被释放。

```
// bad
function assignHandler () {
	var element = document.getElementById('someElement');
	element.onclick = function () {
		// 由于匿名函数中引用了element，所以element的引用数最少是1，导致占用的内存永远不会被回收。
		alert(element.id);
	};
}
// good
function assignHandler () {
	var element = document.getElementById('someElement');
	var id = element.id;
	element.onclick = function () {
		alert(id);
	};
	element = null;
}
```

在 `Swift` 中, 

内存管理是基于 `ARC` 的(Automatic Reference Counting，自动引用计数).

引用计数是一种“局部＋即时”的内存管理策略。

它不需要全局的对象信息，一般每个被管理的对象都会跟一个引用计数器关联，

这个计数器保存着当前对象被引用的次数，一旦创建一个新的引用指向该对象，引用计数就加1,

每当指向该对象的某个引用失效引用计数就减1，直到引用计数为0，就立即释放该对象。

当循环引用发生的时候, 这个策略就会导致内存泄露, 解决办法就是使用 `weak` 弱引用.

```
// 定义VO1
class VO1 {
    var aValue: String?
    // 引用VO2
    func someAction(vo: VO2) -> Void {
        vo.someAction(self)
    }
}
// 定义VO2
class VO2 {
    var aValue: String?
    // 引用VO1
    func someAction(vo: VO1) -> Void {
        // 循环引用
        // vo.someAction(self)
        // 弱引用
        { [weak self] in
            vo.someAction(self!)
        }
    }
}
var vo1 = VO1()
var vo2 = VO2()
vo1.someAction(vo2)
```

#### 可选值

在 `JavaScript` 中, 

如果声明一个变量, 但是从来没有被赋值过, 那么这个变量的值就是 `undefined`

```
var aValue
console.log(aValue)    // undefined
```

在 `Swift` 中, 

使用可选类型(optionals)来处理值可能缺失的情况。没有值的情况就是 `nil` .

如果声明一个可选值类型的变量或者常量, 但是没有赋值, 它们会自动被设置为 `nil`.

使用可选绑定(optional binding)来判断可选类型是否包含值, 如果包含就把值赋给一个临时常量或者变量.

```
var aValue: String?
if let aValue = aValue {
	// TODO
}
```

#### 类型别名

在 `Swift` 中, 

可以用 `typealias` 给现有的类型定义一个别名, 也可以对字符串定义一个别名, 在编译的时候, 会替换掉别名对应的字符串

```
// 没有定义别名的时候
let aHandler: (data: NSData?, response: NSURLResponse?, error: NSError?) -> Void = {
    data,response,error in
    // TODO
}
// 定义了别名之后
typealias Handler = (data: NSData?, response: NSURLResponse?, error: NSError?) -> Void
let bHandler: Handler = { data,response,error in
    // TODO
}
let cHandler: Handler = { data,response,error in
    // TODO
}

```

#### 错误处理

在 `JavaScript` 中, 

当错误发生时，JavaScript 引擎通常会停止，并生成一个错误消息, 然后抛出该错误。

`try` 语句允许我们定义在执行时进行错误测试的代码块。

`catch` 语句允许我们定义当 try 代码块发生错误时，所执行的代码块。

`throw` 语句允许我们创建或抛出异常。

```
try {
	if(1+1==2) throw '挺正常的'
	if(1+1>2) throw '挺励志的'
	if(1+1<2) throw '友谊的小船翻了' 
}
catch(err) {
	console.log(err)
}
```

在 `Swift` 中, 

有 4 种处理错误的方式。

* 把函数抛出的错误传递给调用此函数的代码
* 用 `do-catch` 语句处理错误
* 将错误作为可选类型处理
* 断言此错误根本不会发生

错误用遵循 `ErrorType` 协议类型的值来表示。这个空协议表示一种可以用做错误处理的类型。

可以使用 `defer` 语句在代码执行到要离开当前的代码段之前去执行一套语句。

该语句让你能够做一些应该被执行的必要清理工作, 不管是以何种方式离开当前的代码段的.

* 由于 `抛出错误` 而离开
* 一条 `return` 或者 `break` 的类似语句。

```
// 错误用遵循 `ErrorType` 协议类型的值来表示
enum testError: ErrorType {
    case Error1
    case Error2
}
// 用 throws 关键字标来识一个可抛出错误的函数,方法或是构造器
func canThrowErrors() throws -> String{
    // 指定清理代码
    defer {
        print("All done, clean up here")
    }
    // 抛出错误
    guard 1+1>2 else {
        throw testError.Error1
    }
    return ""
    // 在这里, 作用域的最后调用close(file)
}
// 捕捉错误, 处理错误
do {
    try canThrowErrors()
}
catch testError.Error1 {
    print(1)
}
// 多条处理语句
catch testError.Error2 {
    print(2)
}
// 将错误转换成可选值, 错误抛出的时候表达式的值是 `nil`
let x = try? canThrowErrors()
// 使错误传递失效
let y = try! canThrowErrors()
```

#### 断言

在 `Swift` 中, 

在某些情况下,如果值缺 失或者值并不满足特定的条件,你的代码可能没办法继续执行。

这时,你可以在你的代码中触发一个断言(asser tion)来结束代码运行并通过调试来找到值缺失的原因。

断言会在运行时判断一个逻辑条件是否为 true 。

如果条件判断为 true ,代码运行会继续进行;如 果条件判断为 false ,代码执行结束,你的应用被终止。

触发断言后可以看到不合法的状态发生在什么地方, 断言允许你附加一条调试信息。

```
extension NSObject{
    class func mockData(mockTypes: [String : NSObject]?, length: Int, callbackBlock: (instanceList: [AnyObject]) -> Void) -> Void {
        let mock = SwiftyMock.sharedInstance; 
        mock.instanceList = []
        for index in 0..<length {
            let _mockTypes : [String : NSObject]
            let instance = self.init()
            mock.instanceList.append(instance)
            if let mockTypes = mockTypes {
                _mockTypes = mockTypes
            }
            else {
                if let mockTypes = instance.mockTypes() {
                    _mockTypes = mockTypes
                }
                else {
                    _mockTypes = [:]
                    // 这里由于条件不足, 触发了断言
                    assert(false, "请输入mockTypes参数或者重写mockTypes方法")
                }
            }
            mock.fillInstanceDatas(index, mockTypes: _mockTypes)
        }
        callbackBlock(instanceList: mock.instanceList)
    }
    func mockEntity() -> NSObject {
        let mock = SwiftyMock.sharedInstance;   
        if let mockTypes = self.mockTypes() {
            mock.fillEntityDatas(self, mockTypes: mockTypes)
        }
        else {
            // 这里由于条件不足, 触发了断言
            assert(false, "内嵌的entity必须重写mockTypes方法")
        }
        return self
    }
    func mockTypes() -> [String : NSObject]? {
        return nil
    }
}
```

#### 访问控制

在 `Swift` 中, 

为代码中的实体提供了三种不同的访问级别。

这些访问级别不仅与源文件中定义的实体相关,同时也与源 文件所属的模块相关。

* `public` - 可以访问自己模块中源文件里的任何实体, 别人也可以通过引入该模块来访问源文件里的所有实体。
* `internal` - 可以访问自己模块中源文件里的任何实体, 但是别人不能访问该模块中源文件里的实体。`默认访问级别`
* `private` - 只能在当前源文件中使用的实体, 称为私有实体。

```
// 显式的 public 类
public class SomePublicClass {
    public var somePublicProperty = 0   // 显式的 public 类成员
    var someInternalProperty = 0        // 隐式的 internal 类成员
    private func somePrivateMethod() {} // 显式的 private 类成员
}
// 隐式的 internal 类
class SomeInternalClass {
    var someInternalProperty = 0        // 隐式的 internal 类成员
    private func somePrivateMethod() {} // 显式的 private 类成员
}
// 显式的 private 类
private class SomePrivateClass {
    var somePrivateProperty = 0         // 隐式的 private 类成员
    func somePrivateMethod() {}         // 隐式的 private 类成员
}
```

## 回味


