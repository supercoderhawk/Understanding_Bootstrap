# CSS布局

CSS布局包括：**基础排版** 、**代码**、 **表格**、**表单**、**按钮**、**图片**、**辅助类** 和 **响应式设计**。

## 基础排版
### 标题
|元素|字体大小|计算比例|
|---|---|---|
|h1|36px|14px * 2.6|
|h2|30px|14px * 2.15|
|h3|24px|14px * 1.70|
|h4|18px|14px * 1.25|
|h5|14px|14px * 1.00|
|h6|12px|14px * 0.85|

其中 `h1`~`h3`有`margin-top:20px;margin-bottom:10px;`的样式，`h4`~`h6`有`margin-top:10px;margin-bottom:10px;`

除了使用`h*`元素，还可以使用`class`为`h*`的`div`元素申明标题，效果和`h*`元素小相同。

标题元素中可以应用`small`元素，字体稍小，颜色为`#999`，对于`h1`~`h3`，为原来的65%，对于`h4`~`h6`，为原来的75%。

### 页面主题
Bootstrap默认全局字体（<body>元素）大小为14px，行间距`line-height`为字体大小的1.428倍，即20px。而<html>元素字体大小为10px。

p元素有一个额外的`margin-bottom`，默认为行间距的一半（10px）。

对于p元素，可以使用`lead`类来起强调作用。

使用`text-left`、`text-center`、`text-right`、`text-justify`类可以分别实现文本的左对齐，居中对齐、右对齐和两端对齐。

### 缩略语
Bootstrap在`abbr`元素上实现了缩略词的功能，即鼠标移动到缩略词上，显示`title`属性里面的值。

```html
<abbr title="缩略语" class="initialism">abbr</abbr>
```

### 地址元素
Bootstrap为地址元素定义了简单的通用样式，主要是行间距和底部的`margin`。

### 引用
Bootstrap使用`blockquote`元素实现引用，使用`small`元素可自动在引用说明前面加上短横杠。还提供了`pull-right`，实现右对齐，`small`元素的短横杠加在了后面。

```html
<blockquote>
  <p>引用</p>
  <small><cite title="测试">引用</cite></small>
</blockquote>

<blockquote class="pull-right">
  <p>引用</p>
  <small><cite title="测试">引用</cite></small>
</blockquote>
```


### 列表
Bootstrap提供了六种形式的列表，分别是：

* 普通列表
* 有序列表
* 去点列表
* 内联列表
* 描述列表
* 水平描述列表

#### 普通列表
使用形如

```html
<ul>
  <li></li>
  <li></li>
</ul>
```

的形式插入普通列表，Bootstrap对默认样式进行了微调。

#### 有序列表
使用形如

```html
<ol>
  <li></li>
  <li></li>
</ol>
```

的形式插入有序列表，Bootstrap对默认样式进行了微调。

#### 去点列表
对`ul`元素使用类`list-unstyled`实现去点列表功能。

#### 内联列表
Bootstrap对定义列表做了一些微调，同时定义了类为`dl-horizontal`的样式。可以实现列表的水平显示。其中`dt`标题长度为160，超出将被自动隐藏。

```html
<dl class="dl-horizontal">
  <dt>项一</dt>
  <dd>项一的一些描述</dd>
</dl>
```

## 代码
单行内联代码使用`code`元素，用户输入代码使用`kbd`元素，多行代码使用`pre`元素，`pre`元素显示大段代码，保留格式，使用`pre-scrollable`类样式控制该区域最大高度为340px，并且可以在y方向上滚动。

## 表格
表格组件中，Bootstrap提供了一种基础样式类`table`，四种附加样式类：`table-striped`、`table-bordered`、`table-hover`和`table-condensed`以及一个支持响应式布局的`table-responsive`容器样式。

表格最外层为table元素，table元素内有`thead`和`tbody`元素，`thead`元素中的`th`子元素定义表格列名，`tbody`中的子元素`tr`定义行，`tr`子元素`td`定义单元格。

### 基础样式
`table`类主要增加了单元格内边距，在`thead`底部设置了`2px`的线，在`tr`顶部设置1px的线。
```html
<table class="table">
  <thead>
    <th>头</th>
  </thead>
  <tbody>
    <tr><td>表</td></tr>
  </tbody>
</table>
```

### 带背景条纹的表格
`table`元素的`table-striped`类为表格添加了隔行的背景条纹。IE8即以下无效。


### 带边框的表格
`table-bordered`类为所有单元格添加1条1px的边框。

### 鼠标悬停高亮
`table-hover`类提供了鼠标悬停高亮的功能。

### 紧凑型表格
`table-condensed`类提供了紧凑型表格的效果，实现原理是减少单元格的内边距。

### 行级元素样式
`tr`元素可以有5中额外的样式来控制`tr`背景颜色。

|样式类|描述|
|`active`|表示当前活动的信息|
|`success`|表示成功或者正确的行为|
|`info`|表示中立的信息或者行为|
|`warning`|表示警告，需要特别注意|
|`danger`|表示危险或者可能是错误的行为|

### 响应式表格
将类为`table-responsive`的div元素包在表格外部就可设计响应式表格。效果是在小于768px的小屏幕上水平滚动，屏幕大于768px时，水平滚动条消失。

## 表单
表单是HTML网页交互最重要的部分，同时也是Bootstrap框架中的核心内容，表单提供了丰富的样式（基础、内联和横向等等）。

### 基础表单
Bootstrap对表单元素未做太多的定制化效果设计，仅做微调。

如果在`select`、`input`、`textarea`元素上应用了`form-control`样式，显示的宽度会变为100%，并且`placeholder`颜色都设置成`#999`。

类`form-group`样式提供了`margin-bottom`为15px的底部外边距，该类可以应用到div元素上。

### 内联表单
在`form`元素上应用一个`form-inline`样式，可以将表单内的元素设置为内联样式。

### 横向表单
类`form-horizontal`只设置了`padding`和`margin`值，只能实现单个form-group的水平排列，要实现真正的横向表单，需要使用Bootstrap栅格系统，由于`form-horizontal`改写了`form-group`的行为，将其表现得像栅格系统中的`row`一样，所以对于`form-group`子元素可以直接使用`col-*`类。

示例如下：

```html
<form action="" class="form-horizontal" role="form">
  <div class="form-group">
    <label for="account" class="col-sm-2 control-label">用户名</label>
    <div class="col-sm-10">
      <input type="text" class="form-control" placeholder="请输入你的用户名">
    </div>

  </div>
  <div class="form-group">
    <label for="password" class="col-sm-2 control-label">密码</label>
    <div class="col-sm-10">
      <input type="text" class="form-control" placeholder="请输入你的密码">
    </div>
  </div>
  <div class="form-group">
    <div class="col-sm-offset-2 col-sm-10">
      <div class="checkbox"><label for=""><input type="checkbox">记住密码</label></div>
    </div>
  </div>
  <div class="form-group">
    <div class="col-sm-offset-2 col-sm-10"><button class="btn btn-default" type="submit">登录</button></div>
  </div>
</form>
```

### 表单控件
Bootstrap对`input`、`select`和`textarea`有良好的支持，对现有的HTML5的input都进行了支持，包括`text`、`password`、`datetime`、`datetime-local`、`date`、`month`、`time`、`week`、`number`、`email`、`url`、`search`、`tel`和`color`元素。

#### select元素
```html
select元素是下拉列表框，使用`multiple`属性表示可选择多个。
<select name="" id="" multiple="multiple">
  <option value="">1</option>
  <option value="">2</option>
  <option value="">3</option>
  <option value="">4</option>
</select>
```

#### textarea元素
`textarea`元素中定义`rows`属性即可自定义大文本框的高度，定义`cols`可以定义文本框宽度，如果定义了`form-control`属性，`cols`将失效。

#### checkbox和radio
checkbox是指复选框，radio指单选框。使用方法：声明一个类为`checkbox`或者`radio`的div元素，子元素为`label`元素，在`label`元素中插入类型为`checkbox`或者`radio`的`input`元素，解决左右边距对不齐的问题。

```html
<div class="checkbox">
  <label for="" ><input type="checkbox">选项1</input></label>
  <label for="" class="checkbox-inline"><input type="checkbox">选项2</input></label>
  <label for=""><input type="checkbox">选项3</input></label>
  <label for=""><input type="checkbox">选项4</input></label>
  <label for=""><input type="checkbox">选项5</input></label>
</div>
```

### 控件状态
Bootstrap提供了三种状态样式，分别是：焦点状态、禁用状态和验证提示状态。其中焦点状态和禁用状态需要`form-control`类。

#### 焦点状态
对:focus加的效果。

#### 禁用状态
使用`disabled`属性。父元素设置后子元素会继承。

#### 验证提示状态
Bootstrap提供了`has-warning`、`has-error`和`has-success`三种样式表示警告、错误和成功。不需要`form-control`类。

### 控件大小
用类`*-sm`或者`*-sm`可以设置控件的不同大小，可适用于input、select和textarea元素。

## 按钮
### 按钮样式
通过类`btn`声明按钮，按钮总共有七种样式，分别是`btn-default`、`btn-primary`、`btn-success`、`btn-info`、`btn-warning`、`btn-danager`和`btn-link`。

### 按钮大小
通过类`btn-lg`、`btn-sm`和`btn-xs`调整按钮大小。

按钮默认大小是根据内容进行调整的，可通过设定`btn-block`类让其充满父容器。

### 多标签支持
按钮支持button、a和input（type为submit或者button）的元素。

### 活动状态
通过类`active`将其变为活动状态，效果是按钮按下的效果。

### 禁用状态
通过`disabled`类或者`disabled`属性将其变为禁用状态。

## 图像
Bootstrap为图像提供了三种样式：`img-rounded`、`img-circle`和`img-thumbnail`三种样式。

## 辅助样式
### 文本样式
颜色类：
* `text-muted`：柔和灰
* `text-primary`：主要蓝
* `text-success`：成功绿
* `text-info`：信息蓝
* `text-warning`：警告黄
* `text-danger`：危险红

背景样式类：
* `bg-primary`：主要蓝
* `bg-success`：成功绿
* `bg-info`：信息蓝
* `bg-warning`：警告黄
* `bg-danger`：危险红

### 辅助图标
关闭图标：

```html
<a href="" class="close">&times;</a>   // &times; 代表乘号
<button type="button" class="close">&times;</button>
```

下拉箭头：

```html
<div class="caret"></div>
```

### 内容浮动
* `pull-left`：左浮动
* `pull-right`：右浮动
* `center-block`：居中对齐
* `clearfix`：清除浮动

### 隐藏与显示
类`show`表示显示。
类`invisible`表示不显示但是占用文档流
类`hidden`表示不显示也不占用文档流
类`text-hide`表示不显示文本但是显示背景效果

## 响应式样式
`visible-xs`：只对超小屏幕可见
`visible-sm`：小屏幕可见
`visible-md`：中等屏幕可见
`visible-lg`：大屏幕可见

`hidden-*`：与上面的作用相反

`visible-print`：打印时可见
`hidden-print`：打印时隐藏
