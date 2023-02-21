## Design Pattern (University of Alberta)

[Link to course](https://www.coursera.org/learn/design-patterns)

<a name="link-top"></a>

---

### Table of Contents

<ol>
  <li>
    <a href="#module-1">Module 1</a>
  </li>
  <li>
    <a href="#module-2">Module 2</a>
  </li>
  <li>
    <a href="#module-3">Module 3</a>
  </li>
  <li>
    <a href="#module-4">Module 4</a>
  </li>
</ol>

---

| Module 1             | Module 2                           | Module 3                                     | Module 4                 |
|----------------------|------------------------------------|----------------------------------------------|--------------------------|
| Creational Patterns: | Behavioral Patterns:               | MVC Pattern                                  | Revision of the material |
| 1. Singleton         | 1. Template Method Pattern         | Design Principles Underlying Design Patterns |                          |
| 2. Factory Method    | 2. Chain of Responsibility Pattern | 1. Liskov Substitution Principle             |                          |
| Structural Patterns: | 3. State Pattern                   | 2. Open/Closed Principle                     |                          |
| 1. Facade            | 4. Command Pattern                 | 3. Dependency Inversion Principle            |                          |
| 2. Adapter           | 5. Mediator Pattern                | 4. Interface Segregation Principle           |                          |
| 3. Composite         | 6. Observer Pattern                | 5. Composition over Inheritance              |                          |
| 4. Proxy             |                                    | 6. Law of Demeter                            |                          |
| 5. Decorator         |                                    | Anti-Patterns & Code Smells                  |                          |
|                      |                                    | 1. Primitive obsession                       |                          |
|                      |                                    | 2. Excessive comments                        |                          |
|                      |                                    | 3. God Class                                 |                          |
|                      |                                    | 4. Message chains                            |                          |
|                      |                                    | 5. Feature envy                              |                          |
|                      |                                    | 6. Speculative Generality                    |                          |

--- 

#### Module 1

#### Q1. When is the best time to use a design pattern? Choose two answers.

1. [ ] For a problem that is unique to your program.
2. [x] For a commonly-encountered issue.
3. [ ] When fixing spaghetti code
4. [x] When explaining a solution to your fellow developers

#### Explanation:

Design patterns are practical proven solutions to a recurring design problem.

Benefits of Design Patterns:

1. Enable large-scale reuse of software architectures
2. Inspiration:
    1. Patterns don't provide solutions, they inspire solutions;
    2. Patterns explicitly capture expert knowledge and design tradeoffs and make this expertise widely available;
3. Patterns improve developer communication by forming common vocabulary.
4. Help document the architecture of a system

#### Q2. What is the purpose of the Singleton pattern? Select the two correct answers.

1. [ ] to provide simple classes with only one method
2. [x] to enforce instantiation of only one object of a class
3. [ ] to enforce collaboration of a class with only one other class
4. [x] to provide global access to an object

#### Explanation:

Singleton Pattern says that just "define a class that has only one instance and provides a global point of access to it".

In other words, a class must ensure that only a single instance should be created and a single object can be used by all other classes.

**Real life analogy**:

Singleton is like a single resource which is being shared among multiple users.

For example:

1. Sharing a single washing machine among all the residents in a hotel;
2. Sharing a single appliance like refrigerator among all the family members.

The government is also an excellent example of the Singleton pattern. A country can have only one official government. Regardless of the personal
identities of the individuals who form governments.

The title “The Government of X” is a global point of access that identifies the group of people in charge.

#### Q3. What does it mean to "let the subclass decide" in the Factory Method Pattern?

1. [ ] the subclass decides which object to create, but calls a method that is defined in the superclass to instantiate the class
2. [x] the subclass defines the methods for concrete instantiation. As such, the type of object is determined by which subclass is instantiated.
3. [ ] the subclass will pass a parameter into a factory that determines which object is instantiated.

#### Explanation:

A Factory Pattern says that just define an interface or abstract class for creating an object, but let the subclasses decide which class to
instantiate.

In other words, subclasses are responsible for creating the instance of the class.

**Real life analogy**:

Now one might think, how can there be a situation where the program does not know which objects to create? To answer this question, consider a
scenario where we want to send a notification to the user.

There are 2 ways in which the user can receive the notifications:

1. Email;
2. SMS.
3.

Now the user decides at runtime in which format he wants to receive the notification. As a result, our program doesn't know until runtime which
notification object to create.

This is where the Factory method pattern comes to our rescue.

**Advantage of Factory Design Pattern:**

It promotes the loose-coupling by eliminating the need to bind application-specific classes into the code. That means the code interacts solely with
the resultant interface or abstract class, so that it will work with any classes that implement that interface or that extends that abstract class.

**Example of implementation**:

We're going to create a `Shape` interface and concrete classes implementing this interface.

`FactoryPatternDemo`, our demo class will use `ShapeFactory` to get a `Shape` object. It will pass information (CIRCLE / RECTANGLE / SQUARE)
to `ShapeFactory`
to get the type of object it needs.

![factory-pattern-uml-diagram.jpeg](src%2Fdesign-pattern%2Ffactory-pattern-uml-diagram.jpeg)

**Step 1**: create an interface.

```java
public interface Shape {
    void draw();
}
```

**Step 2**: create concrete classes implementing the same interface.

```java
public class Rectangle implements Shape {

    @Override
    public void draw() {
        System.out.println("Inside Rectangle::draw() method.");
    }
}

public class Square implements Shape {

    @Override
    public void draw() {
        System.out.println("Inside Square::draw() method.");
    }
}

public class Circle implements Shape {

    @Override
    public void draw() {
        System.out.println("Inside Circle::draw() method.");
    }
}
```

**Step 3**: create a Factory to generate object of concrete class based on given information.

```java
public class ShapeFactory {

    //use getShape method to get object of type shape
    public Shape getShape(String shapeType) {
        if (shapeType == null) {
            return null;
        }
        if (shapeType.equalsIgnoreCase("CIRCLE")) {
            return new Circle();

        } else if (shapeType.equalsIgnoreCase("RECTANGLE")) {
            return new Rectangle();

        } else if (shapeType.equalsIgnoreCase("SQUARE")) {
            return new Square();
        }

        return null;
    }
}
```

**Step 4**: use the Factory to get object of concrete class by passing an information such as type.

```java
public class FactoryPatternDemo {

    public static void main(String[] args) {
        ShapeFactory shapeFactory = new ShapeFactory();

        //get an object of Circle and call its draw method.
        Shape shape1 = shapeFactory.getShape("CIRCLE");
        shape1.draw();

        //get an object of Rectangle and call its draw method.
        Shape shape2 = shapeFactory.getShape("RECTANGLE");
        shape2.draw();

        //get an object of Square and call its draw method.
        Shape shape3 = shapeFactory.getShape("SQUARE");
        shape3.draw();
    }
}
```

#### Q4. What do we call the creation of an object, for example, with the 'new' operator in Java?

1. [ ] object realization
2. [ ] manifestation
3. [ ] class creation
4. [x] concrete instantiation.

#### Explanation:

Instantiation: The `new` keyword is a Java operator that creates the object.

#### Q5. What are the advantages of the Facade pattern? Select the three correct answers.

1. [x] The complexity of the subsystem is hidden
2. [x] The Facade class redirects requests as needed
3. [x] The client and the subsystem are more loosely coupled
4. [ ] The subsystem can handle more clients

#### Explanation:

Facade is a structural design pattern that provides a simplified interface to a library, a framework, or any other complex set of classes.

Use the Facade pattern when you need to have a limited but straightforward interface to a complex subsystem.

Advantage of Facade Pattern:

1. It shields the clients from the complexities of the sub-system components;
2. It promotes loose coupling between subsystems and its clients.

#### Q6. Which of the following diagrams shows the Adapter pattern?

![m1-q6.png](src%2Fdesign-pattern%2Fm1-q6.png)

1. [ ] a)
2. [ ] b)
3. [x] c)
4. [ ] d)

#### Explanation:

An Adapter pattern acts as a connector between two incompatible interfaces that otherwise cannot be connected directly. An Adapter wraps an existing
class with a new interface so that it becomes compatible with the client’s interface.

The main motive behind using this pattern is to convert an existing interface into another interface that the client expects.

**The Adapter Pattern in real life**:

It works the same way as a real-life adapter, for example for a power outlet. If you travel from the European Union to Switzerland or the US your
normal power plug won’t fit into the power outlet. Hence, you have to get an adapter which can link the power outlet with the power plug. This example
perfectly describes how the adapter pattern works.

**The Adapter Pattern in software development**:

The adapter pattern is often used in combination with third-party libraries.

For example, you’re creating a stock market monitoring app. The app downloads the stock data from multiple sources in XML format and then displays
nice-looking charts and diagrams for the user.

At some point, you decide to improve the app by integrating a smart 3rd-party analytics library. But there’s a catch: the analytics library only works
with data in JSON format.

**UML Diagram**:

![adapter-pattern-uml-diagram.jpeg](src%2Fdesign-pattern%2Fadapter-pattern-uml-diagram.jpeg)

The UML diagram for the adapter pattern is pretty simple. The client wants to call an operation on the Adaptee. To do that the client implements the
Adapter interface and calls the Operation method. The ConcreteAdapter implements the method and calls the AdaptedOperation of the adaptee. After the
execution, the ConcreteAdapter returns the information needed to the client.

#### Q7. Which of these are the best applications for a Composite Pattern? Choose the three correct answers.

1. [x] Files and folders
2. [x] Elements in a user-interface dialog
3. [ ] Students in a class
4. [x] Music in a playlist

#### Explanation:

The Composite pattern is meant to allow treating individual objects and compositions of objects, or “composites” in the same way.

It can be viewed as a tree structure made up of types that inherit a base type, and it can represent a single part or a whole hierarchy of objects.

We can break the Composite pattern down into 4 parts.

|   Part    |                                                                               Description                                                                                |
|:---------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| component | The base interface for all the objects in the composition. It should be either an interface or an abstract class with the common methods to manage the child composites. |
|   leaf    |                               Implements the default behaviour of the base component. It doesn't contain a reference to the other objects.                               |
| composite |                                    Implements the base component methods and defines the child-related operations (has leaf elements)                                    |
|  client   |                                              It has access to the composition elements by using the base component object.                                               |

![composite-pattern-uml-diagram.png](src%2Fdesign-pattern%2Fcomposite-pattern-uml-diagram.png)

**The Composite Pattern in real life**:

In an organization, It has general managers and under general managers, there can be managers and under managers there can be developers.
Now you can set a tree structure and ask each node to perform common operation like `getSalary()`.

Other example is Armies that for most countries are structured as hierarchies.

1. An army consists of several divisions;
2. A division is a set of brigades;
3. A brigade consists of platoons, which can be broken down into squads.
4. Finally, a squad is a small group of real soldiers.

Orders are given at the top of the hierarchy and passed down onto each level until every soldier knows what needs to be done.

**Example of implementation:**:

Let's suppose we want to build a hierarchical structure of departments in a company.

**Step 1**: The Base Component

```java
public interface Department {
    void printDepartmentName();
}
```

**Step 2**: Leafs

For the leaf components, let's define classes for financial and sales departments:

```java
public class FinancialDepartment implements Department {

    private Integer id;
    private String name;

    public void printDepartmentName() {
        System.out.println(getClass().getSimpleName());
    }

    // standard constructor, getters, setters

}
```

The second leaf class, SalesDepartment, is similar:

```java
public class SalesDepartment implements Department {

    private Integer id;
    private String name;

    public void printDepartmentName() {
        System.out.println(getClass().getSimpleName());
    }

    // standard constructor, getters, setters

}
```

Both classes implement the printDepartmentName() method from the base component, where they print the class names for each of them.

**Step 3**: The Composite Element

As a composite class, let's create a HeadDepartment class:

```java
public class HeadDepartment implements Department {

    private Integer id;
    private String name;

    private List<Department> childDepartments;

    public HeadDepartment(Integer id, String name) {
        this.id = id;
        this.name = name;
        this.childDepartments = new ArrayList<>();
    }

    public void printDepartmentName() {
        childDepartments.forEach(Department::printDepartmentName);
    }

    public void addDepartment(Department department) {
        childDepartments.add(department);
    }

    public void removeDepartment(Department department) {
        childDepartments.remove(department);
    }
}
```

This is a composite class as it holds a collection of Department components, as well as methods for adding and removing elements from the list.

The composite `printDepartmentName()` method is implemented by iterating over the list of leaf elements and invoking the appropriate method for each
one.

#### Q8. What are the object types that are used in the Composite Pattern? Select the two correct answers.

1. [ ] root
2. [ ] trunk
3. [x] leaf
4. [ ] branch
5. [x] composite

#### Explanation:

The Composite pattern is meant to allow treating individual objects and compositions of objects, or “composites” in the same way.

We can break the Composite pattern down into 4 parts:

1. Component
2. Leaf
3. Composite
4. Client

#### Q9. Which of these is NOT a common application of the Proxy Pattern?

1. [x] information proxy
2. [ ] remote proxy
3. [ ] protection proxy
4. [ ] virtual proxy

#### Explanation:

Proxy is a structural design pattern that lets you provide a substitute or placeholder for another object.

A proxy controls access to the original object, allowing you to perform something either before or after the request gets through to the original
object.

The proxy can acts also as a simplified or lightweight version of the original object and able to accomplish the same tasks, but may delegate requests
to the
original object to achieve them.

The proxy pattern can perform a variety of functions:

* **Virtual proxy** is a proxy that controls access to a resource that is expensive to create.
* **Remote proxy** is a proxy is a surrogate or placeholder for another object that controls access to it. A remote proxy provides local
  representation for an object in a different address space.
* **Protection proxy** is a proxy that controls access to a resource based on access rights.

**The Proxy Pattern in real life**:

A credit card is a proxy for a bank account, which is a proxy for a bundle of cash. Both implement the same interface: they can be used for making a
payment.

A consumer feels great because there’s no need to carry loads of cash around. A shop owner is also happy since the income from a transaction gets
added electronically to the shop’s bank account without the risk of losing the deposit or getting robbed on the way to the bank.

Other example of Proxy pattern in corporate networks. Internet access is guarded behind a network proxy. All network requests goes through proxy which
first check the requests for allowed websites and posted data to network. If request looks suspicious, proxy block the request – else request pass
through.

**The Proxy Pattern in software development**:

**In hibernate**, we write the code to fetch entities from the database. Hibernate returns an object which a proxy (by dynamically constructed by
Hibernate by extending the domain class) to the underlying entity class. The client code is able to read the data whatever it needs to read with the
proxy.

These proxy entity classes help in implementing lazy loading scenarios where associated entities are fetched only when they are requested explicitly.
It helps in improving performance of DAO operations.

In Aspect Oriented Programming, an object created by the AOP framework in order to implement the aspect contracts (advise method executions and so
on). For example, in the Spring AOP, an AOP proxy will be a JDK dynamic proxy or a CGLIB proxy.

#### Q10. How does a Decorator Pattern work? Choose one.

1. [ ] encapsulates a class to give it a different interface
2. [ ] adding features to a class with a new class
3. [x] builds a behaviour by stacking objects
4. [ ] expands the methods of a class with inheritance

#### Explanation:

Decorator is a structural design pattern that lets you attach new behaviors to objects by placing these objects inside special wrapper objects that
contain the behaviors.

This is a good choice in the following cases:

1. When we wish to add, enhance or even remove the behavior or state of objects;
2. When we just want to modify the functionality of a single object of class and leave others unchanged.

In the implementation of this pattern, we prefer composition over an inheritance – so that we can reduce the overhead of subclassing again and again
for each decorating element. The recursion involved with this design can be used to decorate our object as many times as we require.

![decorator-pattern-uml-diagram.webp](src%2Fdesign-pattern%2Fdecorator-pattern-uml-diagram.webp)

**The Decorator Pattern in real life**:

Wearing clothes is an example of using decorators. When you’re cold, you wrap yourself in a sweater. If you’re still cold with a sweater, you can wear
a jacket on top. If it’s raining, you can put on a raincoat.

All of these garments “extend” your basic behavior but aren’t part of you, and you can easily take off any piece of clothing whenever you don’t need
it.

**The Decorator Pattern Example**:

Suppose we have a Christmas tree object, and we want to decorate it. The decoration does not change the object itself; it’s just that in addition to
the Christmas tree, we're adding some decoration items like garland, tinsel, tree-topper, bubble lights, etc.:

![decorator-pattern-uml-diagram-example.jpeg](src%2Fdesign-pattern%2Fdecorator-pattern-uml-diagram-example.jpeg)

**Step 1**: First, we'll create a ChristmasTree interface and its implementation.

```java
public interface ChristmasTree {
    String decorate();
}

public class ChristmasTreeImpl implements ChristmasTree {

    @Override
    public String decorate() {
        return "Christmas tree";
    }
}
```

**Step 2**: Create an abstract TreeDecorator class for this tree.

This decorator will implement the `ChristmasTree` interface as well as hold the same object.

The implemented method from the same interface will simply call the `decorate()` method from our interface.

```java
public abstract class TreeDecorator implements ChristmasTree {
    private ChristmasTree tree;

    // standard constructors
    @Override
    public String decorate() {
        return tree.decorate();
    }
}
```

**Step 3**: Create some decorating element.

These decorators will extend our abstract `TreeDecorator` class and will modify its `decorate()` method according to our requirement.

```java
public class BubbleLights extends TreeDecorator {

    public BubbleLights(ChristmasTree tree) {
        super(tree);
    }

    public String decorate() {
        return super.decorate() + decorateWithBubbleLights();
    }

    private String decorateWithBubbleLights() {
        return " with Bubble Lights";
    }
}
```

**Testing**: For this case, the following is true.

```java
@Test
public void whenDecoratorsInjectedAtRuntime_thenConfigSuccess(){
        ChristmasTree tree1=new Garland(new ChristmasTreeImpl());
        assertEquals(tree1.decorate(),
        "Christmas tree with Garland");

        ChristmasTree tree2=new BubbleLights(new Garland(new Garland(new ChristmasTreeImpl())));
        assertEquals(tree2.decorate(),
        "Christmas tree with Garland with Garland with Bubble Lights");
        }
```

#### Q11. Many clients need to create a similar object. You would like to outsource this concrete instantiation to a dedicated class. Which technique will you use, in one word?

**Answer**: factory

#### Explanation:

A Factory Pattern says that just define an interface or abstract class for creating an object, but let the subclasses decide which class to
instantiate.

In other words, subclasses are responsible for creating the instance of the class.

**Benefits of Factory Objects**:

If there are multiple clients that want to instantiate the same set of classes, then by using a Factory object, you have cut out redundant code and
made the software easier to modify.

#### Q12. How do you enforce the creation of only one Singleton object? Select the two correct answers.

1. [ ] Specify in the comments that only one Singleton object is to be instantiated.
2. [x] Write a method that can create a new Singleton object or return the existing one.
3. [ ] Throw an exception if a Singleton object is already instantiated
4. [x] Give the Singleton class a private constructor

#### Explanation:

Singleton Pattern says that just "define a class that has only one instance and provides a global point of access to it".

In other words, a class must ensure that only a single instance should be created and a single object can be used by all other classes.

There are two forms of singleton design pattern:

1. Early Instantiation: creation of an instance at load time;
2. Lazy Instantiation: creation of an instance when required.

**How to create Singleton**:

To create the singleton class, we need to have a static member of class, private constructor and static factory method.

1. **Static member**: It gets memory only once because of static, it contains the instance of the Singleton class.
2. **Private constructor**: It will prevent instantiating the Singleton class from outside the class.
3. **Static factory method**: This provides the global point of access to the Singleton object and returns the instance to the caller.

```java
class A {

    private static A obj = new A(); //Early, instance will be created at load time  

    private A() {
    }

    public static A getA() {
        return obj;
    }

    public void doSomething() {
        …
    }
}
```

```java
class A {

    private static A obj;

    private A() {
    }

    public static A getA() {
        if (obj == null) {
            synchronized (Singleton.class) {
                if (obj == null) {
                    obj = new Singleton(); // instance will be created at request time  
                }
            }
        }
        return obj;
    }

    public void doSomething() {
        …
    }
}  
```

<p align="right">(<a href="#table-of-contents">back to top</a>)</p>

#### Module 2

Behavioral Patterns:

1. Template Method Pattern
2. Chain of Responsibility Pattern
3. State Pattern
4. Command Pattern
5. Mediator Pattern
6. Observer Pattern

--- 

#### Q1. Choose the most appropriately implemented Template pattern

Some UML reminders that will help you:

* a private method or variable is denoted by a `-` as in `-boilWater()`
* a method, variable, or class that is abstract is denoted by italics (as in PastaTemplate)

1. [ ] a
2. [ ] b
3. [ ] c
4. [x] d

![m2-q1.png](src%2Fdesign-pattern%2Fm2-q1.png)

#### Explanation:

1. The `PastaTemplate` class should be abstract therefore answer `B` is incorrect
2. Methods that will be overwritten in child classes and do not have a default implementation should be abstract therefore answer `C` is incorrect
3. The abstract methods of the `PastaTemplate` class must be public therefore answer `A` is incorrect

---

Template Method is a behavioural design pattern that defines the skeleton of an algorithm in the superclass but lets subclasses override specific
steps of the algorithm without changing its structure.

**How to Implement**:

1. Analyze the target algorithm to see whether you can break it into steps. Consider which steps are common to all subclasses and which ones will
   always be unique.
2. Create the abstract base class and declare the template method and a set of abstract methods representing the algorithm’s steps. Outline the
   algorithm’s structure in the template method by executing corresponding steps. Consider making the template method final to prevent subclasses from
   overriding it.
3. For each variation of the algorithm, create a new concrete subclass. It must implement all the abstract steps, but may also override some
   optional ones.

![template-method-structure.png](src%2Fdesign-pattern%2Ftemplate-method-structure.png)

**Example of implementation**:

To demonstrate how the template method pattern works, let's create a simple example which represents building a computer station.

Given the pattern's definition, the algorithm's structure will be defined in a base class that defines the template `build()` method:

```java
public abstract class ComputerBuilder {

    protected Map<String, String> computerParts = new HashMap<>();
    protected List<String> motherboardSetupStatus = new ArrayList<>();

    public final Computer buildComputer() {
        addMotherboard();
        setupMotherboard();
        addProcessor();
        return getComputer();
    }

    public abstract void addMotherboard();

    public abstract void setupMotherboard();

    public abstract void addProcessor();

    public List<String> getMotherboardSetupStatus() {
        return motherboardSetupStatus;
    }

    public Map<String, String> getComputerParts() {
        return computerParts;
    }

    private Computer getComputer() {
        return new Computer(computerParts);
    }
}
```

The `ComputerBuilder` class is responsible for outlining the steps required to build a computer by declaring methods for adding and setting up
different
components, such as a motherboard and a processor.

Here, the `build()` method is the template method, which defines steps of the algorithm for assembling the computer parts and returns
fully-initialised
Computer instances.

**Note**: it's declared as final to prevent it from being overridden.

With the base class already set, let's try to use it by creating two subclasses. One which builds a “standard” computer, and the other that builds a
“high-end” computer:

```java
public class StandardComputerBuilder extends ComputerBuilder {

    @Override
    public void addMotherboard() {
        computerParts.put("Motherboard", "Standard Motherboard");
    }

    @Override
    public void setupMotherboard() {
        motherboardSetupStatus.add(
                "Screwing the standard motherboard to the case.");
        motherboardSetupStatus.add(
                "Pluging in the power supply connectors.");
        motherboardSetupStatus.forEach(
                step -> System.out.println(step));
    }

    @Override
    public void addProcessor() {
        computerParts.put("Processor", "Standard Processor");
    }

}
```

```java
public class HighEndComputerBuilder extends ComputerBuilder {

    @Override
    public void addMotherboard() {
        computerParts.put("Motherboard", "High-end Motherboard");
    }

    @Override
    public void setupMotherboard() {
        motherboardSetupStatus.add(
                "Screwing the high-end motherboard to the case.");
        motherboardSetupStatus.add(
                "Plugging in the power supply connectors.");
        motherboardSetupStatus.forEach(
                step -> System.out.println(step));
    }

    @Override
    public void addProcessor() {
        computerParts.put("Processor", "High-end Processor");
    }

}
```

Let's use it in our application:

```java
public class Application {

    public static void main(String[] args) {
        ComputerBuilder standardComputerBuilder = new StandardComputerBuilder();
        Computer standardComputer = standardComputerBuilder.buildComputer();
        standardComputer.getComputerParts().forEach((k, v) -> System.out.println("Part : " + k + " Value : " + v));

        ComputerBuilder highEndComputerBuilder = new HighEndComputerBuilder();
        Computer highEndComputer = highEndComputerBuilder.buildComputer();
        highEndComputer.getComputerParts().forEach((k, v) -> System.out.println("Part : " + k + " Value : " + v));
    }
}
```

#### Q2. What is the correct situation for the use of a Chain of Responsibility pattern?

1. [ ] You need a set of objects to each contribute information on responding to a request.
2. [x] You have multiple potential handlers, but only one will deal with the request.
3. [ ] You need to pass a message to multiple receivers.
4. [ ] You need to delegate a set of tasks to a hierarchy of objects.

#### Explanation:

Chain of Responsibility is a behavioural design pattern that lets you pass requests along a chain of handlers. Upon receiving a request, each handler
decides either to process the request or to pass it to the next handler in the chain.

**Applicability**:

This pattern is recommended when multiple objects can handle a request and the handler doesn't have to be a specific object. Also, the handler is
determined at runtime.

**Note**: a request not handled at all by any handler is a valid use case.

**Chain of Responsibility Pattern Example in JDK**:

Let’s see the example of chain of responsibility pattern in JDK: we know that we can have multiple catch blocks in a try-catch block code. Here every
catch block is kind of a processor to process that particular exception.

So when any exception occurs in the try block, its send to the first catch block to process. If the catch block is not able to process it, it forwards
the request to next object in chain i.e. next catch block. If even the last catch block is not able to process it, the exception is thrown outside
the chain to the calling program.

**Chain of Responsibility Pattern in real life**:

One of the great example of Chain of Responsibility pattern is ATM Dispense machine.

The user enters the amount to be dispensed and the machine dispense amount in terms of defined currency bills such as 50$, 20$, 10$ etc. If the user
enters an amount that is not multiples of 10, it throws error. We will use Chain of Responsibility pattern to implement this solution.

![cor-pattern-example.png](src%2Fdesign-pattern%2Fcor-pattern-example.png)

Note that we can implement this solution easily in a single program itself but then the complexity will increase and the solution will be tightly
coupled. So we will create a chain of dispense systems to dispense bills of 50$, 20$ and 10$.

#### Q3. What is the purpose of encapsulating state in an object in the State Pattern? Choose the three that are correct.

1. [x] it allows the current state object to decide how to achieve behaviours specific to the state of the context.
2. [x] it allows the current state to be copied from one instance to another
3. [ ] it removes large conditionals that are difficult to maintain.
4. [x] it turns the context into a client of the state.

#### Explanation:

State is a behavioural design pattern that lets an object alter its behaviour when its internal state changes. It appears as if the object changed its
class.

**Advantages of State Design Pattern**:

* With State pattern, the benefits of implementing polymorphic behavior are evident, and it is also easier to add states to support additional
  behavior.
* In the State design pattern, an object’s behavior is the result of the function of its state, and the behavior gets changed at runtime depending on
  the state. This removes the dependency on the `if/else` or `switch/case` conditional logic.
* The State design pattern also improves Cohesion since state-specific behaviors are aggregated into the ConcreteState classes, which are placed in
  one location in the code.
* It can make your code easier to read. Your code may be simpler to comprehend if the behavior is divided into several states, with each state having
  a distinct name that is both obvious and descriptive.
* You may find it helpful to follow the Single Responsibility Principle. According to the SRP, a class should only have one cause to modify. You
  may guarantee that each state has a clear and distinct duty by encapsulating the behavior in multiple states, which can make your code easier to
  maintain and alter.

**UML Diagram**

The **Context** defines an interface for clients to interact. It maintains references to concrete state objects which may be used to define the
current state of objects.

The **State** defines interface for declaring what each concrete state should do.

The **ConcreteState** provides the implementation for methods defined in State.

![state-pattern-uml.png](src%2Fdesign-pattern%2Fstate-pattern-uml.png)

In the UML diagram, we see that Context class has an associated State which is going to change during program execution.

Our context is going to delegate the behavior to the state implementation. In other words, all incoming requests will be handled by the concrete
implementation of the state.

We see that logic is separated and adding new states is simple – it comes down to adding another State implementation if needed.

**Example of implementation**:

let's implement a mobile state scenario. With respect to alerts, a mobile can be in different states.

For example, vibration and silence. Based on this alert state, the behavior of the mobile changes when an alert is to be done.

```java
interface MobileAlertState {
    public void alert(AlertStateContext ctx);
}

class AlertStateContext {

    private MobileAlertState currentState;

    public AlertStateContext() {
        currentState = new Vibration();
    }

    public void setState(MobileAlertState state) {
        currentState = state;
    }

    public void alert() {
        currentState.alert(this);
    }
}

class Vibration implements MobileAlertState {
    @Override
    public void alert(AlertStateContext ctx) {
        System.out.println("vibration... ");
    }
}

class Silent implements MobileAlertState {
    @Override
    public void alert(AlertStateContext ctx) {
        System.out.println("silent... ");
    }
}

class StatePattern {
    public static void main(String[] args) {
        AlertStateContext stateContext = new AlertStateContext();
        stateContext.alert();
        stateContext.alert();
        stateContext.setState(new Silent());
        stateContext.alert();
        stateContext.alert();
        stateContext.alert();
    }
}
```

#### Q4. What design principles is the Command Pattern using?

1. [x] Encapsulation, generalization, loose coupling
2. [ ] Encapsulation, information hiding, loose coupling
3. [ ] Encapsulation, generalization, information hiding
4. [ ] Generalization, information hiding, loose coupling

#### Explanation:

|     Principle      |                                                                                                         Description                                                                                                          | Command Pattern                                                                                                                                                                    |
|:------------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   Generalisation   | Generalisation defines as the technique of extracting the essential characteristics (these include attributes, properties, and methods) from two or more subclasses and then combining them inside a generalized base class. | ✅ The Command interface contains an execute() method that simply calls the action on the receiver.                                                                                 |
|   Encapsulation    |                                                                   Encapsulation refers to the bundling of data with the methods that operate on that data.                                                                   | ✅ The Command pattern encapsulate a request as an object, thereby letting you parametrise clients with different requests, queue or log requests, and support undoable operations. |
|   Loose coupling   |                                        Loose coupling is an approach to interconnecting the components so that those components depend on each other to the least extent practicable.                                        | ✅ The main focus of the command pattern is to inculcate a higher degree of loose coupling between involved parties.                                                                |
| Information hiding |                                               Data hiding is an object-oriented programming technique specifically used to hide internal object details (i.e., data members).                                                | ❌                                                                                                                                                                                  |

---

Command is a behavioural design pattern that turns a request into a stand-alone object that contains all information about the request.

Simply put, the pattern intends to encapsulate in an Object all the data required for performing a given action (command), including:

1. What method to call;
2. The method's arguments;
3. The Object (known as the receiver) to which the method belongs.

This model allows us to decouple objects that produce the commands from their consumers, so that's why the pattern is commonly known as the
producer-consumer pattern.

This transformation lets you:

1. Pass requests as a method argument;
2. Delay or queue the request's execution;
3. Support undoable operations.

**UML Diagram**:

![command-pattern-uml-diagram.png](src%2Fdesign-pattern%2Fcommand-pattern-uml-diagram.png)

**Pros and Cons**:

✅ Single Responsibility Principle:
you can decouple classes that invoke operations from classes that perform these operations.

✅ Open/Closed Principle:
you can introduce new commands into the app without breaking existing client code.

✅ You can implement undo/redo functionality.

✅ You can implement deferred execution of operations.

✅ You can assemble a set of simple commands into a complex one.

❌ The code may become more complicated since you’re introducing a whole new layer between senders and receivers.

#### Q5. Which are the minimum requirements of the Observer pattern? Choose the three that are correct.

1. [x] method to notify observers
2. [x] methods to add or remove observers
3. [x] update method in observers
4. [ ] a state variable to determine if observers have been notified.

#### Explanation:

Observer is a behavioural design pattern that lets you define a subscription mechanism to notify multiple objects about any events that happen to the
object they’re observing.

**UML Diagram**:

![observer-pattern-structure.png](src%2Fdesign-pattern%2Fobserver-pattern-structure.png)

The **Publisher** issues events of interest to other objects.

These events occur when the publisher changes its state or executes some behaviors. Publishers contain a subscription infrastructure that lets new
subscribers join and current subscribers leave the list.

When a new event happens, the publisher goes over the subscription list and calls the notification method declared in the subscriber interface on each
subscriber object.

The **Subscriber** interface declares the notification interface. In most cases, it consists of a single `update()` method. The method may have
several parameters that let the publisher pass some event details along with the update.

The **Concrete Subscriber** performs some actions in response to notifications issued by the publisher. All of these classes must implement the same
interface so the publisher isn’t coupled to concrete classes.

Usually, subscribers need some contextual information to handle the update correctly. For this reason, publishers often pass some context data as
arguments of the notification method. The publisher can pass itself as an argument, letting subscriber fetch any required data directly.

The **Client** creates publisher and subscriber objects separately and then registers subscribers for publisher updates.

**Example of implementation**:

An observable is an object which notifies observers about the changes in its state. For example, a news agency can notify channels when it receives
news.

Receiving news is what changes the state of the news agency, and it causes the channels to be notified.

First, we'll define the NewsAgency class:

```java
public class NewsAgency {

    private String news;
    private List<Channel> channels = new ArrayList<>();

    public void addObserver(Channel channel) {
        this.channels.add(channel);
    }

    public void removeObserver(Channel channel) {
        this.channels.remove(channel);
    }

    public void setNews(String news) {
        this.news = news;
        for (Channel channel : this.channels) {
            channel.update(this.news);
        }
    }
}
```

`NewsAgency` is an observable, and when news gets updated, the state of `NewsAgency` changes. When the change happens, `NewsAgency` notifies the
observers
about it by calling their `update()` method.

**Note**: To be able to do that, the observable object needs to keep references to the observers. In our case, it's the “channels” variable.

Now let's see what the observer, the Channel class, can look like. It should have the update() method, which is invoked when the state of NewsAgency
changes:

```java
public interface Channel {
    public void update(Object o);
}
```

```java
public class NewsChannel implements Channel {

    private String news;

    @Override
    public void update(Object news) {
        this.setNews((String) news);
    }

    // standard getter and setter

}
```

Client code:

```
        NewsAgency observable=new NewsAgency();
        NewsChannel observer=new NewsChannel();

        observable.addObserver(observer);
        observable.setNews("news");
        assertEquals(observer.getNews(),"news");
```

#### Q6. When are you most likely to need a Mediator pattern?

1. [ ] When you want to de-couple a class that is requesting a service from one that is providing it.
2. [x] When you are coordinating the activities of a set of related classes.
3. [ ] When your class is sending a request that might be handled by one of several handlers.
4. [ ] When you have two classes with different interfaces that you must connect.

#### Q7. You have a machine performing a complex manufacturing task, with different sensors and different components of the machine represented by different classes. Which design pattern will you use to arrange the parts?

1. [ ] Template
2. [ ] Command
3. [x] Mediator
4. [ ] Chain of Responsibility

#### Explanation:

Mediator is a behavioural design pattern that lets you reduce chaotic dependencies between objects.

The pattern restricts direct communications between the objects and forces them to collaborate only via a mediator object.

**When to Use the Mediator Pattern**:

The Mediator Pattern is a good choice if we have to deal with a set of objects that are tightly coupled and hard to maintain. This way we can reduce
the dependencies between objects and decrease the overall complexity.

Additionally, by using the mediator object, we extract the communication logic to the single component, therefore we follow the Single Responsibility
Principle. Furthermore, we can introduce new mediators with no need to change the remaining parts of the system. Hence, we follow the Open-Closed
Principle.

Sometimes, however, we may have too many tightly coupled objects due to the faulty design of the system. If this is a case, we should not apply the
Mediator Pattern. Instead, we should take one step back and rethink the way we've modelled our classes.

As with all other patterns, we need to consider our specific use case before blindly implementing the Mediator Pattern.

#### Q8. Marlon is coding part of the software that follows a similar sequence of steps. Depending on the type of object, these steps will be implemented in slightly different ways, but their order is always the same. Which design pattern could Marlon use?

1. [x] Template pattern
2. [ ] Mediator pattern
3. [ ] Command pattern
4. [ ] State pattern

#### Explanation:

Template Method is a behavioural design pattern that defines the skeleton of an algorithm in the superclass but lets subclasses override specific
steps of the algorithm without changing its structure.

**When to Use the Template Method Pattern**:

* Use the Template Method pattern when you want to let clients extend only particular steps of an algorithm,
  but not the whole algorithm or its structure.

The Template Method lets you turn a monolithic algorithm into a series of individual steps which can be easily extended by subclasses while keeping
intact the structure defined in a superclass.

* Use the pattern when you have several classes that contain almost identical algorithms with some minor differences.
  As a result, you might need to modify all classes when the algorithm changes.

When you turn such an algorithm into a template method, you can also pull up the steps with similar implementations into a superclass, eliminating
code duplication. Code that varies between subclasses can remain in subclasses.

#### Q9. What are the important roles in the Command Pattern?

1. [ ] Command, Queue, Receiver
2. [ ] Sender, Receiver, Invoker
3. [ ] Delegate, Command, Requester
4. [x] Command, Receiver, Invoker

#### Explanation:

Command is a behavioural design pattern that turns a request into a stand-alone object that contains all information about the request.

Simply put, the pattern intends to encapsulate in an Object all the data required for performing a given action (command), including:

1. What method to call;
2. The method's arguments;
3. The Object (known as the receiver) to which the method belongs.

**UML Diagram**:

![command-pattern-uml-diagram.png](src%2Fdesign-pattern%2Fcommand-pattern-uml-diagram.png)

The **Sender** class (aka invoker) is responsible for initiating requests.

This class must have a field for storing a reference to a command object. The sender triggers that command instead of sending the request directly to
the receiver.

**Note**: the sender isn’t responsible for creating the command object. Usually, it gets a pre-created command from the client via the constructor.

The **Command** interface usually declares just a single method `execute()` for executing the command.

The **Concrete Command** implements various kinds of requests.

A concrete command isn’t supposed to perform the work on its own, but rather to pass the call to one of the business logic objects. However, for the
sake of simplifying the code, these classes can be merged.

Parameters required to execute a method on a receiving object can be declared as fields in the concrete command.

**Note**: you can make command objects immutable by only allowing the initialization of these fields via the constructor.

The **Receiver** class contains some business logic.

Almost any object may act as a receiver. Most commands only handle the details of how a request is passed to the receiver, while the receiver itself
does the actual work.

The **Client** creates and configures concrete command objects.

The client must pass all the request parameters, including a receiver instance, into the command’s constructor. After that, the resulting command may
be associated with one or multiple senders.

#### Q10. Select the best UML class diagram representation of the Chain of Responsibility pattern.

![m2-q8.png](src%2Fdesign-pattern%2Fm2-q8.png)

1. [ ] a
2. [x] b
3. [ ] c
4. [ ] d

#### Explanation:

Chain of Responsibility is a behavioral design pattern that lets you pass requests along a chain of handlers.

Upon receiving a request, each handler decides either to process the request or to pass it to the next handler in the chain.

**UML Diagram**:

![cor-pattern-uml-diagram.png](src%2Fdesign-pattern%2Fcor-pattern-uml-diagram.png)

The **Client** may compose chains just once or compose them dynamically, depending on the application’s logic.

**Note**: a request can be sent to any handler in the chain—it doesn't have to be the first one.

The **Handler** declares the interface, common for all concrete handlers. It usually contains just a single method for handling requests, but
sometimes it may also have another method for setting the next handler on the chain.

The **Base Handler** is an optional class where you can put the boilerplate code that’s common to all handler classes.

Usually, this class defines a field for storing a reference to the next handler. The clients can build a chain by passing a handler to the constructor
or setter of the previous handler.

The class may also implement the default handling behavior: it can pass execution to the next handler after checking for its existence.

The **Concrete Handler** contains the actual code for processing requests. Upon receiving a request, each handler must decide whether to process it
and, additionally, whether to pass it along the chain.

Handlers are usually self-contained and immutable, accepting all necessary data just once via the constructor.

#### Q11. You have a security system class, and it has 3 modes: normal, lockdown, and open. Which pattern would you use to model the behaviour in these different modes?

1. [ ] Observer
2. [x] State
3. [ ] Mediator
4. [ ] Template

#### Explanation:

State is a behavioural design pattern that lets an object alter its behaviour when its internal state changes. It appears as if the object changed its
class.

**When to Use the State Pattern**:

* Use the State pattern when you have an object that behaves differently depending on its current state,
  the number of states is enormous, and the state-specific code changes frequently.

The pattern suggests that you extract all state-specific code into a set of distinct classes. As a result, you can add new states or change existing
ones independently of each other, reducing the maintenance cost.

* Use the pattern when you have a class polluted with massive conditionals that alter how the class behaves according to the current values of the
  class’s fields.

The State pattern lets you extract branches of these conditionals into methods of corresponding state classes. While doing so, you can also clean
temporary fields and helper methods involved in state-specific code out of your main class.

* Use State when you have a lot of duplicate code across similar states and transitions of a condition-based state machine.

The State pattern lets you compose hierarchies of state classes and reduce duplication by extracting common code into abstract base classes.

#### Q12. One of your classes represents a mailbox, while another is the owner of the mailbox. The person would like to know when new mail arrives. Which design pattern will you probably use?

1. [ ] State
2. [ ] Command
3. [ ] Mediator
4. [x] Observer

#### Explanation:

Observer is a behavioral design pattern that lets you define a subscription mechanism to notify multiple objects about any events that happen to the
object they’re observing.

**When to Use the Observer Pattern**:

* Use the Observer pattern when changes to the state of one object may require changing other objects,
  and the actual set of objects is unknown beforehand or changes dynamically.

You can often experience this problem when working with classes of the graphical user interface. For example, you created custom button classes, and
you want to let the clients hook some custom code to your buttons so that it fires whenever a user presses a button.

The Observer pattern lets any object that implements the subscriber interface subscribe for event notifications in publisher objects. You can add the
subscription mechanism to your buttons, letting the clients hook up their custom code via custom subscriber classes.

* Use the pattern when some objects in your app must observe others, but only for a limited time or in specific cases.

The subscription list is dynamic, so subscribers can join or leave the list whenever they need to.

<p align="right">(<a href="#table-of-contents">back to top</a>)</p>

---

#### Module 3

#### Q1. What does MVC Stand for? Use spaces between each word, no upper case letters, and no punctuation.

**Answer**: model view controller

#### Explanation:

MVC Pattern stands for Model-View-Controller Pattern.

![mvc-pattern.png](src%2Fdesign-pattern%2Fmvc-pattern.png)

| Component  |                                                                                   Aim                                                                                   |
|:----------:|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|   Model    |               Model represents an object or JAVA POJO carrying data and business logic. It can also have logic to update controllers if its data changes.               |
|    View    |                                                  View represents the visualisation of the data that the model contains                                                  |
| Controller | Controller acts on both model and view:  1) Controls the data flow into the model object 2) Updates the view whenever data changes 3) It keeps view and model separate. |

#### Q2. Select the two elements of the open/closed principle:

1. [ ] Closed for extension.
2. [ ] Open for maintenance
3. [x] Closed for modification
4. [x] Open for extension
5. [ ] Closed for maintenance.
6. [ ] Open for modification

#### Explanation:

The Open–Closed Principle states "software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification";
that is, such an entity can allow its behaviour to be extended without modifying its source code.

Let's consider we're building a calculator app that might have several operations, such as addition and subtraction.

```java
public class Calculator {

    public void calculate(CalculatorOperation operation) {

        if (operation == null) {
            throw new InvalidParameterException("Can not perform operation");
        }

        if (operation instanceof Addition) {
            Addition addition = (Addition) operation;
            addition.setResult(addition.getLeft() + addition.getRight());
        } else if (operation instanceof Subtraction) {
            Subtraction subtraction = (Subtraction) operation;
            subtraction.setResult(subtraction.getLeft() - subtraction.getRight());
        }
    }
}
```

Although this may seem fine, it's not a good example of the OCP. When a new requirement of adding multiplication or divide functionality comes in,
we've no way besides changing the calculate method of the Calculator class.

As we've seen our calculator app is not yet OCP compliant. The code in the calculate method will change with every incoming new operation support
request. So, we need to extract this code and put it in an abstraction layer.

One solution is to delegate each operation into their respective class:

```java
public interface CalculatorOperation {
    void perform();
}
```

As a result, the Addition class could implement the logic of adding two numbers:

```java

@Getter
@Setter
public class Addition implements CalculatorOperation {

    private double left;
    private double right;
    private double result;

    public Addition(double left, double right) {
        this.left = left;
        this.right = right;
    }

    @Override
    public void perform() {
        result = left + right;
    }

}

@Getter
@Setter
public class Division implements CalculatorOperation {

    private double left;
    private double right;
    private double result;

    public Division(double left, double right) {
        this.left = left;
        this.right = right;
    }

    @Override
    public void perform() {
        if (right != 0) {
            result = left / right;
        }
    }

}
```

And finally, our Calculator class doesn't need to implement new logic as we introduce new operators:

```java
public class Calculator {

    public void calculate(CalculatorOperation operation) {
        if (operation == null) {
            throw new InvalidParameterException("Cannot perform operation");
        }
        operation.perform();
    }

}
```

Testing:

```java
public class TestCalculator {

    @Test
    public void whenAddTwoNumber_returnSum() {
        Addition addition = new Addition(RIGHT, LEFT);
        calculator.calculate(addition);
        assertEquals(SUM, addition.getResult(), 0.0);
    }
}
```

#### Q3. What is the best description of the Dependency Inversion principle?

1. [ ] Client objects are dependent on a service interface that directs their requests.
2. [x] Client objects depend on generalizations instead of concrete objects.
3. [ ] Client objects depend on an Adaptor Pattern to interface with the rest of the system.
4. [ ] Service objects subscribe to their prospective client objects as Observers, watching for a request.

#### Explanation:

The Dependency Inversion Principle (DIP) states that we should depend on abstractions instead of concrete implementations.

In other words, the abstractions should not depend on details;
Instead, the details should depend on abstractions.

Consider the example below. We have a Car class that depends on the concrete Engine class; therefore, it is not obeying DIP.

```java
public class Car {

    private Engine engine;

    public Car(Engine e) {
        engine = e;
    }

    public void start() {
        engine.start();
    }
}

public class Engine {
    public void start() {...}
}
```

The code will work, for now, but what if we wanted to add another engine type, let’s say a diesel engine? This will require refactoring the Car class.
However, we can solve this by introducing a layer of abstraction. Instead of Car depending directly on Engine, let’s add an interface:

```java
public interface Engine {
    public void start();
}
```

Now we can connect any type of Engine that implements the Engine interface to the Car class:

```java
public class Car {

    private Engine engine;

    public Car(Engine e) {
        engine = e;
    }

    public void start() {
        engine.start();
    }
}

public class PetrolEngine implements Engine {
    public void start() {...}
}

public class DieselEngine implements Engine {
    public void start() {...}
}
```

#### Q4. Which of these statements is true about the Composing Objects principle?

* it provides behaviour with aggregation instead of inheritance
* it leads to tighter coupling

1. [x] The first statement is true
2. [ ] The second statement is true
3. [ ] Neither statement is true
4. [ ] Both statements are true

#### Explanation:

Composing Objects principle (also known as Composition over Inheritance) states that classes should achieve code reuse through aggregation rather than
inheritance.

The advantages of using Composition over Inheritance:

1. Inheritance is tightly coupled whereas composition is loosely coupled.
2. There is no access control in inheritance whereas access can be restricted in composition.
3. Composition provides flexibility in invocation of methods that is useful with multiple subclass scenario.
4. One more benefit of composition over inheritance is testing scope. Unit testing is easy in composition because we know what all methods we are
   using from another class. We can mock it up for testing whereas in inheritance we depend heavily on superclass and don’t know what all methods of
   superclass will be used.

**Link**: [Composition vs Inheritance](https://www.digitalocean.com/community/tutorials/composition-vs-inheritance)

Design patterns, such as the Composite design pattern and Decorator design pattern use this design principle. Both of these patterns compose concrete
classes in order to build more complex objects at one time.

#### Q5. Which of these UML diagrams demonstrates the Interface Segregation principle?

![m3-q5.png](src%2Fdesign-pattern%2Fm3-q5.png)

1. [ ] a)
2. [ ] b)
3. [ ] c)
4. [x] d)

#### Explanation:

The Interface Segregation Principle (ISP) states that clients should not be forced to depend on interface members they do not use.

In other words, do not force any client to implement an interface that is irrelevant to them.

Suppose there’s an interface for vehicle and a Bike class:

```java
public interface Vehicle {
    public void drive();

    public void stop();

    public void refuel();

    public void openDoors();
}

public class Bike implements Vehicle {

    public void drive() {...}

    public void stop() {...}

    public void refuel() {...}

    // Can not be implemented
    public void openDoors() {...}
}
```

As you can see, it does not make sense for a Bike class to implement the openDoors() method as a bike does not have any doors!

To fix this, ISP proposes that the interfaces be broken down into multiple, small cohesive interfaces so that no class is forced to implement any
interface, and therefore methods that it does not need.

#### Q6. Which of these code examples violates the Principle of The Least Knowledge, or Law of Demeter?

```java
public class O {
    M I = new M();

    public void anOperation2() {
        this.I.N.anOperation();
    }
}
```

```java
public class Class1 {
    public void N() {
        System.out.println("Method N invoked");
    }
}

public class Class2 {
    public void M(Class1 P) {
        P.N();
        System.out.println("Method M invoked");
    }
```

```java
public class O {
    public void M() {
        this.N();
        System.out.println("Method M invoked");
    }

    public void N() {
        System.out.println("Method N invoked");
    }
}
```

```java
public class P {
    public void N() {
        System.out.println("Method N invoked");
    }
}

public class O {
    public void M() {
        P I = new P();
        I.N();
        System.out.println("Method M invoked");
    }
} 
```

1. [x] 1
2. [ ] 2
3. [ ] 3
4. [ ] 4

#### Explanation:

According to the law of Demeter, classes should know about and interact with a few other classes as possible. It is used to loosen the coupling by
limiting class interaction with other classes to provide stability as tighter coupling makes the program difficult to maintain.

Considered as local Objects:

1. Objects passed in parameter;
2. Instantiated within a method;
3. An instance variable of a Class;

In the law of Demeter a method should not invoke methods of any object that is not local.

Rules of Law of Demeter

1. Method M of an object O can invoke the method of O itself
2. Method M can call methods of any parameter P
3. Method M can call objects created within M
4. Method M in object O can invoke methods of any type of object that is a direct component of O

The following example breaks the Law of Demeter principle:

```java
public class O {
    M I = new M();

    public void anOperation2() {
        this.I.N.anOperation();
    }
}
```

#### Q7. How can Comments be considered a code smell?

1. [ ] When a comment is used to explain the rationale behind a design decision
2. [x] Excessive commenting can be a coverup for bad code
3. [ ] They can’t! Comments help clarify code.
4. [ ] Too many comments make the files too large to compile.

#### Explanation:

Often, a clarification comment is a code smell.

It tells you that your code is too complex. You should strive to remove clarification comments and simplify the code instead because, “_good code is
self-documenting_.”

#### Q8. What is the primitive obsession code smell about?

1. [ ] Code that contains many low-level objects, without using OO principles like aggregation or inheritance.
2. [x] Overuse of primitive data types like int, long, float
3. [ ] Using many primitive types instead of settling on a few that together capture that appropriate level of detail for your system.
4. [ ] Using key-value pairs instead of abstract data types.

#### Explanation:

Primitive Obsession is when the code relies too much on primitives. It means that a primitive value controls the logic in a class and this value is
not type safe.

Therefore, primitive obsession is when you have a bad practice of using primitive types to represent an object.

Signs and Symptoms:

1. Use of primitives instead of small objects for simple tasks (such as currency, ranges, special strings for phone numbers, post
   code, etc.)
2. Use of constants for coding information (such as a constant USER_ADMIN_ROLE = 1 for referring to users with administrator rights.)
3. Use of string constants as field names for use in data arrays.

#### Q9. You have a class that you keep adding to. Whenever you add new functionality, it just seems like the most natural place to put it, but it is starting to become a problem! Which code smell is this?

1. [ ] Long Method
2. [x] Large Class
3. [ ] Divergent Change
4. [ ] Speculative generality

#### Explanation:

Large Class code smell refers to the classes that tend to centralize the intelligence of the system.

Large Class indicates weaknesses in design that can possibly slow down the development or increase the chance of failures in the future. In addition,
it makes the system more difficult to understand, read and develop.

#### Q10. Why is it important to avoid message chains whenever possible?

1. [ ] If an unexpected object is returned, this could easily lead to runtime errors.
2. [ ] They lower cohesion in your class.
3. [x] The resulting code is usually rigid and complex.
4. [ ] It's a workaround to get to private methods, which are important for encapsulation.

#### Explanation:

The message chain smell arises when a particular class is highly coupled to other classes in chain-like delegations.

To illustrate this smell, suppose we have Class A who needs data from Class E. To retrieve this data, object A firstly needs to retrieve object E from
object D from object C from object B.

**Reasons for the Problem**:

A message chain occurs when a client requests another object, that object requests yet another one, and so on. These chains mean that the client is
dependent on navigation along the class structure. Any changes in these relationships require modifying the client.

**Disadvantages**:

1. Code coupling
2. Complexity
3. Testability

#### Q11. Look at the code snippet. Which code smell do you detect?

```java
public class Class1 {

...

    public void M(Class2 C) {
        C.doSomething(x);
        C.foo(y);
        C.foo2(z, i);
    }
}
```

1. [ ] Long Parameter List
2. [ ] Inappropriate Intimacy
3. [ ] Divergent Change
4. [x] Feature Envy

#### Explanation:

Feature envy is defined as occurring when a method calls methods on another class more times than on the source class.

It often indicates that the intended functionality is located in the wrong class.

Example with feature envy:

```java
public class Phone {
    private final String unformattedNumber;

    public Phone(String unformattedNumber) {
        this.unformattedNumber = unformattedNumber;
    }

    public String getAreaCode() {
        return unformattedNumber.substring(0, 3);
    }

    public String getPrefix() {
        return unformattedNumber.substring(3, 6);
    }

    public String getNumber() {
        return unformattedNumber.substring(6, 10);
    }
}

public class Customer {
    private Phone mobilePhone;

    public String getMobilePhoneNumber() {
        return "(" +
                mobilePhone.getAreaCode() + ") " +
                mobilePhone.getPrefix() + "-" +
                mobilePhone.getNumber();
    }
}
```

Example without feature envy:

```java
public class Phone {
    private final String unformattedNumber;

    public Phone(String unformattedNumber) {
        this.unformattedNumber = unformattedNumber;
    }

    private String getAreaCode() {
        return unformattedNumber.substring(0, 3);
    }

    private String getPrefix() {
        return unformattedNumber.substring(3, 6);
    }

    private String getNumber() {
        return unformattedNumber.substring(6, 10);
    }

    public String toFormattedString() {
        return "(%s) %s-%s".formatted(getAreaCode(), getPrefix(), getNumber());
    }
}

public class Customer {
    private Phone mobilePhone;

    public String getMobilePhoneNumber() {
        return mobilePhone.toFormattedString();
    }
}
```

#### Q12. Joseph was developing a class for his smartphone poker game, and decided that one day he would like to be able to change the picture on the backs of the cards, so he created a Deck superclass. Since his app does not have that feature yet, Deck has only one subclass, RegularDeck. What code smell is this?

1. [ ] Primitive Obsession
2. [ ] Divergent Change
3. [x] Speculative Generality
4. [ ] Refused Bequest
5. [ ] Report an issue

#### Explanation:

Speculative Generality is where code is written with so much caution for possible future changes, that the code becomes unnecessarily complex and
harder to read. It is considered good practice to consider possible future development when writing code, but Speculative Generality is when this is
overdone.

<p align="right">(<a href="#table-of-contents">back to top</a>)</p>

---

#### Module 4
