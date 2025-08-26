---
categories: Avalonia
---

# 数据控件

数据列表

listbox

itemControl

## Property

`ItemsSource` 数据来源 需要Binding

`ListBoxItem` 里面单独的item控件 是个透明的框(可以和鼠标交互,修改背景颜色没用) 


## 用法

``` xaml
<Control>
    <!--这里应该是new了一个ItemTemplate覆盖了原来的模板-->
    <Control.ItemTemplate>
        <!--数据模板 这里面Bindind的已经是集合里面的单个元素,类似foreach-->
        <DateTemplate>
        </DateTemplate>
    </Control.ItemTemplate>
</Control>
```
    


