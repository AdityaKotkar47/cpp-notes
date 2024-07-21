1. decorators are a versatile syntactic feature that allows you to modify the behavior of functions, methods, or classes

2. they essentially add extra functionality to the target object without permanently altering its code

3. they use the `@` symbol followed by the decorator function name placed above the definition of a function, method, or class

4. `@property` decorator - `@property` decorator is placed above a method definition within a class, this method becomes a property instead of a regular method\
it is a decorator used to define a method as a property [it can be accessed like an attribute] with additional logic such as:\
getter -
    - it is a function decorated with `@property`, it is automatically invoked when you access the property like an attribute of the object (e.g., `object.property_name`)
    - it typically retrieves the value of the underlying attribute (often stored privately within the class) and returns it
    - can also perform any necessary calculations or logic before returning the value
    ```py
    class Book:
      def __init__(self, title, author):
        self._year = 2023  # Private attribute

      @property
      def year(self):
        """Returns the year (getter)."""
        return self._year
    ```
    setter -
    - it is a function decorated with `@property.setter`, it controls how the property can be assigned a new value
    - it typically takes the new value as an argument and performs any necessary validation or processing before updating the underlying attribute
    - it can also raise exceptions if the assigned value is invalid
    ```py
    class Book:
      def __init__(self, title, author):
        self._year = 2023

      @year.setter
      def year(self, value):
        """Attempts to set the year, but raises an error if not within a valid range."""
        if 1900 <= value <= 2050:
          self._year = value
        else:
          raise ValueError("Year must be between 1900 and 2050")
    ```
    deleter -
    -  it is a function decorated with `@property.deleter`, it controls how the property can be deleted from the object
    - it typically takes no arguments and performs any necessary cleanup operations when the property is deleted
    - it might also raise exceptions if deletion is not allowed
    ```py
    class Player:
      def __init__(self, name, score):
        self._score = score

      @score.deleter
      def score(self):
        """Deletes the player's score (sets to 0)."""
        print("Player's score has been reset to 0.")
        self._score = 0
    ```
    getters, setters, and deleters are optional, a property can have only a getter, or a getter and a setter, or all three