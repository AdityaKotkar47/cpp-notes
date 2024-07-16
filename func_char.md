1. functions from `<cctype>` -
    - `std::isalnum` - checks if character is alphanumeric\
    *parameter* - character\
    *return value* - non-zero value if the character is an alphanumeric character, 0 otherwise
    - `std::isalpha` - checks if the given character is an alphabetic character\
    *parameter* - character\
    *return value* - non-zero value if the character is an alphabetic character, 0 otherwise
    - `std::isblank` - checks if character is a blank character\
    *parameter* - character\
    *return value* - non-zero value if the character is a blank character, 0 otherwise
    - `std::islower` - checks if character is a lowercase character\
    *parameter* - character\
    *return value* - non-zero value if the character is a lowercase character, 0 otherwise
    - `std::isupper` - checks if character is a uppercase character\
    *parameter* - character\
    *return value* - non-zero value if the character is an uppercase character, 0 otherwise
    - `std::isdigit` - checks if character is a digit\
    *parameter* - character\
    *return value* - non-zero value if the character is a numeric character, 0 otherwise
    - `std::tolower` - converts a character to lowercase\
    *parameter* - character\
    *return value* - lowercase version of character or unmodified character if no lowercase version
    - `std::toupper` - converts a character to uppercase\
    *parameter* - character\
    *return value* - uppercase version of character or unmodified character if no uppercase version

2. functions from `<cstring>` -
    - `std::strlen` - returns the length of a given string\
    *parameter* - string\
    *return value* - the length of the null-terminated string without null character\
    whereas `sizeof` will give the size of the character array or string with null character\
    for character ptrs, `strlen` will give the string size, and `sizeof` will give size of ptr
    - `std::strcmp` - compares two null-terminated strings lexicographically\
    *parameter* - `lhs`, `rhs` - pointers to null-terminated strings\
    *return value* - negative value if `lhs` appears before `rhs` in lexicographical order,\
    zero if `lhs` and `rhs` compare equal,\
    positive value if `lhs` appears after rhs in lexicographical order
    - `std::strchr` - finds the first occurrence of a character\
    *parameter* - `str` - pointer to null-terminated string, `ch` - character to search for\
    *return value* - pointer to the found character in `str`, or a null pointer if no such character is found
    - `std::strrchr` - finds the last occurrence of a character\
    *parameter* - `str` - pointer to null-terminated string, `ch` - character to search for\
    *return value* - pointer to the found character in `str`, or a null pointer if no such character is found
    - `std::strcat` - concatenates two strings\
    *parameter* - `dest` - pointer to the null-terminated string to append to, `src` - pointer to the null-terminated string to copy from\
    *return value* - `dest`
    - `std::strcat` - copies one string to another\
    *parameter* - `dest` - 	pointer to the character array to write to, `src` - pointer to the null-terminated string to copy from\
    *return value* - `dest`
