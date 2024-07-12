## 1. `getline()`

- **Syntax**: `getline(istream& is, string& str, char delim);`
- **Use**:
  - `getline()` reads a string or a line from an input stream.
  - It extracts characters from the input stream until the specified delimiter is encountered.
  - The previously stored value in the string object is replaced by the input string.
- **Default Behavior**:
  - Reads characters from the input stream until the newline character (`'\n'`) is encountered.
- **Special Note**:
  - Use `getline()` to read entire lines of input, especially when dealing with user input that may contain spaces or special characters.

## 2. `cin.peek()`

- **Syntax**: `cin.peek()`
- **Use**:
  - `cin.peek()` retrieves the next character from the input stream without actually consuming it.
  - It allows you to "preview" the next character in the input without removing it.
  - The next call to any consuming operation (such as `>>` or `cin.read`) will read and consume that character.
- **Default Behavior**:
  - It returns the next character in the input sequence without extracting it.
- **Special Note**:
  - Use `cin.peek()` when you want to check the next character without removing it from the stream.

## 3. `cin.get()`

- **Syntax**: `cin.get(string_name, size);`
- **Use**:
  - `cin.get()` reads input into a character array (string) and includes whitespace characters.
  - Unlike `cin >>`, which stops at whitespace, `cin.get()` reads a whole line (including spaces, tabs, and newlines).
- **Default Behavior**:
  - Reads characters from the input stream until the specified size or until the newline character (`'\n'`) is encountered.
- **Special Note**:
  - Use `cin.get()` when you need to read an entire line (including spaces) into a character array.

## 4. `cin.ignore()`

- **Syntax**: `cin.ignore(n, delimiter);`
- **Use**:
  - `cin.ignore()` discards characters from the input stream.
  - It ignores the specified number of characters (up to the delimiter) or until the delimiter is reached.
  - Commonly used to discard the newline character left by `cin >>`.
- **Default Behavior**:
  - Without arguments, it discards one character from the input buffer.
- **Special Note**:
  - Use `cin.ignore()` before using `getline()` to clear any remaining characters (like newline) from the input buffer.
    It ensures that `getline()` reads the desired input correctly.
