1. object is a "bundle" of related attributes (variables) and methods (functions), objects are created using classes

2. class is a blueprint used to design the structure and layout of an object [keep them capitalised]
    ```py
    class class_name:
      pass
    ```

3. `__init__` is a constructor [a function used to create objects], used as
    ```py
    def __init__(self, attribute1, attribute2, attribute3):
      self.attribute1 = attribute1
      self.attribute2 = attribute2
      self.attribute3 = attribute3
      # here we are assigning the parameters passed as arguments to the objects using self, self refers to the current object
    ```

4. objects can be created by initialising a variable using the class with the attributes passed as argument\
    `object1 = class_name(argument1, argument2, argument3)`

5. attributes can be accessed using `.` [attribute access operator] as\
    `print(class_name.attribute1)`

6. methods [functions in classes] are actions that an object can perform\
    `def method1(self, other_params)`\
    and can be accessed as `object1.method1(args)`

7. variables created inside constructor are instance variables, and class variables are created outside the constructor, which are shared among all instances [objects] of a class and they are considered as attributes so can be accessed the same way
    ```py
    object1.class_variable1
    # or also using the class directly
    Class1.class_variable1 # preferred
    ```

8. the code inside constructor will always be executed when an object is instantiated

9. all variables are always given an initial value at the point the variable is declared, thus all variables are initialized\
an object is an instance of some Class, the act of creating an instance of a Class is called instantiation 

10. for accessing variables inside the class
    ```py
    # for instance variables
    self.instance_variable1
    # for class variables
    Class_name1.class_variable2
    ```

11. destructors are methods that are invoked when an object is about to be destroyed, Python has a garbage collector that handles memory management, which reduces the need for destructors\
    `def __del__(self)`\
it gets automatically invoked after program ends\
or you can invoke it by `del instance_name`
*A reference to objects is also deleted when the object goes out of reference or when the program ends*\
for python, destructors are not mandatory due to its automatic garbage collection but still can be used for optimization

12. nested class is a class defined within another class [we don't create objects of inner classes outside the outer class]
    ```py
    class Outer:
        class Inner:
    ```

    benefits - 
    - allows you to logically group classes that are closely related
    - encapsulates private details that aren't relevant outside of the outer class
    - keeps the namespace clean, reduces the possibility of naming conflicts