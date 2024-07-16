1. use `0b` for binary, `0x` for hexadecimal, `0` for octal in int
2. variable braced initialization gives error instead of functional based initialization [uses parantheses] or assignment  [empty braced initialization initializes to 0]
3. `int` and `signed int` are the same things, `unsigned int` stores is different and store non-negative integers
4. integer sizes: `short int` < `int` <= `long int` <= `long long int`
5. interchangeable datatypes:
    - `int` == `signed` == `signed int`
    - `short` == `signed short` == `signed short int`
    - `unsigned shor`t == `unsigned short int`
    - `long` == `signed long` == `signed long int`
    - `unsigned long` == `unsigned long int`
    - `long long` == `signed long long` == `signed long long int`
    - `unsigned long long` == `unsigned long long int`
      - `signed` use is redundant
6. floating point sizes: `float` < `double` < `long double`
7. `double` is the default so while initializing `float` and `long double` append `f` and `L`, resp. as a suffix if you don't want the compiler to implicitly convert it from `double` to `float` or `long double`
8. floating type number when divided by 0.0 gives infinity [with +/- i.e, `inf`/`-inf`], any operation with infinity results in infinity, and 0.0/0.0 gives `nan` [NaN - not a number]
9. `char` can be initialized with the character in single quotes or its ASCII character code directly, while `std::string` is initialized with double quotes
10. precedence - which operation to do first\
associvity - which direction order\
precedence decreasing order =
    - `()`
    - `*`, `/`, `%`
    - `+`, `-`
    - `&`
    - `^`
    - `|`
    - `&&`
    - `||`
11. arithmetic operations are not possible for datatypes with size less than 4 bytes, they'll be implicitly converted to integers if arithmetic operations are attempted
12. `const` can only be assigned a value once which is at the time of initialization\
syntax- `const data_type var_name;` [keep the var_name in uppercase]
13. `size_t` is just an alias of `unsigned int` and should be preferred to keep track of stuff [counts]
14. declaration: informs the compiler about the existence and type of a variable/function\
initialization: assigns a specific value to a previously declared variable