### Expressions
- Expressions denote values.
- Supports *arithmetic operations* with partial support of exponentiation.
- Provides *relational operators*: > < = <= >= == (equality) ~= (negation of equality)
- *Lua compares by reference*
```lua
    a = {}; a.x = 1; a.y = 0
    b = {}; b.x = 1; b.y = 0
    c = a

    -- a == c, but a ~= b (b is reference to other table even if the data is the same)
```

- *Logical operators* `and`, `or`, `not`
- - `and` returns first argument if it's false, otherwise second
- - `or` returns first argument if it's true, otherwise second
- - `not` always returns `true` or `false`
- *Concatenation* operator is `..` and if any of the operands are number, Lua converts it to string
```lua
print(20 .. "40") --> 2040
```
- *Operator precedence* in Lua follows the table
```lua 
    ^
     not  - (unary)
     *   /
     +   -
     ..
     <   >   <=  >=  ~=  ==
     and
     or
```
- - All binary operation are _left associative_, except for `^` and `..`, which are _right associative_.

### Table constructors
- Constructors are expressions that create and initialize table.
- The simplest is empty constructor `{}`, which creates an empty table.
- Constructors also initialize arrays, eg.
`days = {"Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"}`
- - will initialize days with `days[1]` being `Monday`. *Indexes start with 1, not 0*.
- To initialize table used as record, Lua uses syntax `a = {x=0, y=0}`
