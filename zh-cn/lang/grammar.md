# EBNF


script = ***package*** package_decl (using)* ( table_decl | enum_decl | contract_decl )*

using = ***using*** ident(. ident)* ';'

package_decl = ident(. ident)*

table_decl = (attr_decl)* ***table*** ident '{' field_decl+  '}'

field_decl = (attr_decl)* type ident ';'

type = ***bool*** | ***byte*** | ***sbyte*** | ***int16*** | ***uint16*** |
       ***int32*** | ***uint32*** | ***int64*** | ***uint64*** | ***float32*** |
       ***flot64*** | ***string*** | type[] | type[integer_constant] | ref

ref = typeref | enum_constant_ref

typeref = ident

enum_constant_ref = ident.ident

enum_decl = (attr_decl)* ***enum*** ident '{' enum_constant (',' enum_constant)* '}'

enum_constant = ident ('(' integer_constant ')')

contract_decl = (attr_decl)* ***contract*** ident '{' (method_decl ';')+ '}'

method_decl = (attr_decl)* type ident '(' type ident? (',' type ident?)* ')' (throws '(' ref (',' ref)*  ')') ';'

attr_decl = '@' table_init

table_init = typeref ('(' enum_constant_ref | constant | table_init ')' | '(' ident ':' (enum_constant_ref | constant | table_init ) ')')?

constant = integer_constant | float_constant | string_constant

string_constant = " [ ^ " ]* "

integer_constant = -?[0-9]+

float_constant = -?[0-9]+.[0-9]+((e|E)(+|-)?[0-9]+)?
