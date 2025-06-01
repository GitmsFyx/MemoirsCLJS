# 仓储 服务架构模式

竟然创建了6个项目！！！

| BCVP.Net8 主项目
| BCVP.Net8.Model 模型类
| BCVP.Net8.Commom 公共工具类
| BCVP.Net8.Service 服务类
| BCVP.Net8.IService 服务接口
| BCVP.Net8.Repository 仓储类

------------------------------------------------------------------------

BCVP.Net8

> 项目引用 `BCVP.Net8.Service`

BCVP.Net8.Model

> User类
>
> UserVo类 ，包装类 防止被依赖注入或者某些破解手段

BCVP.Net8.Commom

> NuGet包. Newtonsofot.Json Json工具包

BCVP.Net8.Service

> 项目引用 `BCVP.Net8.IService` `BCVP.Net8.Repository`
>
> UserService.cs

BCVP.Net8.IService

> 项目引用 `BCVP.Net8.Model`
>
> IService.cs接口 `Task List<UserVo> Query()`

BCVP.Net8.Repository

> 项目引用 `BCVP.Net8.Model`
>
> IUserRepository.cs接口 `Task List<User> Query()`
>
> UserRepository.cs 实现接口

在Repository中获得的是Model类，在Service中包装成了UserVo.

有了UserVo类 前后端修改不耦合，不用一改全改.
