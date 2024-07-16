1. references cannot be declared without being immediately initialized unlike pointers\
references are an alias to the original variable so has everything same to the original variable except its name\
declaration syntax-
    ```cpp
    int num {1};
    int& ref_to_num = num;
    // or
    int& ref_to_num {num};
    ```
2. about references-
    - references must be initialized
    - references cannot be reassigned
    - references behave like `const pointers`
    - references can modify the value through the reference, and changes made through the reference are reflected in the original variable
    - if a reference is declared with const, it can only refer to a constant object (e.g., `const int& ref_name = constant_variable;`)
3. references vs pointers
    | Property | Pointers | References |
    |---|---|---|
    | Memory Location | Stores memory addresses | Share memory location with the original variable |
    | Reassignment | Can be reassigned to point to different variables | Cannot be reassigned after initialization |
    | Nullability | Can be null (point to nowhere) | Cannot be null (always refer to an existing variable) |
    | Dereferencing | Required to access the value at the pointed-to memory location (using *) | Not required, directly access the value through the reference |
    | Use Cases | - Dynamic memory allocation | - Function arguments (to avoid copying) |
    |             | - Pointers to structures and arrays | - Aliasing existing variables |
4. const stuff-
    ```cpp
    int age = 30;
    // const reference [const applies to reference variable, not to original variable]
    const int& const_ref_age {age};
    // duplicate const reference behavior with pointer
    const int* const const_ptr_to_const_age {&age};
    // the first const ensures the pointed-to data is constant (read-only)
    // the second const ensures the pointer itself is constant (cannot be reassigned)
    // const int& const ref_name = constant_variable; // no such thing
    ```
5. references in range-based for loops
    ```cpp
    for (data_type& reference_name : container_or_range) {
    // Code to be executed for each element
    }
    ```
    - use `const data_type& reference_name` to iterate through a range without modifying elements, ideal for read-only access
    - the reference variable is only valid within the loop iteration
    - references avoid unnecessary copies of elements within the loop, they directly refer to the original elements, improves performance for larger arrays
