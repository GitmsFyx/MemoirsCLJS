---
categories: ASP.net
---

# 状态码

不需要返回独立的两条语句
```C#
Response.StatusCode = 400;
return Content("Something went wrong");
```

## NotFoundResult

```C#
return new NotFoundResult();
return NotFound();
```
## BadRequestResult

```C#
return new BadRequestResult();
return BadRequest();
```
## UnauthorizedResult

```C#
return new UnauthorizedResult();
return Unauthorized();
```