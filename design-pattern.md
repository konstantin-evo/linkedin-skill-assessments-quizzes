## Design Pattern (University of Alberta)

[Link to course](https://www.coursera.org/learn/design-patterns)

#### Module 1

Creational Patterns:

1. Singleton
2. Factory Method

Structural Patterns:

1. Facade
2. Adapter
3. Composite
4. Proxy
5. Decorator

--- 

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
