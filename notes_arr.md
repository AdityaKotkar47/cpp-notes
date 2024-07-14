1. arrays store data of the same type, this is not python
2. indexes can be omitted when initializing arrays using initializer lists or individual initialization\
so in initializer lists `{}` you can't skip starting or middle indexes but can skip indexes at the end\
in individual initialization using `array [index] = value`, any index can be skipped
3. declare means just creating variable, initialize means giving actual values
4. it is not necessary to mention the size of the array while using initializer lists
5. elements get initialized to zero when omitted using initializer lists
6. for size of an array [i.e, no. of elements] -
```cpp
// random array be arr
// method 1:
size_t arrsize1 {std::size(arr)};
// method 2:
size_t arrsize2 {sizeof(arr)/sizeof(arr[0])};
```
7. char arrays should either have a null terminator `'\0'` or a space for one to avoid undefined behaviour
```cpp
char arr1 [] = {'h', 'i', '\0'}
// or 
char arr2 [3] = {'h', 'i'}
// this is a initializer list left empty so end will be initialized with 0 version of character i.e, '\0'
``` 
after adding `'\0'` its called 'c string' or 'null terminated string'\
`std::string` objects do not require this `'\0'` null terminator

8. char arrays can also be initialized and printed like this -
```cpp
// here '\0' is appended implicitly
char ar1 [] {"aye senor"};
char ar2 [] ("aye senor");
char ar3 [] = "aye senor";
char ar4 [] = {"aye senor"};
char ar5 [] = ("aye senor");
cout << ar1 << ar2 << ar3 << ar4 << ar5;
```
9. null character `'\0'` marks the end of the string, instead you can use range-based or normal loops to print their content
10. going out of bounds of the defined index range may cause undefined behaviours