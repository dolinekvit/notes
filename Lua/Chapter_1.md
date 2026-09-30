### Global variables
- Do not need declaration, variables that are not declared will print `nil`.
```lua
print(b) --> nil
b = 10
print(b) --> 10
```
- Global variables do not need to be deleted
- - If you need to delete it, just assign `nil` to the variable
- *A global variable is existent if and only if it has a non-nil value*
