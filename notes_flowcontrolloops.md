1. in switch-
    - expressions can only contain integer and char constants
    - break must be added after each case, except for default label or else after a case is matched, subsequent cases will also be executed
    - duplicate case labels are not allowed
2. options in ternary operator should be of same datatype or at least convertible 
3. curly braces are not necessary when only one statement is in `if`/`else if`/`else`/`for` code block
4. iterator declared inside for is scoped within it
5. iterator can be declared outside the loop then can be completely skipped or just its name can be included
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
8. similar to python's range-based loop
```python
for element in collection_name:
    # Loop body
```
cpp has-
```cpp
for (data_type variable : collection_name) {
    // Loop body
}
```
- `data_type`: The data type of the elements in the collection (e.g., `int`, `double`, `std::string`)
- `variable`: A temporary variable that takes on the value of each element in the collection during each iteration
- `collection_name`: The name of the array, vector, or other collection [strings] you want to iterate through
- similar to python `variable`/`element` holds the current value at particular index but in cpp it is a copy, not a reference so can't modify the original elements directly
9. in nested loops, variables declared by outer loop is only accessible to it and inner loop only
10. use `break` to exit a loop prematurely and use `continue` to skip specific iterations
11. in nested loops, `break` and `continue` affect the current loop where it's placed