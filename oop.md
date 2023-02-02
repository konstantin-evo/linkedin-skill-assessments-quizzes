## Object-Oriented Programming (OOP)

#### Q1. What is an example of dynamic binding?

- [ ] any method
- [ ] method overloading
- [x] method overriding
- [ ] compiling

#### Q2. When does static binding happen?

- [ ] only when you export
- [ ] both at compile time and runtime
- [x] at compile time
- [ ] at runtime

#### Explanation

Connecting a method call to the method body is known as binding.

There are two types of binding:

1. Static Binding (also known as Early Binding).
2. Dynamic Binding (also known as Late Binding).

##### Dynamic Binding

In Dynamic binding compiler doesn't decide the method to be called.

Overriding is a perfect example of dynamic binding. In overriding both parent and child classes have the same method.

```java
public class GFG {

    // Static nested inner class
    // Class 1
    public static class superclass {

        // Method of inner class 1
        void print() {
            System.out.println("print in superclass is called");
        }
    }

    // Static nested inner class
    // Class 2
    public static class subclass extends superclass {

        // Method of inner class 2
        @Override
        void print() {
            System.out.println("print in subclass is called");
        }
    }

    // Method inside main class
    public static void main(String[] args) {

        // Creating object of inner class 1
        // with reference to constructor of super class
        superclass A = new superclass();

        // Creating object of inner class 1
        // with reference to constructor of sub class
        superclass B = new subclass();

        // Calling print() method over above objects
        A.print();
        B.print();
    }
}
```

Output:

```
print in superclass is called
print in subclass is called
```

**Output Explanation**: Here the output differs. But why? Let’s break down the code and understand it thoroughly.

* Methods are not static in this code.
* During compilation, the compiler has no idea as to which print has to be called since the compiler goes only by referencing variable not by the type
  of object, and therefore the binding would be delayed to runtime and therefore the corresponding version of the print will be called based on type
  on an object.

##### Static Binding

The binding which can be resolved at compile time by the compiler is known as static or early binding.

The binding of all the `static`, `private`, and `final` methods is done at compile-time.

```java
class NewClass {

    // Static nested inner class
    // Class 1
    public static class superclass {

        // Method of inner class
        static void print() {
            System.out.println("print() in superclass is called");
        }
    }

    // Static nested inner class
    // Class 2
    public static class subclass extends superclass {

        // Method of inner class
        static void print() {
            System.out.println("print() in subclass is called");
        }
    }

    public static void main(String[] args) {

        // Creating objects of static inner classes
        // inside main() method
        superclass A = new superclass();
        superclass B = new subclass();

        // Calling method over above objects
        A.print();
        B.print();
    }
}
```

Output:

```
print() in superclass is called
print() in superclass is called
```

**Output Explanation**: As you can see, in both cases the print method of the superclass is called. Let us discuss how this happens.

1. We have created one object of subclass and one object of the superclass with the reference of the superclass.
2. Since the print method of the superclass is static, the compiler knows that it will not be overridden in subclasses and hence compiler knows during
   compile time which print method to call and hence no ambiguity.

| Static Binding                                                           | Dynamic Binding                                                    |
|--------------------------------------------------------------------------|--------------------------------------------------------------------|
| It takes place at compile time for which is referred to as early binding | It takes place at runtime so do it is referred to as late binding. |
| It uses overloading more precisely operator overloading method           | It uses overriding methods.                                        |

#### Q3.1 Why would you create an abstract class, if it can have no real instances?

- [x] to avoid redundant coding in children
- [ ] to explore a hypothetical class
- [ ] to prevent unwanted method implementation
- [ ] to reserve memory for an unspecified class type

#### Q3.2 Why would you create an abstract class, if it can have no real instances?

- [x] to have common behavior in derived classes
- [ ] to explore a hypothetical class
- [ ] to prevent unwanted method implementation
- [ ] to reserve memory for an unspecified class type

#### Explanation

An abstract class cannot be instantiated. The purpose of an abstract class is to provide a common definition of a base class that multiple derived
classes can share.

Features of Abstract Class:

1. Template
2. Loose Coupling
3. Code Reusability
4. Abstraction
5. Dynamic Resolution

**Template**

The abstract class in Java enables the best way to execute the process of data abstraction by providing the developers with the option of hiding the
code implementation. It also presents the end-user with a template that explains the methods involved.

**Loose Coupling**

Data abstraction in Java enables loose coupling, by reducing the dependencies at an exponential level.

**Code Reusability**

Using an abstract class in the code saves time. We can call the abstract method wherever the method is necessary. Abstract class avoids the process of
writing the same code again.

**Abstraction**

Data abstraction in Java helps the developers hide the code complications from the end-user by reducing the project's complete characteristics to only
the necessary components.

**Dynamic Resolution**

Using the support of dynamic method resolution, developers can solve multiple problems with the help of one abstract method.

#### Q4. What is multilevel inheritance?

- [ ] a class that does not have more than one parent.
- [ ] a class not derived from another derived object.
- [ ] not doubling single-level inheritance.
- [x] classes derived from other derived classes.

#### Explanation

In Multi-Level Inheritance in Java, a class extends to another class that is already extended from another class.

For example, if there is a class A that extends class B and class B extends from another class C, then this scenario is known to follow Multi-level
Inheritance.

A real-life example would be a child inheriting from his father who inherited from his grandfather. This is an example of a multilevel inheritance
where C inherits from B and B inherits from A.

#### Q5. Can you have two classes with the same name in the same project?

- [ ] No, you cannot.
- [ ] Yes, as long as their constructors are different.
- [ ] Yes, as long as their methods are different.
- [x] Yes, as long as they are in different namespaces.

#### Explanation

With programmers worldwide writing classes and interfaces using the Java programming language, it is likely that many programmers will use the same
name for different types.

The compiler allows both classes to have the same name if they are in different packages.

**Link**: [Handle Classes With the Same Name in Java](https://www.baeldung.com/java-classes-same-name)

#### Q6. What is the best reason to use a design pattern?

- [x] It will result in code that is more extensible and maintainable
- [ ] It will result in a more compact product.
- [ ] It will speed initial development.
- [ ] It will allow you to add that design pattern to your resume.

#### Explanation

Design patterns are well-proven solutions for solving the specific problem.

Design patterns ensures your software is modular and easy to maintain, debug and refactor.

Using it prevents your code from becoming rigid and fragile, which helps you build long-lasting software.

#### Q7. What is encapsulation?

- [ ] defining classes by focusing on what is important for a purpose
- [x] hiding the data and implementation details within a class
- [ ] making all methods private
- [ ] using words to define classes

#### Explanation

**Formal**:

Encapsulation refers to the bundling of data with the methods that operate on that data.

Encapsulation is used to hide the values or state of a structured data object inside a class, preventing unauthorised parties' direct access to them.

**Informal**:

Say we have a program. It has a few logically different objects which communicate with each other — according to the rules defined in the program.

Encapsulation is achieved when each object keeps its state private, inside a class. Other objects don’t have direct access to this state.
Instead, they can only call a list of Public functions — called methods.

So, the object manages its own state via methods — and no other class can touch it unless explicitly allowed. If you want to communicate with the
object, you should use the methods provided. But by default, you can’t change the state.

Let’s say we’re building a tiny Sims game. There are people and there is a cat. They communicate with each other. We want to apply encapsulation, so
we encapsulate all “cat” logic into a Cat class. It may look like this:

![oop-encapsulation.png](src%2Foop%2Foop-encapsulation.png)

You can feed the cat. But you can’t directly change how hungry the cat is.

#### Q8. What is an IS-A relationship?

- [ ] It implies encapsulation.
- [ ] A superclass object has an IS-A relationship with its subclass.
- [ ] It implies a virtual method.
- [x] A subclass object has an IS-A relationship with its superclass or interface

#### Explanation

A relationship in Java means different relations between two or more classes. For example, if a class Bulb inherits another class Device, then we can
say that Bulb is having is-a relationship with Device, which implies Bulb is a device.

In Java, we have two types of relationship:

1. `Is-A` relationship: Whenever one class inherits another class, it is called an IS-A relationship.
2. `Has-A` relationship: Whenever an instance of one class is used in another class, it is called HAS-A relationship.

IS-A Relationship is wholly related to Inheritance. For example – a kiwi is a fruit; a bulb is a device.

* IS-A relationship can simply be achieved by using `extends` Keyword.
* IS-A relationship is additionally used for code reusability in Java and to avoid code redundancy.
* IS-A relationship is unidirectional, which means we can say that a bulb is a device, but vice versa; a device is a bulb is not possible since all
  the devices are not bulbs.
* IS-A relationship is tightly coupled, which means changing one entity will affect another entity.

#### Q9. You want a method with behavior similar to a virtual method--it is meant to be overridden --expect that it does not have a method body. It just has a method signature. What kind of method should you use?

- [x] an abstract method
- [ ] a public internal method
- [ ] an internal method
- [ ] a protected internal method

#### Explanation

In object-oriented programming, abstraction is defined as hiding the unnecessary details (implementation) from the user and to focus on essential
details (functionality). It increases the efficiency and thus reduces complexity.

In Java, abstraction can be achieved using abstract classes and methods.

A method declared using the `abstract` keyword within an abstract class and does not have a definition (implementation) is called an abstract method.

Abstract method is also called subclass responsibility as it doesn't have the implementation in the super class. Therefore, a subclass must override
it to provide the method definition.

Example:

```java
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

**Note**: Q10 - Q12 questions have one explanation.

#### Q10. Which code creates a new object from the Employee class?

- [ ] Employee currentEmployee = Employee.Create();
- [x] Employee currentEmployee = new Employee();
- [ ] Employee currentEmployee;
- [ ] Employee currentEmployee = Employee.New();

#### Q11. Which type of constructor cannot have a return type?

- [ ] default
- [ ] copy
- [ ] parameterized
- [x] Constructors do not have a return type

#### Q12.1 When is a constructor executed?

- [x] when an object is created from a class using the `new` keyword
- [ ] when a class is defined using the class keyword
- [ ] every time an object is referenced
- [ ] when an object is created from a class using the `create` keyword

#### Q12.2 When is a constructor executed?

- [x] when an object is created from a class
- [ ] when a class is defined using the class keyword
- [ ] every time an object is referenced
- [ ] when an object is created from a class using the `create` keyword

#### Explanation

A constructor in Java is a special method that is used to initialize objects.

* The constructor name must match the class name
* The constructor cannot have a return type (like void).
* The constructor is called when the object is created.
* The constructor can be used to set initial values for object attributes:

All classes have constructors by default: if you do not create a class constructor yourself, Java creates one for you. However, then you are not able
to set initial values for object attributes.

Example:

```java
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

#### Q14. If a local class is defined in a function, what is true for an object of that class?

- [x] The object can be accessed, declared, and used locally in that function.
- [ ] The object must be declared inside any other function.
- [ ] The object is temporarily accessible outside the function.
- [ ] The object can call all the other class members anywhere in the program.

#### Explanation

A class i.e., created inside a method, is called local inner class in java.

Local Inner Classes are the inner classes that are defined inside a block. Generally, this block is a method body. Sometimes this block can be a `for`
loop, or an `if` clause.

Local Inner classes are not a member of any enclosing classes. They belong to the block they are defined within, due to which local inner classes
cannot have any access modifiers associated with them. However, they can be marked as final or abstract. These classes have access to the fields of
the class enclosing it.

Example:

```java
public class Outer {
    private void getValue() {
        int sum = 20;

        // Local inner Class inside method
        class Inner {
            public int divisor;
            public int remainder;

            public Inner() {
                divisor = 4;
                remainder = sum % divisor;
            }

            private int getDivisor() {
                return divisor;
            }

            private int getRemainder() {
                return sum % divisor;
            }

            private int getQuotient() {
                System.out.println("Inside inner class");
                return sum / divisor;
            }
        }

        Inner inner = new Inner();
        System.out.println("Divisor = " + inner.getDivisor());
        System.out.println("Remainder = " + inner.getRemainder());
        System.out.println("Quotient = " + inner.getQuotient());
    }

    public static void main(String[] args) {
        Outer outer = new Outer();
        outer.getValue();
    }
}
```

Output:

```
Divisor = 4
Remainder = 0
Inside inner class
Quotient = 5
```

**Note**: A local class can access local variables and parameters of the enclosing block that are effectively final.

#### Q15. Which two blocks are used to handle and check errors?

- [ ] do and check
- [ ] catching and trying
- [x] try and catch
- [ ] do and while

#### Explanation

**Note**: from my point of view there is a syntax error in the question.

All exception classes are subtypes of the `java.lang.Exception` class.

The exception class is a subclass of the `Throwable` class.

Other than the `Exception` class there is another subclass called `Error` which is derived from the `Throwable` class.

**Errors are abnormal conditions that happen in case of severe failures, these are not handled by the Java programs.**

**Example**: JVM is out of memory. Normally, programs can’t recover from errors.

![java-exception.png](src%2Foop%2Fjava-exception.png)

---

Java `try` block is used to enclose the code that might throw an exception. It must be used within the method.

If an exception occurs at the particular statement in the try block, the rest of the block code will not execute.

Java try block must be followed by either `catch` or `finally` block.

Java `catch` block is used to handle the Exception by declaring the type of exception within the parameter. The declared exception must be the parent
class `Exception` or the generated exception type.

Example:

```java
public class TryCatchExample3 {

    public static void main(String[] args) {
        try {
            int data = 50 / 0; //may throw exception   
            // if exception occurs, the remaining statement will not exceute  
            System.out.println("rest of the code");
        }
        // handling the exception   
        catch (ArithmeticException e) {
            System.out.println(e);
        }

    }

}  
```

#### Q16. Why would you implement composition using an id instead of a reference?

- [ ] It makes it easier to save the entity.
- [x] all of these answers
- [ ] It can make the entity retrieval more efficient
- [ ] It minimizes coupling.

#### Explanation

**Note**: Composition in programming languages and databases can be implemented in different ways, and it is not possible to give an unambiguous answer
to the question without additional conditions.

---

The composition is a design technique in java to implement a `has-a` relationship.

Java Inheritance is used for code reuse purposes and the same we can do by using composition. The composition is achieved by using an instance
variable that refers to other objects.

**Real-life Example**: Library system

Let’s understand the composition in Java with the example of books and library. In this example, we create a class Book that contains data members
like author, and title and create another class Library that has a reference to refer to the list of books. A library can have no. of books on the
same or different subjects. So, If the Library gets destroyed then All books within that particular library will be destroyed. i.e., books can not
exist without a library. The relationship between the library and books is composition.

#### Q17. Which statement best describes the method of inheritance in OOP?

- [x] Inheritance describes the ability to create new classes based on an existing class.
- [ ] Inheritance means that a group of related properties, methods, and other members are treated as a single unit or object.
- [ ] Inheritance forces a class to have a single responsibility from only one parent.
- [ ] Inheritance means that you will never have multiple classes that can be used interchangeably, even though each class implements the same
  properties or methods in different ways.

#### Q18. Which type of inheritance, when done continuously, is similar to a tree structure?

- [ ] multilevel
- [ ] hierarchical and multiple
- [x] hierarchical
- [ ] multiple

#### Explanation

**Formal**:

In object–oriented programming, inheritance is the mechanism of basing a class upon another class, retaining similar implementation.

Also defined as deriving new subclasses from existing ones such as superclass and then forming them into a hierarchy of classes (tree structure).

**Informal**:

Objects (or Classes) are often very similar and share common logic, but they’re not entirely the same.

So how do we reuse the common logic and extract the unique logic into a separate class? One way to achieve this is inheritance. It means that you
create a child class by deriving from another parent class.

This way, we form a hierarchy. The child class reuses all fields and methods of the parent class “common part” and can implement its own “unique
part”.

![oop-inheritance.png](src%2Foop%2Foop-inheritance.png)

A private teacher is a type of teacher and any teacher is a type of Person.

If our program needs to manage public and private teachers, but also other types of people like students, we can implement this class hierarchy.

This way, each class adds only what is necessary for it while reusing common logic with the parent classes.

#### Q19. Which statement is true?

- [ ] A default parameter's constructor is not equivalent to the default constructor
- [ ] A default constructor is inherited from a parent class
- [x] A default constructor can be called explicitly
- [ ] A default constructor cannot be defined by the coder

#### Explanation

**Note**: according to the script, the correct answer is the first, but I disagree.

---

**Default Constructor** – A constructor that accepts no parameter is called Default Constructor.

It is not necessary to have a constructor block in your class definition. If you don’t explicitly write a constructor, the compiler automatically
inserts one for you.

```java
public class Demo {
    Demo() {
        System.out.println("I am a constructor");
    }

    public static void main(String args[]) {
        Demo obj = new Demo();
    }
}
```

**Parameterized Constructor** – A constructor is called Parameterized Constructor when it accepts a specific number of parameters. To initialize data
members of a class with distinct values.

```java
public class Demo {
    String studentName;
    int studentAge;

    //constructor
    Demo(String name, int age) {
        studentName = name;
        studentAge = age;
    }

    void display() {
        System.out.println(studentName + " " + studentAge);
    }

    public static void main(String args[]) {
        Edureka myObj = new Edureka("Manan", 19);
        myObj.display();
    }
}
```

#### Q20. Which of the following is NOT an advantage of using getters and setters?

- [x] Getters and setters can speed up compilation.
- [ ] Getters and setters provide encapsulation of behavior.
- [ ] Getters and setters provide a debugging point for when a property changes at runtime.
- [ ] Getters and setters permit different access levels.

#### Explanation

The meaning of Encapsulation, is to make sure that "sensitive" data is hidden from users.

To achieve this, you must:

1. Declare class variables as private
2. Provide public `get` and `set` methods to access and update the value of a private variable

Advantages:

1. Better control of class attributes and methods
2. Class attributes can be made read-only (if you only use the get method), or write-only (if you only use the set method)
3. Flexible: the programmer can change one part of the code without affecting other parts
4. Provide a debugging point for when a property changes at runtime
5. Increased security of data

#### Q21. In context of OOP, what is association?

- [x] Association is a relationship where all objects have their own life cycle and there is no owner.
- [ ] Association is the process where model elements cooperate to provide higher-level behavior.
- [ ] Association is whole/part relationship where one object is composed of one or more other objects, each of which is considered a part of the
  whole.
- [ ] Association is where all objects have their own life cycle, but there is ownership, and child objects can not belong to another parent object.

#### Explanation

Association in Java defines the connection between two classes that are set up through their objects.

Association manages one-to-one, one-to-many, and many-to-many relationships.

Association shows how objects communicate with each other and how they use the functionality and services provided by that communicated object.

In Java, two types of Association are possible:

* IS-A Association
* HAS-A Association
    * Aggregation
    * Composition

![association-in-java.png](src%2Foop%2Fassociation-in-java.png)

**IS-A Association**

The IS-A Association is also referred to as Inheritance.

**HAS-A Association**

The HAS-A Association is further classified into two parts, i.e., Aggregation and Composition.

**Aggregation**

In Java, the Aggregation association defines the HAS-A relationship. Aggregation follows the one-to-one or one-way relationship. If two entities are
in the aggregation composition, and one entity fails due to some error, it will not affect the other entity.

Let's take the example of a toy and its battery. The battery belongs to a toy, and if the toy breaks and deletes from our database, the battery will
still remain in our database, and it may still be working. So in Aggregation, objects always have their own lifecycles when the ownership exists
there.

**Composition**

A restricted form of the Aggregation where the entities are strongly dependent on each other. Unlike Aggregation, Composition represents the part-of
relationship. When there is an aggregation between two entities, the aggregate object can exist without the other entity, but in the case of
Composition, the composed object can't exist.

Let's take an example to understand the concept of Composition.

We create a class Mobile that contains variables, i.e., name, ram and rom. We also create a class MobileStore that has a reference to refer to the
list of mobiles. A mobile store can have more than one mobile. So, if a mobile store is destroyed, then all mobiles within that particular mobile
store will also be destroyed because mobiles cannot exist without a mobile store. The relationship between the mobile store and mobiles is
Composition.

#### Q22. How are user stories different from use cases?

- [x] User Stories are shorter and less detailed.
- [ ] User stories are more accurate.
- [ ] User stories are more detailed and structured.
- [ ] User storied are more anecdotal and personal.

#### Explanation

**A user story** is an informal, general explanation of a software feature written from the perspective of the end user. Its purpose is to articulate
how a software feature will provide value to the customer.

**A Use case** is a written description of how users will perform tasks on your website. It outlines, from a user's point of view, a system's behavior
as it responds to a request. Each use case is represented as a sequence of simple steps, beginning with a user's goal and ending when that goal is
fulfilled.

#### Q23. Which type of inheritance must be used so that the resultant is hybrid?

- [x] multiple
- [ ] any type of inheritance
- [ ] multilevel
- [ ] hierarchical

#### Explanation

Inheritance types:

* **Single Inheritance** is where a derived class inherits properties and behaviour from a single base class. Example: Class A → Class B.
* **Hierarchical Inheritance** is where more than one derived class is created from a single base class. Example: Class A → Class B → Class C.
* **Multiple Inheritance** is for deriving a class from multiple base classes. Here, the child objects programmers create will have combined aspects
  of characteristics and features from multiple parent classes. These objects do follow their hierarchies of base classes.
* **Multilevel Inheritance** is where a child class is derived from another derived class. This feature carries combined aspects of multiple classes
  and follows their hierarchies.
* **Hybrid Inheritance** is a heterogeneous feature of using multiple inheritances. Here a child class is derived from one or more combinations of
  single, hierarchical, and multilevel inheritances. This inheritance is adopted for programs to mix different types of inheritance; for example, when
  mixing a single inheritance with multiple inheritances or maybe a situation when multiple inheritances are mixed within a single program.

![inheritance-in-java.png](src%2Foop%2Finheritance-in-java.png)

---

Hybrid Inheritance in Java is a combination of inheritance. In this type of Inheritance, more than one kind of inheritance is observed.

For example, if we have class A and class B that extend class C and then there is another class D that extends class A, then this type of Inheritance
is known as Hybrid Inheritance.

A hybrid inheritance combines more than two inheritance types, such as multiple and single. In essence, it combines straightforward,
numerous, and hierarchical inheritances.

Interfaces are the sole means through which it is possible because Java does not enable multiple inheritance.

#### Q24. A language that does not support polymorphism but supports classes is considered what?

- [x] an object-based language
- [ ] a class-based language
- [ ] a procedure-oriented language
- [ ] if classes are supported, polymorphism will be supported

#### Explanation

The languages which support classes but doesn't support polymorphism, are known as object-based languages.

#### Q25. Two classes combine private data members and provide public member functions to access and manipulate those data members. Where is abstraction used?

- [ ] Abstraction is using a private access specifier for the data members.
- [x] Abstraction is using public member functions to access and manipulate the data members.
- [ ] Abstraction is using the class concept with both data members and member functions.
- [ ] There is insufficient information to decide where abstraction is being used.

#### Explanation

In object-oriented design, programs are often extremely large and separate objects communicate with each other a lot. So maintaining a large codebase
like this for years – with changes along the way – is difficult. Abstraction is a concept aiming to ease this problem.

Applying abstraction means that each object should only expose a high–level mechanism for using it. This mechanism should hide internal implementation
details. It should only reveal operations relevant for the other objects.

Think – a coffee machine. It does a lot of stuff and makes quirky noises under the hood. But all you have to do is put in coffee
and press a button.

Preferably, this mechanism should be easy to use and should rarely change over time. Think of it as a small set of public methods which any other
class can call without “knowing” how they work.

Another real-life example of abstraction?

![oop-abstraction.png](src%2Foop%2Foop-abstraction.png)

Cell phones are complex. But using them is simple.

#### Q26. What are the five Creational Design patterns by the Gang of Four ?

- [ ] Observer, State, Strategy, Template Method, and Visitor.
- [ ] Composite, Visitor, State, Prototype, and Singleton.
- [ ] Composite, Builder, Factory Method, Prototype, and Singleton.
- [x] Abstract Factory, Builder, Factory Method, Prototype, and Singleton.

#### Explanation

Creational Design Patterns:

1. **Abstract Factory** allows the creation of objects without specifying their concrete type.
2. **Builder** uses to create complex objects.
3. **Factory Method** creates objects without specifying the exact class to create.
4. **Prototype** creates a new object from an existing object.
5. **Singleton** ensures only one instance of an object is created.

#### Q27. In multilevel inheritance, one class inherits how many classes?

- [x] one class only
- [ ] two classes
- [ ] as many classes as required
- [ ] at least two classes

#### Explanation

Inheritance types:

* **Single Inheritance** is where a derived class inherits properties and behaviour from a single base class. Example: Class A → Class B.
* **Hierarchical Inheritance** is where more than one derived class is created from a single base class. Example: Class A → Class B → Class C.
* **Multiple Inheritance** is for deriving a class from multiple base classes. Here, the child objects programmers create will have combined aspects
  of characteristics and features from multiple parent classes. These objects do follow their hierarchies of base classes.
* **Multilevel Inheritance** is where a child class is derived from another derived class. This feature carries combined aspects of multiple classes
  and follows their hierarchies.
* **Hybrid Inheritance** is a heterogeneous feature of using multiple inheritances. Here a child class is derived from one or more combinations of
  single, hierarchical, and multilevel inheritances. This inheritance is adopted for programs to mix different types of inheritance; for example, when
  mixing a single inheritance with multiple inheritances or maybe a situation when multiple inheritances are mixed within a single program.

![inheritance-in-java.png](src%2Foop%2Finheritance-in-java.png)

The multi-level inheritance includes the involvement of at least two or more than two classes. One class inherits the features from a parent class and
the newly created subclass becomes the base class for another new class.

#### Q28. if an object is passed by reference, the changes made in the function are reflected \_.

- [x] to the main object of the caller function, too
- [ ] on the caller function object and also the called function object
- [ ] on the copy of the object that is made during the pass
- [ ] only in the local scope of the called function

#### Explanation

All object references in Java are passed by value. This means that a copy of the value will be passed to a method. But the trick is that passing a
copy of the value also changes the real value of the object.

To understand why, start with this example:

```java
public class ObjectReferenceExample {

    public static void main(String... doYourBest) {
        Simpson simpson = new Simpson();
        transformIntoHomer(simpson);
        System.out.println(simpson.name);
    }

    static void transformIntoHomer(Simpson simpson) {
        simpson.name = "Homer";
    }

}

class Simpson {
    String name;
}
```

The reason is that Java object variables are simply references that point to real objects in the memory heap.

Therefore, even though Java passes parameters to methods by value, if the variable points to an object reference, the real object will also be
changed.

#### Q29. What is a method?

- [ ] a set of instructions designed to perform a frequently used operation within a program and return no values
- [x] the exact same thing as a function and subroutine
- [ ] a set of variables that can change over time
- [ ] a procedure associated with data and behaviour

#### Explanation

A method in object-oriented programming (OOP) is a procedure associated with a message and an object.

* Function — a set of instructions that perform a task.
* Method — a set of instructions that are associated with an object.

#### Q30. A mobile phone is made up of components such as a motherboard, camera, and sensors. The motherboard represents all the functions of a phone, the display shows the display only, and the phone is represented as a whole. Which of the following has the highest level of abstraction?

- [ ] camera
- [ ] display
- [ ] motherboard
- [x] mobile phone

**Link**: [Association in Java](https://www.javatpoint.com/association-in-java)

#### Q31. Which class has the highest degree of abstraction in a multilevel inheritance relationship of five levels?

- [ ] the class at the third level
- [x] the class at the first level
- [ ] All have the same degree of abstraction.
- [ ] the class at the second level

#### Q32. Which is NOT one of the basic types of inheritance?

- [ ] multilevel inheritance
- [x] double inheritance
- [ ] single inheritance
- [ ] hierarchical inheritance

#### Explanation

Inheritance types:

* **Single Inheritance** is where a derived class inherits properties and behaviour from a single base class. Example: Class A → Class B.
* **Hierarchical Inheritance** is where more than one derived class is created from a single base class. Example: Class A → Class B → Class C.
* **Multiple Inheritance** is for deriving a class from multiple base classes. Here, the child objects programmers create will have combined aspects
  of characteristics and features from multiple parent classes. These objects do follow their hierarchies of base classes.
* **Multilevel Inheritance** is where a child class is derived from another derived class. This feature carries combined aspects of multiple classes
  and follows their hierarchies.
* **Hybrid Inheritance** is a heterogeneous feature of using multiple inheritances. Here a child class is derived from one or more combinations of
  single, hierarchical, and multilevel inheritances. This inheritance is adopted for programs to mix different types of inheritance; for example, when
  mixing a single inheritance with multiple inheritances or maybe a situation when multiple inheritances are mixed within a single program.

![inheritance-in-java.png](src%2Foop%2Finheritance-in-java.png)

---

Data abstraction is the process of hiding certain details and showing only essential information to the user.

Abstraction can be achieved with either abstract classes or interfaces.

We use abstraction to hide certain details and only show the important details of an object so the first class has the highest degree of abstraction.

#### Q33. Why is code duplication so insidious?

- [ ] The duplication uses unnecessary space.
- [x] One has to maintain all the duplicates.
- [ ] Duplication can cause intellectual property concerns.
- [ ] Duplication is easy to hide.

#### Explanation

Duplicate code as the name suggests is a repetition of a line or a block of code in the same file. People might consider code duplication acceptable
but in reality, it poses greater problems to your software than what you may have thought.

3 reasons why code duplication is harmful:

1. Duplicate code makes your program lengthy and bulky
2. Duplication decreases your code quality
3. Shotgun Surgery

**Duplicate code makes your program lengthy and bulky**

Many programmers feel that if the software is working properly there is no reason to fix code duplications. You forget that you are just
un-necessarily making your software bulky. Your argument can be that a few blocks of code would just use a few milliseconds to run. Which we agree to
but only if you mean to use your software a few times. Code written for commercial purposes or web-applications is executed thousands and millions of
times every minute.

Each millisecond of delay will contribute to greater delay and greater space requirements at the user’s local machine as well as your servers. Having
well-written code with the least duplications will make sure that your program runs faster and occupy less space. Also, age has gone when people
didn't
care to wait. Now everything needs to be fast and smooth.

**Duplication decreases your code quality**

Have duplication is fine, as long as you plan to throw your software away soon. Code quality is a necessity to make your software survive for long.

Having duplicate code will make your code smelly and increases technical debt associated with it. The cost of repair of this debt is the amount of
capital and time required to pay to a developer to simplify or de-duplicate it. The interest is the decreased productivity of developers.

Sometimes it’s impossible to refactor a duplicate code block but the aim should be to decrease as much technical debt. It helps to make your code of a
higher quality.

**Shotgun Surgery**

Suppose you write buggy code. You do a code review to find out the issue and then fix it. Now replace this scenario of buggy code with duplicate buggy
code. You now have to fix every location that code is, losing your time, efficiency and sometimes temper. This situation is called inverse shotgun
surgery and is pretty nasty for any developer.

#### Q34. When and how often is a static constructor called?

- [ ] It is called initially when an object is created and called with every new object instance.
- [ ] It is called when an object is destroyed and only one time.
- [x] It is called initially when an object is created and only one time.
- [ ] It is created at time when the object is discarded.

#### Q35. What is the purpose of static constructor?

- [x] to initialize all the members with static value
- [ ] to delete the static members when not required
- [ ] to initialize the static members of class
- [ ] to clear all the static members' initialized values

#### Explanation

In Java, a constructor is not allowed to be abstract, final or static. So, there is no static constructor in Java.

A static constructor used to initialize static data means the specified task will execute only once throughout the program. Usually, a static
constructor is automatically called when the first instance is generated, or any static member is referenced. The static constructor is explicitly
declared by using a `static` keyword. However, the static constructor is not allowed in Java.

Some key features of the static constructor are as follows:

* It will not take parameters or access modifiers.
* A specific class can have only one static constructor.
* It does not allow inheritance or overloading.
* It is invoked automatically, can not be called directly or explicitly.
* If the value of static fields is not initialized, it will initialize to default values.

#### Q36. What does the code shown below demonstrate, and why?

```cpp
   static void Multiply(int num1, int num2) {};
   static void Multiply(double num1, double num2, double num3) {};
   static void Multiply(float num1, float num2) {};
```

- [ ] polymorphism, because each method can perform different task
- [ ] method overriding, because it displays the same method name, different or same parameters, and same return type
- [x] method overloading, because it allows the creation of several methods with the same name, which differ by the type of input via parameter
- [ ] method overriding, because it displays the same method name, different parameters, and same return type

#### Explanation

Method overloading in java is a feature that allows a class to have more than one method with the same name, but with different parameters.

Java supports method overloading through two mechanisms:

1. By changing the number of parameters
2. By changing the data type of parameters

Benefits of using Method Overloading

* Method overloading increases the readability of the program.
* This provides flexibility to programmers so that they can call the same method for different types of data.
* This makes the code look clean.
* This reduces the execution time because the binding is done in compilation time itself.
* Method overloading minimises the complexity of the code.

```java
class Demo {
    void multiply(int a, int b) {
        System.out.printIn("Result is" + (a * b));
    }

    void multiply(int a, int b, int c) {
        System.out.printIn("Result is" + (a * b * c));
    }

    public static void main(String[] args) {
        Demo obj = new Demo();
        obj.multiply(8, 5);
        obj.multiply(4, 6, 2);
    }
}
```

#### Q37. What are CRC Cards?

- [ ] Code Responsibility Collection cards are a brainstorming tool used in the design of procedural software
- [x] Class Responsibility collaboration cards are a brainstorming tool used in the design of oop software
- [ ] Code Responsibility Correction cards are tools used for debugging
- [ ] Code Responsibility Correction cards are tools for modeling

#### Explanation

CRC cards are brainstorming tools used for conceptual modeling and detailed design. Using CRC cards is an activity that combines aspects of
role-playing games and object-oriented design.

CRC stands for:

* **Class** refers to a collection of similar objects or (more commonly in product design) people
* **Responsibilities** are something a class knows or an action they perform
* **Collaborator** is another class that the original class will need to work with to achieve their desired goals.

![crc-cards.jpeg](src%2Foop%2Fcrc-cards.jpeg)

#### Q38. How are contents of a composition different from those of aggregation?

- [ ] if one element of an aggregation is dereferenced, all its elements are eligible for garbage collection
- [x] if a composition dies, the contents die
- [ ] the contents of a composition are all siblings
- [ ] an aggregation contains only abstract classes

#### Q39. Which statement about compositions and aggregations is true?

- [ ] if one element of an aggregation is dereferenced, all its elements are eligible for garbage collection
- [x] if a composition dies, the contents die
- [ ] the contents of a composition are all siblings
- [ ] an aggregation contains only abstract classes

#### Explanation

Association in Java defines the connection between two classes that are set up through their objects.

In Java, two types of Association are possible:

* IS-A Association
* HAS-A Association
    * Aggregation
    * Composition

![association-in-java.png](src%2Foop%2Fassociation-in-java.png)

**Aggregation**

In Java, the Aggregation association defines the HAS-A relationship. Aggregation follows the one-to-one or one-way relationship. If two entities are
in the aggregation composition, and one entity fails due to some error, it will not affect the other entity.

Let's take the example of a toy and its battery. The battery belongs to a toy, and if the toy breaks and deletes from our database, the battery will
still remain in our database, and it may still be working.

So in Aggregation, objects always have their own lifecycles when the ownership exists there.

**Composition**

A restricted form of the Aggregation where the entities are strongly dependent on each other. Unlike Aggregation, Composition represents the part-of
relationship. When there is an aggregation between two entities, the aggregate object can exist without the other entity, but in the case of
Composition, the composed object can't exist.

Let's take an example to understand the concept of Composition.

We create a class Mobile that contains variables, i.e., name, ram and rom. We also create a class MobileStore that has a reference to refer to the
list of mobiles. A mobile store can have more than one mobile. So, if a mobile store is destroyed, then all mobiles within that particular mobile
store will also be destroyed because mobiles cannot exist without a mobile store. The relationship between the mobile store and mobiles is
Composition.

#### Q40. What is the result of using more abstraction?

- [ ] it can increase code vulnerability
- [ ] it can make code unsafe
- [x] it can limit code readability
- [ ] it can be safer for coding

#### Explanation

In object-oriented programming, abstraction is defined as hiding the unnecessary details (implementation) from the user and to focus on essential
details (functionality).

What is the disadvantage of using more abstraction?

The most obvious is complexity. Whenever we add another layer to our code, we make it a bit more complex to navigate.

**Note**: It is always a balance, because Abstraction can also reduce the complexity of the code, if applied correctly.

#### Q41. Which statement best describes a friend class?

- [ ] Friend classes support base class when necessary.
- [x] A friend class can access the private and protected members of the class in which it is declared as a friend.
- [ ] Friend classes do not have any implementation.
- [ ] A friend class can access only protected members of the class of which it is a friend.

**Link**: [Friend class in C++](https://www.simplilearn.com/tutorials/cpp-tutorial/friend-class-in-cpp/) (not related to Java)

#### Q42. Why is inheritance used when creating a new class?

- [ ] to protect attributes from unwanted changes
- [ ] to delegate coding responsibility more efficiently
- [ ] to conserve memory
- [x] to separate class behavior from the more general

#### Explanation

Inheritance allows programmers to create classes that are built upon existing classes, to specify a new implementation while maintaining the same
behaviors, to reuse code and to independently extend original software.

#### Q43. In addition to attributes and behaviours, what quality must a class possess?

- [x] a name
- [ ] a state
- [ ] a color
- [ ] an object

#### Explanation

It's impossible to create class without name in Java so name is the mandatory attributes.

**Note**: We can create a class without a name using the Anonymous class. Anonymous class is an inner class which does not have a name and whose
instance is created at the time of the creation of class itself and these classes are somewhat different from normal classes in its creation.

Since they have no name, we can't use them in order to create instances of anonymous classes. As a result, we have to declare and instantiate
anonymous classes in a single expression at the point of use.

```java
Runnable action=new Runnable(){
@Override
public void run(){
        ...
        }
        };
```

#### Q44. Which type of function among the following shows' polymorphism?

- [ ] inline function
- [ ] undefined function
- [x] virtual function
- [ ] class member function

**Link**: [Virtual Function in C++ ](https://www.geeksforgeeks.org/virtual-function-cpp/) (not related to Java)

#### Q45. Which words in the following list are candidates for objects: trumpet, clean, enrage, leaf, tree, collapse, active, and lively?

- [ ] leaf and tree
- [ ] clean, enrage, and collapse
- [ ] clean, active, and lively
- [x] leaf, tree, and trumpet

#### Explanation

An object in OOPS is nothing but a self-contained component which consists of methods and properties to make a particular type of data useful.

For example color name, table, bag, barking. When you send a message to an object, you are asking the object to invoke or execute one of its methods
as defined in the class.

A **Class** in object-oriented programming is a blueprint or prototype that defines the variables and the methods (functions) common to all Java
Objects
of a certain kind.

An **Object** in object-oriented programming is a specimen of a class. Software objects are often used to model real-world objects you find in
everyday life.

![oop-classes.png](src%2Foop%2Foop-classes.png)
