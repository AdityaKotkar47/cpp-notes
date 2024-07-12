| Manipulator(s) | Header       | Purpose                                      |
| -------------- | ------------ | -------------------------------------------- |
| `std::endl`      | `<iostream>` | Insert the newline character |
| `std::flush`     | `<iostream>` | Flush the output stream                       |
| `std::setw()`    | `<iomanip>`  | Set width of the next input/output field     |
| `std::setfill()` | `<iomanip>`  | Fill characters for `setw()`                   |
| `std::left`, `std::right`, `std::internal` | `<ios>` | Value justification                  |
| `std::boolalpha`, `std::noboolalpha` | `<ios>` | Bool output format                  |
| `std::showpos`, `std::noshowpos` | `<ios>` | Show `+` sign for positive numbers          |
| `std::dec`, `std::hex`, `std::oct` | `<ios>` | Controls default number system for integers |
| `std::showbase`, `std::noshowbase` | `<ios>` | Include prefix to showbase                  |
| `std::uppercase`, `std::nouppercase` | `<ios>` | Show digits in uppercase                  |
| `std::fixed`, `std::scientific` | `<ios>` | Control floating point output format           |
| `std::setprecision()` | `<iomanip>` | Set number of digits for floating point types |
| `std::showpoint`, `std::noshowpoint` | `<ios>` | Control whether trailing zeros are shown |


- Syntax- `std::cout << std::manipulator`

- automatic floating point output format syntax-\
`std::cout.unsetf(std::ios::scientific | std::ios::fixed);`