# 扩展类型


###enum类型

默认采用四个字节存储，如果被glang.Flag标注则才用1个字节存储

###Table类型

表字段默认采用Type-Value形式存储，表头存储表字段数量；Type 占用1个字节表示字段类型：

> I8(0),I16(1),I32(2),I64(3),List(4),Table(5),String(6),Skip(7)

Skip标识该字段为可选或者丢弃

Value 存储具体类型数据
