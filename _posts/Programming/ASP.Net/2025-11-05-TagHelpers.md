---
categories: ASP.net
---

# Tag Helpers
标签助手,在开发中**推荐使用**

在`_ViewImports`中

`@addTagHelper "*, Microsoft.AspNetCore.Mvc.TagHelpers"`

好处是**变成强类型,有了智能提示,不用硬编码**,在浏览器中还是原生Html.

## 作用

`asp-for` 会自动生成  
*   `name` 方便提交表单  
*   `id`  方便聚焦  
*   `value` 如果有值则填充  
*   `data-val`  根据模型类验证规则  
*   `data-val-required`  根据模型类验证规则  
*   `type` 默认为`text`  
   
        //要么就用注解写在模型类(DTO)上,就不用特意写type
        [DataType(DataType.EmailAddress)]  
        public string? Email { get; set; }

`asp-controller`和`asp-action`其实就是填充`url`只不过可以智能提示


## 常用


`<a>`和`<form>`的标签助手
*   `asp-controller`
*   `asp-action`
*   `asp-route-x`
*   `asp-route`
*   `asp-area`

--------------------------

`input`,`textarea`,`label`

标签助手 : `asp-for`

-----------------------------

`<select>`

标签助手 : `asp-for`,`asp-items`

------------------------------

`<img>`

`asp-append-version`

--------------------------------

`<script>`

`asp-fallback-src`

`asp-fallback-test`

-------------------------------

`<sapn>`

`asp-validation-for`

---------------------------------

`div`

`asp-validation-summary`