### Statements
- Assignments, such as `x = 4`
- Local variables and blocks
```lua
j = 10 --> global variable
local i = 5 --> local variable

while true do
    local x = 2 --> local variable for while block
end
```
- We can delimit block with `do-end`
```lua
do
    local a = 2
    local b = a + 1
end
```
- *Control structures* are provided by Lua too.
- - `if` for conditional, `while` `repeat` `for` for iteration.
- - - `end` terminates `if`, `until` terminates `repeat`
```lua
-- If control structure
if x > 20 then b = 30 end

if x > 20 then
    b = 30
end

if x > 20 then
    b = 30
elseif x > 30 then
    b = 40
else
    b = 10
end
```

```lua
-- while loop
local i = 1
while a[i] do
    print(a[i])
    i = i + 1
end
```

```lua
-- repeat
repeat
    line = io.read()
until line ~= ""
print(line)
```

```lua
-- numeric for
for var=exp1,exp2,exp3 do
    something
end
```

```lua
-- general for
for i,v in apairs(a) do print(v) end
```

- We can use `break` and `return` to jump out of inner block.

