# 属性/注释

通过属性/注释我们可以在不修改语法的情况下，引入新的功能；不同于C#/java,属性/注释只在目标代码生成阶段有效；


###自定义属性/属性

1. 创建一个table，定义必要字段；
2. 使用预定义属性gslang.annotations.Usage标注属性使用目标；

> ***需要注意的是gslang.annotations.Usage本身会被自己所注释：***

> ```golang
> @Usage(Target.Table)
> table Usage{
>    Target Target;
>}
> ```

###属性/注释适用范围

由枚举gslang.annotations.Target 定义:

> ```golang
> @Flag
> enum Target{
>    Module(1),Script(2),Table(4),Method(8),Param(16),Enum(32)
> }
> ```

###属性/注释的执行过程

1. 编译器编译gslang源码，生成内存AST；
2. 编译器调用目标语言生成器接口生成代码，生成器此时可以获取处理节点的属性/注释列表完成相应的生成器语义动作；
3. 一些预定义属性，会在代码生成阶段前被编译框架查询/执行相应处理；

###预定义属性/注释

> *** gslang.annotations.Usage *** : 注释属性/注释的使用范围

> *** gslang.Flag *** : 标注枚举类型大小为一个byte

> *** gslang.Exception *** : 标注对应的table类型为一个异常类型

> *** gslang.Package *** : 重命名目标语言包/namespace名称
