# 4-CSS组件
Bootstrap的CSS组件包括Icon图标（Glyphicon）、下拉菜单（Dropdown）、按钮组（Button group）、按钮下拉菜单（Button dropdown）、输入框组（Input Group）、导航（Nav）、导航条（NavBar）、面包屑导航（Breadcrumb）、分页导航（Pagination）、标签（Label）、徽章（Badge）、大屏幕展播（Jumbotron）、页面标题（Pageheader）、缩略图（Thumbnail）、警告框（Alert）、进度条（Progress bar）、媒体对象（Media Object）、列表组（Listgroup）、面板（Panel）和洼地（Well）。

## 小图标
使用方式：
```html
<i class="glyphicon glyphicon-search"></i>
<span class="glyphicon glyphicon-search"></span>
```

字体格式：
* TureTpe（.ttf）：Windows和Mac最常用的字体
* OpenType（.otf）：
* Web Open Font Format（.woff）：最佳格式
* Embedded Open Type（.eot）：IE专用字体
* SVG：基于SVG渲染的

小图标可在任何内联元素上引用，可作为很多块级元素的子元素。

## 下拉菜单
```html
<div class="dropdown">
  <button class="btn btn-default dropdown-toggle" type="button" id="dropdownMenu1" data-toggle="dropdown" aria-haspopup="true" aria-expanded="true">
  下拉菜单按钮
  <span class="caret"></span>
</button>
  <ul class="dropdown-menu" aria-labelledby="dropdownMenu1">
    <li class="dropdown-header">菜单头</li>
    <li><a href="#">菜单1</a></li>
    <li><a href="#">菜单2</a></li>
    <li><a href="#">菜单3</a></li>
    <li role="separator" class="divider"></li>
    <li><a href="#">菜单4</a></li>
  </ul>
</div>
```

## 按钮组
### 基本用法
使用类为`btn-group`的div元素包裹按钮。

```html
<div class="btn-group">
  <button class="btn btn-default" type="button">按钮1</button>
  <button class="btn btn-default" type="button">按钮2</button>
  <button class="btn btn-default" type="button">按钮3</button>
</div>
```

### 按钮工具栏
在`btn-group`div外再包一层`btn-toolbar`类。

```html
<div class="btn-toolbar">
  <div class="btn-group">
    <button class="btn btn-default">按钮1</button>
    <button class="btn btn-default">按钮2</button>
    <button class="btn btn-default">按钮3</button>
  </div>
  <div class="btn-group">
    <button class="btn btn-default">按钮4</button>
    <button class="btn btn-default">按钮5</button>
    <button class="btn btn-default">按钮6</button>
  </div>
</div>
```

### 按钮尺寸设置
在`btn-group`类中加上`btn-group-lg`、`btn-group-sm`和`btn-group-xs`三个类表示控制尺寸大小。

### 嵌套分组
将按钮组之一作为下拉菜单的触发按钮：

将下拉菜单触发按钮的div父元素设置为`dropdrown`和`btn-group`。

```html
<div class="btn-group">
  <button class="btn btn-default">按钮4</button>
  <button class="btn btn-default">按钮5</button>
  <button class="btn btn-default">按钮6</button>
  <div class="dropdrown btn-group">
    <button class="btn btn-default dropdown-toggle" type="button" id="dropdownMenu1" data-toggle="dropdown" aria-haspopup="true" aria-expanded="true">
    下拉菜单按钮
    <span class="caret"></span>
      </button>
    <ul class="dropdown-menu" aria-labelledby="dropdownMenu1">
      <li class="dropdown-header">菜单头</li>
      <li><a href="#">菜单1</a></li>
      <li><a href="#">菜单2</a></li>
      <li><a href="#">菜单3</a></li>
      <li role="separator" class="divider"></li>
      <li><a href="#">菜单4</a></li>
    </ul>
  </div>
</div>
```

### 垂直分组
将类`btn-group`换为`btn-group-vertical`即可（不是增加）。

### 自适应分组
在类为`btn-group`的div上应用`btn-group-justified`后子元素会平分父元素空间并占满父元素。

## 输入框组
### 基本用法
文本输入框和小icon（addon）组合起来组成输入框组。

```html
<div class="input-group">
  <span class="input-group-addon">$</span>
  <input type="text" class="form-control">
  <span class="input-group-addon">.00</span>
</div>
```

实现方法：

1. 各元素`margin`设为0，即无缝拼接。
2. 各元素设置为等高显示，即`display`设置为`table-cell`。
3. 设置`addon`元素的显示方式。
4. 将组里第一个的左侧两个角和最后一个右侧两个角进行圆角处理。

### 尺寸大小设置
在类`input-group`上添加类`input-group-lg`或者`input-group-sm`可以实现对输入组大小的调整。

如果不想`addon`元素大小和input相同，那么通过对`addon`添加类`input-lg`或者`input-sm`实现。

## 导航
导航是网站重要的组成部分。使用时主要通过设置`nav`类和具体的样式类来实现效果。其中`nav`类只指定基础布局样式和显示状态，具体样式通过`nav-*`类设定。

### 选项卡导航
类`nav-tabs`。

```html
<ul class="nav nav-tabs">
  <li class="active"><a href="">选项卡1</a></li>
  <li><a href="">选项卡2</a></li>
  <li class="disabled"><a href="">选项卡3</a></li>
</ul>
```

### 胶囊式选项卡导航
类`nav-pills`

### 堆叠式导航
类`nav-stacked`，一般在`nav-pills`类上添加。

在`li`元素上添加`nav-divider`类可实现分隔条效果。

### 自适应导航
类`nav-justified`，子元素平分，占满父元素。

### 禁用链接
对`li`元素使用`disabled`类可以实现对链接禁用，仅实现外观，未实现逻辑。

## 导航条
比导航多背景条

### 基础导航条
```html
<nav class="navbar navbar-default" role="navigation">
  <div class="navbar-header">
    <a href="" class="navbar-brand">标题</a>
  </div>
  <ul class="nav navbar-nav">
    <li class="active"><a href="">导航1</a></li>
    <li><a href="">导航2</a></li>
    <li><a href="">导航3</a></li>
    <li><a href="">导航4</a></li>
  </ul>
</nav>
```

为了增强可访问性，需要增加`role=navigation`的属性。

### 导航条中的表单
```html
<nav class="navbar navbar-default" role="navigation">
  <div class="navbar-header">
    <a href="" class="navbar-brand">表单</a>
  </div>
  <form action="" class="navbar-form navbar-left" role="search">
    <div class="form-group"><input type="text" class="form-control" placeholder="search"></div>
    <button class="btn btn-default" type="submit">左按钮</button>
  </form>
  <form action="" class="navbar-form navbar-right" role="right">
    <div class="form-group"><input type="text" class="form-control" placeholder="search"></div>
    <button class="btn btn-default" type="submit">右按钮</button>
  </form>
</nav>
```

### 导航条左右浮动
类`navbar-left`实现左浮动，类`navbar-right`实现右浮动。

### 顶部固定或者底部固定
类`navbar-fixed-top`和`navbar-fixed-bottom`

### 去圆角
类`navbar-static-top`

### 响应式导航条
```html
<div class="navbar navbar-default">
  <div class="navbar-header">
    <button class="navbar-toggle" data-toggle="collapse" data-target=".navbar-responsive-collapse">
      <span class="sc-only">触发导航</span>
      <span class="icon-bar"></span>
      <span class="icon-bar"></span>
      <span class="icon-bar"></span>
    </button>
    <a href="" class="navbar-brand">标题</a>
  </div>
  <div class="collapse navbar-collapse navbar-responsive-collapse">
    <ul class="nav navbar-nav">
      <li class="active"><a href="">导航1</a></li>
      <li><a href="">导航2</a></li>
      <li><a href="">导航3</a></li>
      <li><a href="">导航4</a></li>
      <li><a href="">导航5</a></li>
      <li class="dropdown">
        <a data-toggle="dropdown" class="dropdown-toggle" href="">下拉菜单<b class="caret"></b></a>
        <ul class="dropdown-menu">
          <li><a href="">子菜单1</a></li>
          <li><a href="">子菜单2</a></li>
          <li><a href="">子菜单3</a></li>
        </ul>
      </li>
    </ul>
  </div>
</div>
```

将导航的HTML包在一个div中，并设置`collapse`、`navbar-collapse`和`navbar-responsive-collapse`三个类，表示小于768px不显示导航项。

同时导航头部使用类为`navbar-toggle`的button将图标包在里面，这是规定。

### 反色导航条
将类`navbar-default`替换为`navbar-inverse`。

## 面包屑导航
```html
<ul class="breadcrumb">
  <li><a href="">条1</a></li>
  <li><a href="">条2</a></li>
  <li class="active">条3</li>
</ul>
```

## 分页导航
类`pagination`，有`active`和`disabled`样式。

```html
<ul class="pagination">
  <li><a href="#">&laquo;</a></li>
  <li><a href="#">1</a></li>
  <li><a href="#">2</a></li>
  <li><a href="#">&raquo;</a></li>
</ul>
```

通过使用`pagination-lg`和`pagination-sm`控制大小。

### 翻页
```html
<ul class="pager">
  <li><a href="">上一页</a></li>
  <li><a href="">下一页</a></li>
</ul>
```

使用`previous`或者`next`实现左右对齐。

使用`disabled`禁用。

## 标签
类`label`，实现对文字添加高亮背景。

设置颜色：`label-default`、`label-primary`、`label-success`、`label-warning`、`label-danger`和`label-info`。

## 徽章
```html
<a href="#">链接<span class="badge">10</span></a>
```

## 大屏幕展播
类`Jumbotron`

## 页面标题
类`page-header`

## 缩略图
类`thumbnail`，然后图片作为其子元素，子元素还可以是其他的文字或者按钮。

## 警告框
```html
<div class="alert">
  <button class="close" data-dismiss="alert">&times;</button>
  <strong>警告！</strong>警告
</div>
```

类`alert`还可添加`alert-info`、`alert-warning`、`alert-danger`和`alert-success`。

警告框中的链接可以使用样式类`alert-link`。

## 进度条
