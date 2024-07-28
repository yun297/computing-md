### 7.1 Procedural and Object-Oriented Programming

#### 7.1.1 Procedural Programming: 
Writing programs made of functions that perform specific tasks
- Procedures typically operate on data items that are separate from the procedures
- Data items commonly passed from one procedure to another
- Focus: to create procedures that operate on the program’s data

#### 7.1.2 Object-Oriented Programming: 
Focused on creating objects

**Object:** Entity that contains data and procedures
- Data is known as data attributes and procedures are known as methods
- Methods perform operations on the data attributes

**Encapsulation:** Combining data and procedure into a single object

**Fundamentals of Object-Oriented Programming**
- Define and understand classes and objects
- Understand encapsulation and how classes support information hiding and implementation independence
- Understand inheritance and how it promotes software reuse
- Understand polymorphism and how it enables code generalisation.

**Exclude:** Method overloading and multiple inheritance

**Draw class diagrams to illustrate the relationship between classes (including attributes and methods)**

**Data hiding:** Object’s data attributes are hidden from code outside the object and access is restricted to the object’s methods
- Protects from accidental corruption
- Outside code does not need to know the internal structure of the object

**An Everyday Example of an Object**
- **Data attributes:** Define the state of an object
  - Example: clock object would have second, minute, and hour data attributes
- **Public methods:** Allow external code to manipulate the object
  - Example: set_time, set_alarm_time
- **Private methods:** Used for the object’s inner workings

### 7.2 Class vs Instance/Object

**Class:** Code that specifies the data attributes and methods of a particular type of object
- Similar to a blueprint of a house or a cookie cutter

**Instance:** An object created from a class
- Similar to a specific house built according to the blueprint or a specific cookie
- There can be many instances of one class
- Example: Housefly and mosquito objects are instances of the Insect class

### 7.3 Class Definitions

Set of statements that define a class’s methods and data attributes
- **Format:** Begin with `class Class_name:`
  - Class names often start with an uppercase letter
- **Method definition:** Like any other Python function definition
  - **self parameter:** Required in every method in the class – references the specific object that the method is working on

#### 7.3.1 Initializer Method

Also called the class’s constructor, this method is automatically executed when an instance of the class is created
- Initializes the object’s data attributes and assigns the self parameter to the object
- **Format:** `def __init__(self):`
- Usually the first method in a class definition

#### 7.3.2 Creating an Instance

- To create a new instance of a class, call the initializer method
  - **Format:** `My_instance = Class_Name()`
- To call any of the class methods using the created instance, use dot notation
  - **Format:** `My_instance.method()`
  - Because the self parameter references the specific instance of the object, the method will affect this instance. The reference to self is passed automatically

#### 7.3.3 Data Hiding

**Hiding Attributes**
An object’s data attributes should be private. In Python, a name prefixed with an underscore (e.g. `_sideup`) is a commonly used convention to denote a private attribute or method.

**Accessor and Mutator Methods**
All of a class’s data attributes are private and provide methods to access and change them.
- **Accessor/Getter methods:** Return a value from a class’s attribute without changing it
  - Safe way for code outside the class to retrieve the value of attributes
- **Mutator/Setter methods:** Store or change the value of a data attribute

**Storing Classes in Modules**
Classes can be stored in modules
- Filename for module must end in .py
- Module can be imported to programs that use the class

**The BankAccount Class**
Class methods can have multiple parameters in addition to self
- For `__init__`, parameters are needed to create an instance of the class
  - Example: A BankAccount object is created with a balance
  - When called, the initializer method receives a value to be assigned to the `_balance` attribute
- For other methods, parameters are needed to perform the required task
  - Example: The deposit method requires the amount to be deposited

**The \_\_str\_\_ Method**

- **Object’s state:** The values of the object’s attributes at a given moment
- **\_\_str\_\_ method:** Displays the object’s state
  - Automatically called when you pass the object’s name to the `print` statement
  - Automatically called when the object is passed as an argument to the `str` function

### 7.4 Working With Instances

- **Instance attribute:** Belongs to a specific instance of a class
  - Created when a method uses the self parameter to create an attribute
- If many instances of a class are created, each would have its own set of attributes

### Passing Objects as Arguments

- Methods and functions often need to accept objects as arguments
- When you pass an object as an argument, you are actually passing a reference to the object. The receiving method or function has access to the actual object
- Methods of the object can be called within the receiving function or method, and data attributes may be changed using mutator methods

### 7.5 Techniques for Designing Classes

Class diagram is a standard diagram for graphically depicting object-oriented systems. General layout:
- **Top section:** Name of the class
- **Middle section:** List of data attributes
- **Bottom section:** List of class methods
- **Access Modifier:**
  - `-` (minus sign) denotes private
  - `+` (plus sign) denotes public

### 7.6 Rules of Thumb for Defining a Simple Class

- Before writing a line of code, think about the behavior and attributes of the objects of the new class
- Choose an appropriate class name and develop a short list of the methods available to users
- Write a short script that appears to use the new class in an appropriate way
- Choose appropriate data structures for attributes
- Fill in class template with `__init__` and `__str__`
- Complete and test remaining methods incrementally
- Document your code

### 7.7 Inheritance

In the real world, many objects are specialized versions of more general objects.
- **Example:** Grasshoppers and bees are specialized types of insects.
  - Grasshoppers can jump.
  - Bees can sting, make honey, and build hives.
- Bumblebees and grasshoppers are specialized versions of an insect.

#### 7.7.1 Inheritance and the "Is a" Relationship

- **“Is a” relationship:** Exists when one object is a specialized version of another object.
  - Specialized object has all the characteristics of the general object plus unique characteristics.
  - **Example:** Rectangle is a shape, Car is a vehicle.
- **Inheritance:** Used to create an “is a” relationship between classes.
  - **Superclass (base class):** A general class.
  - **Subclass (derived class):** A specialized class, an extended version of the superclass.
    - Inherits attributes and methods of the superclass.
    - New attributes and methods can be added.

**Example:** Classes for cars, pickup trucks, and SUVs.
- All are automobiles with attributes like make, year model, mileage, and price (base class attributes).
  - Car has a number of doors.
  - Pickup truck has a drive type.
  - SUV has a passenger capacity.

**In a class definition for a subclass:**
- To indicate inheritance, the superclass name is placed in parentheses after the subclass name.
  - **Example:** `class Car(Automobile):`
- The initializer method of a subclass calls the initializer method of the superclass and then initializes the unique data attributes.
- Add method definitions for unique methods.

#### 7.7.2 Inheritance in Class Diagrams

In a class diagram, show inheritance by drawing a line with an open arrowhead from the subclass to the superclass.

### 7.8 Polymorphism

- **Polymorphism:** An object’s ability to take different forms.
- **Essential ingredients of polymorphic behavior:**
  - Ability to define a method in a superclass and override it in a subclass.
    - Subclass defines a method with the same name.
  - Ability to call the correct version of the overridden method depending on the type of object that is used to call it.

- In previous inheritance examples, we showed how to override the `__init__` method.
  - Called the superclass `__init__` method and then added to it.
- The same can be done for any other method. The method can call the superclass equivalent and add to it, or do something completely different.