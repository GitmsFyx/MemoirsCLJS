# HttpClient

建议在应用程序生命周期中重复使用实例.

HttpClient

> BaseAddress 地址,需要一个Uri实例

HTTPContent 正文

HttpResponseMessage 响应

> IsSuccessStatusCode bool ,200-299
>
> EnsureSuccessStatusCode() 如果不成功这报错
>
> Content 响应正文

`using HttpResponseMessage response = await HttpClient.GetAsync("todos/3");`
