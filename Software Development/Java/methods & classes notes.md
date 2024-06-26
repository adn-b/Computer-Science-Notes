# Java Notes - Methods & Classes - Aidan Butler
### Following the W3Schools curriculum with my own insight and touch.

# Java Methods

## Java Methods

A method is a block of code which only runs when it is called.

You can pass data, known as parameters, into a method.

Methods are used to perform certain actions, and they are also known as functions.

For example:
```java
public class Main {
  static void myMethod() {
    // code to be executed
  }
}
```
- myMethod() is the name of the method.
- "static" means that the method belongs to the Main class and not an object of the Main class.
- "void means" that this method does not have a return value.


## Java Method Parameters

Information can be passed to methods as parameter. Parameters act as variables inside the method.

Parameters are specified after the method name, inside the parentheses. You can add as many parameters as you want, just separate them with a comma.

The following example has a method that takes a String called fname as parameter. When the method is called, we pass along a first name, which is used inside the method to print the full name:
```java
public class Main {
  static void myMethod(String fname) {
    System.out.println(fname + " Refsnes");
  }

  public static void main(String[] args) {
    myMethod("Liam");
    myMethod("Jenny");
    myMethod("Anja");
  }
}
// Liam Refsnes
// Jenny Refsnes
// Anja Refsnes
```
Parameters in java must have their data type declared before the name of the variable.

## Java Method Overloading

With method overloading, multiple methods can have the same name with different parameters:
```java
int myMethod(int x)
float myMethod(float x)
double myMethod(double x, double y)
```
Instead of defining two methods that should do the same thing, it is better to overload one. 


## Java Scope

In Java, variables are only accessible inside the region they are created. This is called scope.

### Method Scope

Variables declared directly inside a method are available anywhere in the method following the line of code in which they were declared:
```java
public class Main {
  public static void main(String[] args) {

    // Code here CANNOT use x

    int x = 100;

    // Code here can use x
    System.out.println(x);
  }
}
```

### Block Scope

A block of code refers to all of the code between curly braces {}.

Variables declared inside blocks of code are only accessible by the code between the curly braces, which follows the line in which the variable was declared:
```java
public class Main {
  public static void main(String[] args) {

    // Code here CANNOT use x

    { // This is a block

      // Code here CANNOT use x

      int x = 100;

      // Code here CAN use x
      System.out.println(x);

    } // The block ends here

  // Code here CANNOT use x

  }
}
```


## Java Recursion

Recursion is the technique of making a function call itself. This technique provides a way to break complicated problems down into simple problems which are easier to solve.

Here is an example of recursion:
```java
public class Main {
  public static void main(String[] args) {
    int result = sum(10);
    System.out.println(result);
  }
  public static int sum(int k) {
    if (k > 0) {
      return k + sum(k - 1);
    } else {
      return 0;
    }
  }
}
```

When the sum() function is called, it adds parameter k to the sum of all numbers smaller than k and returns the result. When k becomes 0, the function just returns 0. When running, the program follows these steps:
- 10 + sum(9)
- 10 + ( 9 + sum(8) )
- 10 + ( 9 + ( 8 + sum(7) ) )
- ...
- 10 + 9 + 8 + 7 + 6 + 5 + 4 + 3 + 2 + 1 + sum(0)
- 10 + 9 + 8 + 7 + 6 + 5 + 4 + 3 + 2 + 1 + 0 


# Java Classes

## Java OOP

OOP stands for Object-Oriented Programming.

Procedural programming is about writing procedures or functions that perform operations on the data, while object-oriented programming is about creating objects that contain both data and functions.

Object-oriented programming has several advantages over procedural programming:
- OOP is faster and easier to execute
- OOP provides a clear structure for the programs
- OOP helps to keep the Java code DRY "Don't Repeat Yourself", and makes the code easier to maintain, modify and debug
- OOP makes it possible to create full reusable applications with less code and shorter development time

Java is an object-oriented language, which means it uses classes, objects, and therefore techniques like encapsulation, inheritence, and polymorphism, which provide many advantages in coding, as will be discussed in the following chapters.

### What are Classes and Objects?

The following table will explain the differences:
| Class | Objects |
|:-----:|:-------:|
Fruit | Apple
| | Banana
| | Mango

Or:

| Class | Objects |
|:-----:|:-------:|
Car Brand | Volvo
| | Audi
| | Toyota

A class is effectively a template for objects, consisting of "attributes" and "methods", which are variables or functions. When the individual objects are created, they inherit all the variables and functions from the class. 

## Java Classes/Objects

Everything in Java is associated with classes and objects, along with its attributes and methods. For example: in real life, a car is an object. The car has attributes, such as weight and color, and methods, such as drive and brake. 

Attributes and methods are basically variables and functions that belongs to the class. These are often referred to as "class members".

A class is a user-defined data type that we can use in our program, and it works as an object constructor, or a "blueprint" for creating objects.

### Creating a Class

To create a class, use the class keyword. In the example below, a class "Main" is created, and an integer variable is defined.
```java
public class Main {
  int x = 5;
}
```

### Creating an Object

In Java, an object is created from a class. We have already created the class named Main, so now we can use this to create objects.

To create an object of Main, specify the class name, followed by the object name, and use the keyword new:
```java
public class Main {
  int x = 5;

  public static void main(String[] args) {
    Main myObj = new Main();
    System.out.println(myObj.x);
  }
}
```

### Multiple Objects

You can create multiple objects of one class, for example:
```java
public class Main {
  int x = 5;

  public static void main(String[] args) {
    Main myObj1 = new Main();  // Object 1
    Main myObj2 = new Main();  // Object 2
    System.out.println(myObj1.x);
    System.out.println(myObj2.x);
  }
}
```

### Using Multiple Classes

You can also create an object of a class and access it in another class. This is often used for better organization of classes (one class has all the attributes and methods, while the other class holds the main() method (code to be executed)).

Remember that the name of the java file should match the class name. In this example, we have created two files in the same directory/folder:

- Main.java
- Second.java

**Main.java:**
```java
public class Main {
  int x = 5;
}
```
**Second.java:**
```java
class Second {
  public static void main(String[] args) {
    Main myObj = new Main();
    System.out.println(myObj.x);
  }
}
```

When both files have been compiled:

    C:\Users\Your Name>javac Main.java
    C:\Users\Your Name>javac Second.java

Run the Second.java file:

    C:\Users\Your Name>java Second

And the output will be:

    5


## Java Class Attributes

Each class has variables, known as "attributes". These enable classes to essentially act as templates for new objects, making it easy for you to assign values to variables in new objects without having to redefine them.

### Accessing Attributes

You can access attributes by creating an object of the class, and by using the dot syntax (.):
```java
public class Main {
  int x = 5;

  public static void main(String[] args) {
    Main myObj = new Main();
    System.out.println(myObj.x);
  }
}
```

### Modify Attributes

You can also modify attribute values:
```java
public class Main {
  int x;

  public static void main(String[] args) {
    Main myObj = new Main();
    myObj.x = 40;
    System.out.println(myObj.x);
  }
}
```


## Java Class Methods

### Static vs Public

You will often see Java programs that have either static or public attributes and methods.

"static" means that a method or attribute can be accessed without creating an object of the class, unlike "public", which means they can only be accessed by objects of that class.

### Access Methods With an Object
```java
// Create a Main class
public class Main {
 
  // Create a fullThrottle() method
  public void fullThrottle() {
    System.out.println("The car is going as fast as it can!");
  }

  // Create a speed() method and add a parameter
  public void speed(int maxSpeed) {
    System.out.println("Max speed is: " + maxSpeed);
  }

  // Inside main, call the methods on the myCar object
  public static void main(String[] args) {
    Main myCar = new Main();   // Create a myCar object
    myCar.fullThrottle();      // Call the fullThrottle() method
    myCar.speed(200);          // Call the speed() method
  }
}

// The car is going as fast as it can!
// Max speed is: 200
```

Example explained:

1) We created a custom Main class with the class keyword.
2) We created the fullThrottle() and speed() methods in the Main class.
3) The fullThrottle() method and the speed() method will print out some text, when they are called.
4) The speed() method accepts an int parameter called maxSpeed - we will use this in 8).
5) In order to use the Main class and its methods, we need to create an object of the Main Class.
6) Then, go to the main() method, which you know by now is a built-in Java method that runs your program (any code inside main is executed).
7) By using the new keyword we created an object with the name myCar.
8) Then, we call the fullThrottle() and speed() methods on the myCar object, and run the program using the name of the object (myCar), followed by a dot (.), followed by the name of the method (fullThrottle(); and speed(200);). Notice that we add an int parameter of 200 inside the speed() method.

### Using Multiple Classes

Using Multiple Classes

Like we specified in the Classes chapter, it is a good practice to create an object of a class and access it in another class.

Remember that the name of the java file should match the class name. In this example, we have created two files in the same directory:

- Main.java
- Second.java

Main.java
```java
public class Main {
  public void fullThrottle() {
    System.out.println("The car is going as fast as it can!");
  }

  public void speed(int maxSpeed) {
    System.out.println("Max speed is: " + maxSpeed);
  }
}
```

Second.java
```java
class Second {
  public static void main(String[] args) {
    Main myCar = new Main();     // Create a myCar object
    myCar.fullThrottle();      // Call the fullThrottle() method
    myCar.speed(200);          // Call the speed() method
  }
}
```
When both files have been compiled:

    C:\Users\Your Name>javac Main.java
    C:\Users\Your Name>javac Second.java

Run the Second.java file:

    C:\Users\Your Name>java Second

And the output will be:

    The car is going as fast as it can!
    Max speed is: 200 


## Java Constructors

A constructor in Java is a special method that is used to initialize objects. The constructor is called when an object of a class is created. It can be used to set initial values for object attributes:
```java
// Create a Main class
public class Main {
  int x;  // Create a class attribute

  // Create a class constructor for the Main class
  public Main() {
    x = 5;  // Set the initial value for the class attribute x
  }

  public static void main(String[] args) {
    Main myObj = new Main(); // Create an object of class Main (This will call the constructor)
    System.out.println(myObj.x); // Print the value of x
  }
}

// Outputs 5
```

**Note that the constructor name must match the class name, and it cannot have a return type (like void).**

**Also note that the constructor is called when the object is created.**

**All classes have constructors by default: if you do not create a class constructor yourself, Java creates one for you. However, then you are not able to set initial values for object attributes.**


### Constructor Parameters

Constructors can also take parameters, which is used to initialize attributes.

The following example adds an int y parameter to the constructor. Inside the constructor we set x to y (x=y). When we call the constructor, we pass a parameter to the constructor (5), which will set the value of x to 5:
```java
public class Main {
  int x;

  public Main(int y) {
    x = y;
  }

  public static void main(String[] args) {
    Main myObj = new Main(5);
    System.out.println(myObj.x);
  }
}

// Outputs 5
```


## Java Modifiers

### Modifiers

There are two types of "modifier" keywords in Java:
- **Access Modifiers,** which control the access level
- **Non-Access Modifiers,** which do not control access level, but provide other functionality


### Access Modifiers

For classes, you can use either public or default:

| Modifier | Description |
|----------|-------------|
| public | The class is accessible by any other class. 
| default | The class is only accessible by classes in the same package. This is used when you don't specify a modifier.	


For attributes, methods and constructors, you can use the one of the following:

| Modifier | Description |
|----------|-------------|
| public | The code is accessible for all classes. 
| private | The code is only accessible within the declared class. 
| default | The code is only accessible in the same package. This is used when you don't specify a modifier.
| protected | The code is accessible in the same package and subclasses.


### Non-Access Modifiers

For classes, you can use either final or abstract:

| Modifier | Description |
|----------|-------------|
| final | The class cannot be inherited by other classes.
| abstract | The class cannot be used to create objects. To access an abstract class, it must be inherited from another class.


For attributes and methods, you can use the one of the following:

| Modifier | Description |
|----------|-------------|
| final | Attributes and methods cannot be overridden/modified
| static | Attributes and methods belongs to the class, rather than an object.
| abstract | Can only be used in an abstract class, and can only be used on methods. The method does not have a body, for example abstract void run();. The body is provided by the subclass (inherited from).
| transient | Attributes and methods are skipped when serializing the object containing them.
| synchronized | Methods can only be accessed by one thread at a time.
| volatile | The value of an attribute is not cached thread-locally, and is always read from the "main memory".


## Java Encapsulation

The meaning of Encapsulation, is to make sure that "sensitive" data is hidden from users. To achieve this, you must:
- Declare class variables/attributes as private
- Provide public get and set methods to access and update the value of a private variable

### Get and Set

Ordinarily, private variables can only be accessed within the same class (an outside class has no access to it). However, it is possible to access them if we provide public get and set methods.

The get method returns the variable value, and the set method sets the value.

Syntax for both is that they start with either get or set, followed by the name of the variable, with the first letter in upper case:
```java
public class Person {
  private String name; // private = restricted access

  // Getter
  public String getName() {
    return name;
  }

  // Setter
  public void setName(String newName) {
    this.name = newName;
  }
}
```


## Java Packages / API

A package in Java is used to group related classes. Think of it as a folder in a file directory. We use packages to avoid name conflicts, and to write a better maintainable code. Packages are divided into two categories:
- Built-in Packages (packages from the Java API)
- User-defined Packages (create your own packages)

The library is divided into packages and classes. Meaning you can either import a single class (along with its methods and attributes), or a whole package that contain all the classes that belong to the specified package.

```java
import package.name.Class;   // Import a single class
import package.name.*;   // Import the whole package
```


## Java Inheritance

### Subclass & Superclass

In Java, it is possible to inherit attributes and methods from one class to another. We group the "inheritance concept" into two categories:

- subclass (child) - the class that inherits from another class
- superclass (parent) - the class being inherited from

To inherit from a class, use the extends keyword.

In the example below, the Car class (subclass) inherits the attributes and methods from the Vehicle class (superclass):
```java
class Vehicle {
  protected String brand = "Ford";        // Vehicle attribute
  public void honk() {                    // Vehicle method
    System.out.println("Tuut, tuut!");
  }
}

class Car extends Vehicle {
  private String modelName = "Mustang";    // Car attribute
  public static void main(String[] args) {

    // Create a myCar object
    Car myCar = new Car();

    // Call the honk() method (from the Vehicle class) on the myCar object
    myCar.honk();

    // Display the value of the brand attribute (from the Vehicle class) and the value of the modelName from the Car class
    System.out.println(myCar.brand + " " + myCar.modelName);
  }
}
```

### The "final" Keyword

If you don't want other classes to inherit from a class, use the final keyword:

If you try to access a final class, Java will generate an error:
```java
final class Vehicle {
  ...
}

class Car extends Vehicle {
  ...
}
```


## Java Polymorphism

Polymorphism means "many forms", and it occurs when we have many classes that are related to each other by inheritance.

As specified in the previous chapter; Inheritance lets us inherit attributes and methods from another class. Polymorphism uses those methods to perform different tasks. This allows us to perform a single action in different ways.

For example, think of a superclass called Animal that has a method called animalSound(). Subclasses of Animals could be Pigs, Cats, Dogs, Birds - And they also have their own implementation of an animal sound (the pig oinks, and the cat meows, etc.):
```java
class Animal {
  public void animalSound() {
    System.out.println("The animal makes a sound");
  }
}

class Pig extends Animal {
  public void animalSound() {
    System.out.println("The pig says: wee wee");
  }
}

class Dog extends Animal {
  public void animalSound() {
    System.out.println("The dog says: bow wow");
  }
}
```

Now we can create Pig and Dog objects and call the animalSound() method on both of them:
```java
class Animal {
  public void animalSound() {
    System.out.println("The animal makes a sound");
  }
}

class Pig extends Animal {
  public void animalSound() {
    System.out.println("The pig says: wee wee");
  }
}

class Dog extends Animal {
  public void animalSound() {
    System.out.println("The dog says: bow wow");
  }
}

class Main {
  public static void main(String[] args) {
    Animal myAnimal = new Animal();  // Create a Animal object
    Animal myPig = new Pig();  // Create a Pig object
    Animal myDog = new Dog();  // Create a Dog object
    myAnimal.animalSound();
    myPig.animalSound();
    myDog.animalSound();
  }
}
```


## Java Inner Classes

In Java, it is also possible to nest classes (a class within a class). The purpose of nested classes is to group classes that belong together, which makes your code more readable and maintainable.

To access the inner class, create an object of the outer class, and then create an object of the inner class:
```java
class OuterClass {
  int x = 10;

  class InnerClass {
    int y = 5;
  }
}

public class Main {
  public static void main(String[] args) {
    OuterClass myOuter = new OuterClass();
    OuterClass.InnerClass myInner = myOuter.new InnerClass();
    System.out.println(myInner.y + myOuter.x);
  }
}

// Outputs 15 (5 + 10)
```

### Private Inner Class

Unlike a "regular" class, an inner class can be private or protected. If you don't want outside objects to access the inner class, declare the class as private:
```java
class OuterClass {
  int x = 10;

  private class InnerClass {
    int y = 5;
  }
}

public class Main {
  public static void main(String[] args) {
    OuterClass myOuter = new OuterClass();
    OuterClass.InnerClass myInner = myOuter.new InnerClass();
    System.out.println(myInner.y + myOuter.x);
  }
}
```

### Static Inner Class

An inner class can also be static, which means that you can access it without creating an object of the outer class:
```java
class OuterClass {
  int x = 10;

  static class InnerClass {
    int y = 5;
  }
}

public class Main {
  public static void main(String[] args) {
    OuterClass.InnerClass myInner = new OuterClass.InnerClass();
    System.out.println(myInner.y);
  }
}

// Outputs 5
```

### Access Outer Class From Inner Class

One advantage of inner classes, is that they can access attributes and methods of the outer class:
```java
class OuterClass {
  int x = 10;

  class InnerClass {
    public int myInnerMethod() {
      return x;
    }
  }
}

public class Main {
  public static void main(String[] args) {
    OuterClass myOuter = new OuterClass();
    OuterClass.InnerClass myInner = myOuter.new InnerClass();
    System.out.println(myInner.myInnerMethod());
  }
}

// Outputs 10
```


## Java Abstraction

### Abstract Classes and Methods

Data abstraction is the process of hiding certain details and showing only essential information to the user.
Abstraction can be achieved with either abstract classes or interfaces (which you will learn more about in the next chapter).

The abstract keyword is a non-access modifier, used for classes and methods:

    Abstract class: is a restricted class that cannot be used to create objects (to access it, it must be inherited from another class).

    Abstract method: can only be used in an abstract class, and it does not have a body. The body is provided by the subclass (inherited from).

An abstract class can have both abstract and regular methods:

abstract class Animal {
  public abstract void animalSound();
  public void sleep() {
    System.out.println("Zzz");
  }
}
 
 

From the example above, it is not possible to create an object of the Animal class:
```java
Animal myObj = new Animal(); // will generate an error
```

To access the abstract class, it must be inherited from another class. In the example below, I convert the Animal class used in the Polymorphism chapter to an abstract class:
```java
// Abstract class
abstract class Animal {
  // Abstract method (does not have a body)
  public abstract void animalSound();
  // Regular method
  public void sleep() {
    System.out.println("Zzz");
  }
}

// Subclass (inherit from Animal)
class Pig extends Animal {
  public void animalSound() {
    // The body of animalSound() is provided here
    System.out.println("The pig says: wee wee");
  }
}

class Main {
  public static void main(String[] args) {
    Pig myPig = new Pig(); // Create a Pig object
    myPig.animalSound();
    myPig.sleep();
  }
}
```


## Java Interface

Another way to achieve abstraction in Java, is with interfaces.

An interface is a completely "abstract class" that is used to group related methods with empty bodies, for example:
```java
// interface
interface Animal {
  public void animalSound(); // interface method (does not have a body)
  public void run(); // interface method (does not have a body)
}
```

To access the interface methods, the interface must be "implemented" (similar to inherited) by another class with the implements keyword (instead of extends). The body of the interface method is provided by the "implement" class:
```java
// Interface
interface Animal {
  public void animalSound(); // interface method (does not have a body)
  public void sleep(); // interface method (does not have a body)
}

// Pig "implements" the Animal interface
class Pig implements Animal {
  public void animalSound() {
    // The body of animalSound() is provided here
    System.out.println("The pig says: wee wee");
  }
  public void sleep() {
    // The body of sleep() is provided here
    System.out.println("Zzz");
  }
}

class Main {
  public static void main(String[] args) {
    Pig myPig = new Pig();  // Create a Pig object
    myPig.animalSound();
    myPig.sleep();
  }
}
```

**Notes on Interfaces:**

- Like abstract classes, interfaces cannot be used to create objects (in the example above, it is not possible to create an "Animal" object in the MyMainClass)
- Interface methods do not have a body - the body is provided by the "implement" class
- On implementation of an interface, you must override all of its methods
- Interface methods are by default abstract and public
- Interface attributes are by default public, static and final
- An interface cannot contain a constructor (as it cannot be used to create objects)

**Why And When To Use Interfaces?**

1) To achieve security - hide certain details and only show the important details of an object (interface).
2) Java does not support "multiple inheritance" (a class can only inherit from one superclass). However, it can be achieved with interfaces, because the class can implement multiple interfaces. Note: To implement multiple interfaces, separate them with a comma (see example below).


### Multiple Interfaces

To implement multiple interfaces, separate them with a comma:
```java
interface FirstInterface {
  public void myMethod(); // interface method
}

interface SecondInterface {
  public void myOtherMethod(); // interface method
}

class DemoClass implements FirstInterface, SecondInterface {
  public void myMethod() {
    System.out.println("Some text..");
  }
  public void myOtherMethod() {
    System.out.println("Some other text...");
  }
}

class Main {
  public static void main(String[] args) {
    DemoClass myObj = new DemoClass();
    myObj.myMethod();
    myObj.myOtherMethod();
  }
}
```



## Java Enums

An enum is a special "class" that represents a group of constants (unchangeable variables, like final variables).

To create an enum, use the enum keyword (instead of class or interface), and separate the constants with a comma. Note that they should be in uppercase letters:
```java
enum Level {
  LOW,
  MEDIUM,
  HIGH
}
```

You can access enum constants with the dot syntax:
```java
Level myVar = Level.MEDIUM; 
```

### Enum inside a Class

You can also have an enum inside a class:
```java
public class Main {
  enum Level {
    LOW,
    MEDIUM,
    HIGH
  }

  public static void main(String[] args) {
    Level myVar = Level.MEDIUM; 
    System.out.println(myVar);
  }
}
```

### Other Uses

Enums can also be used in switch statements to check for corresponding values, or looped through with the "values()" method, which returns an array of all enum constants:
```java
for (Level myVar : Level.values()) {
  System.out.println(myVar);
}
```

An enum can, just like a class, have attributes and methods. The only difference is that enum constants are public, static and final (unchangeable - cannot be overridden).

An enum cannot be used to create objects, and it cannot extend other classes (but it can implement interfaces).

Use enums when you have values that you know aren't going to change, like month days, days, colors, deck of cards, etc.

## Java User Input

### Scanner

The Scanner class is used to get user input, and it is found in the java.util package.

To use the Scanner class, create an object of the class and use any of the available methods found in the Scanner class documentation. In our example, we will use the nextLine() method, which is used to read Strings:
```java
import java.util.Scanner;  // Import the Scanner class

class Main {
  public static void main(String[] args) {
    Scanner myObj = new Scanner(System.in);  // Create a Scanner object
    System.out.println("Enter username");

    String userName = myObj.nextLine();  // Read user input
    System.out.println("Username is: " + userName);  // Output user input
  }
}
```

### Input Types

In the example above, we used the nextLine() method, which is used to read Strings. To read other types, look at the table below:
| Method | Description |
|--------|-------------|
| nextBoolean() | Reads a boolean value from the user
| nextByte() | Reads a byte value from the user
| nextDouble() | Reads a double value from the user
| nextFloat() | Reads a float value from the user
| nextInt() | Reads a int value from the user
| nextLine() | Reads a String value from the user
| nextLong() | Reads a long value from the user
| nextShort() | Reads a short value from the user

For example:
```java
import java.util.Scanner;

class Main {
  public static void main(String[] args) {
    Scanner myObj = new Scanner(System.in);

    System.out.println("Enter name, age and salary:");

    // String input
    String name = myObj.nextLine();

    // Numerical input
    int age = myObj.nextInt();
    double salary = myObj.nextDouble();

    // Output input by user
    System.out.println("Name: " + name);
    System.out.println("Age: " + age);
    System.out.println("Salary: " + salary);
  }
}
```


## Java Date

Java does not have a built-in Date class, but we can import the java.time package to work with the date and time API. The package includes many date and time classes. For example:
| Class | Description |
|-------|-------------| 
| LocalDate | Represents a date (year, month, day (yyyy-MM-dd))
| LocalTime | Represents a time (hour, minute, second and nanoseconds (HH-mm-ss-ns))
| LocalDateTime | Represents both a date and a time (yyyy-MM-dd-HH-mm-ss-ns)
| DateTimeFormatter | Formatter for displaying and parsing date-time objects


## Java ArrayList

The ArrayList class is a resizable array, which can be found in the java.util package.

The difference between a built-in array and an ArrayList in Java, is that the size of an array cannot be modified (if you want to add or remove elements to/from an array, you have to create a new one). While elements can be added and removed from an ArrayList whenever you want. The syntax is also slightly different:
```java
import java.util.ArrayList; // import the ArrayList class

ArrayList<String> cars = new ArrayList<String>(); // Create an ArrayList object
```

### Add Items

You can use the "add()" method from the ArrayList class to add elements to the ArrayList.

### Access an Item

To access an element in the ArrayList, use the get() method and refer to the index number.

### Change an Item

To modify an element, use the set() method and refer to the index number.

### Remove an Item

To remove an element, use the remove() method and refer to the index number.

### ArrayList Size

To find out how many elements an ArrayList have, use the size() method.

### Loop Through an ArrayList

Loop through the elements of an ArrayList with a for loop, and use the size() method to specify how many times the loop should run.



## Java LinkedList

The LinkedList class is almost identical to the ArrayList:
```java
// Import the LinkedList class
import java.util.LinkedList;

public class Main {
  public static void main(String[] args) {
    LinkedList<String> cars = new LinkedList<String>();
    cars.add("Volvo");
    cars.add("BMW");
    cars.add("Ford");
    cars.add("Mazda");
    System.out.println(cars);
  }
}
```

### ArrayList vs. LinkedList

The LinkedList class is a collection which can contain many objects of the same type, just like the ArrayList.

The LinkedList class has all of the same methods as the ArrayList class because they both implement the List interface. This means that you can add items, change items, remove items and clear the list in the same way.

However, while the ArrayList class and the LinkedList class can be used in the same way, they are built very differently.

### How the ArrayList works

The ArrayList class has a regular array inside it. When an element is added, it is placed into the array. If the array is not big enough, a new, larger array is created to replace the old one and the old one is removed.

### How the LinkedList works

The LinkedList stores its items in "containers." The list has a link to the first container and each container has a link to the next container in the list. To add an element to the list, the element is placed into a new container and that container is linked to one of the other containers in the list.

### When To Use

Use an ArrayList for storing and accessing data, and LinkedList to manipulate data.

### LinkedList Methods

For many cases, the ArrayList is more efficient as it is common to need access to random items in the list, but the LinkedList provides several methods to do certain operations more efficiently:

| Method | Description |
|--------|-------------|
| addFirst() | Adds an item to the beginning of the list. 	
| addLast() | Add an item to the end of the list 	
| removeFirst() | Remove an item from the beginning of the list. 	
| removeLast() | Remove an item from the end of the list 	
| getFirst() | Get the item at the beginning of the list 	
| getLast() | Get the item at the end of the list


## Java HashMap

A "HashMap" is a data structure which stores items in key/value pairs, and you can access them by an index of another type (e.g. a string).

One object is used as a key (index) to another object (value). It can store different types: String keys and Integer values, or the same type, like: String keys and String values:

For example, here I create a HashMap object called capitalCities that will store String keys and String values:
```java
import java.util.HashMap; // import the HashMap class

HashMap<String, String> capitalCities = new HashMap<String, String>();
```

### Add Items

The HashMap class has many useful methods. For example, to add items to it, use the put() method:
```java
// Import the HashMap class
import java.util.HashMap;

public class Main {
  public static void main(String[] args) {
    // Create a HashMap object called capitalCities
    HashMap<String, String> capitalCities = new HashMap<String, String>();

    // Add keys and values (Country, City)
    capitalCities.put("England", "London");
    capitalCities.put("Germany", "Berlin");
    capitalCities.put("Norway", "Oslo");
    capitalCities.put("USA", "Washington DC");
    System.out.println(capitalCities);
  }
}
```

### Other Uses

- To access a value in the HashMap, use the get() method and refer to its key.
- To remove an item, use the remove() method and refer to the key.
- To remove all items, use the clear() method.
- To find out how many items there are, use the size() method.

Keys and values in a HashMap are actually objects. In the examples above, I used objects of type "String". Remember that a String in Java is an object (not a primitive type). To use other types, such as int, you must specify an equivalent wrapper class: Integer. For other primitive types, use: Boolean for boolean, Character for char, Double for double, etc.


## Java HashSet

A HashSet is a collection of items where every item is unique, and it is found in the java.util package.

Here is the syntax to create a HashSet object called cars that will store strings:
```java
import java.util.HashSet; // Import the HashSet class

HashSet<String> cars = new HashSet<String>();
```

### Add Items

The HashSet class has many useful methods. For example, to add items to it, use the add() method:
Example

// Import the HashSet class
import java.util.HashSet;

public class Main {
  public static void main(String[] args) {
    HashSet<String> cars = new HashSet<String>();
    cars.add("Volvo");
    cars.add("BMW");
    cars.add("Ford");
    cars.add("BMW");
    cars.add("Mazda");
    System.out.println(cars);
  }
}

### Other Uses

- To check whether an item exists in a HashSet, use the contains() method.
- To remove an item, use the remove() method.
- To remove all items, use the clear() method.
- To find out how many items there are, use the size() method.

Items in an HashSet are actually objects. In the examples above, I created items (objects) of type "String". Remember that a String in Java is an object (not a primitive type). To use other types, such as int, you must specify an equivalent wrapper class: Integer. For other primitive types, use: Boolean for boolean, Character for char, Double for double, etc:


## Java Iterator

An Iterator is an object that can be used to loop through collections, like ArrayList and HashSet. It is called an "iterator" because "iterating" is the technical term for looping.

To use an Iterator, you must import it from the java.util package.

### Getting an Iterator

The iterator() method can be used to get an Iterator for any collection:
```java
// Import the ArrayList class and the Iterator class
import java.util.ArrayList;
import java.util.Iterator;

public class Main {
  public static void main(String[] args) {

    // Make a collection
    ArrayList<String> cars = new ArrayList<String>();
    cars.add("Volvo");
    cars.add("BMW");
    cars.add("Ford");
    cars.add("Mazda");

    // Get the iterator
    Iterator<String> it = cars.iterator();

    // Print the first item
    System.out.println(it.next());
  }
}
```

### How to Use

- To loop through a collection, use the hasNext() and next() methods of the Iterator.
- Iterators are designed to easily change the collections that they loop through. The remove() method can remove items from a collection while looping.


## Java Wrapper Classes

Wrapper classes provide a way to use primitive data types (int, boolean, etc..) as objects.

The table below shows the primitive type and the equivalent wrapper class:

| Primitive Data Type | Wrapper Class |
|---------------------|---------------|
| byte | Byte
| short | Short
| int | Integer
| long | Long
| float | Float
| double | Double
| boolean | Boolean
| char | Character

Sometimes you must use wrapper classes, for example when working with Collection objects, such as ArrayList, where primitive types cannot be used (the list can only store objects):
```java
ArrayList<int> myNumbers = new ArrayList<int>(); // Invalid

ArrayList<Integer> myNumbers = new ArrayList<Integer>(); // Valid
```

### Creating Wrapper Objects

To create a wrapper object, use the wrapper class instead of the primitive type. To get the value, you can just print the object:
```java
public class Main {
  public static void main(String[] args) {
    Integer myInt = 5;
    Double myDouble = 5.99;
    Character myChar = 'A';
    System.out.println(myInt);
    System.out.println(myDouble);
    System.out.println(myChar);
  }
}
```

Since you're now working with objects, you can use certain methods to get information about the specific object.

For example, the following methods are used to get the value associated with the corresponding wrapper object: intValue(), byteValue(), shortValue(), longValue(), floatValue(), doubleValue(), charValue(), booleanValue().

Another useful method is the toString() method, which is used to convert wrapper objects to strings.

In the following example, I convert an Integer to a String, and use the length() method of the String class to output the length of the "string":
```java
public class Main {
  public static void main(String[] args) {
    Integer myInt = 100;
    String myString = myInt.toString();
    System.out.println(myString.length());
  }
}
```


## Java Exceptions

When executing Java code, different errors can occur: coding errors made by the programmer, errors due to wrong input, or other unforeseeable things.

When an error occurs, Java will normally stop and generate an error message. The technical term for this is: Java will throw an exception (throw an error).

### Java "try" and "catch"

The try statement allows you to define a block of code to be tested for errors while it is being executed.

The catch statement allows you to define a block of code to be executed, if an error occurs in the try block.

The try and catch keywords come in pairs:
```java
try {
  //  Block of code to try
}
catch(Exception e) {
  //  Block of code to handle errors
}
```

### Finally

The finally statement lets you execute code, after try...catch, regardless of the result:
```java
public class Main {
  public static void main(String[] args) {
    try {
      int[] myNumbers = {1, 2, 3};
      System.out.println(myNumbers[10]);
    } catch (Exception e) {
      System.out.println("Something went wrong.");
    } finally {
      System.out.println("The 'try catch' is finished.");
    }
  }
}
```

The output will be:

    Something went wrong.
    The 'try catch' is finished. 


### The "throw" Keyword

The throw statement allows you to create a custom error.

The throw statement is used together with an exception type. There are many exception types available in Java: ArithmeticException, FileNotFoundException, ArrayIndexOutOfBoundsException, SecurityException, etc:
```java
public class Main {
  static void checkAge(int age) {
    if (age < 18) {
      throw new ArithmeticException("Access denied - You must be at least 18 years old.");
    }
    else {
      System.out.println("Access granted - You are old enough!");
    }
  }

  public static void main(String[] args) {
    checkAge(15); // Set age to 15 (which is below 18...)
  }
}
 ```

The output will be:

    Exception in thread "main" java.lang.ArithmeticException: Access denied - You must be at least 18 years old.
            at Main.checkAge(Main.java:4)
            at Main.main(Main.java:12) 


## Java RegEx

"RegEx", or a "regular expression" is a sequence of characters that forms a search pattern. You can use this pattern to filter search results, or describe what you are searching for within a text.

A regular expression can be a single character, or a more complicated pattern.

Regular expressions can be used to perform all types of text search and text replace operations.

Java does not have a built-in Regular Expression class, but we can import the java.util.regex package to work with regular expressions. The package includes the following classes:
- Pattern Class - Defines a pattern (to be used in a search)
- Matcher Class - Used to search for the pattern
- PatternSyntaxException Class - Indicates syntax error in a regular expression pattern

Below is an example of RegEx being used:
```java
import java.util.regex.Matcher;
import java.util.regex.Pattern;

public class Main {
  public static void main(String[] args) {
    Pattern pattern = Pattern.compile("coding", Pattern.CASE_INSENSITIVE);
    Matcher matcher = pattern.matcher("Coding is cool");
    boolean matchFound = matcher.find();
    if(matchFound) {
      System.out.println("Match found");
    } else {
      System.out.println("Match not found");
    }
  }
}
// Outputs Match found
```

**Example Explained**

- In this example, The word "w3schools" is being searched for in a sentence.
- First, the pattern is created using the Pattern.compile() method. The first parameter indicates which pattern is being searched for and the second parameter has a flag to indicates that the search should be case-insensitive. The second parameter is optional.
- The matcher() method is used to search for the pattern in a string. It returns a Matcher object which contains information about the search that was performed.
- The find() method returns true if the pattern was found in the string and false if it was not found.


### Flags

Flags in the compile() method change how the search is performed. Here are a few of them:
- Pattern.CASE_INSENSITIVE - The case of letters will be ignored when performing a search.
- Pattern.LITERAL - Special characters in the pattern will not have any special meaning and will be treated as ordinary characters when performing a search.
- Pattern.UNICODE_CASE - Use it together with the CASE_INSENSITIVE flag to also ignore the case of letters outside of the English alphabet


### Regular Expression Patterns

The first parameter of the Pattern.compile() method is the pattern. It describes what is being searched for.

Brackets are used to find a range of characters:

| Expression | Description |
|-----------|-------------|
| [abc] | Find one character from the options between the brackets
| [^abc] | Find one character NOT between the brackets
| [0-9] | Find one character from the range 0 to 9


### Metacharacters

Metacharacters are characters with a special meaning:

| Metacharacter | Description |
|---------------|-------------|
| \| | Find a match for any one of the patterns separated by \| as in: cat\|dog\|fish
| . | Find just one instance of any character
| ^ | Finds a match as the beginning of a string as in: ^Hello
| $ | Finds a match at the end of the string as in: World$
| \d | Find a digit
| \s | Find a whitespace character
| \b | Find a match at the beginning of a word like this: \bWORD, or at the end of a word like this: WORD\b
| \uxxxx | Find the Unicode character specified by the hexadecimal number xxxx


### Quantifiers

Quantifiers define quantities:

| Quantifier | Description |
|------------|-------------|
| n+ | Matches any string that contains at least one n
| n* | Matches any string that contains zero or more occurrences of n
| n? | Matches any string that contains zero or one occurrences of n
| n{x} | Matches any string that contains a sequence of X n's
| n{x,y} | Matches any string that contains a sequence of X to Y n's
| n{x,} | Matches any string that contains a sequence of at least X n's


## Java Threads

Threads allows a program to operate more efficiently by doing multiple things at the same time.

Threads can be used to perform complicated tasks in the background without interrupting the main program.

### Creating a Thread

There are two ways to create a thread.

It can be created by extending the Thread class and overriding its run() method:
```java
public class Main extends Thread {
  public void run() {
    System.out.println("This code is running in a thread");
  }
}
```

Another way to create a thread is to implement the Runnable interface:
```java
public class Main implements Runnable {
  public void run() {
    System.out.println("This code is running in a thread");
  }
}
```

### Running Threads

If the class extends the Thread class, the thread can be run by creating an instance of the class and call its start() method:
```java
public class Main extends Thread {
  public static void main(String[] args) {
    Main thread = new Main();
    thread.start();
    System.out.println("This code is outside of the thread");
  }
  public void run() {
    System.out.println("This code is running in a thread");
  }
}
```

If the class implements the Runnable interface, the thread can be run by passing an instance of the class to a Thread object's constructor and then calling the thread's start() method:
```java
public class Main implements Runnable {
  public static void main(String[] args) {
    Main obj = new Main();
    Thread thread = new Thread(obj);
    thread.start();
    System.out.println("This code is outside of the thread");
  }
  public void run() {
    System.out.println("This code is running in a thread");
  }
}
```

### Differences between "extending" and "implementing" Threads

The major difference is that when a class extends the Thread class, you cannot extend any other class, but by implementing the Runnable interface, it is possible to extend from another class as well, like: class MyClass extends OtherClass implements Runnable.


### Concurrency Problems

Because threads run at the same time as other parts of the program, there is no way to know in which order the code will run. When the threads and main program are reading and writing the same variables, the values are unpredictable. The problems that result from this are called concurrency problems.

A code example where the value of the variable amount is unpredictable:
```java
public class Main extends Thread {
  public static int amount = 0;

  public static void main(String[] args) {
    Main thread = new Main();
    thread.start();
    System.out.println(amount);
    amount++;
    System.out.println(amount);
  }

  public void run() {
    amount++;
  }
}
```

To avoid concurrency problems, it is best to share as few attributes between threads as possible. If attributes need to be shared, one possible solution is to use the isAlive() method of the thread to check whether the thread has finished running before using any attributes that the thread can change.

Use isAlive() to prevent concurrency problems:
```java
public class Main extends Thread {
  public static int amount = 0;

  public static void main(String[] args) {
    Main thread = new Main();
    thread.start();
    // Wait for the thread to finish
    while(thread.isAlive()) {
    System.out.println("Waiting...");
  }
  // Update amount and print its value
  System.out.println("Main: " + amount);
  amount++;
  System.out.println("Main: " + amount);
  }
  public void run() {
    amount++;
  }
}
```

## Java Lambda

A lambda expression is a short block of code which takes in parameters and returns a value. Lambda expressions are similar to methods, but they do not need a name and they can be implemented right in the body of a method.

### Syntax

The simplest lambda expression contains a single parameter and an expression:

    parameter -> expression

To use more than one parameter, wrap them in parentheses:

    (parameter1, parameter2) -> expression

Expressions are limited. They have to immediately return a value, and they cannot contain variables, assignments or statements such as if or for. In order to do more complex operations, a code block can be used with curly braces. If the lambda expression needs to return a value, then the code block should have a return statement.

    (parameter1, parameter2) -> { code block }


### Using Lambda Expressions

Lambda expressions are usually passed as parameters to a function, however they can also be stored in variables if the variable's type is an interface which has only one method, such as the "Consumer" method. To use a lambda expression in a method, the method should have a parameter with a single-method interface as its type. Calling the interface's method will run the lambda expression:
```java
interface StringFunction {
  String run(String str);
}

public class Main {
  public static void main(String[] args) {
    StringFunction exclaim = (s) -> s + "!";
    StringFunction ask = (s) -> s + "?";
    printFormatted("Hello", exclaim);
    printFormatted("Hello", ask);
  }
  public static void printFormatted(String str, StringFunction format) {
    String result = format.run(str);
    System.out.println(result);
  }
}
```





## Footnote

This has been my Java notes for Methods & Classes, please use at your leisure for studying or reference. I hope they are of use :)

Aidan Butler - https://aidan.vip