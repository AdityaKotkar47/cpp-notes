1. aggregation represents a "has-a" relationship between objects, one object (the container) has a reference to another object (the contained object), but they are independent entities\
use aggregation when objects have a loose relationship and can exist independently
    ```py
    class Student:
      def __init__(self, name):
        self.name = name

    class Course:
      def __init__(self, name, teacher):
        self.name = name
        self.teacher = teacher  # Aggregation: Course has a Student (teacher)

    # Create objects
    student1 = Student("Alice")
    course1 = Course("Programming 101", student1)


    # Access attributes
    print(course1.name)  # Output: Programming 101
    print(course1.teacher.name)  # Output: Alice

    # Modifying Student object doesn't affect Course
    student1.name = "Bob"
    print(course1.teacher.name)  # Still outputs: Alice (independent objects)
    ```

    here -
    - `Student` and `Course` are separate classes
    - `Course` has a `teacher` attribute that holds a reference to a `Student` object
    - the `Student` object can exist independently of the `Course` object, modifying the `Student` object doesn't affect the `Course` object

2. composition represents a "owns-a" relationship between objects. One object (the whole) is composed of other objects (the parts)\
use composition when objects have a strong relationship and the parts are essential for the whole to function
    ```py
    class Engine:
      def __init__(self, type):
        self.type = type

    class Car:
      def __init__(self, model, engine):
        self.model = model
        self.engine = engine  # Composition: Car is composed of an Engine

    # Create objects
    engine1 = Engine("V8")
    car1 = Car("Sports Car", engine1)

    # Access attributes
    print(car1.model)  # Output: Sports Car
    print(car1.engine.type)  # Output: V8

    # Deleting Car destroys Engine
    del car1
    # engine1 would also be garbage collected as it's part of Car
    ```
    here -
    - `Engine` and `Car` are separate classes
    - `Car` has an `engine` attribute that holds a reference to an `Engine` object
    - The `Engine` object is typically created within the `Car` constructor, indicating a strong dependency
    - Deleting the `Car` object would also lead to the `Engine` object being garbage collected because it's considered a part of the `Car`



2. key differences\
    | Feature	| Aggregation	| Composition |
    |-----------|----------|---------|
    | Strength of Association |	Weak | Strong |
    | Ownership |	Parts can exist independently |	Composite owns the parts |
    | Lifetime Management |	Parts might outlive the whole |	Parts are destroyed with the whole |
    | Implementation |	Simple attribute assignment |	Constructor injection or creation within composite [class] |
