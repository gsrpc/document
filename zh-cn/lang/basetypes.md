# 基本类型

###整型

gslang仅支持定长整型：

>   8bit  : byte, sbyte, bool

>   16bit : uint16, int16

>   32bit : uint32, int32

>   64bit : uint64, int64


###浮点数

> 32bit : float32

> 64bit : float64

###复杂内建类型

gslang支持多种内建的复杂类型（non-scalar）：

* Array  : gslang支持任意类型作为基类型的定长数组类型，例如:byte[4],string[5],user[12]
* List   : gslang支持任意类型作为基类型的列表类型，例如:byte[],string[],user[]
* string : string作为定长数组类型的特例，仅支持UTF-8编码
