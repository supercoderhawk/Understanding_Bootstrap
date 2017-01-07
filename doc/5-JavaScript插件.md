# JavaScript插件
## 模态弹窗
```html
<a data-target="#modal1" data-toggle="modal" class="btn btn-primary">触发弹窗</a>

<div class="modal" id="modal1">
  <div class="modal-dialog">
    <div class="modal-content">
      <div class="modal-header">
        <button class="close" data-dismiss="modal" aria-hidden="true">&times;</button>
      </div>
      <div class="modal-body">
        <p>弹窗内容</p>
      </div>
      <div class="modal-footer">
        <button class="btn btn-default" data-dismiss="modal">关闭</button>
        <button class="btn btn-primary">保存</button>
      </div>
    </div>
  </div>
</div>
```
顶层类：`modal`，然后是类`modal-dialog`，接着`modal-content`，然后`modal-header`、`modal-body`和`modal-footer`。

触发后弹窗后还添加默认背景类`modal-backdrop`。

### 声明式用法
常用使用`button`或者`a`元素声明的按钮触发弹窗，声明触发的元素必须声明两个属性，`data-toggle`和`data-target`，其中`data-toggle`为`modal`，`data-target`设置为DOM的ID值或者类名。

|属性名|类型|默认值|说明|
|--|--|--|--|
|`data-backdrop`|布尔值|true|是否包含一个背景div元素，如果为`true`，单击背景时关闭弹窗，如果为`static`，单击背景时不关闭模态框|  
|`data-keyboard`|布尔值|true|按Esc时关闭弹窗，设为false，不关闭|
|`data-show`|布尔值|true|初始化时是否显示|

### JavaScript用法

使用`$(selector).modal(option)`触发弹窗。

#### 属性
使用option对象指定属性，属性名和上表中相同，但是无`data-`前缀，且增加一个`remote`指定url，url中内容显示在弹窗中。

#### 参数
|参数名称|使用方式|说明|
|---|---|---|
|`toggle`|$().modal('toggle')|反转弹窗状态|
|`show`|$().modal('show')|显示弹窗|
|`hide`|$().modal('hide')|关闭弹窗|

#### 事件
模态弹窗支持四种事件订阅，分别对应弹出前，弹出后，关闭前和关闭后。

|事件类型|描述|
|---|---|
|`show.bs.modal`|显示前触发，被单击元素作为事件的`relatedTarget`属性|
|`shown.bs.modal`|弹出后触发，被单击元素作为事件的`relatedTarget`属性|
|`hide.bs.modal`|关闭前触发|
|`hidden.bs.modal`|关闭后触发|

## 下拉菜单
### 声明式用法
在按钮上声明`data-toggle="dropdown"`。

**为避免设置`href="#"`后调到顶部，可设置`data-target="#"`代替`href="#"`。**

设置`data-target`后，触发元素可以放在菜单父容器外部。

### JavaScript用法
`$().dropdown()`，可以带有参数`toggle`，但是会造成二次绑定事件，可以使用jquery的`one`方法，实现保证只注册一个事件。

```javascript
$().one('click',function(){

});
```

事件：`show.bs.dropdown`、`shown.bs.dropdown`、`hide.bs.dropdown`和`hidden.bs.dropdown`，作用和模态弹窗一样，但是没有`relatedTarget`。

## 滚动侦测
### 声明式用法
滚动容器（侦测目标）设置属性`data-target`为菜单id和`data-spy="scroll"`。

### JavaScript用法
`$().scrollspy({target:selector})`。 其中`target`为菜单的选择器。

示例：`$(body).scrollspy({target:'#menu'})`。

如果需要在滚动侦测容器内进行DOM更新，需用如下方式：

```javascript
$('[data-spy="scroll"]').each(function(){
  var $spy = $(this).scrollspy('refresh');
});
```

属性`offset`：滚动内容距滚动容器`offset`像素就高亮，默认值为10。

事件：`activate.bs.scrollspy`某元素设置为`active`时，触发事件。

## 选项卡
需要同时声明导航选项卡和选项卡面板，在导航链接里声明`data-toogle="tab"`。

```html
<ul class="nav nav-tabs">
  <li><a href="#home" data-toggle="tab">主页</a></li>
  <li><a href="#profile" data-toggle="tab">个人信息</a></li>
  <li><a href="#messages" data-toggle="tab">消息</a></li>
  <li><a href="#settings" data-toggle="tab">设置</a></li>
</ul>
<div class="tab-content">
  <div class="tab-pane fade active" id="home">
    <p>这是主页</p>
  </div>
  <div class="tab-pane fade" id="profile">
    <p>这是个人信息</p>
  </div>
  <div class="tab-pane fade" id="messages">
    <p>这是消息</p>
  </div>
  <div class="tab-pane fade" id="settings">
    <p>这是设置</p>
  </div>
</div>
```

将`nav-tabs`设置为`nav-pills`以及`data-toggle="pill"`可以实现胶囊导航。  

## 提示框
设置`data-toggle="tooltip"`和`data-original-title=""`启用，**只能通过JavaScript方式生效**。

### JavaScript

|属性名称|类型|默认值|描述|
|--|--|--|--|
|`animation`|布尔值|true|应用CSS fade动画|
|`html`|布尔值|false|将HTML代码作为提示语，默认使用`text`作为提示语|
|`placement`|string &#124; function|top|显示位置，包括`top`、`bottom`、`right`、`left`和`auto`，其中`auto left`表示尽量在左边，实在不行在右边|
|`selector`|string|false|触发selector时才显示tooltip|
|original-title|string &#124; function|''|提示语内容|
|`title`|string &#124; function|''|未定义`original-title`，取这个值|
|`trigger`|string|hover focus|如何触发tooltip，选项是`click`、`hover`、`focus`和`manual`，可取多个值，使用空格分开|
|`delay`|number &#124; object|0|延迟多久才显示或者关闭tooltip，不适用于`manual`触发器，传入数字，表示显示关闭时间相同，对象：{hide:100,show:200}|
|`container`| string &#124; false|false|将tooltip附加到特定的元素上|
|`template`|string|`<div class="tooltip"><div class="tooltip-arrow"></div><div class="tooltip-inner"></div></div>`|显示提示语的HTML模板|

调用

`$().tooltip()`

函数可传的参数包括`show`、`hide`、`toggle`和`destroy`。

四种事件，包括`show.bs.tooltip`、`shown.bs.tooltip`、`hide.bs.tooltip`和`hidden.bs.tooltip`。

## 弹出框
### 声明式
`data-toggle="popover"`，增加属性`data-content`表示弹出框内容。

注意：

* 在`btn-group`和`input-group`内的元素上使用`popover`时，需要指定`container:'body'`选项以避免不必要的副作用（例如popover显示后，相关页面元素可能变得更宽或者去圆角）。

* 给`disabled`或者`.disabled`元素添加`popover`，需要将增加`popover`效果的元素包裹到一个`div`中，然后对这个`div`应用`popover`。

### JavaScript用法
`$().popover(options)`。

可用选项和提示框一样，多了一个`content`，`template`变为`<div class="popover"><div class="arrow"></div><h3 class="popover-title"></h3><div class="popover-content"></div></div>`

事件和提示框一样。

## 警告框插件
### 声明式用法
```html
<div class="alert alert-warning fade in">
  <button class="close" data-dismiss="alert" type="button">&times;</button>
  <h4>警告标题</h4>
  <p>警告内容</p>
</div>
```

可以使用按钮关闭，只要在按钮上添加属性`data-dismiss="alert"`。在警告框外部也可以进行关闭操作，除了`data-dismiss`之外，还要设置`data-target`。

### JavaScript用法
禁用：`$(document).off('.alert.data-api')`。

恢复：`$([data-dismiss="alert"]).alert()`

上面的方法需要在按钮上设置`data-dismiss="alert"`，不设置的话，可以使用`$('#btn').close()`直接使用。

事件：`close.bs.alert`和`closed.bs.alert`。

## 按钮
### 声明式用法
按钮插件声明式用法支持三种元素：按钮，复选框和单选框。

设置`data-toggle="button"`后，就可以在单击的时候将按钮状态反转。

应用于单选框：

```html
<div class="btn-group" data-toggle="buttons">
  <label for="" class="btn btn-primary"><input type="radio" name="options" id="option1">男</label>
  <label for="" class="btn btn-primary"><input type="radio" name="options" id="option2">女</label>
  <label for="" class="btn btn-primary"><input type="radio" name="options" id="option3">未知</label>
</div>
```

自定义状态设置：

```html
<button id="btn1" class="btn btn-default" data-loading-text="正在加载..." data-completed-text="已完成">获取内容</button>
<script type="text/javascript">
$('#btn1').click(function(){
  var btn = $(this);
  btn.button('loading');
  setTimeout(function(){btn.button('completed')},3000);
  btn.button('reset'); //恢复
});  
</script>
```

其中`data-loading-text`表示加载，会将按钮禁用，其他情况，`data-*-text`中的`*`可以自由定义，触发时保证相同即可。

### JavaScript
`$().button('toggle')`：反转按钮状态。

## 折叠
折叠，又称手风琴效果。

```html
<div class="panel-group" id="accordion" role="tablist" aria-multiselectable="true">
  <div class="panel panel-default">
    <div class="panel-heading" role="tab" id="headingOne">
      <h4 class="panel-title">
        <a role="button" class="btn-block" data-toggle="collapse" data-parent="#accordion" href="#collapseOne" aria-expanded="true" aria-controls="collapseOne">
          Collapsible Group Item #1
        </a>
      </h4>
    </div>
    <div id="collapseOne" class="panel-collapse collapse in" role="tabpanel" aria-labelledby="headingOne">
      <div class="panel-body">
        Anim pariatur cliche reprehenderit, enim eiusmod high life accusamus terry richardson ad squid. 3 wolf moon officia aute, non cupidatat skateboard dolor brunch. Food truck quinoa nesciunt laborum eiusmod. Brunch 3 wolf moon tempor, sunt aliqua put a bird on it squid single-origin coffee nulla assumenda shoreditch et. Nihil anim keffiyeh helvetica, craft beer labore wes anderson cred nesciunt sapiente ea proident. Ad vegan excepteur butcher vice lomo. Leggings occaecat craft beer farm-to-table, raw denim aesthetic synth nesciunt you probably haven't heard of them accusamus labore sustainable VHS.
      </div>
    </div>
  </div>
  <div class="panel panel-default">
    <div class="panel-heading" role="tab" id="headingTwo">
      <h4 class="panel-title">
        <a class="collapsed btn-block" role="button" data-toggle="collapse" data-parent="#accordion" href="#collapseTwo" aria-expanded="false" aria-controls="collapseTwo">
          Collapsible Group Item #2
        </a>
      </h4>
    </div>
    <div id="collapseTwo" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingTwo">
      <div class="panel-body">
        Anim pariatur cliche reprehenderit, enim eiusmod high life accusamus terry richardson ad squid. 3 wolf moon officia aute, non cupidatat skateboard dolor brunch. Food truck quinoa nesciunt laborum eiusmod. Brunch 3 wolf moon tempor, sunt aliqua put a bird on it squid single-origin coffee nulla assumenda shoreditch et. Nihil anim keffiyeh helvetica, craft beer labore wes anderson cred nesciunt sapiente ea proident. Ad vegan excepteur butcher vice lomo. Leggings occaecat craft beer farm-to-table, raw denim aesthetic synth nesciunt you probably haven't heard of them accusamus labore sustainable VHS.
      </div>
    </div>
  </div>
  <div class="panel panel-default">
    <div class="panel-heading" role="tab" id="headingThree">
      <h4 class="panel-title">
        <a class="collapsed btn-block"  role="button" data-toggle="collapse" data-parent="#accordion" href="#collapseThree" aria-expanded="false" aria-controls="collapseThree">
          Collapsible Group Item #3
        </a>
      </h4>
    </div>
    <div id="collapseThree" class="panel-collapse collapse" role="tabpanel" aria-labelledby="headingThree">
      <div class="panel-body">
        Anim pariatur cliche reprehenderit, enim eiusmod high life accusamus terry richardson ad squid. 3 wolf moon officia aute, non cupidatat skateboard dolor brunch. Food truck quinoa nesciunt laborum eiusmod. Brunch 3 wolf moon tempor, sunt aliqua put a bird on it squid single-origin coffee nulla assumenda shoreditch et. Nihil anim keffiyeh helvetica, craft beer labore wes anderson cred nesciunt sapiente ea proident. Ad vegan excepteur butcher vice lomo. Leggings occaecat craft beer farm-to-table, raw denim aesthetic synth nesciunt you probably haven't heard of them accusamus labore sustainable VHS.
      </div>
    </div>
  </div>
</div>
```

触发元素设置`data-toggle="collapse"`和`data-parent="#id"`。

### JavaScript
`$().collapse()`

参数：`show`、`hide`和`toggle`。

option:
* `parent`：类型为`selector`，指定parent，所有折叠区域都隐藏。
* `toggle`：`boolean`，默认值为`true`，是否开启反转功能。

事件：`show.bs.collapse`、`shown.bs.collapse`、`hide.bs.collapse`和`hidden.bs,collapse`。

## 旋转轮播
```html
<div class="carousel slide" id="carousel-container" data-ride="carousel">
  <div class="carousel-inner">
    <div class="item"><img src="image/rabbit (1).jpg" alt=""></div>
    <div class="item active"><img src="image/rabbit (2).jpg" alt=""></div>
    <div class="item"><img src="image/rabbit (3).jpg" alt=""></div>
    <div class="item">
      <img src="image/rabbit (4).jpg" alt="">
      <div class="carousel-caption">
        <h3>标题</h3>
        <p>内容</p>
      </div>
    </div>
  </div>
  <ol class="carousel-indicators">
    <li data-slide-to="0" data-target="#carousel-container"></li>
    <li class="active" data-slide-to="1" data-target="#carousel-container"></li>
    <li data-slide-to="2" data-target="#carousel-container"></li>
    <li data-slide-to="3" data-target="#carousel-container"></li>
  </ol>
  <a href="#carousel-container" class="left carousel-control" data-slide="prev"><span class="glyphicon glyphicon-chevron-left"></a>
  <a href="#carousel-container" class="right carousel-control" data-slide="next"><span class="glyphicon glyphicon-chevron-right"></a>
</div>
```

说明：

* 父容器div设置`data-ride="carousel"`，并设置ID，设置类为`carousel`和`slide`。
* 内部分成三个部分：`carousel-inner`类的div，用于放置图片，`carousel-indicators`类的div，用于设置圆圈指示符，`carousel-control`和`left`与`right`类用于设置左右箭头。这两个箭头一定要放在`carousel-inner`元素后面。
* `carousel-indicators`子元素中，`data-slide-to`用于绑定图片，索引从0开始，`data-target`设置为父元素。
* a元素用于显示左右箭头，属性`data-slide`只能为`next`和`prev`。
* `item`类还可以设置字幕说明，用`carousel-caption`类div包裹。

自定义属性

|属性名称|类型|默认值|描述|
|--|--|--|--|
|`data-interval`|number|5000|幻灯片轮换的等待时间，如果为`false`，不自动开始循环|
|`data-pause`|string|hover|默认鼠标停留停止轮播，离开启动轮播|
|`data-wrap`|boolean|true|轮播是否持续循环|

### JavaScript用法
`$('#carousel-container').carousel()`。

可加的选项：`interval`、`pause`和`wrap`，意思和上表相同。

可传入不同的参数：

* `'cycle'`：循环各帧。
* `'pause'`：停止轮播。
* `number`：轮播到指定图片上。
* `'prev'`：返回上一张。
* `'next'`：转到下一张。

事件：

`slide.bs.carousel`：一张图片的轮播开始前调用
`slid.bs.carousel`：一张图片轮播开始后

## 自动定位浮标
指在顶部和底部随滚动条滚动，在页面中部保持不动，一般用于显示一些重要数据。
### 声明式用法
```html
<div data-spy="affix" data-offset="60" style="background-color:red;">导航内容</div>
<div data-spy="affix" data-offset-top="60" data-offset-bottom="60" style="background-color:red;">导航内容</div>
```

affix插件有三种不同的状态：

* `affix-top`：在正常文档流中状态定义的状态。
* `affix`：以`fixed`方式定位时的状态。
* `affix-bottom`：以absolute方式定位的状态。

### JavaScript用法
`$().affix(options)`：

选项：
offset：可设置为数字或者对象，数字表示上下偏移相同，对象设置为`{top:value,bottom:value}`形式，`value`可以为指或者 **函数**。

事件：

* `affix.bs.affix`：定位结束之前触发。
* `affixed.bs.affix`：定位结束之后触发。
* `affix-top.bs.affix`：定位元素应用`affix-top`效果之前触发。
* `affixed-top.bs.affix`：定位元素应用`affix-top`效果之后触发。
* `affix-bottom.bs.affix`：定位元素应用`affix-bottom`效果之前触发。
* `affixed-bottom.bs.affix`：定位元素应用`affix-bottom`效果之后触发。
