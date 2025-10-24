---
categories: ASP.net
---

# Configuration

可以写在以下几种

*   appsettings.json
*   Environment Variables
*   File Configuration
*   In-Memory Configuration
*   Secret Manager

IConfiguration

`app.Configuration["MyKey"]` 获取值,不区分大小写

`app.Configuration.GetValue<string>("Mykey", "DefaultValue")` 泛型获取,还能提供默认值

## 分层配置

```JSON
"weatherapi": {
"ClientID": "CLientID123",
"ClientSecret": "abcd"
}
```

*   使用冒号读取子键

    `app.Configuration["weatherapi:ClientID"]` 

*   或者使用`GetSection()`

    `ViewBag.MyKey=_configuration.GetSection("weatherapi")["ClientID"];`

*   **选项模式 (方便读取多个值)**
   
    创建一个选项类

    ```C#
    public class WeatherApiOptions
    {
        //属性名字得对应配置
        public string? ClientID { get; set; }
        public string? ClientSecret { get; set; }
    }
    ```

    `Get`方法
    ```C#
    //Get<>会将得到的配置同名装进选项类里面
    var weatherApiOptions = _configuration.GetSection("weatherapi").Get<WeatherApiOptions>();
    
    ViewBag.Mykey= weatherApiOptions?.ClientID;
    ViewBag.MyAPIKey= weatherApiOptions?.ClientSecret;
    ```

    `Bind` 方法
    ```C#
    var apiOptions = new WeatherApiOptions();
    _configuration.GetSection("weatherapi").Bind(apiOptions);

    ViewBag.Mykey= weatherApiOptions?.ClientID;
    ViewBag.MyAPIKey= weatherApiOptions?.ClientSecret;
    ```

    区别就是`Bind`需要先`new`一个实例.

## 依赖注入配置 推荐

```C#
//Program.cs

//泛型表示类型,参数表示从哪个配置得到(这里是配置里面的weatherapi)
builder.Services.Configure<WeatherApiOptions>(builder.Configuration.GetSection("weatherapi"));
```
```C#
public class HomeController : Controller
{
    private readonly WeatherApiOptions _options;
    
    //IOptions,被注册的选项
    public HomeController(IOptions<WeatherApiOptions> weatherApiOptions)
    {
        //Value为真正的类,WeatherApiOptions
        _options = weatherApiOptions.Value;
    }
}
```
好处能使Action方法更简洁.