1. `std::string` is safer and more convenient than C-strings due to automatic memory management [you can change the text as much as you like without worrying about memory space],\
bounds checking [it prevents you from accidentally accessing parts of the text that don't exist, avoiding crashes],\
and rich functionality [offers built-in tools for common text operations, making text manipulation easy and efficient]

2. declaration and initialisation -
    ```cpp
    std::string name; // Declares an empty string

    std::string greeting = "Hello"; // Initializes with a string literal, braces can be used too, parantheses can be used too

    const char* c_str = "World";
    std::string message(c_str); // Initializes from an existing C-string or std::string, braces can be used too

    std::string initial(10, 'C'); // Initialize with multiple copies of a char, braces can be used too

    std::string message {"Hello there", 5}; // Initialize with part of a string literal, parantheses can be used too

    std::string greeting{"Hello World"};
    std::string saying_hello{greeting, 6, 5}; // Initialize with part of an existing string, starting at index 6, taking 5 characters, parantheses can be used too
    ```
