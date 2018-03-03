
# CSS编码规范

[CSS](#user-content-1-css)

　　[1.1 缩进](#user-content-11-缩进)

　　[1.2 分号](#user-content-12-分号)

　　[1.3 空格](#user-content-13-空格)

　　[1.4 空行](#user-content-14-空行)

　　[1.5 换行](#user-content-15-换行)

　　[1.6 注释](#user-content-16-注释)

　　[1.7 引号](#user-content-17-引号)

　　[1.8 命名](#user-content-18-命名)

　　[1.9 属性声明顺序](#user-content-19-属性声明顺序)

　　[1.10 颜色](#user-content-110-颜色)

　　[1.11 属性简写](#user-content-111-属性简写)

　　[1.12 LESS相关](#user-content-112-LESS相关)

　　[1.13 媒体查询](#user-content-113-媒体查询)

　　[1.14 其他](#user-content-114-其他)

## CSS

### 1.1 缩进

    使用soft tab（4个空格）

### 1.2 分号

    每个属性声明末尾都要加分号

### 1.3 以下几种情况不需要空格：

    属性名后
    多个规则的分隔符','前
    !important '!'后
    属性值中'('后和')'前
    行末不要有多余的空格
    以下几种情况需要空格：

    属性值前
    选择器'>', '+', '~'前后
    '{'前
    !important '!'前
    @else 前后
    属性值中的','后
    注释'/*'后和'*/'前
```css
/* not good */
.element{
    ...
}

/* good */
.element {
    ...
}

/* not good */
@if{
    ...
}@else{
    ...
}

/* good */
@if {
    ...
} @else {
    ...
}
```
### 1.4 空行
    以下几种情况需要空行：

    文件最后保留一个空行
    '}'后最好跟一个空行，包括less中嵌套的规则
    属性之间需要适当的空行，具体见[属性声明顺序](#user-content-19-属性声明顺序)

### 1.5 换行

    以下几种情况不需要换行：
    '{'前
    以下几种情况需要换行：
    '{'后和'}'前
    每个属性独占一行
    多个规则的分隔符','后

### 1.6 注释
    注释统一用'/* */'（不要用'//'），具体参照右边的写法；

    缩进与下一行代码保持一致；

    可位于一个代码行的末尾，与代码间隔一个空格。
```css
/* Modal header */
.modal-header {
    ...
}
```
### 1.7 引号
    最外层统一使用双引号；

    url的内容要用引号；

    属性选择器中的属性值需要引号。
```css
.element:after {
    content: "";
    background-image: url("logo.png");
}

li[data-type="single"] {
    ...
}
```
### 1.8 命名
    类名使用小写字母，以中划线分隔 如：form-wrap
    id采用驼峰式命名
    less中的变量、函数、混合、placeholder采用驼峰式命名
```css
/* class */
.form-wrap {
    ...
}

/* id */
#myDialog {
    ...
}

/* 变量 */
@colorBlack: #000;

```
### 1.9 属性声明顺序
    同一 rule set 下的属性在书写时，应按功能进行分组，并以 Formatting Model（布局方式、位置） > Box Model（尺寸） > Typographic（文本相关） > Visual（视觉效果） 的顺序书写
### 解释：

#### `Formatting Model 相关属性包括`：position / top / right / bottom / left / float / display / overflow 等
#### `Box Model 相关属性包括`：border / margin / padding / width / height 等
#### `Typographic 相关属性包括`：font / line-height / text-align / word-wrap 等
#### `Visual 相关属性包括`：background / color / transition / list-style 等

```css
.sidebar {
    /* formatting model: positioning schemes / offsets / z-indexes / display / ...  */
    position: absolute;
    top: 50px;
    left: 0;
    overflow-x: hidden;

    /* box model: sizes / margins / paddings / borders / ...  */
    width: 200px;
    padding: 5px;
    border: 1px solid #ddd;

    /* typographic: font / aligns / text styles / ... */
    font-size: 14px;
    line-height: 20px;

    /* visual: colors / shadows / gradients / ... */
    background: #f5f5f5;
    color: #333;
    -webkit-transition: color 1s;
       -moz-transition: color 1s;
            transition: color 1s;
}
```
### 1.10 颜色

    颜色16进制用小写字母；
    颜色16进制尽量用简写。
```css
/* not good */
.element {
    color: #ABCDEF;
    background-color: #001122;
}

/* good */
.element {
    color: #abcdef;
    background-color: #012;
}
```
### 1.11 属性简写
    属性简写需要你非常清楚属性值的正确顺序，而且在大多数情况下并不需要设置属性简写中包含的所有值，所以建议尽量分开声明会更加清晰；

    margin 和 padding 相反，需要使用简写；

#### `常见的属性简写包括：`

font
background
transition
animation
```css
/* not good */
.element {
    transition: opacity 1s linear 2s;
}

/* good */
.element {
    transition-delay: 2s;
    transition-timing-function: linear;
    transition-duration: 1s;
    transition-property: opacity;
}
```
### 1.12 LESS相关
    代码必须（MUST）按如下形式按顺序组织：

    1. @import
    2. 变量声明
    3. 样式声明

    当多个选择器共享一个声明块时，每个选择器声明必须（MUST）独占一行。
```css
@import "est/all.less";

@default-text-color: #333;

.page {
    width: 960px;
    margin: 0 auto;
}
/* not good */
h1, h2, h3 {
    font-weight: 700;
}

/* good */
h1,
h2,
h3 {
    font-weight: 700;
}
```
### 1.13 媒体查询
    尽量将媒体查询的规则靠近与他们相关的规则，不要将他们一起放到一个独立的样式文件中，或者丢在文档的最底部，这样做只会让大家以后更容易忘记他们。

```css
.element {
    ...
}

@media (min-width: 480px) {
    .element {
        ...
    }
}
```
### 1.14 其他

#### 私有属性前缀
    同一属性有不同私有前缀的，尽量按前缀长度降序书写，标准形式必须写在最后。且这一组属性以第一条的位置为准，尽量按冒号的位置对齐

```css
.box {
    -webkit-transform: rotate(30deg);
       -moz-transform: rotate(30deg);
        -ms-transform: rotate(30deg);
         -o-transform: rotate(30deg);
            transform: rotate(30deg);
}
```
#### `一些常用规则`
    不允许有空的规则；

    元素选择器用小写字母；

    去掉小数点前面的0；

    去掉数字中不必要的小数点和末尾的0；

    属性值'0'后面不要加单位；

    同个属性不同前缀的写法需要在垂直方向保持对齐，具体参照右边的写法；

    无前缀的标准属性应该写在有前缀的属性后面；

    不要在同个规则里出现重复的属性，如果重复的属性是连续的则没关系；

    不要在一个文件里出现两个相同的规则；

    用 border: 0; 代替 border: none;；

    选择器不要超过4层（在scss中如果超过4层应该考虑用嵌套的方式来写）；

    发布的代码中不要有 @import；

    尽量少用'*'选择器。


