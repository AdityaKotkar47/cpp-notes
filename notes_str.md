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
3. concatenating `std::strings` -
    - `+` operator\
    *syntax* - `std::string result = string1 + string2;`\
    *effect* - creates a new `std::string` object named `result` by appending the characters from `string2` to the end of `string1`
    - `append` method\
    *syntax* - `string1.append(string2);` (or `string1.append(char_array, length);`)\
    *effect* - appends the characters from `string2` (or the specified `char_array` with a given `length`) to the end of the current `string1` object, modifies the original `string1` in-place
    - `+=` operator\
    *syntax* - `string1 += string2;`\
    *effect* - similar to `append`, this is a shorthand for `string1.append(string2)`, it provides a concise way to perform in-place concatenation

4. accessing characters in `std::string` -
    - `[]` operator\
    *syntax* - `char character = string[index];`\
    *effect* - this operator allows you to access the character at the specified `index` within the string, behavior is undefined if you access an index that is out of bounds
    - `at` method\
    *syntax* - `char character = string_object.at(index);`\
    *effect* - similar to `[]`, it retrieves the character at the specified `index`, however unlike `[]`, the `at` method throws a `std::out_of_range` exception if the `index` is out of bounds

5. size of `std::string` - the number of characters currently stored in the `std::string` object, excluding the null terminator
    - `size_t string_object.length();` (both return the same value)
    - `size_t string_object.size();` (equivalent to `size_t size(string_object);`)

6. modifying `std::string` -
    - concatenating `std::string` methods can be used
    - `insert` method\
    *syntax* - `string_object.insert(position, string_to_insert);`\
    *effect* - inserts the characters from `string_to_insert` at a specific position within `string_object`, the original content is shifted to accommodate the insertion
    - `erase` method\
    *syntax* - `string_object.erase(position, length);`\
    *effect* - removes a specified number of characters (`length`) starting from the given `position` within `string_object`
    - `replace` method\
    *syntax* - there are multiple variations of `replace`\
    `string_object.replace(position, length, new_string);` : replaces `length` characters starting at `position` with `new_string`\
    `string_object.replace(start_it, end_it, new_string);` : replaces the range of characters from iterator `start_it` to `end_it` (exclusive) with `new_string`\
    `string_object.replace(old_substring, new_substring);` : replaces all occurrences of `old_substring` within `string_object` with `new_substring`\
    *effect* - replaces a specific substring within a `std::string` with another string
    - `substr` method\
    *syntax* - `substring = string_object.substr(start, length);`\
    *effect* - returns a substring from a `std::string` object based on a starting position and optionally a length
    - `resize` method\
    *syntax* - `string_object.resize(new_size);`\
    *effect* - adjusts the size of a `std::string` object by adding or removing characters, if `new_size` is greater than the current size, the string is padded with null characters (`\0`) at the end whereas if `new_size` is less than the current size, the string is truncated to the new `size`.\
    - `assign` method\
    *syntax* - there are multiple variations of `assign`\
    `string_object.assign(new_string);` : assigns the entire content of `new_string` to `string_object`\
    `string_object.assign(start_it, end_it);` : assigns the characters from iterator `start_it` to `end_it` (exclusive) of another string object to `string_object`\
    *effect* - similar to the assignment operator (`=`), this method allows you to replace the entire content of a `std::string` object with a new string or a portion of another string

7. comparing `std::string` [lexicographically] using relational operators -
    - `==` : Returns true if the strings are equal.
    - `!=` : Returns true if the strings are not equal.
    - `<` : Returns true if the first string is lexicographically less than the second.
    - `>` : Returns true if the first string is lexicographically greater than the second.
    - `<=` : Returns true if the first string is lexicographically less than or equal to the second.
    - `>=` : Returns true if the first string is lexicographically greater than or equal to the second.

8. searching within `std::strings` -
    - `find` method\
    *syntax* - `position = string_object.find(substring);`\
    *effect* - searches for the first occurrence of a specified `substring` within a `std::string` object, if the `substring` is found, it returns the index (position) of the first character of the occurrence within `string_object` whereas if the `substring` is not found, it returns `std::string::npos`
    - `rfind` method\
    *syntax* - `position = string_object.rfind(substring);`\
    *effect* - similar to `find`, but it searches for the last occurrence of the `substring` within the string, if the `substring` is found, it returns the index of the first character of the last occurrence whereas if the `substring` is not found, it returns `std::string::npos`
    - `find_first_of` method\
    *syntax* - `position = string_object.find_first_of(char_set);`\
    *effect* - searches for the first occurrence of any character in `char_set` within `string_object`, similar to `find` and `rfind`, it returns the index of the first occurrence of a matching character, or `std::string::npos` if no match is found
    - `last_first_of` method\
    *syntax* - `position = string_object.last_first_of(char_set);`\
    *effect* - searches for the last occurrence of any character in `char_set` within `string_object`, similar to `find` and `rfind`, it returns the index of the last occurrence of a matching character, or `std::string::npos` if no match is found

9. raw string literals -
    - raw string literals provide a way to define string literals in C++ while preserving all characters within the quotes, including escape sequences like `\n` (newline) or `\"` (double quote)
    - syntax -\
        1. `R"(string_content)"` : this syntax uses a capital `R` followed by an opening parenthesis `("`, the actual string content, and a closing parenthesis `")`
        2. `R"delimiter(string_content)delimiter"` : this syntax offers more flexibility. You can choose any delimiter character (except backslash `\`, whitespace, or parentheses) to enclose the string content, the same delimiter character appears at the beginning and end of the literal
    - raw string literals cannot be used for character literals (single quotes)
    - nested raw string literals are not allowed (you cannot have a raw string literal within another raw string literal)