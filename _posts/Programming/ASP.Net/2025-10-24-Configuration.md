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

## 环境特定配置

下覆盖上

1.  appsetting.json 
2.  appsettings.EnvironmentName.json  
3.  User Secrets(Secret Manager)  
4.  Environment Variables  
5.  Command Line Arguments 

## 密钥管理器

不会被储存到**源代码**中.在本机机器项目外创建了一个文件,并在csproj中仅存下了该文件ID.

**初始化**

1.  打开终端(用IDE终端更方便)
2.  进入项目根目录
3.  `dotnet user-secrets init` 初始化,会自动生成一个十六进制代码作为userSecret的ID，并以此名存为一个JSON存在app data中.

**查看** 

1.  Rider : 右键项目 -> 工具 -> .NET用户密钥
2.  会自动打开`secrets.Json`
3.  你也可以使用命令`dotnet user-secrets list`查看 (一般不使用)

**储存**

*   你不应该直接编辑JSON文件,而是应该使用命令
*   ` dotnet user-secrets set "weatherapi:ClientID" "ClientID from Secrets"` 设置键值对
  
按照顺序它会覆盖掉appsetting文件的值.

**它仅在开发环境下起效**