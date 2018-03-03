
# HTML编码规范

[1 命名规则](#user-content-1-%E5%89%8D%E8%A8%80)

　　[1.1 项目命名](#user-content-12-%E7%BC%A9%E8%BF%9B)

　　[1.2 目录命名](#user-content-12-%E7%BC%A9%E8%BF%9B)

　　[1.3 JS文件命名](#user-content-13-%E7%A9%BA%E6%A0%BC)

　　[1.4 css文件命名](#user-content-14-%E8%A1%8C%E9%95%BF%E5%BA%A6)

　　[1.5 HTML文件命名](#user-content-15-%E9%80%89%E6%8B%A9%E5%99%A8)

[2 HTML](#user-content-2-%E4%BB%A3%E7%A0%81%E9%A3%8E%E6%A0%BC)

　　[2.1 语法](#user-content-21-%E6%96%87%E4%BB%B6)

　　[2.2 HTML5 doctype](#user-content-22-%E7%BC%A9%E8%BF%9B)

　　[2.3 lang属性](#user-content-23-%E7%A9%BA%E6%A0%BC)

　　[2.4 字符编码](#user-content-24-%E8%A1%8C%E9%95%BF%E5%BA%A6)

　　[2.5 IE兼容模式](#user-content-25-%E9%80%89%E6%8B%A9%E5%99%A8)

　　[2.6 引入CSS, JS](#user-content-26-%E5%B1%9E%E6%80%A7)

　　[2.7 属性顺序](#user-content-27-%E5%B1%9E%E6%80%A7)

　　[2.8 boolean属性](#user-content-28-%E5%B1%9E%E6%80%A7)

　　[2.9 JS生成标签](#user-content-29-%E5%B1%9E%E6%80%A7)

　　[2.10 减少标签数量](#user-content-210-%E5%B1%9E%E6%80%A7)

## 1 命名规则


### 1.1 项目命名

    全部采用小写方式， 以下划线分隔。
    例：my_project_name

### 1.2 目录命名

    使用 Camel命名法
    有复数结构时，要采用复数命名法。

    例：scripts, styles, images, dataModels

### 1.3 JS文件命名

    使用 Camel命名法
    gameCenter.js

### 1.4 CSS文件命名

    使用小写命名
    例：test.css

### 1.5 HTML文件命名

    使用 Camel命名法
    例：gameCenter.html

## 2 HTML


### 2.1 语法

    缩进使用soft tab（4个空格）；
    嵌套的节点应该缩进；
    在属性上，使用双引号，不要使用单引号；
    属性名全小写，用中划线做分隔符；
    不要在自动闭合标签结尾处使用斜线（HTML5 规范 指出他们是可选的）；
    不要忽略可选的关闭标签，例：</li> 和 </body>。

### 2.2 HTML5 doctype
    在页面开头使用这个简单地doctype来启用标准模式，使其在每个浏览器中尽可能一致的展现；

#### 虽然doctype不区分大小写，但是按照惯例， `doctype大写` 

示例：

```html
<!DOCTYPE html>
<html>
	...
</html>
```

### 2.3 lang属性

    根据HTML5规范：

    应在html标签上加上lang属性。这会给语音工具和翻译工具帮助，告诉它们应当怎么去发音和翻译。

    更多关于 lang 属性的说明在[这里](http://www.w3.org/html/wg/drafts/html/master/semantics.html#the-html-element)；

### 2.4 字符编码

    通过声明一个明确的字符编码，让浏览器轻松、快速的确定适合网页内容的渲染方式，通常指定为`UTF-8`。

### 2.5 IE兼容模式

    用 `meta` 标签可以指定页面应该用什么版本的IE来渲染；

    更多IE meta，请点击[这里](https://stackoverflow.com/questions/6771258/what-does-meta-http-equiv-x-ua-compatible-content-ie-edge-do)；

    不同doctype在不同浏览器下会触发不同的渲染模式,[点击这里](https://hsivonen.fi/doctype/)。

### 2.6 引入CSS, JS

    根据HTML5规范, 通常在引入CSS和JS时不需要指明 type，因为 text/css 和 text/javascript 分别是他们的默认值。
    
### 2.7 属性顺序

    属性应该按照特定的顺序出现以保证易读性；
     - class
     - id
     - name
     - data-*
     - src, for, type, href, value , max-length, max, min, pattern
     - placeholder, title, alt
     - aria-*, role
     - required, readonly, disabled

`class是为高可复用组件设计的，所以应处在第一位；`

`id更加具体且应该尽量少使用，所以将它放在第二位。`

### 2.8 boolean属性

    boolean属性指不需要声明取值的属性，XHTML需要每个属性声明取值，但是HTML5并不需要；

`boolean属性的存在表示取值为true，不存在则表示取值为false。`

```html
<input type="text" disabled>

<input type="checkbox" value="1" checked>

<select>
    <option value="1" selected>1</option>
</select>
```

### 2.9 JS生成标签
`在JS文件中生成标签让内容变得更难查找，更难编辑，性能更差。应该尽量避免这种情况的出现。`

### 2.10 减少标签数量
    在编写HTML代码时，需要尽量避免多余的父节点；

    很多时候，需要通过迭代和重构来使HTML变得更少。
```html
<!-- Not well -->
<span class="avatar">
    <img src="...">
</span>

<!-- Better -->
<img class="avatar" src="...">
```

`实用高于完美
尽量遵循HTML标准和语义，但是不应该以浪费实用性作为代价；
任何时候都要用尽量小的复杂度和尽量少的标签来解决问题。`






