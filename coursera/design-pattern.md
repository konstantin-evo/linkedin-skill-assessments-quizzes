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

Therefore, they are most effective when applied to problems that have been encountered before and have well-established solutions.

Additionally, design patterns can be helpful when explaining a solution to other developers as they provide a shared language and understanding of the
problem and solution.

Using a design pattern for a unique problem or when fixing spaghetti code may not be the most effective approach as it may not fit the specific needs
of the problem and may introduce unnecessary complexity.

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

![factory-pattern-example.jpeg](..%2Fsrc%2Fdesign-pattern%2Ffactory-pattern-example.jpeg)

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

![m1-q6.png](..%2Fsrc%2Fdesign-pattern%2Fm1-q6.png)

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

![adapter-pattern-uml-diagram.jpeg](..%2Fsrc%2Fdesign-pattern%2Fadapter-pattern-uml-diagram.jpeg)

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

![composite-pattern-uml-diagram.png](..%2Fsrc%2Fdesign-pattern%2Fcomposite-pattern-uml-diagram.png)

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

The option that is NOT a common application of the Proxy Pattern is "Information proxy".

The other options are common applications of the Proxy Pattern:

1. **Remote proxy**: A remote proxy provides a local representative for an object that exists in a different address space, usually on a different
   machine.
2. **Protection proxy**: A protection proxy controls access to the original object. It is useful in situations where some clients should not have
   access to the real object.
3. **Virtual proxy**: A virtual proxy creates expensive objects on demand. It is used when creating an object is expensive or when an object needs to
   be accessed in a lazy manner.

The Information Proxy is not a common application of the Proxy Pattern. The term "information proxy" is not a well-defined pattern name. It is
possible that it refers to some specific usage of a proxy pattern in a particular context. However, it is not a standard use case for the Proxy
Pattern.

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

![decorator-pattern-uml-diagram.webp](..%2Fsrc%2Fdesign-pattern%2Fdecorator-pattern-uml-diagram.webp)

**The Decorator Pattern in real life**:

Wearing clothes is an example of using decorators. When you’re cold, you wrap yourself in a sweater. If you’re still cold with a sweater, you can wear
a jacket on top. If it’s raining, you can put on a raincoat.

All of these garments “extend” your basic behavior but aren’t part of you, and you can easily take off any piece of clothing whenever you don’t need
it.

**The Decorator Pattern Example**:

Suppose we have a Christmas tree object, and we want to decorate it. The decoration does not change the object itself; it’s just that in addition to
the Christmas tree, we're adding some decoration items like garland, tinsel, tree-topper, bubble lights, etc.:

![decorator-pattern-uml-diagram-example.jpeg](..%2Fsrc%2Fdesign-pattern%2Fdecorator-pattern-uml-diagram-example.jpeg)

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

![m2-q1.png](..%2Fsrc%2Fdesign-pattern%2Fm2-q1.png)

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

![template-method-structure.png](..%2Fsrc%2Fdesign-pattern%2Ftemplate-method-structure.png)

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

The Chain of Responsibility pattern is used when there are multiple objects that can handle a request, but it's not known which object can handle the
request at runtime.

The pattern allows the request to be passed down a chain of objects until one of the objects can handle it. This avoids coupling the sender of the
request to the receiver, and allows multiple objects to handle the request without the sender knowing which one will handle it.

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

![cor-pattern-example.png](..%2Fsrc%2Fdesign-pattern%2Fcor-pattern-example.png)

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

The correct answers are:

1. It allows the current state object to decide how to achieve behaviors specific to the state of the context.
2. It allows the current state to be copied from one instance to another.
3. It turns the context into a client of the state.

Encapsulating state in an object in the State Pattern allows the context object to delegate behavior to the current state object. This means that the
behavior of the context object depends on the state object it is currently holding. By encapsulating state, the current state object can determine how
to achieve behaviors that are specific to the state of the context.

Copying the current state object from one instance to another is also a benefit of encapsulating state in an object. This can be useful when creating
new instances of a context object with the same state as an existing instance.

Finally, encapsulating state in an object turns the context into a client of the state. This means that the context object depends on the state object
to determine its behavior, rather than the other way around.

**Example of implementation**:

let's implement a mobile state scenario. With respect to alerts, a mobile can be in different states.

For example, vibration and silence. Based on this alert state, the behavior of the mobile changes when an alert is to be done.

```java
interface MobileAlertState {
    public void alert(AlertStateContext ctx);
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

Command is a behavioural design pattern that turns a request into a stand-alone object that contains all information about the request.

Simply put, the pattern intends to encapsulate in an Object all the data required for performing a given action (command), including:

1. What method to call;
2. The method's arguments;
3. The Object (known as the receiver) to which the method belongs.

The correct answer is 1. Encapsulation, generalization, and loose coupling are the design principles that the Command Pattern uses.

Encapsulation is used to encapsulate a request as an object, thus allowing the request to be parameterized with different arguments, queued, or
logged.

Generalization is used to create a common interface for all commands, which allows them to be treated uniformly and simplifies the design.

Loose coupling is used to separate the object that invokes the operation from the object that knows how to perform it, by having the invoker hold a
reference to an abstract Command, rather than to a concrete command. This decouples the invoker from the concrete command, allowing for greater
flexibility and extensibility in the design.

An example of how the Command Pattern can be implemented in Java:

First, we'll create an interface for the Command:

```java
public interface Command {
    public void execute();
}
```

Next, we'll create a few concrete commands that implement this interface.

Here, we've created four different commands: `LightOnCommand`, `LightOffCommand`, `FanOnCommand`, and `FanOffCommand`. Each command takes a different
receiver object (a `Light` or a `Fan`) as a parameter in its constructor and implements the `execute()` method, which calls the corresponding method
on the receiver object.

```java
public class LightOnCommand implements Command {
    private Light light;

    public LightOnCommand(Light light) {
        this.light = light;
    }

    public void execute() {
        light.switchOn();
    }
}

public class LightOffCommand implements Command {
    private Light light;

    public LightOffCommand(Light light) {
        this.light = light;
    }

    public void execute() {
        light.switchOff();
    }
}

public class FanOnCommand implements Command {
    private Fan fan;

    public FanOnCommand(Fan fan) {
        this.fan = fan;
    }

    public void execute() {
        fan.switchOn();
    }
}

public class FanOffCommand implements Command {
    private Fan fan;

    public FanOffCommand(Fan fan) {
        this.fan = fan;
    }

    public void execute() {
        fan.switchOff();
    }
}
```

Finally, we'll create an Invoker class that can be used to execute the commands:

```java
public class RemoteControl {
    private Command command;

    public void setCommand(Command command) {
        this.command = command;
    }

    public void pressButton() {
        command.execute();
    }
}
```

Here, the `RemoteControl` class has a `Command` instance variable, and a setCommand method that can be used to set the command to be executed.
The `pressButton()` method is used to execute the command.

```java
public class Main {
    public static void main(String[] args) {

        // Create the receiver objects
        Light light = new Light();
        Fan fan = new Fan();

        // Create the commands
        LightOnCommand lightOn = new LightOnCommand(light);
        LightOffCommand lightOff = new LightOffCommand(light);
        FanOnCommand fanOn = new FanOnCommand(fan);
        FanOffCommand fanOff = new FanOffCommand(fan);

        // Create the invoker object
        RemoteControl remote = new RemoteControl(lightOn);

        // Execute the commands
        remote.pressButton();

        remote.setCommand(fanOn);
        remote.pressButton();

        remote.setCommand(lightOff);
        remote.pressButton();

        remote.setCommand(fanOff);
        remote.pressButton();
    }
}
```

#### Q5. Which are the minimum requirements of the Observer pattern? Choose the three that are correct.

1. [x] method to notify observers
2. [x] methods to add or remove observers
3. [x] update method in observers
4. [ ] a state variable to determine if observers have been notified.

#### Explanation:

Observer is a behavioural design pattern that lets you define a subscription mechanism to notify multiple objects about any events that happen to the
object they’re observing.

Here are the three minimum requirements of the Observer pattern:

1. A method to notify observers;
2. Methods to add or remove observers;
3. An update method in observers.

The fourth option, "a state variable to determine if observers have been notified," is not a requirement of the Observer pattern.

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
observers about it by calling their `update()` method.

To be able to do that, the observable object needs to keep references to the observers. In our case, it's the “channels” variable.

Now let's see what the observer, the Channel class, can look like. It should have the `update()` method, which is invoked when the state of NewsAgency
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

```java
public class NewsAgencyTest {
    @Test
    public void testObserverPattern() {
        NewsAgency observable = new NewsAgency();
        NewsChannel observer = new NewsChannel();

        observable.addObserver(observer);
        observable.setNews("news");

        assertEquals(observer.getNews(), "news");
    }
}
```

#### Q6. When are you most likely to need a Mediator pattern?

1. [ ] When you want to de-couple a class that is requesting a service from one that is providing it.
2. [x] When you are coordinating the activities of a set of related classes.
3. [ ] When your class is sending a request that might be handled by one of several handlers.
4. [ ] When you have two classes with different interfaces that you must connect.

#### Explanation:

The Mediator pattern is most likely to be needed when you want to de-couple a class that is requesting a service from one that is providing it. This
can help to reduce dependencies between classes and simplify the overall design of your system.

For example, let's say you have a system that consists of a number of different components that need to communicate with each other. If each component
communicates directly with every other component, you end up with a tightly-coupled system that can be difficult to maintain and extend. By
introducing a Mediator object between the components, you can reduce the number of direct dependencies and provide a centralized point of control for
communication.

Example of implementation in answer to the next question.

#### Q7. You have a machine performing a complex manufacturing task, with different sensors and different components of the machine represented by different classes. Which design pattern will you use to arrange the parts?

1. [ ] Template
2. [ ] Command
3. [x] Mediator
4. [ ] Chain of Responsibility

#### Explanation:

The Mediator is a behavioural design pattern that lets you reduce chaotic dependencies between objects.

The Mediator design pattern is a suitable choice for arranging the different sensors and components of a machine performing a complex manufacturing
task. The Mediator pattern helps to reduce the coupling between the individual classes, and instead allows them to communicate with each other
indirectly through a mediator object.

Here's an example implementation of the Mediator pattern in Java that shows how you could use it to arrange the different sensors and components of a
machine.

We define the `MachineMediator` interface to represent the mediator object, and the `Component` interface to represent the individual components of
the machine. We then create concrete `SensorComponent` and `MachineComponent` classes to implement the `Component` interface.

We also define a `MachineMediatorImpl` class to provide a concrete implementation of the `MachineMediator` interface. This class maintains a list of
all the components that it is mediating, and provides methods for starting and stopping all the components, as well as a `notify()` method for
notifying the mediator when a component performs an action.

```java
import lombok.Setter;
import lombok.Getter;

import java.util.ArrayList;
import java.util.List;

// Define the Mediator interface
public interface MachineMediator {
    void start();

    void stop();

    void notify(Component component, String event);
}

// Define the Component interface
public interface Component {
    void setMediator(MachineMediator mediator);

    void start();

    void stop();

    void doAction(String event);
}

// Define a Concrete Component class for sensor components
@Getter
@Setter
class SensorComponent implements Component {
    private MachineMediator mediator;

    public void start() {
        System.out.println("Starting sensor");
    }

    public void stop() {
        System.out.println("Stopping sensor");
    }

    public void doAction(String event) {
        System.out.println("Sensor doing " + event);
        mediator.notify(this, event);
    }
}

// Define a Concrete Component class for machine components
@Getter
@Setter
class MachineComponent implements Component {
    private MachineMediator mediator;

    public void start() {
        System.out.println("Starting machine");
        mediator.notify(this, "start");
    }

    public void stop() {
        System.out.println("Stopping machine");
        mediator.notify(this, "stop");
    }

    public void doAction(String event) {
        System.out.println("Machine doing " + event);
    }
}

// Define a Concrete Mediator class
@Getter
@Setter
class MachineMediatorImpl implements MachineMediator {
    private List<Component> components = new ArrayList<>();

    public void addComponent(Component component) {
        components.add(component);
        component.setMediator(this);
    }

    public void start() {
        for (Component component : components) {
            component.start();
        }
    }

    public void stop() {
        for (Component component : components) {
            component.stop();
        }
    }

    public void notify(Component component, String event) {
        if (event.equals("start")) {
            System.out.println("Starting " + component.getClass().getSimpleName());
        } else if (event.equals("stop")) {
            System.out.println("Stopping " + component.getClass().getSimpleName());
        }
    }
}

// Usage example
public class Main {
    public static void main(String[] args) {
        // Create some sensor components
        Component sensor1 = new SensorComponent();
        Component sensor2 = new SensorComponent();

        // Create a machine component that contains the sensors
        Component machine1 = new MachineComponent();

        // Create a mediator and add the components to it
        MachineMediator mediator = new MachineMediatorImpl();
        mediator.addComponent(sensor1);
        mediator.addComponent(sensor2);
        mediator.addComponent(machine1);

        // Start and stop the mediator, which will start and stop all of the components
        mediator.start();
        mediator.stop();
    }
}
```

#### Q8. Marlon is coding part of the software that follows a similar sequence of steps. Depending on the type of object, these steps will be implemented in slightly different ways, but their order is always the same. Which design pattern could Marlon use?

1. [x] Template pattern
2. [ ] Mediator pattern
3. [ ] Command pattern
4. [ ] State pattern

#### Explanation:

Marlon could use the Template pattern to implement the sequence of steps with variations for different object types.

The Template pattern defines the skeleton of an algorithm in a method, deferring some steps to subclasses. The subclasses can override certain steps
of the algorithm without changing its structure.

Here is an example implementation of the Template pattern in Java:

The `ObjectProcessor` class defines the sequence of steps in the `processObject` method, which is the template method. The `TextProcessor`
and `ImageProcessor` classes inherit from `ObjectProcessor` and override the primitive operations to implement the steps in a specific way for text
and image objects, respectively. Finally, the Main class creates instances of the concrete processors and calls their `processObject` methods to
execute the algorithm.

```java
abstract class ObjectProcessor {
    // This is the template method that defines the sequence of steps
    public void processObject() {
        openFile();
        readData();
        processData();
        closeFile();
    }

    // These methods are primitive operations that can be overridden by subclasses
    protected abstract void openFile();

    protected abstract void readData();

    protected abstract void processData();

    protected abstract void closeFile();
}

class TextProcessor extends ObjectProcessor {
    protected void openFile() {
        System.out.println("Opening text file...");
    }

    protected void readData() {
        System.out.println("Reading text data...");
    }

    protected void processData() {
        System.out.println("Processing text data...");
    }

    protected void closeFile() {
        System.out.println("Closing text file...");
    }
}

class ImageProcessor extends ObjectProcessor {
    protected void openFile() {
        System.out.println("Opening image file...");
    }

    protected void readData() {
        System.out.println("Reading image data...");
    }

    protected void processData() {
        System.out.println("Processing image data...");
    }

    protected void closeFile() {
        System.out.println("Closing image file...");
    }
}

public class Main {
    public static void main(String[] args) {
        ObjectProcessor textProcessor = new TextProcessor();
        ObjectProcessor imageProcessor = new ImageProcessor();

        textProcessor.processObject();
        imageProcessor.processObject();
    }
}
```

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

![command-pattern-uml-diagram.png](..%2Fsrc%2Fdesign-pattern%2Fcommand-pattern-uml-diagram.png)

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

![m2-q8.png](..%2Fsrc%2Fdesign-pattern%2Fm2-q8.png)

1. [ ] a
2. [x] b
3. [ ] c
4. [ ] d

#### Explanation:

Chain of Responsibility is a behavioral design pattern that lets you pass requests along a chain of handlers.

Upon receiving a request, each handler decides either to process the request or to pass it to the next handler in the chain.

**UML Diagram**:

![cor-pattern-uml-diagram.png](..%2Fsrc%2Fdesign-pattern%2Fcor-pattern-uml-diagram.png)

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

The State pattern would be suitable for modeling the behavior in the different security system modes. This pattern allows an object to change its
behavior when its internal state changes. In this case, the security system object can change its behavior based on the current mode it's in.

Here's an example of implementing the State pattern in Java for the security system class:

```java
// State interface
public interface SecuritySystemState {
    void enterPassword(String password);

    void switchMode(String mode);
}

// Normal mode state
public class NormalModeState implements SecuritySystemState {
    private SecuritySystem securitySystem;

    public NormalModeState(SecuritySystem securitySystem) {
        this.securitySystem = securitySystem;
    }

    @Override
    public void enterPassword(String password) {
        // Check if password is correct
        if (password.equals("1234")) {
            System.out.println("Correct password entered. System disarmed.");
            securitySystem.setState(new OpenModeState(securitySystem));
        } else {
            System.out.println("Incorrect password entered.");
        }
    }

    @Override
    public void switchMode(String mode) {
        if (mode.equals("lockdown")) {
            System.out.println("Switching to lockdown mode.");
            securitySystem.setState(new LockdownModeState(securitySystem));
        } else if (mode.equals("open")) {
            System.out.println("Switching to open mode.");
            securitySystem.setState(new OpenModeState(securitySystem));
        } else {
            System.out.println("Invalid mode specified.");
        }
    }
}

// Lockdown mode state
public class LockdownModeState implements SecuritySystemState {
    private SecuritySystem securitySystem;

    public LockdownModeState(SecuritySystem securitySystem) {
        this.securitySystem = securitySystem;
    }

    @Override
    public void enterPassword(String password) {
        System.out.println("System in lockdown mode. Password entry disabled.");
    }

    @Override
    public void switchMode(String mode) {
        if (mode.equals("normal")) {
            System.out.println("Switching to normal mode.");
            securitySystem.setState(new NormalModeState(securitySystem));
        } else if (mode.equals("open")) {
            System.out.println("Switching to open mode.");
            securitySystem.setState(new OpenModeState(securitySystem));
        } else {
            System.out.println("Invalid mode specified.");
        }
    }
}

// Open mode state
public class OpenModeState implements SecuritySystemState {
    private SecuritySystem securitySystem;

    public OpenModeState(SecuritySystem securitySystem) {
        this.securitySystem = securitySystem;
    }

    @Override
    public void enterPassword(String password) {
        System.out.println("System already disarmed.");
    }

    @Override
    public void switchMode(String mode) {
        if (mode.equals("normal")) {
            System.out.println("Switching to normal mode.");
            securitySystem.setState(new NormalModeState(securitySystem));
        } else if (mode.equals("lockdown")) {
            System.out.println("Switching to lockdown mode.");
            securitySystem.setState(new LockdownModeState(securitySystem));
        } else {
            System.out.println("Invalid mode specified.");
        }
    }
}

// Context class
public class SecuritySystem {
    private SecuritySystemState state;

    public SecuritySystem() {
        this.state = new NormalModeState(this);
    }

    public void setState(SecuritySystemState state) {
        this.state = state;
    }

    public void enterPassword(String password) {
        state.enterPassword(password);
    }

    public void switchMode(String mode) {
        state.switchMode(mode);
    }
}
```

#### Q12. One of your classes represents a mailbox, while another is the owner of the mailbox. The person would like to know when new mail arrives. Which design pattern will you probably use?

1. [ ] State
2. [ ] Command
3. [ ] Mediator
4. [x] Observer

#### Explanation:

The Observer design pattern is a good choice for this scenario, as it allows objects to subscribe to and receive notifications when a subject
undergoes a change.

Here's an example implementation in Java using the Observer pattern:

Define the `Observer` interface, which will be implemented by the Mailbox class:

```java
public interface Observer {
    public void update(boolean hasNewMail);
}
```

Implement the `Subject` interface, which defines the methods for registering, removing, and notifying observers:

```java
public interface Subject {
    public void registerObserver(Observer o);

    public void removeObserver(Observer o);

    public void notifyObservers();
}
```

Implement the `Owner` class, which will act as the subject and maintain a list of observers (the mailboxes):

```java
import java.util.ArrayList;
import java.util.List;

public class Owner implements Subject {

    private List<Observer> observers;
    private boolean hasNewMail;

    public Owner() {
        this.observers = new ArrayList<>();
        this.hasNewMail = false;
    }

    public void setHasNewMail(boolean hasNewMail) {
        this.hasNewMail = hasNewMail;
        notifyObservers();
    }

    @Override
    public void registerObserver(Observer o) {
        observers.add(o);
    }

    @Override
    public void removeObserver(Observer o) {
        observers.remove(o);
    }

    @Override
    public void notifyObservers() {
        for (Observer observer : observers) {
            observer.update(hasNewMail);
        }
    }
}
```

Implement the `Mailbox` class, which will act as the observer and implement the update method:

```java
public class Mailbox implements Observer {

    private String ownerName;
    private boolean hasNewMail;

    public Mailbox(String ownerName) {
        this.ownerName = ownerName;
        this.hasNewMail = false;
    }

    @Override
    public void update(boolean hasNewMail) {
        this.hasNewMail = hasNewMail;
        if (hasNewMail) {
            System.out.println("Hey " + ownerName + ", you've got mail!");
        } else {
            System.out.println("No new mail for " + ownerName);
        }
    }

}
```

Finally, here's an example usage:

```java
public class Main {

    public static void main(String[] args) {

        Owner owner = new Owner();
        Mailbox mailbox1 = new Mailbox("Alice");
        Mailbox mailbox2 = new Mailbox("Bob");
        Mailbox mailbox3 = new Mailbox("Charlie");

        owner.registerObserver(mailbox1);
        owner.registerObserver(mailbox2);
        owner.registerObserver(mailbox3);

        // simulate new mail arriving
        owner.setHasNewMail(true);
    }

}
```

In this example, the `Owner` class acts as the subject and maintains a list of observers (the mailboxes). When the owner receives new mail, it
calls `setHasNewMail(true)` which in turn calls `notifyObservers()` to update all registered mailboxes. The update method of each mailbox is then
called, which updates the mailbox's `hasNewMail` state and prints a message to the console.

---

#### Module 3

#### Q1. What does MVC Stand for? Use spaces between each word, no upper case letters, and no punctuation.

**Answer**: model view controller

#### Explanation:

MVC Pattern stands for Model-View-Controller Pattern.

![mvc-pattern.png](..%2Fsrc%2Fdesign-pattern%2Fmvc-pattern.png)

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

The design pattern used in the improved implementation is the Strategy pattern. The Strategy pattern allows encapsulating a family of related
algorithms or behaviors and making them interchangeable without changing the object's client's interface.

In this case, the `CalculatorOperation` interface represents the family of algorithms that can be performed by the calculator. Each
operation (`Addition`, `Subtraction`, `Division`) implements the `CalculatorOperation` interface and provides its own implementation of
the `perform()` method, which encapsulates the algorithm's logic for that specific operation.

The `Calculator` class is decoupled from the specific operation's implementation details and only knows how to invoke the `perform()` method on the
provided `CalculatorOperation` object. Therefore, the Strategy pattern enables us to add new operations without modifying the Calculator class's
code, making it more open for extension and less prone to errors.

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
2. There is no access control in inheritance whereas access can be restricted in composition. In other words, the child class has full access to all
   the public, protected, and package-private members of the parent class.
3. Composition provides flexibility in invocation of methods that is useful with multiple subclass scenario.
4. One more benefit of composition over inheritance is testing scope. Unit testing is easy in composition because we know what all methods we are
   using from another class. We can mock it up for testing whereas in inheritance we depend heavily on superclass and don’t know what all methods of
   superclass will be used.

**Link**: [Composition vs Inheritance](https://www.digitalocean.com/community/tutorials/composition-vs-inheritance)

Design patterns, such as the Composite design pattern and Decorator design pattern use this design principle. Both of these patterns compose concrete
classes in order to build more complex objects at one time.

#### Q5. Which of these UML diagrams demonstrates the Interface Segregation principle?

![m3-q5.png](..%2Fsrc%2Fdesign-pattern%2Fm3-q5.png)

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

For example, consider a class that represents a customer's address using primitive data types:

```java
public class Customer {
    private String firstName;
    private String lastName;
    private String streetAddress;
    private String city;
    private String state;
    private String zipCode;
// ...
}
```

This class has a primitive obsession code smell because it uses primitive data types to represent a complex concept like an address. As a result, it
can be difficult to maintain and understand, especially if the same logic for validating addresses is scattered throughout the codebase.

Instead of using primitive types, we can create a custom Address class that encapsulates the concept of an address and provides behavior for it. For
example:

```java
public class Address {
    private String streetAddress;
    private String city;
    private String state;
    private String zipCode;

    public Address(String streetAddress, String city, String state, String zipCode) {
        this.streetAddress = streetAddress;
        this.city = city;
        this.state = state;
        this.zipCode = zipCode;
    }

    public boolean isValid() {
        // implementation for validating address
    }

    // getters and setters
}

public class Customer {
    private String firstName;
    private String lastName;
    private Address address;
// ...
}
```

This approach improves the maintainability and readability of the code. By creating a custom class for the address, we can encapsulate the behavior
and validation logic of the address, making it easier to understand and maintain. Additionally, we can reuse the same `Address` class across the
application, making the code more consistent and reducing duplication.

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

#### Q1. Mohsin needs to create various user objects for his University learning platform. What is the act of creating an object called?

1. [ ] object invocation
2. [ ] object realization
3. [ ] class creation
4. [x] concrete instantiation

#### Explanation:

The act of creating an object is called instantiation.

In the case of Mohsin creating user objects for his University learning platform, he would first need to define a `User` class that describes the
properties and behaviors of a user on the platform, and then create instances of that class to represent individual users.

Each instance of the `User` class would be a separate object with its own set of attributes and methods, and Mohsin would be able to interact with
those
objects programmatically to manage user accounts and perform other platform functions.

Here's an example in Java that demonstrates how to create an object using a class:

```java
public class User {
    String username;
    String email;

    public User(String username, String email) {
        this.username = username;
        this.email = email;
    }

    public void printDetails() {
        System.out.println("Username: " + username);
        System.out.println("Email: " + email);
    }
}

    // Creating an object of the User class
    User user1 = new User("johndoe", "johndoe@example.com");

// Accessing object's properties and methods
    System.out.println("User details:");
            user1.printDetails();
```

In this example, we have defined a User class with two instance variables username and email. We have also defined a constructor method that takes two
parameters and initializes the instance variables with those values.

To create an object of the User class, we use the new keyword followed by the name of the class and the constructor arguments. In this case, we are
creating an object named user1 with the username "johndoe" and the email "johndoe@example.com".

Once the object is created, we can access its properties and methods using the dot notation. In this example, we are calling the printDetails method
of the user1 object to print its properties to the console.

#### Q2. Mohsin has a superclass that performs various operations on these user objects - Student, Professor, Assistant, for example. He wants the subclass to determine which object is created. This is sketched below in a UML diagram for the StudentUser class. What is this design pattern called?

![m4-q2.png](..%2Fsrc%2Fdesign-pattern%2Fm4-q2.png)

1. [ ] Template Pattern
2. [x] Factory Method Pattern
3. [ ] Simple Factory
4. [ ] Composite Pattern

#### Explanation:

The design pattern depicted in the UML diagram is the Factory Method pattern.

The Factory Method pattern is a creational design pattern that provides an interface for creating objects, but allows subclasses to alter the type of
objects that will be created. In this pattern, a superclass provides a factory method, which is responsible for creating objects of a particular type.
Subclasses then override the factory method to specify the types of objects that should be created.

Here's an example of how this pattern can be implemented in Java, using the UML diagram as a guide:

```java
// Superclass that defines the factory method
public abstract class UserFactory {
    public abstract User createUser();
}

// Concrete subclass that implements the factory method to create Student objects
public class StudentFactory extends UserFactory {
    public User createUser() {
        return new Student();
    }
}

// Concrete subclass that implements the factory method to create Professor objects
public class ProfessorFactory extends UserFactory {
    public User createUser() {
        return new Professor();
    }
}

// Concrete subclass that implements the factory method to create Assistant objects
public class AssistantFactory extends UserFactory {
    public User createUser() {
        return new Assistant();
    }
}

// Abstract superclass for all user objects
public abstract class User {
// Define common properties and methods for all user objects
}

// Concrete subclass for student user objects
public class Student extends User {
// Define properties and methods specific to student user objects
}

// Concrete subclass for professor user objects
public class Professor extends User {
// Define properties and methods specific to professor user objects
}

// Concrete subclass for assistant user objects
public class Assistant extends User {
// Define properties and methods specific to assistant user objects
}
```

With this implementation, Mohsin can create new user objects by calling the `createUser()` method on an instance of the appropriate UserFactory
subclass. For example:

```
// Create a new Student object using a StudentFactory
        UserFactory studentFactory = new StudentFactory();
        User student = studentFactory.createUser();

// Create a new Professor object using a ProfessorFactory
        UserFactory professorFactory = new ProfessorFactory();
        User professor = professorFactory.createUser();

// Create a new Assistant object using an AssistantFactory
        UserFactory assistantFactory = new AssistantFactory();
        User assistant = assistantFactory.createUser();
```

This way, the `UserFactory` subclasses determine which type of User object is created, allowing Mohsin to easily create new user objects without
worrying about the details of object creation.

#### Q3. Select the correct UML class diagram representation of the Composite Pattern:

![m4-q3.png](..%2Fsrc%2Fdesign-pattern%2Fm4-q3.png)

1. [ ] a)
2. [ ] b)
3. [ ] c)
4. [x] d)

#### Explanation:

The Composite Pattern is a design pattern that allows you to treat a group of objects in the same way as a single instance of an object. It is used
when you have a hierarchical structure of objects, and you want to treat both the individual objects and the groups of objects in the same way.

In the Composite Pattern, there is a base class or interface that defines the common methods and properties that all the objects in the hierarchy
share.

We can break the pattern down into 4 parts:

1. Component
2. Leaf
3. Composite
4. Client

|   Part    |                                                                               Description                                                                                |
|:---------:|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| component | The base interface for all the objects in the composition. It should be either an interface or an abstract class with the common methods to manage the child composites. |
|   leaf    |                               Implements the default behaviour of the base component. It doesn't contain a reference to the other objects.                               |
| composite |                                    Implements the base component methods and defines the child-related operations (has leaf elements)                                    |
|  client   |                                              It has access to the composition elements by using the base component object.                                               |

![composite-pattern-uml-diagram.png](..%2Fsrc%2Fdesign-pattern%2Fcomposite-pattern-uml-diagram.png)

The composite classes contain a list of their child objects, which can be either leaf or composite classes. When a method is called on a composite
object, it is recursively called on all of its child objects.

This pattern allows you to treat a group of objects in the same way as a single object, without having to know whether it is a single object or a
group of objects. It also simplifies the code by eliminating the need for separate code to handle leaf and composite classes.

Example:

```java
import java.util.ArrayList;
import java.util.List;

public interface Component {
    void operation();
}

public class Leaf implements Component {
    @Override
    public void operation() {
        System.out.println("Leaf operation.");
    }
}

public class Composite implements Component {
    private List<Component> components = new ArrayList<>();

    public void add(Component component) {
        components.add(component);
    }

    public void remove(Component component) {
        components.remove(component);
    }

    @Override
    public void operation() {
        System.out.println("Composite operation.");
        for (Component component : components) {
            component.operation();
        }
    }
}

public class Client {
    public static void main(String[] args) {
        Component leaf1 = new Leaf();
        Component leaf2 = new Leaf();
        Component composite1 = new Composite();
        Component composite2 = new Composite();

        composite1.add(leaf1);
        composite2.add(leaf2);
        composite1.add(composite2);

        composite1.operation();
    }
}
```

#### Q4. Yola is programming for a grocery store system. She has a complex SalesData class that updates inventories and tracks sales figures, and a lightweight AccessSales class that will give select sales data to a user, depending on their credentials. AccessSales delegates to SalesData when more complex data is needed. This situation is shown below. Which Pattern is this?

![m4-q4.png](..%2Fsrc%2Fdesign-pattern%2Fm4-q4.png)

1. [x] Proxy Pattern
2. [ ] Facade Pattern
3. [ ] Singleton Pattern
4. [ ] Decorator Pattern

#### Explanation:

The Proxy Pattern is a design pattern that allows you to provide a surrogate or placeholder object for another object in order to control access to
it. It is used when you want to add a layer of indirection to access an object, without changing the interface or functionality of that object.

In the Proxy Pattern, there is a subject interface that defines the common methods and properties that the real subject and proxy share. Then, there
are two types of classes:

1. Real subject class, which represents the actual object that the client wants to access.
2. Proxy class, which provides a surrogate or placeholder for the real subject class and controls access to it.

![proxy-pattern-uml-diagram.png](..%2Fsrc%2Fdesign-pattern%2Fproxy-pattern-uml-diagram.png)

The proxy class implements the subject interface and contains a reference to the real subject object. When a method is called on the proxy object, it
can either directly invoke the method on the real subject object or perform some additional logic before or after invoking the method on the real
subject object.

This pattern allows you to control access to the real subject object and add additional functionality such as caching, logging, or security checks
without changing the interface or behavior of the real subject object. It also provides a way to delay the creation of the real subject object until
it is actually needed, which can improve performance and memory usage.

#### Q5. Which of these UML class diagrams shows the Facade pattern?

![m4-q5.png](..%2Fsrc%2Fdesign-pattern%2Fm4-q5.png)

1. [ ] a)
2. [ ] b)
3. [x] c)
4. [ ] d)

#### Explanation:

Facade is a structural design pattern that provides a simplified interface to a library, a framework, or any other complex set of classes.

**UML diagram**:

![facade-pattern-uml-diagram.png](..%2Fsrc%2Fdesign-pattern%2Ffacade-pattern-uml-diagram.png)

* Facade: the facade class abstracts Packages 1, 2, and 3 from the rest of the application.
* Clients: the objects are using the Facade Pattern to access resources from the Packages.

#### Q6. What is the difference between the Factory Method and a Simple Factory?

1. [ ] In the factory method pattern, the factory itself must be instantiated before it starts creating objects. This is usually done with a dedicated
   method.
2. [ ] A simple factory instantiates only one kind of object.
3. [ ] Simple factories cannot be subclassed.
4. [x] In Factory Method, concrete instantiation is done in a designated method, where a Simply Factory creates objects for external clients

#### Explanation:

The Factory Method and Simple Factory are two design patterns used in software development to create objects in a flexible and reusable way.

The main difference between the two is that the Factory Method allows subclasses to decide which class to instantiate while the Simple Factory only
has one factory class that creates objects of different types based on input parameters.

Let's see an example in Java for both patterns:

Simple Factory:

```java
public class AnimalFactory {
    public static Animal createAnimal(String type) {
        switch (type) {
            case "dog":
                return new Dog();
            case "cat":
                return new Cat();
            case "lion":
                return new Lion();
            default:
                throw new IllegalArgumentException("Invalid animal type: " + type);
        }
    }
}

public interface Animal {
    void makeSound();
}

public class Dog implements Animal {
    @Override
    public void makeSound() {
        System.out.println("Bark");
    }
}

public class Cat implements Animal {
    @Override
    public void makeSound() {
        System.out.println("Meow");
    }
}

public class Lion implements Animal {
    @Override
    public void makeSound() {
        System.out.println("Roar");
    }
}
```

In this example, the AnimalFactory is a Simple Factory that creates objects of different animal types based on a string parameter. The client code can
use the AnimalFactory to create objects without knowing the details of how each animal type is created.

```java
public class Main {
    public static void main(String[] args) {
        Animal dog = AnimalFactory.createAnimal("dog");
        Animal cat = AnimalFactory.createAnimal("cat");
        Animal lion = AnimalFactory.createAnimal("lion");

        dog.makeSound(); // Bark
        cat.makeSound(); // Meow
        lion.makeSound(); // Roar
    }
}
```

Factory Method:

```java
public interface AnimalFactory {
    Animal createAnimal();
}

public class DogFactory implements AnimalFactory {
    @Override
    public Animal createAnimal() {
        return new Dog();
    }
}

public class CatFactory implements AnimalFactory {
    @Override
    public Animal createAnimal() {
        return new Cat();
    }
}

public class LionFactory implements AnimalFactory {
    @Override
    public Animal createAnimal() {
        return new Lion();
    }
}
```

In this example, the AnimalFactory is an abstract factory interface that defines the createAnimal method. The DogFactory, CatFactory, and LionFactory
are concrete factory classes that implement the AnimalFactory interface and provide their own implementation of the createAnimal method to create
objects of their respective animal types.

```java
public class Main {
    public static void main(String[] args) {
        AnimalFactory dogFactory = new DogFactory();
        AnimalFactory catFactory = new CatFactory();
        AnimalFactory lionFactory = new LionFactory();

        Animal dog = dogFactory.createAnimal();
        Animal cat = catFactory.createAnimal();
        Animal lion = lionFactory.createAnimal();

        dog.makeSound(); // Bark
        cat.makeSound(); // Meow
        lion.makeSound(); // Roar
    }
}
```

In this example, the client code can create objects using a specific factory, which determines the concrete class of the object. The factory method
allows subclasses to decide which class to instantiate, providing more flexibility than the Simple Factory.

#### Q7. José wants to build behaviours by stacking objects and calling their behaviours with an interface. When he makes a call on this interface, the stack of objects all perform their functions in order, and the exact combination of behaviours he needs depends on what objects he stacked and in which order. Which Design Pattern best fits this need?

1. [ ] Factory Method Pattern
2. [ ] Singleton Pattern
3. [ ] Composite Pattern
4. [x] Decorator Pattern

#### Explanation:

The Design Pattern that best fits this need is the Decorator pattern.

In the Decorator pattern, you can stack objects and call their behaviours with an interface. When you make a call on this interface, the stack of
objects all perform their functions in order, and the exact combination of behaviours you need depends on what objects you stacked and in which order.

In this pattern, you can add new behaviour to an object by wrapping it with a decorator object that provides the desired behaviour, and you can stack
multiple decorators on top of each other to create complex combinations of behaviour.

Therefore, the Decorator pattern is the best fit for José's need to stack objects and call their behaviours with an interface.

---

An example of how you can implement the Decorator pattern in Java to stack objects and call their behaviors with an interface:

Let's say you have a base interface called `Component` that defines the common behavior of all the objects you want to stack:

```java
public interface Component {
    void performAction();
}
```

Now, you can create a concrete implementation of this interface, let's call it `ConcreteComponent`, which will provide the basic functionality that
you
want to decorate:

```java
public class ConcreteComponent implements Component {
    @Override
    public void performAction() {
        System.out.println("Performing basic action.");
    }
}
```

Next, you can create a decorator abstract class, let's call it Decorator, that implements the same interface Component and holds a reference to
another Component object:

```java
public abstract class Decorator implements Component {

    private Component component;

    public Decorator(Component component) {
        this.component = component;
    }

    @Override
    public void performAction() {
        component.performAction();
    }

}
```

Now, you can create concrete implementations of the Decorator class that add new behavior to the wrapped Component object. For example, let's create
two decorators that add logging functionality and encryption functionality respectively:

```java
public class LoggingDecorator extends Decorator {

    public LoggingDecorator(Component component) {
        super(component);
    }

    @Override
    public void performAction() {
        System.out.println("Logging before performing action.");
        super.performAction();
    }

}

public class EncryptionDecorator extends Decorator {
    public EncryptionDecorator(Component component) {
        super(component);
    }

    @Override
    public void performAction() {
        System.out.println("Encrypting before performing action.");
        super.performAction();
    }

}
```

Finally, you can stack these decorators on top of each other and call the performAction() method, which will execute the behavior in the order the
decorators were added:

```java
Component component=new EncryptionDecorator(new LoggingDecorator(new ConcreteComponent()));
        component.performAction();
```

The output of this code will be:

```
Encrypting before performing action.
Logging before performing action.
Performing basic action.
```

As you can see, the decorators added their behavior in the order they were wrapped around the ConcreteComponent, and the final behavior was a
combination of all the behaviors added by the decorators and the ConcreteComponent itself.

#### Q8. You need to connect to a third-party library, but you think it might change later, so you want to keep the connection loosely coupled by having your object call a consistent interface. Which Design Pattern do you need?

1. [ ] Decorator
2. [x] Adapter
3. [ ] Proxy
4. [ ] Facade

#### Explanation:

The Design Pattern you need for this scenario is the Adapter Pattern.

The Adapter Pattern allows you to wrap an existing class with a new interface, so that it can be used by other classes without requiring any changes
to the underlying code. This provides a layer of abstraction that makes it easier to modify or replace the original class in the future, without
affecting the rest of the system.

Here's an example in Java:

Suppose you have an existing library that provides a ThirdPartyConnection class, which you need to use in your code. However, you want to keep your
code loosely coupled by using a consistent interface, so you create a new interface MyConnection that your code will use instead:

```
public interface MyConnection {
    void connect();
    void disconnect();
}
```

To connect to the third-party library, you create an adapter class ThirdPartyAdapter that implements the MyConnection interface and wraps the
ThirdPartyConnection class:

```java
public class ThirdPartyAdapter implements MyConnection {
    private ThirdPartyConnection connection;

    public ThirdPartyAdapter(ThirdPartyConnection connection) {
        this.connection = connection;
    }

    @Override
    public void connect() {
        connection.open();
    }

    @Override
    public void disconnect() {
        connection.close();
    }
}
```

Now you can use the MyConnection interface in your code, and create an instance of the ThirdPartyAdapter to connect to the third-party library:

```
MyConnection connection = new ThirdPartyAdapter(new ThirdPartyConnection());
connection.connect();
// use the connection...
connection.disconnect();
```

If the third-party library changes in the future, you can simply update the ThirdPartyAdapter class to adapt to the new interface, without having to
modify the rest of your code that uses the MyConnection interface.

**Why not Facade pattern?**

The Facade pattern is another pattern that can help simplify the use of complex systems by providing a simplified interface. However, it is not the
best pattern to use in the scenario where you want to keep your connection to a third-party library loosely coupled.

The Facade pattern is typically used to provide a simpler and more unified interface to a complex subsystem, where the goal is to hide the complexity
of the subsystem from the client code. In other words, the Facade pattern is used to provide a simpler and more convenient interface to a subsystem
that is already in place, rather than to adapt to a subsystem that might change in the future.

In contrast, the Adapter pattern is used specifically to adapt an existing interface to a new interface, without changing the underlying code. This
allows you to keep your code loosely coupled and provides a layer of abstraction that makes it easier to modify or replace the underlying subsystem in
the future.

Therefore, in the scenario where you want to keep your connection to a third-party library loosely coupled, it is more appropriate to use the Adapter
pattern rather than the Facade pattern.

#### Q9. Which of these diagrams shows the State pattern?

![m4-q9.png](..%2Fsrc%2Fdesign-pattern%2Fm4-q9.png)

1. [ ] a)
2. [x] b)
3. [ ] c)
4. [ ] d)

#### Explanation:

State is a behavioural design pattern that lets an object alter its behaviour when its internal state changes.

**UML Diagram**:

![state-pattern-uml.png](..%2Fsrc%2Fdesign-pattern%2Fstate-pattern-uml.png)

The UML diagram shows the relationship between the Context, which is the object whose behavior changes based on its internal state, and the State,
which is an interface that defines the behavior associated with a particular state.

The Context has a reference to the current State object, and it delegates the handling of requests to this object. The `State` interface has
a `handle()` method that represents the behavior associated with that state.

`ConcreteStateA` and `ConcreteStateB` are concrete implementations of the State interface. They each define their own behavior for the `handle()`
method.

When the internal state of the Context object changes, it sets the current State object to a different concrete implementation of the State interface.

In summary, the State pattern uses an object to represent the different states of an object and the behavior associated with each state. The pattern
helps to separate the behavior of an object from its state, making it easier to change the behavior independently of the state.

**Example in Java**:

This example is a simplified implementation of a traffic light system that cycles through three states: red, green, and yellow.

First, let's create an interface called `TrafficLightState`, which represents the state of the traffic light system:

```java
public interface TrafficLightState {
    void changeState(TrafficLight light);
}
```

Next, let's create three concrete classes that implement the `TrafficLightState` interface:

```java
public class RedLightState implements TrafficLightState {
    @Override
    public void changeState(TrafficLight light) {
        System.out.println("Changing traffic light state from RED to GREEN");
        light.setState(new GreenLightState());
    }
}

public class YellowLightState implements TrafficLightState {
    @Override
    public void changeState(TrafficLight light) {
        System.out.println("Changing traffic light state from YELLOW to RED");
        light.setState(new RedLightState());
    }
}

public class GreenLightState implements TrafficLightState {
    @Override
    public void changeState(TrafficLight light) {
        System.out.println("Changing traffic light state from GREEN to YELLOW");
        light.setState(new YellowLightState());
    }
}
```

Each concrete state class implements the `TrafficLightState` interface and defines its own behavior for the changeState method.

Finally, let's create a `TrafficLight` class that will use the State pattern to delegate the behavior to the different state objects:

```java
public class TrafficLight {

    private TrafficLightState state;

    public TrafficLight() {
        state = new RedLightState();
    }

    public void changeState() {
        state.changeState(this);
    }

    public void setState(TrafficLightState state) {
        this.state = state;
    }
}
```

The `TrafficLight` class has a reference to the current `TrafficLightState` object, and it delegates the handling of state changes to this object.

The `changeState()` method calls the `changeState()` method on the current state object, which in turn changes the state of the `TrafficLight` object
to a different concrete implementation of the `TrafficLightState` interface.

This example demonstrates how the State pattern can be used to simplify the implementation of a system that cycles through different states. By using
the State pattern, we can separate the behavior associated with each state into separate objects, making it easier to change the behavior of the
system independently of its state.

#### Q10. Which of these design principles best describes the Proxy pattern?

1. [ ] decomposition, because the Proxy object has different concerns than the subject
2. [ ] separation of concerns, because the Proxy object has different concerns from the subject
3. [ ] encapsulation, because the Proxy hides some detail of the subject
4. [ ] generalization, because a proxy is a general version of the real subject

#### Explanation:

The design principle that best describes the Proxy pattern is "encapsulation," because the Proxy object hides some detail of the subject.

The Proxy pattern is a structural design pattern that allows for the creation of a substitute or placeholder for another object. The Proxy acts as an
intermediary between the client and the real object, which may be remote, expensive to create, or in need of secure access.

Here's an example implementation of the Proxy pattern in Java:

```java
// Subject interface
public interface Image {
    void display();
}

// Real Subject
public class RealImage implements Image {
    private String fileName;

    public RealImage(String fileName) {
        this.fileName = fileName;
        loadImageFromDisk();
    }

    @Override
    public void display() {
        System.out.println("Displaying " + fileName);
    }

    private void loadImageFromDisk() {
        System.out.println("Loading " + fileName + " from disk");
    }
}

// Proxy class
public class ProxyImage implements Image {
    private RealImage realImage;
    private String fileName;

    public ProxyImage(String fileName) {
        this.fileName = fileName;
    }

    @Override
    public void display() {
        if (realImage == null) {
            realImage = new RealImage(fileName);
        }
        realImage.display();
    }
}

// Client
public class Client {
    public static void main(String[] args) {
        Image image = new ProxyImage("test_image.jpg");

        // Image will be loaded from disk
        image.display();

        // Image will not be loaded from disk again
        image.display();
    }
}
```

#### Q11. Ashley has a method in her class that needs to make a request. This request could be handled by one of several handlers. Which design pattern does she need?

1. [ ] Facade
2. [ ] Decorator
3. [x] Chain of Responsibility
4. [ ] Template

#### Explanation:

Ashley needs to use the Chain of Responsibility design pattern.

The Chain of Responsibility pattern is used when there are multiple handlers that can process a request and the appropriate handler is determined
dynamically at runtime. The request is passed through a chain of handlers until one of them is able to handle it.

**An example implementation in Java**:

In this example, `Handler` is an abstract class that defines the interface for handling requests.

Each concrete handler (`RequestHandler`, `AnotherRequestHandler`, etc.) implements the `canHandle` method to determine if it can handle a given
request, and the process method to actually handle the request.

The `setSuccessor` method is used to set the next handler in the chain. When a request is received by the first handler in the chain (`handler1`), it
is
passed through the chain of handlers until one of them is able to handle it.

```java
public abstract class Handler {

    private Handler successor;

    public void setSuccessor(Handler successor) {
        this.successor = successor;
    }

    public void handleRequest(Request request) {
        if (canHandle(request)) {
            process(request);
        } else if (successor != null) {
            successor.handleRequest(request);
        }
    }

    protected abstract boolean canHandle(Request request);

    protected abstract void process(Request request);
}

public class Request {
    private String type;
    private String payload;

    public Request(String type, String payload) {
        this.type = type;
        this.payload = payload;
    }

    public String getType() {
        return type;
    }

    public String getPayload() {
        return payload;
    }
}

public class RequestHandler extends Handler {
    @Override
    protected boolean canHandle(Request request) {
// Check if this handler can handle the request type
        return request.getType().equals("type1");
    }

    @Override
    protected void process(Request request) {
        // Process the request
        System.out.println("Request handled by RequestHandler");
    }
}

public class AnotherRequestHandler extends Handler {
    @Override
    protected boolean canHandle(Request request) {
// Check if this handler can handle the request type
        return request.getType().equals("type2");
    }

    @Override
    protected void process(Request request) {
        // Process the request
        System.out.println("Request handled by AnotherRequestHandler");
    }
}

public class Client {
    public static void main(String[] args) {
        // Create the chain of handlers
        Handler handler1 = new RequestHandler();
        Handler handler2 = new AnotherRequestHandler();
        handler1.setSuccessor(handler2);

        // Create the request
        Request request = new Request("type1", "payload");

        // Send the request through the chain of handlers
        handler1.handleRequest(request);
    }
}
```

#### Q12. Colin is designing a class for managing transactions in software for a banking machine software. Each transaction has many of the same steps, like reading the card, getting a PIN, and returning the card. Other steps are particular to the type of transaction. Which pattern does he need?

1. [x] Template
2. [ ] MVC
3. [ ] Mediator
4. [ ] State

#### Explanation:

Colin needs to use the Template Method pattern to manage the common steps for each transaction and allow for customization of specific steps depending
on the type of transaction.

Here's an example implementation in Java:

```java
public abstract class TransactionManager {

    public final void executeTransaction() {
        readCard();
        int pin = getPIN();
        if (verifyPIN(pin)) {
            performTransaction();
        } else {
            System.out.println("Incorrect PIN.");
        }
        returnCard();
    }

    private void readCard() {
        // code to read card
    }

    private int getPIN() {
        // code to get PIN
    }

    private boolean verifyPIN(int pin) {
        // code to verify PIN
    }

    private void returnCard() {
        // code to return card
    }

    protected abstract void performTransaction();

}

public class DepositTransactionManager extends TransactionManager {

    protected void performTransaction() {
        // code to perform deposit transaction
    }

}

public class WithdrawTransactionManager extends TransactionManager {

    protected void performTransaction() {
        // code to perform withdraw transaction
    }

}
```

#### Q13. Which of these is NOT a good use of the Command pattern?

1. [ ] Supporting undo/redo queues of commands
2. [ ] Building a user-interface that can be used to perform operations
3. [x] Sending a command to a third-party service or library
4. [ ] Building macros, for example in an image manipulation program

#### Explanation:

**Note**: From my point of view all the options listed are good use cases for the Command pattern.

The right answer is "Sending a command to a third-party service or library", but it's actually a good use case for the Command pattern.

In fact, the Command pattern is often used in situations where a client needs to send requests to a service or library and wants to encapsulate the
request as an object. The client can create a Command object that represents the request, and the service or library can execute the command when it
receives it.

By using the Command pattern in this way, the client and the service or library are decoupled from each other. The client does not need to know how
the service or library implements the request, and the service or library does not need to know how the client created the request. This can make the
code more modular and easier to maintain.

So, to clarify, sending a command to a third-party service or library can be a good practice and is actually a common use case for the Command
pattern.

---

Here's an example of using the Command pattern in Java to send a request to a hypothetical payment processing service:

```java
import lombok.AllArgsConstructor;
import lombok.Getter;

// The Command interface
public interface PaymentCommand {
    void execute();
}

// Concrete command implementations
@AllArgsConstructor
public class CreditCardPaymentCommand implements PaymentCommand {
    private final PaymentService paymentService;
    @Getter
    private final String creditCardNumber;
    @Getter
    private final double amount;

    public void execute() {
        paymentService.processCreditCardPayment(creditCardNumber, amount);
    }
}

@AllArgsConstructor
public class PayPalPaymentCommand implements PaymentCommand {
    private final PaymentService paymentService;
    @Getter
    private final String paypalAccount;
    @Getter
    private final double amount;

    public void execute() {
        paymentService.processPayPalPayment(paypalAccount, amount);
    }
}

// The Invoker
public class PaymentInvoker {
    private PaymentCommand paymentCommand;

    public void setPaymentCommand(PaymentCommand paymentCommand) {
        this.paymentCommand = paymentCommand;
    }

    public void processPayment() {
        paymentCommand.execute();
    }
}

// The Receiver
public class PaymentService {
    public void processCreditCardPayment(String creditCardNumber, double amount) {
        // Process the credit card payment
    }

    public void processPayPalPayment(String paypalAccount, double amount) {
        // Process the PayPal payment
    }
}

// Client code
public class Main {
    public static void main(String[] args) {
        PaymentService paymentService = new PaymentService();
        CreditCardPaymentCommand creditCardPaymentCommand = new CreditCardPaymentCommand(paymentService, "1234 5678 9012 3456", 100.0);
        PayPalPaymentCommand payPalPaymentCommand = new PayPalPaymentCommand(paymentService, "example@paypal.com", 50.0);

        PaymentInvoker paymentInvoker = new PaymentInvoker();

        // Process a credit card payment
        paymentInvoker.setPaymentCommand(creditCardPaymentCommand);
        paymentInvoker.processPayment();

        // Process a PayPal payment
        paymentInvoker.setPaymentCommand(payPalPaymentCommand);
        paymentInvoker.processPayment();
    }
}
```

#### Q14. Choose the correct UML class diagram representation of the Observer pattern:

![m4-q14.png](..%2Fsrc%2Fdesign-pattern%2Fm4-q14.png)

1. [ ] a)
2. [ ] b)
3. [ ] c)
4. [x] d)

#### Explanation:

The Observer Pattern is a design pattern used in object-oriented programming that allows an object, called the subject, to notify a group of other
objects, called observers, when a change to its state occurs.

The pattern promotes loose coupling between the subject and the observers, making it easy to add or remove observers without affecting the subject's
functionality.

**UML Diagram**:

![observer-pattern-uml-diagram.png](..%2Fsrc%2Fdesign-pattern%2Fobserver-pattern-uml-diagram.png)

The UML diagram for the Observer Pattern consists of two main components:

1. The `Subject` class
2. The `Observer` interface.

The Subject class contains a list of Observers and methods for adding, removing, and notifying observers.

The Observer interface defines an update method that the Subject calls to notify the Observer of changes to its state.

**Example of implementation**:

Let's consider an example where we have a weather station that measures temperature, humidity, and pressure.

We want to notify several displays when any of these values change.

Create the Observer interface:

```java
public interface Observer {
    void update(float temperature, float humidity, float pressure);
}
```

Create the Subject class:

```java
import java.util.ArrayList;

public class WeatherData implements Subject {
    private ArrayList<Observer> observers;
    private float temperature;
    private float humidity;
    private float pressure;

    public WeatherData() {
        observers = new ArrayList<>();
    }

    @Override
    public void registerObserver(Observer observer) {
        observers.add(observer);
    }

    @Override
    public void removeObserver(Observer observer) {
        int index = observers.indexOf(observer);
        if (index >= 0) {
            observers.remove(index);
        }
    }

    @Override
    public void notifyObservers() {
        for (Observer observer : observers) {
            observer.update(temperature, humidity, pressure);
        }
    }

    public void measurementsChanged() {
        notifyObservers();
    }

    public void setMeasurements(float temperature, float humidity, float pressure) {
        this.temperature = temperature;
        this.humidity = humidity;
        this.pressure = pressure;
        measurementsChanged();
    }
}
```

Create the Subject interface:

```
public interface Subject {
    void registerObserver(Observer observer);
    void removeObserver(Observer observer);
    void notifyObservers();
}
```

Create the Concrete Observers:

```java
public class CurrentConditionsDisplay implements Observer {
    private float temperature;
    private float humidity;

    @Override
    public void update(float temperature, float humidity, float pressure) {
        this.temperature = temperature;
        this.humidity = humidity;
        display();
    }

    public void display() {
        System.out.println("Current conditions: " + temperature + "F degrees and " + humidity + "% humidity");
    }
}

public class StatisticsDisplay implements Observer {
    private float temperature;
    private float humidity;

    @Override
    public void update(float temperature, float humidity, float pressure) {
        this.temperature = temperature;
        this.humidity = humidity;
        display();
    }

    public void display() {
        System.out.println("Statistics: " + temperature + "F degrees and " + humidity + "% humidity");
    }
}
```

Use the pattern in the main method:

```java
public class WeatherStation {
    public static void main(String[] args) {
        WeatherData weatherData = new WeatherData();

        CurrentConditionsDisplay currentConditionsDisplay = new CurrentConditionsDisplay();
        weatherData.registerObserver(currentConditionsDisplay);

        StatisticsDisplay statisticsDisplay = new StatisticsDisplay();
        weatherData.registerObserver(statisticsDisplay);

        weatherData.setMeasurements(80, 65, 30.4f);
        weatherData.setMeasurements(82, 70, 29.2f);
        weatherData.setMeasurements(78, 90, 29.2f);
    }
}
```

#### Q15. Which code smell may become a problem with the Mediator design pattern?

1. [ ] Inappropriate Intimacy
2. [ ] Refused Bequest
3. [ ] Speculative Generality
4. [x] Large Class

#### Explanation:

The code smell that may become a problem with the Mediator design pattern is "Large Class".

In the Mediator design pattern, the mediator object acts as a central hub that coordinates communication between other objects, which can lead to a
large number of responsibilities being assigned to the mediator. If not properly managed, this can result in a bloated and complex Mediator class,
which violates the Single Responsibility Principle and makes the code difficult to understand and maintain.

Here's an example in Java that illustrates how the Mediator pattern can lead to a large class:

```java
public class ChatRoomMediator {
    private List<User> users = new ArrayList<>();

    public void addUser(User user) {
        this.users.add(user);
    }

    public void sendMessage(String message, User sender) {
        for (User user : users) {
            if (user != sender) {
                user.receive(message);
            }
        }
    }

// More methods for managing users, such as removeUser(), etc.
}
```

In this example, the ChatRoomMediator class acts as a mediator between User objects, allowing them to communicate with each other. However, as more
functionality is added to the mediator (e.g. managing user accounts, handling different types of messages), the class can quickly become large and
difficult to maintain. To avoid this, it's important to carefully consider the responsibilities of the mediator and ensure that it stays focused on
its core responsibilities.

#### Q16. Hyun-Ji is developing a program. She wants to create a Student class that behaves differently based on if the student has not registered for classes, is partially registered, fully registered, or fully registered and paid. Which design pattern does she need?

1. [ ] Proxy
2. [x] State
3. [ ] Template Method
4. [ ] Mediator

#### Explanation:

The design pattern that best fits the scenario described is the State pattern.

The State pattern allows an object to alter its behavior when its internal state changes. In this case, the behavior of the Student class should
change depending on the state of registration and payment.

Here's an example implementation of the State pattern in Java.

In this example, the `Student` class is the context and maintains a reference to the current state.

The different registration and payment states are represented by separate classes that implement the `StudentState` interface. When a registration or
payment method is called on the `Student` class, it delegates the behavior to the current state object. Each state class determines the appropriate
behavior based on the current state of the `Student` object.

```java
interface StudentState {
    void registerForClasses();

    void payTuition();
}

class NotRegisteredState implements StudentState {
    private Student student;

    public NotRegisteredState(Student student) {
        this.student = student;
    }

    public void registerForClasses() {
        System.out.println("Registering for classes...");
        student.setState(new PartiallyRegisteredState(student));
    }

    public void payTuition() {
        System.out.println("Cannot pay tuition yet - not registered for classes.");
    }
}

class PartiallyRegisteredState implements StudentState {
    private Student student;

    public PartiallyRegisteredState(Student student) {
        this.student = student;
    }

    public void registerForClasses() {
        System.out.println("Already registered for classes.");
    }

    public void payTuition() {
        System.out.println("Paying tuition...");
        student.setState(new FullyRegisteredState(student));
    }
}

class FullyRegisteredState implements StudentState {
    private Student student;

    public FullyRegisteredState(Student student) {
        this.student = student;
    }

    public void registerForClasses() {
        System.out.println("Already fully registered for classes.");
    }

    public void payTuition() {
        System.out.println("Tuition already paid.");
        student.setState(new FullyRegisteredAndPaidState(student));
    }
}

class FullyRegisteredAndPaidState implements StudentState {
    private Student student;

    public FullyRegisteredAndPaidState(Student student) {
        this.student = student;
    }

    public void registerForClasses() {
        System.out.println("Already fully registered for classes.");
    }

    public void payTuition() {
        System.out.println("Tuition already paid.");
    }
}

class Student {
    private StudentState state;

    public Student() {
        this.state = new NotRegisteredState(this);
    }

    public void setState(StudentState state) {
        this.state = state;
    }

    public void registerForClasses() {
        state.registerForClasses();
    }

    public void payTuition() {
        state.payTuition();
    }
}

// Example usage
public class Main {
    public static void main(String[] args) {
        Student student = new Student();

        student.registerForClasses();
        student.payTuition();
        student.registerForClasses();
        student.payTuition();
        student.payTuition();
    }
}
```

#### Q17. Which of these methods is found in a typical Observer class?

1. [ ] addObserver()
2. [ ] getState()
3. [x] update()
4. [ ] notify()

#### Explanation:

The Observer pattern is implemented using two main components:

1. The Subject
2. The Observer.

The Observer interface typically defines one method, which is the `update()` method. This method is called by the Subject to notify the Observer of a
change in the Subject's state.

#### Q18. Fernando is making pizza objects with the Template Method pattern. The make() function is the whole process of making the pizza. Some steps are the same for every pizza - makeDough(), and bake(). The other steps - addSauce(), addToppings() and addCheese() - vary by the pizza. Which of these subclasses shows the proper way to use a template method?

1. [ ] a)
2. [x] b)
3. [ ] c)
4. [ ] d)

#### Explanation:

```java
abstract class Pizza {
    public final void make() {
        makeDough();
        addSauce();
        addToppings();
        addCheese();
        bake();
    }

    public void makeDough() {
        System.out.println("Making dough");
    }

    public void bake() {
        System.out.println("Baking pizza");
    }

    public abstract void addSauce();

    public abstract void addToppings();

    public abstract void addCheese();
}

class VeggiePizza extends Pizza {

    public void addSauce() {
        System.out.println("Adding tomato sauce");
    }

    public void addToppings() {
        System.out.println("Adding basil leaves");
    }

    public void addCheese() {
        System.out.println("Adding mozzarella cheese");
    }
}
```

#### Q19. In the Mediator Pattern, which pattern is often used to make sure the Mediator always receives the information it needs from its collaborators?

1. [x] Observer
2. [ ] Chain of Responsibility
3. [ ] Command
4. [ ] Template Method

#### Explanation:

The pattern that is often used to ensure that the Mediator always receives the information it needs from its collaborators is the Observer pattern.

In the Observer pattern, an object (the subject) maintains a list of its dependents (observers) and notifies them automatically of any state changes.
In the context of the Mediator pattern, the Mediator plays the role of the subject, and the collaborators play the role of the observers.

Here's an example implementation of the Mediator pattern using the Observer pattern in Java:

In this example, the `ConcreteMediator` class plays the role of the Mediator, and the `ConcreteColleague1` and `ConcreteColleague2` classes play the
role of
the collaborators. When a colleague sends a message through the mediator, the mediator notifies all the other colleagues by calling their
`receiveMessage()` method.

```java
import java.util.ArrayList;
import java.util.List;

// Mediator interface
interface Mediator {
    void sendMessage(String message, Colleague colleague);
}

// Concrete Mediator class
class ConcreteMediator implements Mediator {
    private List<Colleague> colleagues;

    public ConcreteMediator() {
        colleagues = new ArrayList<>();
    }

    public void addColleague(Colleague colleague) {
        colleagues.add(colleague);
    }

    @Override
    public void sendMessage(String message, Colleague originator) {
        for (Colleague colleague : colleagues) {
            if (colleague != originator) {
                colleague.receiveMessage(message);
            }
        }
    }
}

// Colleague interface
interface Colleague {
    void sendMessage(String message);

    void receiveMessage(String message);
}

// Concrete Colleague classes
class ConcreteColleague1 implements Colleague {

    private Mediator mediator;

    public ConcreteColleague1(Mediator mediator) {
        this.mediator = mediator;
        mediator.addColleague(this);
    }

    @Override
    public void sendMessage(String message) {
        mediator.sendMessage(message, this);
    }

    @Override
    public void receiveMessage(String message) {
        System.out.println("ConcreteColleague1 received message: " + message);
    }
}

class ConcreteColleague2 implements Colleague {

    private Mediator mediator;

    public ConcreteColleague2(Mediator mediator) {
        this.mediator = mediator;
        mediator.addColleague(this);
    }

    @Override
    public void sendMessage(String message) {
        mediator.sendMessage(message, this);
    }

    @Override
    public void receiveMessage(String message) {
        System.out.println("ConcreteColleague2 received message: " + message);
    }
}

// Example usage
public class Main {
    public static void main(String[] args) {
        ConcreteMediator mediator = new ConcreteMediator();
        ConcreteColleague1 colleague1 = new ConcreteColleague1(mediator);
        ConcreteColleague2 colleague2 = new ConcreteColleague2(mediator);

        colleague1.sendMessage("Hello from Colleague1!");
        colleague2.sendMessage("Hi there, Colleague1!");
    }
}
```

#### Q20. In the MVC Pattern, which of these is usually made into an Observer?

1. [ ] Model
2. [ ] Controller
3. [ ] Back-End
4. [x] View

#### Explanation:

View is usually made into an Observer in the MVC Pattern.

In the MVC (Model-View-Controller) pattern:

1. The View represents the user interface and displays the data from the Model.
2. The Model represents the data and business logic of an application,
3. The Controller acts as an intermediary between the Model and the View.

The View can be made into an Observer in the MVC pattern because it observes the Model's state and updates its display accordingly. When the Model's
state changes, it notifies the View, which updates itself with the new data.

Here is an example in Java:

The `View` class implements the `Observer` interface and updates itself whenever the Model's state changes. The `Controller` class sets the data
through the
Model by calling its `setData()` method.

In the main method, we create the Model, View, and Controller objects, and set the data through the Controller. The View updates itself automatically
when the data changes, and the `displayData()` method displays the data from the Model in the View.

```java
import java.util.Observable;
import java.util.Observer;

public class Model extends Observable {
    private int data;

    public Model() {
        data = 0;
    }

    public void setData(int newData) {
        data = newData;
        // Mark the Observable as changed
        setChanged();
        // Notify the Observers that the data has changed
        notifyObservers();
    }

    public int getData() {
        return data;
    }
}

public class View implements Observer {
    private Model model;

    public View(Model model) {
        this.model = model;
        model.addObserver(this); // Register the View as an Observer of the Model
    }

    @Override
    public void update(Observable o, Object arg) {
        // Update the view with the new data
        int data = ((Model) o).getData();
        System.out.println("Data has changed: " + data);
    }

    public void displayData() {
        // Display the data from the model
        int data = model.getData();
        System.out.println("Data is: " + data);
    }
}

public class Controller {
    private Model model;
    private View view;

    public Controller(Model model, View view) {
        this.model = model;
        this.view = view;

        // Register the view as an observer of the model
        model.addObserver(view);
    }

    public void setData(int newData) {
        model.setData(newData);
    }
}

public class MVCPatternDemo {
    public static void main(String[] args) {
        // Create the Model, View, and Controller
        Model model = new Model();
        View view = new View(model);
        Controller controller = new Controller(model, view);

        // Set the data through the controller
        controller.setData(5);

        // Display the data in the view
        view.displayData();
    }
}
```

#### Q21. Which of these answers does NOT accurately complete the following sentence? “A class is considered closed to modification when…”

1. [ ] ... all the attributes and behaviours are encapsulated
2. [x] ... its collaborators are fixed
3. [ ] ... it is tested to be functioning properly
4. [ ] ... it is proven to be stable within your system

#### Explanation:

The statement "A class is considered closed to modification when its collaborators are fixed" is not entirely true because a class can still be
modified even if its collaborators are fixed.

The concept of open/closed principle in object-oriented design states that a class should be open for extension but closed for modification. This
means that a class should be designed in a way that allows new behavior to be added to it without modifying its existing code.

For example, consider a class called `PaymentProcessor` in Java that processes payments using different payment methods such as credit card, PayPal,
and bank transfer.

The `PaymentProcessor` class has a method called `processPayment()` that takes an instance of a payment method class as a parameter and
processes the payment using that method.

```java
public class PaymentProcessor {
    public void processPayment(PaymentMethod paymentMethod) {
        paymentMethod.process();
    }
}

public interface PaymentMethod {
    void process();
}

public class CreditCardPayment implements PaymentMethod {
    public void process() {
// code to process credit card payment
    }
}

public class PayPalPayment implements PaymentMethod {
    public void process() {
// code to process PayPal payment
    }
}

public class BankTransferPayment implements PaymentMethod {
    public void process() {
// code to process bank transfer payment
    }
}
```

#### Q22. How does the Dependency Inversion Principle improve your software systems?

1. [x] Client classes become dependent on high level generalizations rather than dependent on low level concrete classes
2. [ ] Client classes become dependent on low-level concrete classes, rather than dependent on high-level generalizations
3. [ ] Dependency becomes inverted by having the system depend on the client classes
4. [ ] Client classes use an adapter to facilitate communication between itself and the rest of the system

#### Explanation:

The Dependency Inversion Principle (DIP) is a design principle in object-oriented programming that promotes decoupling between software modules by
inverting the traditional dependency relationships between them.

In a traditional design, high-level modules depend on low-level modules, which can create a rigid and brittle system that is difficult to change. By
inverting this relationship, high-level modules depend on abstractions rather than concrete implementations, allowing for greater flexibility and
easier maintenance.

Here's an example in Java:

The `DataProcessor` class depends on the `Database` interface rather than a concrete implementation like `MySqlDatabase`.

This allows the `DataProcessor` to be easily changed to use a different database implementation without requiring changes to the rest of the system.
This improves the flexibility and maintainability of the system.

```java
public interface Database {
    void save(String data);
}

public class MySqlDatabase implements Database {
    public void save(String data) {
// save data to MySQL database
    }
}

public class DataProcessor {
    private Database database;

    public DataProcessor(Database database) {
        this.database = database;
    }

    public void process(String data) {
// do some processing on the data
        database.save(data);
    }
}

public class Application {
    public static void main(String[] args) {
        Database database = new MySqlDatabase();
        DataProcessor processor = new DataProcessor(database);
        processor.process("some data");
    }
}
```

#### Q23. Allison has a search algorithm, and she would like to try a different implementation of it in her software. She tries replacing it everywhere it is used and this is a huge task! Which design principle could Allison have used to avoid this situation?

1. [x] Dependency Inversion
2. [ ] Composing Objects Principle
3. [ ] Don't Repeat Yourself
4. [ ] Principle of The Least Knowledge

#### Explanation:

The principle that Allison could have used to avoid this situation is the "Dependency Inversion Principle". This principle states that high-level
modules should not depend on low-level modules, both should depend on abstractions.

1. Abstractions should not depend on details;
2. Details should depend on abstractions.

By applying this principle, Allison could have designed her search algorithm with an abstract interface, which could be implemented by different
classes. Then, she could have used this interface everywhere in her software instead of the concrete implementation. If she needed to change the
implementation, she would only need to change the implementation of the interface, without affecting the rest of the code.

Here's an example implementation of the Dependency Inversion Principle in Java:

```java
public interface SearchAlgorithm {
    List<String> search(List<String> items, String query);
}

public class BinarySearch implements SearchAlgorithm {
    @Override
    public List<String> search(List<String> items, String query) {
// implementation of binary search algorithm
    }
}

public class LinearSearch implements SearchAlgorithm {
    @Override
    public List<String> search(List<String> items, String query) {
// implementation of linear search algorithm
    }
}

public class SearchService {
    private final SearchAlgorithm searchAlgorithm;

    public SearchService(SearchAlgorithm searchAlgorithm) {
        this.searchAlgorithm = searchAlgorithm;
    }

    public List<String> search(List<String> items, String query) {
        return searchAlgorithm.search(items, query);
    }
}

public class Main {
    public static void main(String[] args) {
        SearchAlgorithm algorithm = new BinarySearch();
        SearchService searchService = new SearchService(algorithm);

        List<String> items = Arrays.asList("apple", "banana", "orange", "peach", "pear");
        List<String> results = searchService.search(items, "peach");

        System.out.println(results);
    }
}
```

#### Q24. Which of the code smells is shown in this code example of a method declaration?

```java
private void anOperation(String colour,int x,int y,int z,int speed)
```

1. [x] Large Parameter List
2. [ ] Primitive Obsession
3. [ ] Message Chains
4. [ ] Long Method

#### Explanation:

The code smell shown in the code example of a method declaration is "Large Parameter List".

The method has five parameters, which can make it difficult to read and understand the method's purpose, especially if the parameter names are not
clear. This can also make the method harder to maintain and test.

To improve this code smell, you can consider using objects or data structures to group related parameters together, or refactoring the method to split
it into smaller, more focused methods that each take fewer parameters.

Here's an example of refactoring the method to use a data object:

```java
public class Coordinates {
    private int x;
    private int y;
    private int z;

    public Coordinates(int x, int y, int z) {
        this.x = x;
        this.y = y;
        this.z = z;
    }

    // getters and setters for each field
}

    public void anOperation(Coordinates coordinates, String colour, int speed) {
// implementation code using coordinates object, colour parameter, and speed parameter
    }
```

#### Q25. Which object-oriented design principle do Long Message Chains, a code smell, usually violate?

1. [ ] Open/Closed Principle
2. [ ] Cohesion
3. [ ] Separation of Concerns
4. [x] Principle of The Least Knowledge / Law of Demeter

#### Explanation:

The Long Message Chain code smell typically violates the Principle of The Least Knowledge, also known as the Law of Demeter.

This principle states that an object should have limited knowledge of the structure of other objects it interacts with and should only interact with
objects directly related to its functionality.

An example of violating the Law of Demeter due to a Long Message Chain.

The `getCity` method in the `Customer` class is calling multiple getter methods on objects that are not directly related to the `Customer`
object, creating a long message chain.

This makes the code harder to understand and maintain, and violates the Law of Demeter. A better solution would be to pass the required information
directly to the `Customer` object, or to provide a method in the `Address` class that returns the city name directly.

```java
public class Customer {
    private Address address;

    public Customer() {
        this.address = new Address();
    }

    public String getCity() {
        return this.address.getStreet().getCity().toString();
    }
}

public class Address {
    private Street street;

    public Address() {
        this.street = new Street();
    }

    public Street getStreet() {
        return this.street;
    }
}

public class Street {
    private City city;

    public Street() {
        this.city = new City();
    }

    public City getCity() {
        return this.city;
    }
}

public class City {
    private String name;

    public City() {
        this.name = "New York";
    }

    public String getName() {
        return this.name;
    }
}
```

#### Q26. Which code smell can you detect here?

```java
public class Person {
    int age;
    int height;
    String hairColour;

    public int getAge() {
        return age;
    }
    ...

}
```

1. [ ] Feature Envy
2. [ ] Primitive Obsession
3. [x] Data Class
4. [ ] Data Clump

#### Explanation:

**Note**: the right answer is Data Class, but Primitive Obsession also has a place.

---

This code violates the Data Class code smell because it is a class that only contains fields and getter/setter methods, and does not contain any
behavior or logic. In other words, it is a "dumb" data container that only holds data and does not do anything useful with it.

The Data Class code smell is a symptom of a design problem where the behavior and data in the system are not properly separated, leading to a class
that is neither truly a behavior (i.e., a service or controller) nor truly a data container (i.e., a DTO or value object). This can lead to issues
with maintainability, testability, and flexibility.

To fix this code smell, we should consider moving the behavior associated with the data into this class, or alternatively, separating the behavior
into a separate class or classes. By doing so, we can create a better separation of concerns, improve the modularity and flexibility of the system,
and make the code easier to maintain and test.

Here is an example of how we can fix this code smell by adding some behavior to the `Person` class:

```java

@AllArgConstructor
public class Person {
    private int age;
    private int height;
    private String hairColour;

    public Person(int age, int height, String hairColour) {
        this.age = age;
        this.height = height;
        this.hairColour = hairColour;
    }

    public void celebrateBirthday() {
        this.age++;
        System.out.println("Happy birthday! You are now " + this.age + " years old.");
    }

    public int calculateBMI(double weight) {
        return (int) (weight / (Math.pow(height / 100.0, 2)));
    }

    // other methods...
}
```

In this example, we have added some behavior to the Person class, such as a method to celebrate a birthday, a method to calculate the BMI (body mass
index) based on the person's weight, and potentially some other methods related to a person's characteristics or behaviors. This way, the Person class
is not just a dumb data container, but has some meaningful behavior associated with it.

---

The code smell in this code is "Primitive Obsession." It means that the code is using primitive data types such as int and string to represent more
complex concepts like a person's age, height, and hair color. This can lead to code duplication, difficulty in maintaining the code, and decreased
readability.

To fix this problem, we can create separate classes to represent these concepts. For example, we can create an "Age" class with a private integer
field to represent a person's age, and then modify the "Person" class to use this "Age" class. This will make the code more readable, maintainable,
and flexible.

#### Q27. What are the components of the MVC pattern?

1. [ ] Model, Vision, Command
2. [x] Member, Vision, Controller
3. [ ] Model, View, Command
4. [ ] Model, View, Controller

#### Explanation:

The answer is the part of Q20.

#### Q28. The interface segregation principle encourages you to use which of these object-oriented design principles? Choose the 2 correct answers.

1. [x] decomposition
2. [ ] generalization
3. [x] abstraction
4. [x] encapsulation

#### Explanation:

**Note**: according to the course the second right answers are decomposition and abstraction, but encapsulation matches too.

The Interface Segregation Principle (ISP) is a principle of object-oriented design that states that clients should not be forced to depend on
interfaces they do not use. In other words, a class should not be forced to implement interfaces that contain methods it does not need.

Abstraction is important in ISP because it allows classes to define their own interfaces, which can be tailored to their specific needs. This way,
classes can avoid implementing unnecessary methods and dependencies on other classes.

Encapsulation is also important in ISP because it allows classes to hide their implementation details and expose only the methods that are relevant to
the interface. This way, clients can interact with objects through their interfaces without needing to know the details of their implementation.

Decomposition can be used to break down large interfaces into smaller, more focused interfaces that only contain the methods
that are relevant to the client. This way, clients can interact with objects through smaller, more specific interfaces, rather than being forced to
depend on large, monolithic interfaces that contain methods they don't need.

#### Q29. Interface Segregation is a good way to avoid which code smell? Choose the best possible answer.

1. [ ] Divergent Change
2. [ ] Long Method
3. [ ] Switch Statements
4. [x] Refused Bequest

#### Explanation:

The Interface Segregation Principle (ISP) is a good way to avoid the code smell of Refused Bequest, which occurs when a subclass inherits from a
superclass or interface but doesn't actually use all the inherited methods, leading to unused or unnecessary code.

#### Q30. Which of these statements about the Decorator pattern are true?

1. The decorator classes inherit from the basic object which is being decorated
2. Decorator objects can be stacked in different order

--- 

1. [ ] The first statement is true
2. [ ] The second statement is true
3. [ ] Neither statement is true
4. [x] Both statements are true

#### Explanation:

**Note**: according to the course only the first statement is true, but I don't agree.

--- 

Both statements are true.

**1-st statement**: The decorator classes usually implement the same interface or extend the same base class as the object being decorated. This
allows the decorator to add functionality to the base object while still being able to treat it as the same type of object.

For example, if you have a basic `Coffee` interface, you could have a decorator class called `Milk` that adds milk to the coffee, and it would still
be treated as a `Coffee` object.

**2-nd statement**: Decorator objects can be stacked in any order, allowing for multiple layers of functionality to be added to the base object. For
example, you could have a `Coffee` object decorated with `Milk`, then decorated with `Sugar`, then decorated with `WhippedCream`.

Here's an example implementation of the Decorator pattern in Java:

```java
// Base Coffee interface
public interface Coffee {
    public String getDescription();

    public double getCost();
}

// Concrete Coffee class
public class BasicCoffee implements Coffee {
    public String getDescription() {
        return "Basic Coffee";
    }

    public double getCost() {
        return 1.0;
    }
}

// Decorator class for adding milk
public class MilkDecorator implements Coffee {
    private Coffee coffee;

    public MilkDecorator(Coffee coffee) {
        this.coffee = coffee;
    }

    public String getDescription() {
        return coffee.getDescription() + ", Milk";
    }

    public double getCost() {
        return coffee.getCost() + 0.5;
    }
}

// Decorator class for adding sugar
public class SugarDecorator implements Coffee {
    private Coffee coffee;

    public SugarDecorator(Coffee coffee) {
        this.coffee = coffee;
    }

    public String getDescription() {
        return coffee.getDescription() + ", Sugar";
    }

    public double getCost() {
        return coffee.getCost() + 0.25;
    }
}

// Decorator class for adding whipped cream
public class WhippedCreamDecorator implements Coffee {
    private Coffee coffee;

    public WhippedCreamDecorator(Coffee coffee) {
        this.coffee = coffee;
    }

    public String getDescription() {
        return coffee.getDescription() + ", Whipped Cream";
    }

    public double getCost() {
        return coffee.getCost() + 0.75;
    }
}

public class Main {
    public static void main(String[] args) {
        Coffee coffee = new BasicCoffee(); // Create a basic coffee
        coffee = new MilkDecorator(coffee); // Add milk to the coffee
        coffee = new SugarDecorator(coffee); // Add sugar to the coffee
        coffee = new WhippedCreamDecorator(coffee); // Add whipped cream to the coffee

        System.out.println(coffee.getDescription()); // Prints "Basic Coffee, Milk, Sugar, Whipped Cream"
        System.out.println(coffee.getCost()); // Prints "2.5" (1.0 + 0.5 + 0.25 + 0.75)
    }
}
```
