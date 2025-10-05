---
categories: ASP.net
---

# 状态码

```C#
//Response.StatusCode = 400;

//使用返回方法设置状态码,无响应体
return StatusCode(401);
```

## NotFoundResult

不需要返回独立的两条语句

```C#
Response.StatusCode = 400;
return Content("Something went wrong");
```

直接使用

```C#
//return new NotFoundResult();

//有参数返回值为NotFoundObjectResult,无参数为NotFoundResult,没影响
return NotFound();
```
## BadRequestResult

```C#
//return new BadRequestResult();
return BadRequest();
```
## UnauthorizedResult

```C#
//return new UnauthorizedResult();
return Unauthorized();
```