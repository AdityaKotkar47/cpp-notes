1. inheritance allows a class to inherit attributes and methods from another class, helps with code reusability and extensibility

2. `Child` class can inherit from `Parent` class, but not vice versa\
`class Child(Parent)`

3. if the constructor is missing in the child class, then constructor in parent class is called implicitly whereas to call it explicitly include\
`super().__init__(args)`

4. multiple inheritance - inherit from more than one parent class\
C(A, B)

5. multilevel inheritance - inherit from a parent which inherits from another parent\
C(B) <- B(A) <- A

6. abstract classes are the classes that cannot be instantiated on its own, they are meant to be subclassed [be a parent to chidren classes], they can contain abstract methods, which are declared but have no implementation\
abstract classes benefits:
    - prevents instantiation of the class itself
    - requires children to implement inherited abstract methods mandatorily\

    syntax -
    ```py
    from abc import ABC, abstractmethod # Abstract Base Classes

    class Parent_class(ABC):

      @abstractmethod
      def am1(self):
        pass         # do not define here, just pass
      @abstractmethod
      def am2(self):
        pass         # deine in children class
      
    class Children_class1(Parent_class):

      def am1(self):
        # something here
      def am2(self):
        # something here
    ```

7.  Parent classes are super classes [`class Super`], children classes are sub classes [`class Sub(Super)`]

8. `super()` function is used in a child class to call methods from a parent class (superclass), to extend the functionality of the inherited methods as in 3, usually used in the constructor of child class to assign attributes [that all sibings have in common] and used in the method of child class to extend its functionality

9. method overriding - if a child shares a similar method with a parent, child's version will be used, so to also use the parent version with child's version\
`super().method_name()`\
or to use only parent's version directly\
`Parent_class.method_name(children_class, other_args)`