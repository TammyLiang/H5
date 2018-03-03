
# JavaScript编码规范

[JavaScript](#user-content-1-css)

　　[1.1 缩进](#user-content-11-缩进)

　　[1.2 单行长度](#user-content-12-单行长度)

　　[1.3 分号](#user-content-13-分号)

　　[1.4 空格](#user-content-14-空格)

　　[1.5 空行](#user-content-15-空行)

　　[1.6 换行](#user-content-16-换行)

　　[1.7 单行注释](#user-content-17-单行注释)

　　[1.8 多行注释](#user-content-18-多行注释)

　　[1.9 文档注释](#user-content-19-文档注释)

　　[1.10 引号](#user-content-110-引号)

　　[1.11 变量命名](#user-content-111-变量命名)

　　[1.12 变量声明](#user-content-112-变量声明)

　　[1.13 函数](#user-content-113-函数)

　　[1.14 数组、对象](#user-content-114-数组、对象)

　　[1.15 括号](#user-content-115-括号)

　　[1.16 null](#user-content-116-null)

　　[1.17 undefined](#user-content-117-undefined)

　　[1.18 jshint](#user-content-118-jshint)

　　[1.19 其他](#user-content-119-其他)

## JavaScript

### 1.1 缩进

    使用soft tab（4个空格）

### 1.2 单行长度

    不要超过80，但如果编辑器开启word wrap可以不考虑单行长度。

### 1.3 分号
    以下几种情况后需加分号：

    变量声明
    表达式
    return
    throw
    break
    continue
```js
/* var declaration */
var x = 1;

/* expression statement */
x++;

/* do-while */
do {
    x++;
} while (x < 10);
```

### 1.4 空格

#### `以下几种情况不需要空格：`
    对象的属性名后
    前缀一元运算符后
    后缀一元运算符前
    函数调用括号前
    无论是函数声明还是函数表达式，'('前不要空格
    数组的'['后和']'前
    对象的'{'后和'}'前
    运算符'('后和')'前

#### `以下几种情况需要空格：`
    二元运算符前后
    三元运算符'?:'前后
    代码块'{'前
    下列关键字前：else, while, catch, finally
    下列关键字后：if, else, for, while, do, switch, case, try, catch, finally, with, return, typeof
    单行注释'//'后（若单行注释和代码同行，则'//'前也需要），多行注释'*'后
    对象的属性值前
    for循环，分号后留有一个空格，前置条件如果有多个，逗号后留一个空格
    无论是函数声明还是函数表达式，'{'前一定要有空格
    函数的参数之间

### 1.5 空行

`以下几种情况需要空行：`

    变量声明后（当变量声明在代码块的最后一行时，则无需空行）
    注释前（当注释在代码块的第一行时，则无需空行）
    代码块后（在函数调用、数组、对象中则无需空行）
    文件最后保留一个空行

### 1.6 换行

    换行的地方，行末必须有','或者运算符；

    以下几种情况不需要换行：

    下列关键字后：else, catch, finally
    代码块'{'前
    以下几种情况需要换行：

    代码块'{'后和'}'前
    变量赋值后

### 1.7 单行注释

    双斜线后，必须跟一个空格；

    缩进与下一行代码保持一致；

    可位于一个代码行的末尾，与代码间隔一个空格。
```js
if (condition) {
    // if you made it here, then all security checks passed
    allowed();
}

var zhangsan = 'zhangsan'; // one space after code
```

### 1.8 多行注释

    最少三行, '*'后跟一个空格，具体参照下方的写法；

`建议在以下情况下使用：`

    难于理解的代码段
    可能存在错误的代码段
    浏览器特殊的HACK代码
    业务逻辑强相关的代码
```js
/*
 * one space after '*'
 */
var x = 1;
```

### 1.9 文档注释
    各类标签@param, @method等请参考usejsdoc和JSDoc Guide；

`建议在以下情况下使用：`

    所有常量
    所有函数
    所有类
```js
/**
 * @func
 * @desc 一个带参数的函数
 * @param {string} a - 参数a
 * @param {number} b=1 - 参数b默认值为1
 * @param {string} c=1 - 参数c有两种支持的取值</br>1—表示x</br>2—表示xx
 * @param {object} d - 参数d为一个对象
 * @param {string} d.e - 参数d的e属性
 * @param {string} d.f - 参数d的f属性
 * @param {object[]} g - 参数g为一个对象数组
 * @param {string} g.h - 参数g数组中一项的h属性
 * @param {string} g.i - 参数g数组中一项的i属性
 * @param {string} [j] - 参数j是一个可选参数
 */
function foo(a, b, c, d, g, j) {
    ...
}
```
### 1.10 引号
    最外层统一使用单引号。
```js
// not good
var x = "test";

// good
var y = 'foo',
    z = '<div id="test"></div>';
```
### 1.11 变量命名

    标准变量采用驼峰式命名（除了对象的属性外，主要是考虑到cgi返回的数据）
    'ID'在变量名中全大写
    'URL'在变量名中全大写
    'Android'在变量名中大写第一个字母
    'iOS'在变量名中小写第一个，大写后两个字母
    常量全大写，用下划线连接
    构造函数，大写第一个字母
    jquery对象必须以'$'开头命名
```js
var goodID;

var reportURL;

var AndroidVersion;

var iOSVersion;

var MAX_COUNT = 10;

function Person(name) {
    this.name = name;
}

// not good
var body = $('body');

// good
var $body = $('body');
```
### 1.12 变量声明

    一个函数作用域中所有的变量声明尽量提到函数首部，用一个var声明，不允许出现两个连续的var声明。
```js
function doSomethingWithItems(items) {
    // use one var
    var value = 10,
        result = value + 10,
        i,
        len;

    for (i = 0, len = items.length; i < len; i++) {
        result += 10;
    }
}
```
### 1.13 函数
    无论是函数声明还是函数表达式，'('前不要空格，但'{'前一定要有空格；

    函数调用括号前不需要空格；

    立即执行函数外必须包一层括号；

    不要给inline function命名；

    参数之间用', '分隔，注意逗号后有一个空格。
```js
// no space before '(', but one space before'{'
var doSomething = function(item) {
    // do something
};

function doSomething(item) {
    // do something
}

// not good
doSomething (item);

// good
doSomething(item);

// requires parentheses around immediately invoked function expressions
(function() {
    return 1;
})();

// not good
[1, 2].forEach(function x() {
    ...
});

// good
[1, 2].forEach(function() {
    ...
});

// not good
var a = [1, 2, function a() {
    ...
}];

// good
var a = [1, 2, function() {
    ...
}];

// use ', ' between function parameters
var doSomething = function(a, b, c) {
    // do something
};
```

### 1.14 数组、对象
    对象属性名不需要加引号；

    对象以缩进的形式书写，不要写在一行；

    数组、对象最后不要有逗号。
```js
// not good

var a = {'b': 1};

// good
var a = {
    b: 1,
    c: 2
};
```
### 1.15 括号

`下列关键字后必须有大括号（即使代码块的内容只有一行）：`

if, else, for, while, do, switch, try, catch, finally, with。

### 1.16 null

`适用场景：`

    初始化一个将来可能被赋值为对象的变量

    与已经初始化的变量做比较

    作为一个参数为对象的函数的调用传参

    作为一个返回对象的函数的返回值

`不适用场景：`

    不要用null来判断函数调用时有无传参

    不要与未初始化的变量做比较
```js
// not good
function test(a, b) {
    if (b === null) {
        // not mean b is not supply
        ...
    }
}

var a;

if (a === null) {
    ...
}

// good
var a = null;

if (a === null) {
    ...
}
```

### 1.17 undefined

`永远不要直接使用undefined进行变量判断；`

`使用typeof和字符串'undefined'对变量进行判断。`

```js
// not good
if (person === undefined) {
    ...
}

// good
if (typeof person === 'undefined') {
    ...
}
```

### 1.18 jshint

    用'===', '!=='代替'==', '!='；

    for-in里一定要有hasOwnProperty的判断；

    不要在内置对象的原型上添加方法，如Array, Date；

    不要在内层作用域的代码里声明了变量，之后却访问到了外层作用域的同名变量；

    变量不要先使用后声明；

    不要在一句代码中单单使用构造函数，记得将其赋值给某个变量；

    不要在同个作用域下声明同名变量；

    不要在一些不需要的地方加括号，例：delete(a.b)；

    不要使用未声明的变量（全局变量需要加到.jshintrc文件的globals属性里面）；

    不要声明了变量却不使用；

    不要在应该做比较的地方做赋值；

    debugger不要出现在提交的代码里；

    数组中不要存在空元素；

    不要在循环内部声明函数；

    不要像这样使用构造函数，例：new function () { ... }, new Object；

### 1.19 其他

    不要混用tab和space；

    不要在一处使用多个tab或space；

    换行符统一用'LF'；

    对上下文this的引用只能使用'_this', 'that', 'self'其中一个来命名；

    行尾不要有空白字符；

    switch的falling through和no default的情况一定要有注释特别说明；

    不允许有空的代码块



