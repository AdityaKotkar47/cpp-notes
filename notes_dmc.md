1. 
| Stack | Heap       |
| -------------- | ------------ |
| finite memory      | finite memory |
| developer not in full control of memory lifetime  | developer not in full control of when memory is allocated and freed    |
| lifetime is controlled by scope mechanism | lifetime is controlled explicitly through new and delete operators |
2. using heap and stack
```cpp
{
  int local_var {};
}
// stored on stack, scope delimited by braces here

int *pvar {nullptr};
pvar = new int;
*pvar = 9;
//...
delete pvar;
pvar = nullptr;
// stored on heap, allocated by `new`, released by `delete`
// another way of initialization-
int *pa { new int {4} };
```
3. these pointers can be reused after being released
4. deleting the pointer/releasing the pointer multiple times may cause undefined behavior
5. a dangling pointer doesn't point to valid memory address, deferencing it will result in undefined behavior, types-
    - uninitialized pointer
    - deleted pointer
    - multiple pointers pointing to same memory
    ```cpp
    int *p_num1 {new int{83}};
    int *p_num2 {p_num1};
    // p_num2 was initialized by p_num1 using its value, which is address on heap indirectly, and not directly by `new`
    // so deleting p_num1 [middle person] i.e, releasing memory allocated on heap will kind of break p_num2
    
    delete p_nur1;
    // dereferencing p_num2 will cause undefined behavior
    ```
6. to avoid dangling pointers-
    - initialize your pointers [atleast to `nullptr`]
    - reset pointers after delete
    - for multiple pointers to same address, make sure the master pointer [which has `delete` rights, slave pointers do not have this right] is very clear
7. if the 'new' operator will fail in a rare case to allocate dynamic memory from the heap, and if no mechanism is in place to handle that failure, an exception will occur\
solutions-
    - exception mechanism
    ```cpp
    for (size_t i{} ; i < 100000000000 ; ++i) {
      try {
        int* lots_of_ints3 { new int[10000000]};
      } catch (std::exception& e) {
        std::cout << "Cought exception ourselves : " << e.what() << std::endl;
      }
    }
    ```
    - `std::nothrow` setting
    ```cpp
    for (size_t i{} ; i < 100000000000 ; ++i) {
      int *lots_of_ints4 { new(std :: nothrow) int[10000000] };
      if (lots_of_ints4 == nullptr) {
        std::cout << "Memory allocation failed" << std::endl;
      } else {
        std::cout << "Memory allocation succeeded" << std::endl;
      }
    }
    ```
8. while dealing with pointers, check for null pointers-
    - verbose null pointer check
    ```cpp
    int *p_number{};
    if(!(p_number == nullptr)){
      std::cout << "p_number points to a VALID address : " << p_number << std::endl;
    } else {
      std::cout << "p_number points to an INVALID address." << std::endl;
    }
    ```
    - compact null pointer check
    ```cpp
    if(p_number){
      std::cout << "p_number points to a VALID address : " << p_number << std::endl;
    } else {
    std::cout << "p_number points to an INVALID address." << std::endl;
    }
    ```
    - no need to check for null pointer before using delete, it is safe to call `delete` on null pointers
9. memory leak occurs when a program allocates memory on the heap but fails to deallocate it, often caused by losing all references to allocated memory without calling `delete`\
references are either lost by reassigning to stack or double allocating to heap or due to delimited scope [nested]\
over time, leaks can consume memory resources, leading to reduced performance or system crashes
10. - arrays can be allocated on the heap using `new`
    ```cpp
    size_t size{10}; // const not necessary

    double *p_salaries { new double[size]};
    int *p_students { new(std::nothrow) int[size]{} };
    double *p_scores { new(std::nothrow) double[size]{1,2,3,4,5}};
    ```
    - printing elements
    ```cpp
    if(p_scores){
    //Print out elements. Can use regular array access notation, or pointer arithmetic
      for( size_t i{}; i < size ; ++i){
        std::cout << "value : " << p_scores[i] << " : " << *(p_scores + i) << std::endl;
      }
    }
    ```
    - releasing memory
    ```cpp
    delete[] p_scores;
    p_scores = nullptr;

    delete[] p_students;
    p_students = nullptr;

    delete[] p_salaries;
    p_salaries = nullptr;
    ```
    - pointers initialized with dynamic arrays are different from arrays as they have decayed into a pointer [lost all info except the address to the first element], `std::size` doesn't work on them, and they don't support range-based for loops
    - example
    ```cpp
    int n;
    cin >> n;

    int* DynamicArray;
    DynamicArray = new int[n];

    for (size_t i = 0; i < n; i++) {
      std::cin >> DynamicArray[i];
    }

    for (size_t i = 0; i < n; i++) {
      std::cout << DynamicArray[i] << std::endl;
    }

    delete[] DynamicArray;
    ```