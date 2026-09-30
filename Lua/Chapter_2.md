### Types
- `nil`
- `Boolean` - *lua considers both zero and empty strings as true in conditionals*
- `numbers` - Integers and floating-point numbers are still number type for lua
- `string` - Strings in lua are *immutable*, usage of single and double quotes is allowed and won't change the outcome
- - We can delimit string literals with `[[ ]]`
```lua
page = [[
<HTML>
<HEAD>
<TITLE>Page</TITLE>
</HEAD>
</HTML>
]]
```
- - Any numeric operation applied to a string converts the said string to number
- - Conversely, when a Lua expects a string and gets number, the said number is converted to string `print(10 .. 20) --> 1020`
- `Table` - Implements associative arrays, has no fixed size. Table is created using a _constructor expression_ `{}`
- `Functions` - Functions are first-class values in lua.

