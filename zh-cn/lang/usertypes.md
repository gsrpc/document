# 扩展类型

gslang的扩展类型，由用户通过编写***.gs***脚本定义:


###表类型(table)

1. table类型与c语言中的struct类似，字段的定义顺序暗示了序列化后的顺序；
2. 默认的table类型实例中，各个字段不允许为空；
3. table类型暂不支持默认值；
4. table类型不支持递归定义；
5. [annotation](./annotations.md)是一类特殊的table类型；


```golang
table User {
    string      Name;
    byte        Age;
    string      Address;
}
```

###枚举类型(enum)

与c++/c#的枚举类型有相同的含义：

> ```golang
> // attribute target flag
> @Flag
> enum Target{
    Module(1),Script(2),Table(4),Method(8),Param(16),Enum(32)
> }
> ```



###协议类型(contract)

contract类型定义rpc两端的交互协议，类似于其它语言中的interface概念：

* contract 可以包含多个方法，方法只支持单一返回值；
* contract 方法有一个可选的异常列表，异常类型由table定义并由gslang.Exception标注；



```csharp

@Exception
table ResourceException{}

@Exception
table UnknownException{}


table IPV4 {
    byte[4]     Address;
}

contract DNSResolver {
    IPV4 Resolve(string domain) throws(UnknownException,ResourceException);
}
```
