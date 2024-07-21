1. instance methods are functions defined within a class that operate on specific instances (objects) of that class, they provide a way for objects to interact with their own data (attributes) and potentially modify it\
to call an instance method you have to access one of the instances of the class to use it `object.method_name(arguments)`\
the first argument of an instance method is always `self`, a special parameter that automatically refers to the current object instance [to access and modify the object's attributes]

2. static methods are a special type of method defined within a class that don't operate directly on an object's state (attributes), they behave more like regular functions but are associated with the class itself\
to call a static method you only have to access the class to use it `MyClass.static_method_name(arguments)` or call it on an instance like `object.static_method_name(arguments)` which is functionally equivalent to calling it on the class\
they don't take `self` as the first argument when called, declared using the `@staticmethod` decorator\
    ```py
    class MyClass:
      @staticmethod
      def static_method_name(arguments):
        # Method body
    ```
    these are utility functions that are conceptually related to the class [do not need access to class data] but don't require modifying object data

3. class methods are a special type of method defined within a class that operate with some awareness of the class itself (unlike static methods) but don't directly operate on the data (attributes) of a specific object instance (unlike instance methods)\
to call a class method you only have to access the class to use it `MyClass.class_method_name(arguments)`\
the first argument of a class method is `cls`, which refers to the class itself, this allows class methods to access and modify class-level attributes or create new instances of the class\
they take `cls` as the first argument when called, declared using the `@classmethod` decorator
    ```py
    class MyClass:
      @classmethod
      def class_method_name(cls, arguments):
          # Method body
    ```
    these are used for accessing class-level data or require access to the class itself


4. magic methods [also sometimes called dunder methods] are special methods in Python that have a predefined meaning for the interpreter
    - they are automatically invoked when certain operations are performed on objects, allowing you to customize how those operations behave
    - they provide a powerful way to control how objects behave in various scenarios, you can use them to:
      1. overload operators (e.g., `__add__` for addition, `__mul__` for multiplication)
      2. control object creation (`__init__`, `__new__`)
      3. define string representation for printing (`__str__`)
      4. implement comparisons (`__eq__`, `__lt__`), etc.
    - the behavior of the `self` argument in magic methods varies, some methods (like `__init__`) require `self` to refer to the current object, while others might not (like `@staticmethod` magic methods)
    - examples
      1. `__init__(self)`: the constructor method, automatically called when you create a new object of the class
      2. `__str__(self)`: defines how an object is converted into a string for printing
      3. `__add__(self, other)`:defines the behavior of the `+` operator for the object
      4. `__eq__(self, other)`: defines how objects are compared for equality using the `==` operator


5. key differences

    | feature          | magic methods                 | instance methods                 | static methods                 | class methods                 |
    |-------------------|--------------------------------|---------------------------------|---------------------------------|---------------------------------|
    | naming convention | double underscores (`__name__`) | regular method names           | `@staticmethod` decorator       | `@classmethod` decorator      |
    | invocation       | automatic                     | explicitly called (`object.method()`) | explicitly called (`class.method()`) | explicitly called (`class.method()`) |
    | `self` argument   | varies (might or might not)   | required as first argument (`self`) | not present                     | first argument is `cls` (the class) |
    | object binding    | varies (might or might not)   | bound to the object              | bound to the class                | bound to the class                |
    | use cases         | customize object behavior     | object-specific actions         | utility functions               | class-level operations, factory methods |
