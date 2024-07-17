1. declaration is in the header file that allows the compiler to recognize `x` in `main.cpp`\
definition in `main.cpp` provides the data type (`int`) and allocates memory for `x`\
initialization assigns the starting value (`5`) to `x`

2. one definition rule [ODR] - dictates that a variable or non-inline function can have only one definition across all the translation units (source files .cpp and header files .h) that make up your program.

    applies to:
    - non-inline functions [not declared as `inline`]
    - global variables [declared outside of any function and with external linkage]
    - static variables with external linkage
    
    exceptions:
    - inline functions
    - static variables with internal linkage [a single definition within a translation unit, but their scope is limited to that unit]
    - same classes in different translation units

3. linkage determines how variables and functions are accessible across different translation units (source files .cpp and header files .h) in your program, it allows you to control which parts of your program can access specific variables and functions\
types

    external linkage [default]
    - variables and functions declared outside of any function (global variables) or declared with the `extern` keyword have external linkage by default
    - these entities are visible and accessible throughout the entire program, as long as the header file containing their declarations is included in the translation units where they are used

    internal linkage
    - variables and functions declared with the static keyword within a function or at namespace scope have internal linkage by default
    - these entities are only visible and accessible within the translation unit where they are defined, they are not accessible from other translation units

4. a namespace is a named scope [visibility and lifetime of variables, functions, and other entities] that groups identifiers (functions, variables, etc.) to prevent naming conflicts and improve code organization

5. `inline` keyword is a suggestion, not a guarantee, the compiler decides whether inlining is beneficial based on factors like function size, complexity, and potential drawbacks

6. inline functions
    - an inline function is a suggestion to the compiler to replace the function call with the actual function body at the call site
    - this eliminates function call overhead [the extra work the computer needs to do to execute the function call itself,  separate from the actual work the function performs] for small, frequently called functions
    - syntax -
    ```cpp
    inline return_type function_name(parameter_list) {
      // Function body
    }
    ```

7. inline variables
    -  inline variables allow you to define a variable with similar behavior to an inline function
    - the compiler might strategically place a copy of the variable in each translation unit where it's used, avoiding the overhead of accessing a single copy from another file
    - syntax -
    ```cpp
    inline data_type variable_name = value;  // For constants
    inline data_type variable_name;          // For non-constants (definition required)
    ```

8. inline vs static


    | Feature | Inline | Static |
    |---|---|---|
    | Purpose | Reduce function call overhead, optimize variable access (C++17+) | Restrict function linkage, define static variables |
    | Scope | Function body duplication is possible | Limited to current translation unit |
    | Lifetime | Function/variable lifetime depends on context | Static variables persist throughout program execution |
    | Linkage | (Suggestion) Function can potentially be accessed from other units | Function has internal linkage (not accessible from other units) |
    | Usage Considerations |  Use `inline` for small, frequently called functions where reducing function call overhead is beneficial. | Use `static` for functions you only want to use within the current translation unit or for variables that need to persist throughout the program's execution within that specific file. |

9. forward declarations
    - declare the existence of a function or variable without providing its complete definition
    - only provide information about the existence of a function or variable, not its implementation
    - it essentially tells the compiler that a specific function or variable will be defined elsewhere in the program
    - allows referencing a function or variable before its full definition is available, facilitating code organization and modularity
    - syntax -
    ```cpp
    return_type function_name(parameter_list);
    // This declares the function's return type, name, and parameter list, but omits the function body

    data_type variable_name;
    // This declares the data type and name of the variable, without assigning a value

10. regular definition vs forward declaration

    - for function

    | Feature | Regular Definition | Forward Declaration |
    |---|---|---|
    | Purpose | Defines a function with complete details in one source file. | Announces a function's existence before definition in another file. |
    | Information Provided | Return type, name, parameter list, function body. | Return type, name, and parameter list only. |
    | Location | Within the source file where the function is defined. | In a header file (`*.h`) typically. |
    | Impact on Compilation | Provides a complete definition for the compiler (including the function body). | Informs the compiler about the function but requires definition elsewhere (including the function body). |

    - for variable

    | Feature | Regular Definition | Forward Declaration |
    |---|---|---|
    | Purpose | Defines a variable with complete details in one source file. | Announces a variable's existence before definition in another file. |
    | Information Provided | Data type, name, optional initial value. | Data type and name only. |
    | Location | Within the source file where the variable is used. | In a header file (`*.h`) typically. |
    | Impact on Compilation | Provides a complete definition for the compiler (including memory allocation and optional initial value). | Informs the compiler about the variable but requires definition elsewhere (including memory allocation and optional initial value). |
