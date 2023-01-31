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
        try  
        {  
        int data=50/0; //may throw exception   
                         // if exception occurs, the remaining statement will not exceute  
        System.out.println("rest of the code");  
        }  
             // handling the exception   
        catch(ArithmeticException e)  
        {  
            System.out.println(e);  
        }  
          
    }  

}  
```
