1. the datatype of the ptr should be the same as the datatype of the variable whose address it is pointing to
2. null pointer [pointing to nothing during initialization, any access to it is undefined behaviour] can be initialized as -
```cpp
int * p_var1 {};
// or
int * p_var2 {nullptr};
```
3. all pointers regardless of their datatypes are of same size as they store addresses to variables
4. position of the `*` doesn't matter
```cpp
int* p_number2{nullptr};
int * p_number3{nullptr};
int *p_number4{nullptr}; // preferred
```
5. general syntax- `datatype *pvar;`
```cpp
int var {42};
int *pvar {&var};
// this ptr can be later assigned to another variable of same type
int a = 3;
pvar = &a;
```
6. `&` is the reference operator and can be read as “address of”.\
`*` is the dereference operator [or indirection operator] and can be read as “value pointed by”.
7. string literals [c-strings] can be directly initialized with char pointers, but these ptrs need to be constant as the string literal is going to be turned into an array of const chars and the first element of that array will be pointed by this const char pointer
```cpp
const char *pvar {"hehe lol"};

std::cout << pvar; // prints hehe lol
std::cout << *pvar; // prints h
// *pvar = 'k'; its const so erroneous

// to be able to modify it, use char array
char message1 [] {"Hello World!"};
message1[0] = 'B';
```
8. constant pointer and pointer to const
* declared with `const` before the pointer type.
* cannot be reassigned a new memory address after initialization.
* can modify the value at the pointed-to location.
9. pointer to const:
* points to a constant value.
* cannot modify the value at the pointed-to location through the pointer.
* can be reassigned to a different constant memory location.
10. array of const pointers to const chars
```cpp
const char* messages[] = {
  "Hello, world!",
  "This is a constant string.",
  "These characters cannot be modified."
};
```
11. - the name of an array itself behaves like a constant pointer that points to the first element's memory address for an array like `int numbers[5];`, `numbers` and `&numbers[0]` can be used interchangeably as the name `numbers` itself doesn't store the actual data, instead it holds the memory address of the first element (`numbers[0]`)
    - array name behaves like a constant pointer to the first element
    - both array notation (`numbers[i]`) and pointer dereference (`*(numbers + i)`) can be used to access elements within bounds
    - the array name itself cannot be reassigned to a different memory location unlike a regular pointer
    - array pointer `int *ptr = numbers`
12. by adding or subtracting integers to a pointer, you can "move" [it shifts by the size of the datatype it is pointing to] it to point to different elements within the array. this is because arrays store elements contiguously in memory, with a fixed size difference between each element.
```cpp
int numbers[5] = {10, 20, 30, 40, 50};
int* ptr = numbers;

std::cout << *(ptr) << std::endl; // Prints 10 (dereference ptr)
std::cout << *(ptr + 1) << std::endl; // Prints 20 (ptr + 1 points to numbers[1])
std::cout << *(ptr + 2) << std::endl; // Prints 30 (ptr + 2 points to numbers[2])

std::cout << *(ptr - 1) << std::endl; // Assuming ptr is not the first element, this would print an error (out of bounds)
```
13. when an array is passed to a function:
    - they are passed by reference
    - this allows the function to modify the original array content
    - the array decays into a constant pointer that points to the first element's memory address
    - pass the size explicitly