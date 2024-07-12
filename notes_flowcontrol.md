1. in switch-
    - expressions can only contain integer and char constants
    - break must be added after each case, except for default label or else after a case is matched, subsequent cases will also be executed
    - duplicate case labels are not allowed
2. options in ternary operator should be of same datatype or at least convertible 
3. curly braces are not necessary when only one statement is in `if`/`else if`/`else`/`for` code block
4. iterator declared inside for is scoped within it
5. iterator can be declared outside the loop then can be completely skipped or just its name can be included\
```cpp
size_t i {};
for (i; i < count; i++) {

}
//or
size_t i {};
for (; i < count; i++) {

}
```
6. afaik so basically these loops `()` have statements as expressions in them and they just run in a pre-defined manner when some statements are set to true
7. multiple comma separated declarations are possible inside for loop parantheses\
`for (int i=0, j=2; i < count; i++)`\
and this is called `,` comma operator