# FluentAPI

CodeFirst 代码优先，创建数据库

DataAnnotation

> 直接 `[Required]` 标注

FluentAPI

> 创建一个类继承 `IEntityTypeConfiguration<Person>`
>
>     clasee PersonConfig: IEntityTypeConfiguration<Person> 
>     {
>         public void Configure(EntityTypeConfiguration<Person> builder)
>         {
>             //具体还没看，在用DataAnnotations
>         }
>     }
