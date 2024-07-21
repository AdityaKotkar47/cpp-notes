1. polymorphism allows objects of different classes to be treated uniformly, it enables flexibility and adaptability by providing a consistent interface for interacting with diverse types of objects

2. using inheritance\
subclass object can be treated as the same way as parent class object using abstract classes and methods
    ```py
    # example
    from abc import ABC, abstractmethod

    class Animal(ABC):
    @abstractmethod
      def sound(self):
          pass

    # Then we can define subclasses of Animal that implement the sound method differently
    class Dog(Animal):
      def sound(self):
        print("Woof")

    class Cat(Animal):
      def sound(self):
          print("Meow")

    animals = [Dog(), Cat()]

    # The sound method will behave differently depending on the type of the animal
    for animal in animals:
      animal.sound()
    ```
  
3. using duck typing\
the type or class of an object is less important than the methods it defines, it comes from the phrase, "If it looks like a duck and quacks like a duck, it must be a duck."\
this means that instead of checking the type of an object, you check for the presence of a given method or attribute, if an object implements the minimum necessary methods and behaviors, it can be used in place of another object, regardless of its actual type
    ```py
    class Animal:
      alive = True

    class Dog(Animal):
      def speak(self):
        print("Woof")

    class Cat(Animal):
      def speak(self):
        print("Meow")

    class Car:
      def speak(self):
        print("Vroom")

    animals = [Dog(), Cat(), Car()]

    # The speak method will behave differently depending on the type of the animal
    for animal in animals:
        animal.speak()
    
    # The Cat and Dog classes demonstrate inheritance polymorphism, they both inherit from the common base class Animal
    # The Car class showcases duck typing polymorphism, it doesn’t inherit from Animal, but it still provides a speak method
    ```
