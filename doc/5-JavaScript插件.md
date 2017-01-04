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
使用option对象
