# 中间件

是ASP.NET Core
中的核心组件，MVC,响应缓存,身份验证,CORS,Swagger都是内置中间件

app.Use() 参数是委托

app.Run() 有一个参数的委托，参数是一个 HttpContext 对象 并且返回 Task

app.UseRewriter(new RewriteOptions().AddRedirect(\"history\",\"about\"))
将histroy 重定向到 about **重定向会发送一个新的请求**

Map,Use,Run 最后一个
