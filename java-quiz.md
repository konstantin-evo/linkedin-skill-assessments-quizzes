## Java

#### Q1. Given the string "strawberries" saved in a variable called fruit, what would `fruit.substring(2, 5)` return?

- [ ] rawb
- [x] raw
- [ ] awb
- [ ] traw

#### Explanation

The Java String class `substring()` method returns a part of the string.

We pass `beginIndex` and `endIndex` number positions in the Java substring method where beginIndex is inclusive, and
endIndex is exclusive. In other words, the beginIndex starts from 0, whereas the endIndex starts from 1.

Signature:

```java
public String substring(int startIndex)  // type - 1  
public String substring(int startIndex,int endIndex)  // type - 2
```

Parameters:

- startIndex – starting index is inclusive;
- endIndex – ending index is exclusive.
-

Example:

```java
public class SubstringExample {
    public static void main(String[] args) {
        String s1 = "javatpoint";
        System.out.println(s1.substring(2, 4));//returns 'va' 
        System.out.println(s1.substring(2));//returns 'vatpoint'
    }
} 
```

#### Q2. How can you achieve runtime polymorphism in Java?

- [ ] method overloading
- [ ] method overrunning
- [x] method overriding
- [ ] method calling

#### Explanation

Polymorphism in Java is a concept by which we can perform a single action in different ways.

There are two types of polymorphism in Java:

- compile-time polymorphism;
- runtime polymorphism.
-

We can perform polymorphism in Java by:

- method overloading;
- method overriding.

If you overload a static method in Java, it is an example of compile time polymorphism.

Runtime polymorphism in Java is also known as Dynamic Binding or Dynamic Method Dispatch. In this process, the call to
an overridden method is resolved dynamically at runtime rather than at compile-time.

An overridden method is called through the reference variable of a superclass. The determination of the method to be
called is based on the Object being referred to by the reference variable.

Runtime polymorphism is achieved through Method Overriding.

#### Q3. Given the following definitions, which of these expressions will **NOT** evaluate to true?

```java
boolean b1=true,b2=false;
        int i1=1,i2=2;
```

- [ ] `(i1 | i2) == 3`
- [x] `i2 && b1`
- [ ] `b1 || !b2`
- [ ] `(i1 ^ i2) < 4`

#### Explanation

| Operator | Name                   | Description                                                                                                                      | Example                                  |
|----------|------------------------|----------------------------------------------------------------------------------------------------------------------------------|------------------------------------------|
| ❘        | Binary “Or”            | Returns true if at least one of the operands evaluates to true. Both operands are evaluated before the “Or” operator is applied. | int i1 = 1; int i2 = 2; 01 ❘ 10 = 11 (3) |
| &&       | Logical “And”          | Returns true if both statements are true                                                                                         | x < 5 && x < 10                          |
| ❘❘       | Logical “Or”           | Returns true if one of the statements is true                                                                                    | x < 5 ❘❘ x < 4                           |
| ^        | Logical “Exclusive Or” | Returns true if and only if the operands are different.                                                                          | int i1 = 1; int i2 = 2; 01 ^ 10 = 11 (3  |

Example:

```java
public static void main(String[]args){
        boolean b1=true;
        boolean b2=false;
        int i1=1;
        int i2=2;

        boolean res=i2&&b1;
        }

        Compile-time Error:
        Operator'&&'cannot be applied to'int','boolean' 
```

#### Q4. What is the output of this code?

```
1: class Main {
2:   public static void main (String[] args) {
3:     int array[] = {1, 2, 3, 4};
4:     for (int i = 0; i < array.size(); i++) {
5:        System.out.print(array[i]);
6:     }
7:   }
8: }
```

- [x] It will not compile because of line 4.
- [ ] It will not compile because of line 3.
- [ ] 123
- [ ] 1234

#### Explanation

```
Compile-time error:
Cannot resolve method 'size()'
```

In Java, the array length is the number of elements that an array can hold. There is no predefined method to obtain the
length of an array. We can find the array length in Java by using the array attribute `length`. We use this attribute
with the array name.

With the help of the `length` variable, we can obtain the size of the array.

```java
public class Test {
    public static void main(String[] args) {
        int[] array = new int[4];
        System.out.println("The size of the array is "
                + array.length);

        String str = "LinkedIn Java Assessment";
        System.out.println("The size of the String is "
                + str.length());
    }
}
```

#### Q5. Which of the following can replace the CODE SNIPPET to make the code below print "Hello World"?

```java
interface Interface1 {
    static void print() {
        System.out.print("Hello");
    }
}

interface Interface2 {
    static void print() {
        System.out.print("World!");
    }
}
```

- [ ] `super1.print(); super2.print();`
- [ ] `this.print();`
- [ ] `super.print();`
- [x] `Interface1.print(); Interface2.print();`

#### Explanation

An interface is an abstract type that is used to specify a behavior that classes must implement.

An interface contains abstract methods except default and static methods.

For creating a default method in the Java interface, we need to use the `default` keyword with the method signature.

#### Q6. What does the following code print?

```java
public class Test {
    public static void main(String[] args) {
        String str = "abcde";
        str.trim();
        str.toUpperCase();
        str.substring(3, 4);
        System.out.println(str);
    }
}

```

- [ ] CD
- [ ] CDE
- [ ] D
- [x] "abcde"

#### Explanation

The value of `str` doesn't change since a variable is never assigned a new value during program execution.

Methods from the question:

The `trim()` method eliminates leading and trailing spaces. The Unicode value of space character is `\u0020`. This
method in Java string checks this Unicode value before and after the string, if it exists then the method removes the
spaces and returns the omitted string.

The `substring()` method returns a part of the string. We pass `beginIndex` and `endIndex` number positions in the Java
substring method where beginIndex is inclusive, and endIndex is exclusive. In other words, the beginIndex starts from 0,
whereas the endIndex starts from 1.

The `toUpperCase()` method returns the string in uppercase letter. In other words, it converts all characters of the
string into upper case letter.

#### Q7. What is the result of this code?

```java
class Main {
    public static void main(String[] args) {
        System.out.println(print(1));
    }

    static Exception print(int i) {
        if (i > 0) {
            return new Exception();
        } else {
            throw new RuntimeException();
        }
    }
}
```

- [ ] It will show a stack trace with a runtime exception.
- [x] "java.lang.Exception"
- [ ] It will run and throw an exception.
- [ ] It will not compile.

#### Explanation

An exception is an abnormal event that arises during the execution of the program and disrupts the normal flow of the
program.

![](src/java/java-exceptions-classes.png)

The class `Exception` and its subclasses are a form of Throwable that indicates conditions that a reasonable application
might want to catch.

The class `Exception` and any subclasses that are not also subclasses of RuntimeException are checked exceptions.
Checked exceptions need to be declared in a method or constructor's throws clause if they can be thrown by the execution
of the method or constructor and propagate outside the method or constructor boundary.

The class `RuntimeException` is the superclass of those exceptions that can be thrown during the normal operation of the
Java Virtual Machine.

The class `RuntimeException` and its subclasses are unchecked exceptions. Unchecked exceptions do not need to be
declared in a method or constructor's throws clause if they can be thrown by the execution of the method or constructor
and propagate outside the method or constructor boundary.

#### Q8. Which class can compile given these declarations?

```java
interface One {
    default void method() {
        System.out.println("One");
    }
}

interface Two {
    default void method() {
        System.out.println("One");
    }
}
```

- [ ] A

```java
class Three implements One, Two {
    public void method() {
        super.One.method();
    }
}
```

- [ ] B

```java
class Three implements One, Two {
    public void method() {
        One.method();
    }
}
```

- [ ] C

```java
class Three implements One, Two {
}
```

- [x] D

```java
class Three implements One, Two {
    public void method() {
        One.super.method();
    }
}
```

#### Explanation

If you use `super` in a class it usually refers to the ancestor of that class.

In the case of override default method of an interface you have to specify the specific interface which default
implementation you want to invoke.

Syntax:

```java
<Interface>.super.<method>();
```

#### Q9. What is the output of this code?

```java
class Main {
    public static void main(String[] args) {
        List list = new ArrayList();
        list.add("hello");
        list.add(2);
        System.out.print(list.get(0) instanceof Object);
        System.out.print(list.get(1) instanceof Integer);
    }
}
```

- [ ] The code does not compile.
- [ ] truefalse
- [x] truetrue
- [ ] falsetrue

#### Explanation

The `instanceof` is a binary operator used to test if an object is of a given type. The result of the operation is
either `true` or `false`.

Class `Object` is the root of the class hierarchy. Every class has an Object as a superclass.

All objects, including arrays, implement the methods of this class.

#### Q10. Given the following two classes, what will be the output of the Main class?

```java
package mypackage;

public class Math {
    public static int abs(int num) {
        return num < 0 ? -num : num;
    }
}
```

```java
package mypackage.elementary;

public class Math {
    public static int abs(int num) {
        return -num;
    }
}
```

```java
import mypackage.Math;
import mypackage.elementary.*;

class Main {
    public static void main(String[] args) {
        System.out.println(Math.abs(123));
    }
}
```

- [ ] Lines 1 and 2 generate compiler errors due to class name conflicts.
- [ ] "-123"
- [ ] It will throw an exception on line 5.
- [x] "123"

#### Explanation

The answer is "123". The `abs()` method evaluates to the one inside `mypackage`.Math class.

#### Q11. What is the result of this code?

```java
class MainClass {
    final String message() {
        return "Hello!";
    }
}

class Main extends MainClass {
    public static void main(String[] args) {
        System.out.println(message());
    }

    String message() {
        return "World!";
    }
}
```

- [x] It will not compile because of line 10.
- [ ] "Hello!"
- [ ] It will not compile because of line 2.
- [ ] "World!"

#### Explanation

Java `final` keyword is a non-access specifier that is used to restrict a class, variable, and method.

If we declare a method as `final`, then it can’t be overridden by any subclasses. And, if we declare a class as `final`,
we restrict the other classes to inherit or extend it.

#### Q12. Given this code, which command will output "2"?

```java
class Main {
    public static void main(String[] args) {
        System.out.println(args[2]);
    }
}
```

- [ ] `java Main 1 2 "3 4" 5`
- [x] `java Main 1 "2" "2" 5`
- [ ] `java Main.class 1 "2" 2 5`
- [ ] `java Main 1 "2" "3 4" 5`

#### Explanation

A Java application can accept any number of arguments from the command line. This allows the user to specify
configuration information when the application is launched.

The user enters command-line arguments when invoking the application and specifies them after the name of the class to
be run.

For example, suppose a Java application called Sort sorts lines in a file. To sort the data in a file
named `friends.txt`, a user would enter:

```
java Sort friends.txt
```

When an application is launched, the runtime system passes the command-line arguments to the application's main method
via an array of Strings.

In the previous example, the command-line arguments passed to the Sort application in an array that contains a single
String: "friends.txt".

**Link**:
[Command-Line Arguments](https://docs.google.com/document/d/1esnVFZLjSsrBb6tK4BCaWsJqjwXQ8gTxboTXTZw9yzg/edit#heading=h.tj8iikd1nrrx)

#### Q13. What is the output of this code?

```java
class Main {
    public static void main(String[] args) {
        int a = 123451234512345;
        System.out.println(a);
    }
}
```

- [ ] "123451234512345"
- [x] Nothing - this will not compile.
- [ ] a negative integer value
- [ ] "12345100000"

#### Explanation

The `int` type in Java can be used to represent any whole number from -2.147.483.648 to 2.147.483.647.

Therefore, this code will not compile as the number assigned to `a` is larger than the `int` type can hold.

#### Q14. What is the output of this code?

```java
class Main {
    public static void main(String[] args) {
        String message = "Hello world!";
        String newMessage = message.substring(6, 12)
                + message.substring(12, 6);
        System.out.println(newMessage);
    }
}
```

- [ ] The code does not compile.
- [x] A runtime exception is thrown.
- [ ] "world!!world"
- [ ] "world!world!"

#### Explanation

```java
public String substring(int startIndex):
```

The `substring(int startIndex)` method returns a new String object containing the substring of the given string from
specified startIndex.

The method throws an `IndexOutOfBoundException` when the `startIndex` is larger than the length of String or less than
zero.

**Note**: Index starts from `0`.

The public class `IndexOutOfBoundsException` extends RuntimeException. Thrown to indicate that an index of some sort (
such as to an array, to a string, or to a vector) is out of range.

![](src/java/java-exceptions-classes.png)

#### Q15. How do you write a foreach loop that will iterate over ArrayList\<Pencil\>pencilCase?

- [x] `for (Pencil pencil : pencilCase) {}`
- [ ] `for (pencilCase.next()) {}`
- [ ] `for (Pencil pencil : pencilCase.iterator()) {}`
- [ ] `for (pencil in pencilCase) {}`

#### Explanation

For-each is another array traversing technique like for loop, while loop and do-while loop.

Syntax:

```
class Main {
    public static void main(String[] args) {
        for (type var : array) {
            // statements using var;
        }
    }
}
```

Example:

```java
class TestClass {

    public static void main(String[] arg) {
        {
            int[] marks = {125, 132, 95, 116, 110};

            int highest_marks = maximum(marks);
            System.out.println("The highest score is " + highest_marks);
        }
    }

    public static int maximum(int[] numbers) {
        int maxSoFar = numbers[0];

        for (int num : numbers) {
            if (num > maxSoFar) {
                maxSoFar = num;
            }
        }
        return maxSoFar;
    }
}
Output:The highest score is 132
```

#### Q16. What does this code print?

```java
System.out.print("apple".compareTo("banana"));
```

- [ ] `0`
- [ ] positive number
- [x] negative number
- [ ] compilation error

#### Explanation

The Java String class `compareTo()` method compares the given string with the current string lexicographically.

The `compareTo()` method returns a positive number, negative number, or 0

- If the first string is lexicographically greater than the second string, it returns a positive number (difference of
  character value);
- If the first string is less than the second string lexicographically, it returns a negative number;
- If the first string is lexicographically equal to the second string, it returns 0.

```java
public class CompareToExample {
    public static void main(String[] args) {
        String s1 = "hello";
        String s2 = "hello";
        String s3 = "meklo";
        String s4 = "hemlo";
        String s5 = "flag";
        System.out.println(s1.compareTo(s2)); //0 because both are equal  
        System.out.println(s1.compareTo(s3)); //-5 because "h" is 5 times lower than "m"  
        System.out.println(s1.compareTo(s4)); //-1 because "l" is 1 times lower than "m"  
        System.out.println(s1.compareTo(s5)); //2 because "h" is 2 times greater than "f"  
    }
}
```

Alphabet:

```
ABCDEFGHIJKLMNOPQRSTUVWXYZ
```

#### Q17. You have an ArrayList of names that you want to sort alphabetically. Which approach would **NOT** work?

- [ ] `names.sort(Comparator.comparing(String::toString))`
- [ ] `Collections.sort(names)`
- [x] `names.sort(List.DESCENDING)`
- [ ] `names.stream().sorted((s1, s2) -> s1.compareTo(s2)).collect(Collectors.toList())`

#### Explanation

Let's take a quick look at the sorting methods offered in each answer.

Pojo class to compare methods:

```java
public class Player {
    private int ranking;
    private String name;
    private int age;
// constructor, getters, setters  
}
```

**1. `names.sort(Comparator.comparing(String::toString))`**

The `Comparator` interface defines a `compare(arg1, arg2)` method with two arguments that represent compared objects and
works similarly to the `Comparable.compareTo()` method.

The `Comparator.comparing` method returns a `Comparator` object that will use the specified field as the sort key.

We'll create a `Comparator` to use the ranking attribute of Player to sort the players:

```java
public class PlayerRankingComparator implements Comparator<Player> {

    @Override
    public int compare(Player firstPlayer, Player secondPlayer) {
        return Integer.compare(firstPlayer.getRanking(), secondPlayer.getRanking());
    }
}
```

The `Comparator.comparing` method takes a method calculating the property that will be used for comparing items, and
returns a matching Comparator instance:

```java
Comparator<Player> byRanking=Comparator.comparing(Player::getRanking);
```

**2. `Collections.sort(names)`**

The `java.util.Collections.sort()` method is used to sort the elements present in the specified list of Collection in
ascending order. It works similar to the `java.util.Arrays.sort()` method, but it is better than as it can sort the
elements of Array as well as linked list, queue and many more present in it.

Java program to demonstrate working of `Collections.sort()`

```java
public class CollectionSorting {
    public static void main(String[] args) {
        ArrayList<String> list = new ArrayList<String>();
        list.add("Geeks For Geeks");
        list.add("Friends");
        list.add("Dear");

        /* Collections.sort method is sorting the
        elements of ArrayList in ascending order. */
        Collections.sort(list);

        System.out.println("List after the use of" +
                " Collection.sort() :\n" + al);
    }
}
```

`names.sort(List.DESCENDING)`**

The `sort()` method accepts an instance of Comparator implementing class which must be able to compare the elements
contained in the arraylist. Internally, the `sort()` method uses `Arrays.sort()` method to compare and sort the elements
in the list.

```
public void sort(Comparator<? super E>c){

final int expectedModCount=modCount;

        Arrays.sort((E[])elementData,0,size,c);

        if(modCount!=expectedModCount)
        throw new ConcurrentModificationException();
        modCount++;

        }
```

**4. `names.stream().sorted((s1,s2)->s1.compareTo(s2)).collect(Collectors.toList())`

The Stream `sorted()` returns a stream consisting of the elements of this stream, sorted according to natural order.

```java
class GFG {

    public static void main(String[] args) {
        List<Integer> list = Arrays.asList(-9, -18, 0, 25, 4);
        System.out.println("The sorted stream is : ");
        list.stream().sorted().forEach(System.out::println);
    }
}
```

The `compareTo(T o)` method compares this object with the specified object for order.

```java
public class Player implements Comparable<Player> {

    // same as before

    @Override
    public int compareTo(Player otherPlayer) {
        return Integer.compare(getRanking(), otherPlayer.getRanking());
    }
}
```

The sorting order is decided by the return value of the `compareTo()` method. The `Integer.compare(x, y)` returns

- -1 if x is less than y;
- 0 if they're equal;
- 1 otherwise.

The method returns a number indicating whether the object being compared is less than, equal to, or greater than the
object being passed as an argument.

#### Q18. By implementing encapsulation, you cannot directly access the class's \_ properties unless you are writing code inside the class itself.

- [x] private
- [ ] protected
- [ ] no-modifier
- [ ] public

#### Explanation

The `private` keyword is an access modifier used for attributes, methods and constructors, making them only accessible
within the declared class.

#### Q19. Which is the most up-to-date way to instantiate the current date?

- [ ] `new SimpleDateFormat("yyyy-MM-dd").format(new Date())`
- [ ] `new Date(System.currentTimeMillis())`
- [x] `LocalDate.now()`
- [ ] `Calendar.getInstance().getTime()`

#### Explanation

LocalDate is the newest class added in java 8.

The `now()` method of a `LocalDate` class is used to obtain the current date from the system clock in the default
time-zone:

- **Parameters**: This method accepts no parameter;
- **Return value**: This method returns the current date using the system clock and default time-zone.

#### Q20. Fill in the blank to create a piece of code that will tell whether `int0` is divisible by `5`:

`boolean isDivisibleBy5 = _____`

- [ ] `int0 / 5 ? true: false`
- [x] `int0 % 5 == 0`
- [ ] `int0 % 5 != 5`
- [ ] `Math.isDivisible(int0, 5)`

#### Q21. How many times will this code print "Hello World!"?

```
class Main {
    public static void main(String[] args) {
        for (int i = 0; i < 10; i = i++) {
            i += 1;
            System.out.println("Hello World!");
        }
    }
}
```

- [x] 10 times
- [ ] 9 times
- [ ] 5 times
- [ ] infinite number of times

#### Explanation

Observe the loop increment. It's not an increment, it's an assignment.

Standard syntax:

```java
for(int i=0;i< 5;i++){
        System.out.println(i);
        }
```

Our case:

```java
for(int i=0;i< 10;i=i++){
        i+=1;
        System.out.println("Hello World!");
        }
```

Note the difference between `i++` and `i=i++`.

#### Q22. The runtime system starts your program by calling which function first?

- [ ] print
- [ ] iterative
- [ ] hello
- [x] main

#### Explanation

A Java application must contain a `main()` method whose signature looks like this

```java
public static void main(String args[])
```

The method signature for the `main()` method contains three modifiers:

1. `public` indicates that the `main()` method can be called by any object.
2. `static` indicates that the `main()` method is a class method.
3. `void` indicates that the `main()` method has no return value.

The runtime system starts your program by calling its `main()` function first.

#### Q23. What code would you use in Constructor A to call Constructor B?

```java
public class Jedi {
    /* Constructor A */
    Jedi(String name, String species) {
    }

    /* Constructor B */
    Jedi(String name, String species, boolean followsTheDarkSide) {
    }
}
```

- [ ] Jedi(name, species, false)
- [ ] new Jedi(name, species, false)
- [x] this(name, species, false)
- [ ] super(name, species, false)

**Note:** This code won't compile, possibly broken code sample.

#### Explanation

In Java, a constructor is a block of codes similar to the method. It is called when an instance of the class is created.
At the time of calling constructor, memory for the object is allocated in the memory.

Constructor is a special type of method which is used to initialize the object.

```java
public class Foo {
    private int x;

    public Foo() {
        this(1);
    }

    public Foo(int x) {
        this.x = x;
    }
}
```

To chain to a particular superclass constructor instead of one and the same class, use `super` instead of `this`
keyword. Note that you can only chain to one constructor, and it has to be the first statement in your constructor body.

#### Q24. Which statement is **NOT** true?

- [ ] An anonymous class may specify an abstract base class as its base type.
- [x] An anonymous class does not require a zero-argument constructor.
- [ ] An anonymous class may specify an interface as its base type.
- [ ] An anonymous class may specify both an abstract class and interface as base types.

#### Explanation

An Anonymous class is an inner class without a name and for which only a single object is created.

1. There might exist exactly one instance of an anonymous class;
2. Therefore, they can never be abstract;
3. Since they have no name, we can't extend them;
4. Since they have no name, anonymous classes can’t have explicitly declared constructors.

An anonymous inner class can be useful when making an instance of an object with certain “extras” such as overloading
methods of a class or interface, without having to actually subclass a class.

Implementation without using an anonymous class:

```java
class AnonymousDemo {
    public static void main(String[] args) {
        MyClass obj = new MyClass();
        // calling getAge() method implemented at MyClass
        obj.getAge();
    }

}
```

```java
class MyClass implements Age {

    @Override
    public void getAge() {
        System.out.print("Age is " + x);
    }
}
```

```java
interface Age {
    int x = 21;

    void getAge();
}
```

In the program, interface Age is created with `getAge()` method and `x=21`.

`MyClass` is written as an implementation class of `Age` interface. As done in the Program, there is no need to write a
separate class `MyClass`. Instead, directly copy the code of `MyClass` into this parameter, as shown here:

```java
interface Age {
    int x = 21;

    void getAge();
}
```

```java
class AnonymousDemo {

    public static void main(String[] args) {
        // MyClass is hidden inner class of Age interface
        // whose name is not written but an object to it is created. 
        Age oj1 = new Age() {

            @Override
            public void getAge() {
                System.out.print("Age is " + x);
            }
        };
        oj1.getAge();
    }
}
```

#### Q25. What will this program print out to the console when executed?

```java
public class Main {
    public static void main(String[] args) {
        LinkedList<Integer> list = new LinkedList<>();
        list.add(5);
        list.add(1);
        list.add(10);
        System.out.println(list);
    }
}
```

- [x] [5, 1, 10]
- [ ] [10, 5, 1]
- [ ] [1, 5, 10]
- [ ] [10, 1, 5]

#### Explanation

Java LinkedList class uses a doubly linked list to store the elements. It provides a linked-list data structure.

LinkedList example:

![](src/java/java-collection-linkedlist.png)

It inherits the AbstractList class and implements List and Deque interfaces.

![](src/java/java-collection-hierarchy.png)

The important points about Java LinkedList are:

1. Java LinkedList class can contain duplicate elements.
2. Java LinkedList class maintains insertion order.
3. Java LinkedList class is non synchronized.
4. In Java LinkedList class, manipulation is fast because no shifting needs to occur.
5. Java LinkedList class can be used as a list, stack or queue.

Example:

```java
import java.util.*;

public class Test {

    public static void main(String[] args) {

        LinkedList<String> list = new LinkedList<String>();

        list.add("A");
        list.add("B");
        list.addLast("C");
        list.addFirst("D");
        list.add(2, "E");

        System.out.println(list);

        list.remove("B");
        list.remove(3);
        list.removeFirst();
        list.removeLast();

        System.out.println(list);
    }
}

Output:
        [D,A,E,B,C]
        [A]
```

#### Q26. What is the output of this code?

```java
class Main {
    public static void main(String[] args) {
        String message = "Hello";
        for (int i = 0; i < message.length(); i++) {
            System.out.print(message.charAt(i + 1));
        }
    }
}
```

- [ ] "Hello"
- [x] A runtime exception is thrown.
- [ ] The code does not compile.
- [ ] "ello"

#### Explanation

```
Output:
ello
Exception in thread "main" java.lang.StringIndexOutOfBoundsException: String index out of range: 5
at java.lang.String.charAt(String.java:658)
at Main.main(Main.java:5)
```

The `StringIndexOutOfBoundsException` exception thrown by String methods to indicate that an index is either negative or
greater than the size of the string.

For some methods such as the `String.charAt(int)` method, this exception also is thrown when the index is equal to the
size of the string.

`StringIndexOutOfBoundsException` class hierarchy

```
Class StringIndexOutOfBoundsException
java.lang.Object
java.lang.Throwable
java.lang.Exception
java.lang.RuntimeException
java.lang.IndexOutOfBoundsException
java.lang.StringIndexOutOfBoundsException
```

#### Q27. Object-oriented programming is a style of programming where you organize your program around \_ rather than \_ and data rather than logic.

- [ ] functions; actions
- [x] objects; actions
- [ ] actions; functions
- [ ] actions; objects

#### Explanation

In Object-Oriented Programming, a program is divided into small parts called objects.

Object-oriented programming is based on the concept of objects. In object-oriented programming data structures, or
objects are defined, each with its own properties or attributes. Each object can also contain its own procedures or
methods. Software is designed by using objects that interact with one another.

#### Q28. What statement returns true if "nifty" is of type String?

- [ ] `"nifty".getType().equals("String")`
- [ ] `"nifty".getType() == String`
- [ ] `"nifty".getClass().getSimpleName() == "String"`
- [x] `"nifty" instanceof String`

#### Q29. What is the output of this code?

```java
import java.util.*;

class Main {
    public static void main(String[] args) {
        List<Boolean> list = new ArrayList<>();
        list.add(true);
        list.add(Boolean.parseBoolean("FalSe"));
        list.add(Boolean.TRUE);
        System.out.print(list.size());
        System.out.print(list.get(1) instanceof Boolean);
    }
}
```

- [ ] A runtime exception is thrown.
- [ ] 3false
- [ ] 2true
- [x] 3true

#### Explanation

```java
System.out.println(list);

        Output:
        [true,false,true]
```

The `size()` method of List interface in Java is used to get the number of elements in this list. That is, this method
returns the count of elements present in this list container.

The `get(int i)` method of List interface in Java is used to get the element present in this list at a given specific
index.

The `instanceof` is a binary operator used to test if an object is of a given type. The result of the operation is
either true or false.

#### Q30. What is the result of this code?

```
1: class Main {
2: 	Object message(){
3: 		return "Hello!";
4: 	}
5: 	public static void main(String[] args) {
6: 		System.out.print(new Main().message());
7: 		System.out.print(new Main2().message());
8: 	}
9: }
10: class Main2 extends Main {
11: 	String message(){
12: 		return "World!";
13: 	}
14: }
```

- [ ] It will not compile because of line 7.
- [ ] Hello!Hello!
- [x] Hello!World!
- [ ] It will not compile because of line 11.

#### Explanation

The `extends` keyword is used to indicate that the class which is being defined is derived from the base class using
inheritance. So basically, `extends` keyword is used to extend the functionality of the parent class to the subclass.

The `Default` access modifier is package-private, and it is visible only from the same package.

Therefore, we can create objects of this class in any other class of the package (so no exception).

#### Q31. What method can be used to create a new instance of an object?

- [ ] another instance
- [ ] field
- [x] constructor
- [ ] private method

#### Explanation

A Constructor is similar to a method that is invoked when an object of the class is created. Unlike Java methods, a
constructor has the same name as that of the class and does not have any return type.

#### Q32. Which is the most reliable expression for testing whether the values of two string variables are the same?

- [ ] string1 == string2
- [ ] string1 = string2
- [ ] string1.matches(string2)
- [x] string1.equals(string2)

#### Explanation

The Java String class `equals() `method compares the two given strings based on the content of the string:

- If any character is not matched, it returns false;
- If all characters are matched, it returns true.

The String `equals()` method overrides the `equals()` method of the Object class.

#### Q33. Which letters will print when this code is run?

```java
public static void main(String[]args){
        try{
        System.out.println("A");
        badMethod();
        System.out.println("B");
        }catch(Exception ex){
        System.out.println("C");
        }finally{
        System.out.println("D");
        }
        }

public static void badMethod(){
        throw new Error();
        }
```

- [ ] A, B, and D
- [ ] A, C, and D
- [ ] C and D
- [x] A and D

#### Explanation

The letter "B" will not be printed because the program will terminate with an Error.

The letter "C" will not be printed because the program will throw an Error (not an Exception).

**Note**: `Error` is not inherited from `Exception`

![](src/java/java-exceptions-classes.png)

#### Q34. What is the output of this code?

```java
class Main {
    static int count = 0;

    public static void main(String[] args) {
        if (count < 3) {
            count++;
            main(null);
        } else {
            return;
        }
        System.out.println("Hello World!");
    }
}
```

- [ ] It will throw a runtime exception.
- [ ] It will not compile.
- [x] It will print "Hello World!" three times.
- [ ] It will run forever.

#### Q35. What is the output of this code?

```java
import java.util.*;

class Main {
    public static void main(String[] args) {
        String[] array = {"abc", "2", "10", "0"};
        List<String> list = Arrays.asList(array);
        Collections.sort(list);
        System.out.println(Arrays.toString(array));
    }
}
```

- [ ] `[abc, 0, 2, 10]`
- [ ] The code does not compile.
- [ ] `[abc, 2, 10, 0]`
- [x] `[0, 10, 2, abc]`

#### Explanation

The `asList()` method of `java.util.Arrays` class is used to return a fixed-size list backed by the specified array.

This method acts as a bridge between array-based and collection-based APIs, in combination with `Collection.toArray()`.

The `asList()` method returns a fixed-size list backed by the specified array. Since an array cannot be structurally
modified, it is impossible to add elements to the list or remove elements from it. The list will throw
an `UnsupportedOperationException` if any resize operation is performed on it.

```
public class UnsupportedOperationException
        extends RuntimeException
```

Example:

```java
class Main {
    public static void main(String[] args) {
        String[] array = {"abc", "2", "10", "0"};
        List<String> list = Arrays.asList(array);
        list.add("22");
    }
}

Output:
        Exception in thread"main"java.lang.UnsupportedOperationException at java.base/java.util.AbstractList.add(
        AbstractList.java:153)
```

#### Q36. What is the output of this code?

```
class Main {
	public static void main(String[] args) {
		String message = "Hello";
		print(message);
		message += "World!";
		print(message);
	}
	static void print(String message){
		System.out.print(message);
		message += " ";
	}
}
```

- [ ] Hello World!
- [x] HelloHelloWorld!
- [ ] Hello Hello World!
- [ ] Hello HelloWorld!

#### Q37. What is displayed when this code is compiled and executed?

```
public class Main {
	public static void main(String[] args) {
		int x = 5;
		x = 10;
		System.out.println(x);
	}
}
```

- [ ] x
- [ ] null
- [x] 10
- [ ] 5

#### Q38. Which approach cannot be used to iterate over a List named _theList_?

- [ ] A

```java
for(int i=0;i<theList.size();i++){
        System.out.println(theList.get(i));
        }
```

- [ ] B

```java
for(Object object:theList){
        System.out.println(object);
        }
```

- [x] C

```java
Iterator it=theList.iterator();
        for(it.hasNext()){
        System.out.println(it.next());
        }
```

- [ ] D

```java
theList.forEach(System.out::println);
```

#### Explanation

Consider each answer:

```java
for(int i=0;i<theList.size();i++){
        System.out.println(theList.get(i));
        }
```

The `size()` method of `List` interface in Java is used to get the number of elements in this list.

```java
for(Object object:theList){
        System.out.println(object);
        }
```

Class `Object` is the root of the class hierarchy and every class has an Object as a superclass. All objects, including
arrays, implement the methods of this class.

```java
Iterator it=theList.iterator();

        for(it.hasNext()){
        System.out.println(it.next());
        }

        Warning:cant resolve symbol hasNext.
```

**Explanation**: `for (it.hasNext())` should be `while (it.hasNext())`.

The `Iterator` is an interface which belongs to the collection framework. It allows us to traverse the collection,
access the data element and remove the data elements of the collection.

The `java.util` package has public interface `Iterator` and contains three methods:

| Method name        | Description of the method                                                                                                                                       |
|--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| boolean hasNext(): | It returns true if the Iterator has more elements to iterate.                                                                                                   |
| Object next()      | It returns the next element in the collection until the hasNext() method returns true. This method throws ‘NoSuchElementException’ if there is no next element. |
| void remove()      | It removes the current element in the collection. This method throws ‘IllegalStateException’ if this function is called before next( ) is invoked.              |

```java
ArrayList<String> people=new ArrayList<String>();
        people.add("Tom");
        people.add("Alice");
        people.add("Kate");
        people.forEach(System.out::println);
```

The `forEach()` method of ArrayList is used to perform a certain operation for each element in ArrayList. This method
traverses each element of the `Iterable` of ArrayList until all elements have been Processed by the method or an
exception is raised.

#### Q39. What method signature will work with this code?

`boolean healthyOrNot = isHealthy("avocado");`

- [ ] public void isHealthy(String avocado)
- [x] boolean isHealthy(String string)
- [ ] public isHealthy("avocado")
- [ ] private String isHealthy(String food)

#### Q40. Which are valid keywords in a Java module descriptor (module-info.java)?

- [ ] provides, employs
- [ ] imports, exports
- [ ] consumes, supplies
- [x] requires, exports

#### Explanation

A Java Module is a packaging mechanism that enables you to package a Java application or Java API as a separate Java
module.

A Java module is packaged as a modular JAR file. A Java module can specify which of the Java packages it contains that
should be visible to other Java modules which use this module.

A Module descriptor is the compiled version of a module declaration that's defined in a file named module-info.java

```
module moduleName {
  ...
}
```

The module declaration’s body can be empty or may contain various module directives, including

- requires;
- exports;
- provides… with;
- uses and opens (each of which we discuss).

A `requires` module directive specifies that this module depends on another module — this relationship is called a
module dependency. Each module must explicitly state its dependencies.

When `module A` requires `module B`, module A is said to read module B and module B is read by module A. To specify a
dependency on another module, use requires, as in:

```java
requires moduleName;
```

An `exports` module directive specifies one of the module’s packages whose public types (and their nested public and
protected types) should be accessible to code in all other modules.

An `exports… to` directive enables you to specify in a comma-separated list precisely which module’s or modules’ code
can access the exported package — this is known as a qualified export.

#### Q41. Which type of variable keeps a constant value once it is assigned?

- [ ] non-static
- [ ] static
- [x] final
- [ ] private

#### Explanation

Java `final` keyword is a non-access specifier that is used to restrict a class, variable, and method.

- If we initialize a variable with the `final` keyword, then we can’t modify its value;
- If we declare a method as `final`, then it can’t be overridden by any subclasses.

#### Q42. How does the keyword `volatile` affect how a variable is handled?

- [ ] It will be read by only one thread at a time.
- [ ] It will be stored on the hard drive.
- [x] It will never be cached by the CPU.
- [ ] It will be preferentially garbage collected.

#### Explanation

The Java `volatile` keyword is used to mark a Java variable as "being stored in main memory".

More precisely that means, that:

1. Every read of a volatile variable will be read from the computer's main memory, and not from the CPU cache;
2. Every write to a volatile variable will be written to main memory, and not just to the CPU cache.

#### Q43. What is the result of this code?

```java
char smooch='x';
        System.out.println((int)smooch);
```

- [ ] an alphanumeric character
- [ ] a negative number
- [x] a positive number
- [ ] a ClassCastException

#### Explanation

We can convert `char` to `int` in Java using various ways. If we directly assign a char variable to int, it will return
the ASCII value of the given character.

Let's see the simple code to convert char to int in java.

```
public class CharToIntExample1 {
  public static void main(String[] args) {
    char c = 'a';
    char c2 = '1';
    int a = c;
    int b = c2;
    System.out.println(a);
    System.out.println(b);
  }
}

Output:
        97
        49
```

#### Q44. You get a NullPointerException. What is the most likely cause?

- [ ] A file that needs to be opened cannot be found.
- [ ] A network connection has been lost in the middle of communications.
- [ ] Your code has used up all available memory.
- [x] The object you are using has not been instantiated.

#### Explanation

`NullPointerException` is raised in an application when we are trying to do some operation on null where an object is
required.

Some common reasons for `NullPointerException` in java programs are:

1. Invoking a method on an object instance but at runtime the object is null;
2. Accessing variables of an object instance that is null at runtime;
3. Throwing null in the program;
4. Accessing index or modifying value of an index of an array that is null;
5. Checking the length of an array that is null at runtime.

![](src/java/java-exceptions-classes.png)

#### Q45. How would you fix this code so that it compiles?

```java
public class Nosey {
    int age;

    public static void main(String[] args) {
        System.out.println("Your age is: " + age);
    }
}
```

- [x] Make age static.
- [ ] Make age global.
- [ ] Make age public.
- [ ] Initialize age to a number.

#### Explanation

The error `non static variable can’t be referenced from a static context` in Java is mostly faced by the beginners at
the time of compilation of Java programs.

The reason for this error is that they use a non-static member variable in the `main()` method. Because the `main()`
method in Java is a static method, and it is invoked automatically, we need not create an object to invoke it.

To understand the error, first we should understand the static and non-static method in Java:

1. Each instance of a non-static variable has a different value and is created when the `new()` operator initializes an
   instance of an object;
2. The static variables are created or initialized when the class loads into JVM.

We need an instance of an object for calling the non-static variable. We can create many objects by giving different
values to that non-static or instance variable.

#### Q46. Add a Duck called "Waddles" to the ArrayList **ducks**.

```java
public class Duck {
    private String name;

    Duck(String name) {
    }
}
```

- [ ] `Duck waddles = new Duck();`
  `ducks.add(waddles);`
- [ ] `Duck duck = new Duck("Waddles");`
  `ducks.add(waddles);`
- [x] `ducks.add(new Duck("Waddles"));`
- [ ] `ducks.add(new Waddles());`

#### Q47. If you encounter `UnsupportedClassVersionError` it means the code was `___` on a newer version of Java than the JRE `___` it.

- [ ] executed; interpreting
- [ ] executed; compiling
- [x] compiled; executing
- [ ] compiled, translating

#### Explanation

The `UnsupportedClassVersionError` is a subclass of the `LinkageError` class and specifically, of the `ClassFormatError`
class. This error is thrown by the JVM when it tries to read a class file whose major and minor version numbers are not
supported.

The JRE is a software layer that runs on top of a computer’s operating system software and provides the class libraries
and other resources that a specific Java program needs to run.

Difference between JDK,JRE and JVM:

![](src/java/jdk-jre-jvm.png)

#### Q48. Given this class, how would you make the code compile?

```java
public class TheClass {
    private final int x;
}
```

- [ ] A

```java
public TheClass(){
        x+=77;
        }
```

- [ ] B

```java
public TheClass(){
        x=null;
        }
```

- [x] C

```java
public TheClass(){
        x=77;
        }
```

- [ ] D

```java
private void setX(int x){
        this.x=x;
        }
public TheClass(){
        setX(77);
        }
```

#### Explanation

The program gives an error at the compilation stage:

`Variable 'x' might not have been initialized`

This error occurs when you are trying to use a local variable without initializing it. You won't get this error if you
use an uninitialized class or instance variable because they are initialized with their default value e.g.

Reference types are initialized with `null` and integer types are initialized with `0`, but if you try to use an
uninitialized local variable in Java, you will get this error.

This is because Java has the rule to initialize the local variable before accessing or using them and this is checked at
compile time. If the compiler believes that a local variable might not have been initialized before the next statement
which is using it, you get this error.

The `final` class members are allowed to be assigned only in three places:

1. declaration;
2. constructor;
3. instance-initializer block.

#### Q49. How many times f will be printed?

```java
public class Solution {
    public static void main(String[] args) {
        for (int i = 44; i > 40; i--) {
            System.out.println("f");
        }
    }
}
```

- [x] 4
- [ ] 3
- [ ] 5
- [ ] A Runtime exception will be thrown

#### Explanation

```
Output:

i = 44 Print:  f
i = 43 Print:  f
i = 42 Print:  f
i = 41 Print:  f
```

#### Q50. Which statements about `abstract` classes are true?

1. `abstract` classes can be instantiated.
2. `abstract` classes allow member variables and methods to be inherited by subclasses.
3. `abstract` classes can contain constructors.

- [ ] 1, 2, and 3
- [ ] only 3
- [x] 2 and 3
- [ ] only 2

#### Explanation

An abstract class is a template definition of methods and variables of a class that contains one or more abstracted
methods.

Abstract classes can’t be instantiated, but they can be subclassed.

We can’t instantiate an abstract class in Java because it is abstract, it is not complete, hence it can’t be used.

```java
public abstract class GraphicObject {
    // declare fields and non-abstract methods
    abstract void draw();
}
```

An abstract class can have a constructor in Java. You can either explicitly provide a constructor to the abstract class
or if you don't, the compiler will add a default constructor of no argument in the abstract class.

```java
abstract class Server {
    protected final String name;

    public Server(String name) {
        this.name = name;
    }

    public abstract boolean start();
}
```

#### Q51. Which keyword lets you call the constructor of a parent class?

- [ ] parent
- [x] super
- [ ] this
- [ ] new

#### Explanation

The `super` keyword in Java is a reference variable which is used to refer to an immediate parent class object. Whenever
you create the instance of a subclass, an instance of the parent class is created implicitly which is referred to by
`super` reference variable.

Usage of Java super Keyword:

1. `super()` can be used to refer to an immediate parent class instance variable;
2. `super()` can be used to invoke the immediate parent class method;
3. `super()` can be used to invoke immediate parent class constructor.

Let's see a simple example:

```java
class Animal {
    Animal() {
        System.out.println("animal is created");
    }
}

class Dog extends Animal {
    Dog() {
        super();
        System.out.println("dog is created");
    }
}

class TestSuper3 {
    public static void main(String[] args) {
        Dog d = new Dog();
    }
}

Output:
        animal is created
        dog is created
```

#### Q52. What is the result of this code?

```java
  1:int a=1;
        2:int b=0;
        3:int c=a/b;
        4:System.out.println(c);
```

- [x] It will throw an ArithmeticException.
- [ ] It will run and output 0.
- [ ] It will not compile because of line 3.
- [ ] It will run and output infinity.

#### Explanation

The `java.lang.ArithmeticException` is an unchecked exception in Java. Usually, one would come across
`java.lang.ArithmeticException: / by zero` which occurs when an attempt is made to divide two numbers and the number in
the denominator is zero.

ArithmeticException objects may be constructed by the JVM.

To handle `ArithmeticException` use try and catch blocks. Surround the statements that can throw `ArithmeticException`
with try and catch blocks;

Take necessary action for our program, as the execution doesn’t abort.

```java
public class ArithmeticExceptionTest {
    public static void main(String[] args) {
        int a = 0, b = 10;
        int c = 0;
        try {
            c = b / a;
        } catch (ArithmeticException e) {
            e.printStackTrace();
            System.out.println("We are just printing the stack trace.\n"
                    + "ArithmeticException is handled. But take care of the variable \"c\"");
        }
        System.out.println("Value of c :" + c);
    }
}
```

#### Q53. Normally, to access a static member of a class such as Math.PI, you would need to specify the class "Math". What would be the best way to allow you to use simply "PI" in your code?

- [x] Add a static import.
- [ ] Declare local copies of the constant in your code.
- [ ] This cannot be done. You must always qualify references to static members with the class form which they came
  from.
- [ ] Put the static members in an interface and inherit from that interface.

#### Explanation

The static import construct allows unqualified access to static members without inheriting from the type containing the
static members.

```java
public class WithoutStaticImport {
    public static void main(String[] args) {
        double value = Math.cos(Math.PI * 4);
        System.out.println(value);
    }
}
```

```java
package oop;

import static java.lang.Math.PI;
import static java.lang.Math.cos;

public class StaticImport {
    public static void main(String[] args) {
        double value = cos(PI * 4);
        System.out.println(value);
    }
}
```

#### Q54. Which keyword lets you use an interface?

- [ ] extends
- [x] implements
- [ ] inherits
- [ ] import

#### Explanation

An interface in the Java programming language is an abstract type that is used to specify a behavior that classes must
implement.
To access the interface methods, the interface must be "implemented" by another class with the “implements” keyword. The
body of the interface method is provided by the "implement" class.

Example:

```java
interface Animal {
    public void animalSound(); // interface method (does not have a body)

    public void sleep();
}
```

```java
class Pig implements Animal {
    public void animalSound() {
        System.out.println("The pig says: wee wee");
    }

    public void sleep() {
        System.out.println("Zzz");
    }
}

class MyMainClass {
    public static void main(String[] args) {
        Pig myPig = new Pig();
        myPig.animalSound();
        myPig.sleep();
    }
}
```

#### Q55. Why are ArrayLists better than arrays?

- [x] You don't have to decide the size of an ArrayList when you first make it.
- [ ] You can put more items into an ArrayList than into an array.
- [ ] ArrayLists can hold more kinds of objects than arrays.
- [ ] You don't have to decide the type of an ArrayList when you first make it.

#### Explanation

An ArrayList is a resizable array, also called a dynamic array. It grows its size to accommodate new elements and
shrinks the size when the elements are removed.

Before discussing the advantages of ArrayList, let’s see what are the drawbacks of arrays:

1. Arrays are of fixed length so you can’t change the size of the arrays once they are created;
2. You can’t accommodate an extra element in an array after they are created;
3. Memory is allocated to an array during its creation only, much before the actual elements are added to it.

Because of these drawbacks, use of Arrays is less preferred. Instead of arrays, you can use the ArrayList class which
addresses all these drawbacks. Here are some advantages of using ArrayList over arrays.

1. You can define ArrayList as a resizable array. Size of the ArrayList is not fixed. ArrayList can grow and shrink
   dynamically;
2. Elements can be inserted at or deleted from a particular position;
3. ArrayList class has many methods to manipulate the stored objects.
4. If generics are not used, ArrayList can hold any type of objects.
5. You can traverse an ArrayList in both the directions – forward and backward using ListIterator.

```java
  class ArrayListDemo {
    public static void main(String[] args) {
        ArrayList list = new ArrayList();     //ArrayList without generics

        list.add("ZERO");    //adding string type object
        list.add(1);        //adding primitive int type
        list.add(20.24);    //adding primitive double type
        list.add(new Float(23.56));   //Adding Float wrapper type object
        list.add(new Long(25));      //Adding Long wrapper type object

        System.out.println(list);     //Output : [ZERO, 1, 20.24, 23.56, 25]
    }
}
```

#### Q56. Declare a variable that holds the first four digits of Π

- [ ] int pi = 3.141;
- [ ] decimal pi = 3.141;
- [x] double pi = 3.141;
- [ ] float pi = 3.141;

#### Explanation

The default Java type which Java will be using for a float variable will be double.

So, even if you declare any variable as float, what the compiler has to actually do is to assign a double value to a
float variable, which is not possible.

So, to tell the compiler to treat this value as a float, that 'F' is used.

```java
public class TestReal {
    public static void main(String[] argv) {
        double pi = 3.14159265;       //accuracy up to 15 digits
        float pi2 = 3.141F;           //accuracy up to 6-7 digits

        System.out.println("Pi=" + pi);
        System.out.println("Pi2=" + pi2);
    }
}
```

#### Q57. Use the magic power to cast a spell

```java
public class MagicPower {
    void castSpell(String spell) {
    }
}
```

- [x] `new MagicPower().castSpell("expecto patronum")`
- [ ] `MagicPower magicPower = new MagicPower();`
  `magicPower.castSpell();`
- [ ] `MagicPower.castSpell("expelliarmus");`
- [ ] `new MagicPower.castSpell();`

#### Q58. What language construct serves as a blueprint containing an object's properties and functionality?

- [ ] constructor
- [ ] instance
- [x] class
- [ ] method

#### Explanation

A class is a user defined blueprint or prototype from which objects are created. It represents the set of properties or
methods that are common to all objects of one type.

#### Q59. What does this code print?

```java
public static void main(String[]args){
        int x=5,y=10;
        swapsies(x,y);
        System.out.println(x+" "+y);
        }

static void swapsies(int a,int b){
        int temp=a;
        a=b;
        b=temp;
        }
```

- [ ] 10 10
- [x] 5 10
- [ ] 10 5
- [ ] 5 5

#### Explanation

What happens inside a static method does not affect the variables x and y.

#### Q60. What is the result of this code?

```java
try{
        System.out.println("Hello World");
        }catch(Exception e){
        System.out.println("e");
        }catch(ArithmeticException e){
        System.out.println("e");
        }finally{
        System.out.println("!");
        }
```

- [ ] Hello World
- [x] It will not compile because the second catch statement is unreachable
- [ ] Hello World!
- [ ] It will throw runtime exception

The `ArithmeticException` is thrown when an exceptional arithmetic condition has occurred. For example, an integer "
divide by zero" throws an instance of this class.

```java
public class ArithmeticException extends RuntimeException
```

```
java.lang.Object
  java.lang.Throwable
    java.lang.Exception
      java.lang.RuntimeException
        java.lang.ArithmeticException
```

#### Q70. Java programmers commonly use design patterns. Some examples are the **

\_**, which helps create instances of a class, the **
\_**, which ensures that only one instance of a class can be created; and the **
\_**, which allows for a group of algorithms to be interchangeable.

- [x] static factory method; singleton; strategy pattern
- [ ] strategy pattern; static factory method; singleton
- [ ] creation pattern; singleton; prototype pattern
- [ ] singleton; strategy pattern; static factory method

#### Explanation

A Design Pattern is a well-proven solution for solving a specific task.

Now, a question will be arising in your mind: what kind of specific problem? Let me explain by taking an example.

Problem:

Suppose you want to create a class for which only a single instance should be created and that single object can be used
by all other classes.

Solution:
The Singleton design pattern is the best solution to the above specific problem. So, every design pattern has some
specification or set of rules for solving the problems. What are those specifications, you will see later in the types
of design patterns.
___


The `Static Factory Method` is a public static method on the object that returns a new instance of the object.
The `Singleton` is a design pattern used in object-oriented programming that ensures only a single instance of an object
exists within a system at any given time.
The `Strategy` pattern is a behavioral software design pattern that enables selecting an algorithm at runtime.

#### Q71. Using Java's Reflection API, you can use \_ to get the name of a class and \_ to retrieve an array of its methods.

- [x] this.getClass().getSimpleName(); this.getClass().getDeclaredMethods()
- [ ] this.getName(); this.getMethods()
- [ ] Reflection.getName(this); Reflection.getMethods(this)
- [ ] Reflection.getClass(this).getName(); Reflection.getClass(this).getMethods()

#### Explanation

Reflection is an API which is used to examine or modify the behavior of methods, classes, interfaces at runtime.

* The required classes for reflection are provided under `java.lang.reflect` package
* Reflection gives us information about the class to which an object belongs and also the methods of that class which
  can be executed by using the object
* Through reflection, we can invoke methods at runtime irrespective of the access specifier used with them

The `java.lang.Class.getSimpleName()` returns the simple name of the underlying class as given in the source code.
Returns an empty string if the underlying class is anonymous.

The `java.lang.Class.getDeclaredMethods()` method returns an array of Method objects including public, protected,
default (package) access, and private methods, but excludes inherited methods.

The method returns an array of length 0 if the class or interface declares no methods, or if this Class object
represents a primitive type, an array class, or void

#### Q72. Which is not a valid lambda expression?

- [ ] `a -> false;`
- [ ] `(a) -> false;`
- [x] `String a -> false;`
- [ ] `(String a) -> false;`

#### Explanation

A lambda expression is a short block of code which takes in parameters and returns a value. Lambda expressions are
similar to methods, but they don’t need a name, and they can be implemented right in the body of a method.

The simplest lambda expression contains a single parameter and an expression:

```
parameter -> expression
```

Example of using a lambda expression in the ArrayList's forEach() method to print every item in the list:

```java
public class Main {
    public static void main(String[] args) {
        ArrayList<Integer> numbers = new ArrayList<Integer>();
        numbers.add(9);
        numbers.add(8);
        numbers.forEach((n) -> {
            System.out.println(n);
        });
    }
}
```

#### Q73. Which access modifier makes variables and methods visible only in the class where they are declared?

- [ ] public
- [ ] protected
- [ ] nonmodifier
- [x] private

#### Explanation

| Modifier  | Description                                                        |
|-----------|--------------------------------------------------------------------|
| Default   | declarations are visible only within the package (package private) |
| Private   | declarations are visible within the class only                     |
| Protected | declarations are visible within the package or all subclasses      |
| Public    | declarations are visible everywhere                                |

#### Q74. What type of variable can be assigned to only once?

- [ ] private
- [ ] non-static
- [x] final
- [ ] static

#### Explanation

In Java, when the `final` keyword is used with a variable of primitive data types (int, float, .. etc), the value of the
variable can’t be changed.

Once a final variable has been assigned, it always contains the same value.

#### Q75. How would you convert a String to an Int?

- [ ] `"21".intValue()`
- [ ] `String.toInt("21")`
- [x] `Integer.parseInt("21")`
- [ ] `String.valueOf("21")

#### Explanation

The `parseInt (String s)`  method parses the String argument as a signed decimal integer object. Example:

```java
int myVar=Integer.parseInt("20");  
```

#### Q76. What method should be added to the Duck class to print the name Moby?

```java
public class Duck {

    private String name;

    Duck(String name) {
        this.name = name;
    }

    public static void main(String[] args) {
        System.out.println(new Duck("Moby"));
    }
}
```

- [x] `public String toString() { return name; } `
- [ ] `public void println() { System.out.println(name); } `
- [ ] `String toString() { return this.name; } `
- [ ] `public void toString() { System.out.println(this.name); } `

#### Explanation

If you want to represent any object as a string, `toString()` method comes into existence.

The `toString()` method returns the string representation of the object.

Example:

```java
class Student {
    String name;
    String city;

    Student(String name, String city) {
        this.name = name;
        this.city = city;
    }

    public String toString() {//overriding the toString() method  
        return name + " " + city;
    }

    public static void main(String[] args) {
        Student s1 = new Student("Raj", "lucknow");
        Student s2 = new Student("Vijay", "ghaziabad");

        System.out.println(s1);//compiler writes here s1.toString()  
        System.out.println(s2);//compiler writes here s2.toString()  
    }
}  
```

#### Q77. Which operator is used to concatenate Strings in Java

- [x] `+`
- [ ] `&`
- [ ] `.`
- [ ] `-`

#### Explanation

Concatenation in the Java programming language is the operation of joining two strings together.

You can concatenate Strings in Java using the "+" operator. Example:

```java
import java.util.Scanner;

public class StringExample {
    public static void main(String[] args) {
        System.out.println("Enter the first string: ");
        String str1 = sc.next();
        System.out.println("Enter the second string: ");
        String str2 = sc.next();
        String result = str1 + str2;
        System.out.println(result);
    }
}
```

```
Output:
Enter the first string:
Krishna
Enter the second string:
Kasyap
KrishnaKasyap
```

#### Q78. How many times does this loop print "exterminate"?

```java
for(int i=44;i>40;i--){
        System.out.println("exterminate");
        }
```

- [ ] two
- [x] four
- [ ] three
- [ ] five

#### Explanation

When you know exactly how many times you want to loop through a block of code, use the “for loop”:

Syntax:

```java
for(statement 1;statement 2;statement 3){
// code block to be executed
        }
```

* Statement 1 is executed (one time) before the execution of the code block.
* Statement 2 defines the condition for executing the code block.
* Statement 3 is executed (every time) after the code block has been executed.

The example below will print the numbers 0 to 4:

```java
for(int i=0;i< 5;i++){
        System.out.println(i);
        }
```

#### Q79. What is the value of myCharacter after line 3 is run?

```
1: public class Main {
2:   public static void main (String[] args) {
3:     char myCharacter = "piper".charAt(3);
4:   }
5: }
```

- [ ] p
- [ ] r
- [x] e
- [ ] i

#### Explanation

The `charAt()` method returns the character at the specified index in a string.

The index of the first character is 0, the second character is 1, and so on.

```java
String myStr="Hello";
        char result=myStr.charAt(1);
        System.out.println(result);
```

```
Output:
e
```

#### Q80. When should you use a static method?

- [ ] when your method is related to the object's characteristics
- [x] when you want your method to be available independently of class instances
- [ ] when your method uses an object's instance variable
- [ ] when your method is dependent on the specific instance that calls it

#### Explanation

A static method is a method that belongs to a class rather than an instance of a class.
A static method invoked without the need for creating an instance of a class.

#### Q81. What phrase indicates that a function receives a copy of each argument passed to it rather than a reference to the objects themselves?

- [ ] pass by reference
- [ ] pass by occurrence
- [x] pass by value
- [ ] API call

#### Explanation

**Pass by value**: makes a copy in memory of the parameter’s value, or a copy of the contents of the parameter.

Here is an example in Java:

```java
public static void main(String[]args){
        ...
        int y=5;
        System.out.println(y); // prints "5"
        myMethod(y);
        System.out.println(y); // prints "5"
        }

public static void myMethod(int x){
        ...
        x=4; // myMethod has a copy of x, so it doesn't
        // overwrite the value of variable y used
        // in main() that called myMethod
        }
```

**Pass by reference**: a copy of the address (or reference) to the parameter is stored rather than the value itself.

In this case, modifying the value of the parameter will change the value.

Here is an example in C++, which is very similar to Java syntax (count is C++’s way of printing to the terminal):

```cpp
int main(){
        ...
        int y=5;
        cout<<y; // prints "5"
        myMethod(y);
        cout<<y; // prints "4"
        }

        // & below tells C++ to specifically "pass x by reference"
        int myMethod(int&x){
        ...
        x=4; // myMethod has the address of x, or the
        // reference to x (rather than the value),
        // so it overwrites the value of variable y
        // used in main() that called myMethod
        }
```

#### Q82. In Java, what is the scope of a method's argument or parameter?

- [x] inside the method
- [ ] both inside and outside the method
- [ ] neither inside nor outside the method
- [ ] outside the method

#### Explanation

The scope for a parameter is simply the method body in which the parameter is located. Parameter names only have to be
unique in a parameter list.

For example, we can have two methods testRightTriangle and testScaleneTriangle, both of which have parameter “int”
hypotenuse. Since the scope is just the method body, we know which hypotenuse is being referred to.

```java
public class TwoSides {
    int side1, side2;

    public boolean testRightTriangle(int hypoteneuse) {
// hypoteneuse refers to parameter above
// hypoteneuse is NOT same as testScaleneTriangle
    }

    public boolean testScaleneTriangle(int hypoteneuse) {
// hypoteneuse refers to parameter above
// hypoteneuse is NOT same as testRightTriangle
    }
}
```

Each method has its own hypoteneuse and they don’t affect each other.

#### Q83. What is the output of this code?

```java
public class Main {
    public static void main(String[] args) {
        int[] sampleNumbers = {8, 5, 3, 1};
        System.out.println(sampleNumbers[2]);
    }
}
```

- [ ] 5
- [ ] 8
- [ ] 1
- [x] 3

#### Explanation

An array is a container object that holds a fixed number of values of a single type. The length of an array is
established when the array is created and after creation, its length is fixed.

Each item in an array is called an element, and each element is accessed by its numerical index. Numbering begins with 0
so the 9th element, for example, would therefore be accessed at index 8.

#### Q84. Which change will make this code compile successfully?

```
1: public class Main {
2:   String MESSAGE ="Hello!";
3:   static void print(){
4:     System.out.println(message);
5:   }
6:   void print2(){}
7: }
```

- [ ] Change line 2 to `public static final String message`
- [ ] Change line 6 to `public void print2(){}`
- [ ] Remove the body of the `print2` method and add a semicolon.
- [x] Remove the body of the `print` method.

#### Explanation

```
Output:
Compile-time error: can't resolve symbol 'message'
```

The 1st answer is not correct due to changing line 2 to `public static final String message` raises the
error `message not initialized in the default constructor`.

#### Q85. What is the output of this code?

```java
import java.util.*;

class Main {
    public static void main(String[] args) {
        String[] array = new String[]{"A", "B", "C"};
        List<String> list1 = Arrays.asList(array);
        List<String> list2 = new ArrayList<>(Arrays.asList(array));
        List<String> list3 = new ArrayList<>(Arrays.asList("A", new String("B"), "C"));
        System.out.print(list1.equals(list2));
        System.out.print(list1.equals(list3));
    }
}
```

- [ ] falsefalse
- [x] truetrue
- [ ] falsetrue
- [ ] truefalse

#### Explanation

The `equals()` method of List interface compares the specified object with this collection for equality.

The `equals()` method returns a Boolean value true if both the lists have the same elements and are of the same size.

Example:

```java
import java.util.LinkedList;
import java.util.List;

public class JavaListEqualsExample1 {
    public static void main(String[] args) {
        List<Integer> list = new LinkedList<>();
        for (int i = 0; i < 11; i++) {
            list.add(i);
        }

        List<Integer> list1 = new LinkedList<>();
        for (int i = 0; i < 11; i++) {
            list1.add(i);
        }
//It returns a Boolean value true if both lists have the same elements and size..  
        Boolean bool = list.equals(list1);
        if (bool) {
            System.out.println("Both the lists are equal.\n" + "List  : " + list + "\n" + "List1 : " + list1);
        } else {
            System.out.println("Both the lists are equal.\n" + "List : " + list + "\n" + "List1 : " + list1);
        }
    }
}
```

```
Output:
Both the lists are equal.
List  : [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
List1 : [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

#### Q86. Which code snippet is valid?

- [ ] `ArrayList<String> words = new ArrayList<String>(){"Hello", "World"};`
- [ ] `ArrayList words = Arrays.asList("Hello", "World");`
- [ ] `ArrayList<String> words = {"Hello", "World"};`
- [x] `ArrayList<String> words = new ArrayList<>(Arrays.asList("Hello", "World"));`

#### Explanation

```
ArrayList<String> words = new ArrayList<String>(){"Hello", "World"};
Comment: illegal start of type (syntax error)
```

```
ArrayList words = Arrays.asList("Hello", "World");
Comment: Incompatible types. Found: 'java.util.List<java.lang.String>', required: 'java.util.ArrayList'
```

```
ArrayList<String> words = {"Hello", "World"};
Comment: Array initializer is not allowed here
```

#### Q87. What is the output of this code?

```java
class Main {
    public static void main(String[] args) {
        StringBuilder sb = new StringBuilder("hello");
        sb.deleteCharAt(0).insert(0, "H"). " World!";
        System.out.println(sb);
    }
}
```

- [ ] A runtime exception is thrown.
- [ ] "HelloWorld!"
- [ ] "hello"
- [ ] ????

#### Explanation

An incorrect answer is given – in fact, the code will not compile due to a syntax error.
Let's assume the code would look like this:

```java
class Main {
    public static void main(String[] args) {
        StringBuilder sb = new StringBuilder("hello");
        sb.deleteCharAt(0).insert(0, "H");
        System.out.println(sb);
    }
}
```

```
Output:
Hello
```

#### Q88. How would you use the TaxCalculator to determine the amount of tax on $50?

```java
class TaxCalculator {
    static calculate(total) {
        return total * .05;
    }
}
```

- [ ] TaxCalculator.calculate(50);
- [ ] new TaxCalculator.calculate(50);
- [ ] calculate(50);
- [ ] new TaxCalculator.calculate($50);

#### Explanation

This code won't compile, broken code sample.

#### Q89. Which characteristic does not apply to instance of java.util.HashSet=

- [ ] uses hashcode of objects when inserted
- [ ] contains unordered elements
- [ ] contains unique elements
- [x] contains sorted elements

#### Explanation

The `java.util.HashSet` class implements the `Set` interface, backed by a hash table.

Following are the important points about HashSet −

1. This class makes no guarantees as to the iteration order of the set; in particular, it does not guarantee that the
   order will remain constant over time.
2. This class permits the null element.
3. A HashSet is a collection of items where every item is unique.

#### Q90. What is the output?

```java
import java.util.*;

public class Main {
    public static void main(String[] args) {
        PriorityQueue<Integer> queue = new PriorityQueue<>();
        queue.add(4);
        queue.add(3);
        queue.add(2);
        queue.add(1);
        while (queue.isEmpty() == false) {
            System.out.printf("%d", queue.remove());
        }
    }
}
```

- [ ] 1 3 2 4
- [ ] 4 2 3 1
- [x] 1 2 3 4
- [ ] 4 3 2 1

#### Explanation

A `PriorityQueue` is used when the objects are supposed to be processed based on the priority. It is known that
a `Queue` follows the First-In-First-Out algorithm, but sometimes the elements of the queue are needed to be processed
according to the priority, that’s when the `PriorityQueue` comes into play.

The `PriorityQueue` is based on the priority heap. The elements of the priority queue are ordered according to the
natural ordering, or by a `Comparator` provided at queue construction time, depending on which constructor is used.

![](src/java/java-collection-queque.png)

We do not specify a comparator, i.e. the integer elements are sorted according to their natural order.

```java
public class PriorityQueueExample {
    public static void main(String[] args) {
        Queue<Integer> queue = new PriorityQueue<>();

        // Enqueue random numbers
        for (int i = 0; i < 8; i++) {
            int element = ThreadLocalRandom.current().nextInt(100);
            queue.offer(element);
            System.out.printf("queue.offer(%2d)    -->  queue = %s%n", element, queue);
        }

        // Dequeue all elements
        while (!queue.isEmpty()) {
            Integer element = queue.poll();
            System.out.printf("queue.poll() = %2d  -->  queue = %s%n", element, queue);
        }
    }
}
```

The following is an example output of the program:

```
queue.offer(80)    -->  queue = [80]
queue.offer(14)    -->  queue = [14, 80]
queue.offer(10)    -->  queue = [10, 80, 14]
queue.offer(50)    -->  queue = [10, 50, 14, 80]
queue.offer( 9)    -->  queue = [9, 10, 14, 80, 50]
queue.offer(58)    -->  queue = [9, 10, 14, 80, 50, 58]
queue.offer(41)    -->  queue = [9, 10, 14, 80, 50, 58, 41]
queue.offer( 1)    -->  queue = [1, 9, 14, 10, 50, 58, 41, 80]
queue.poll() =  1  -->  queue = [9, 10, 14, 80, 50, 58, 41]
queue.poll() =  9  -->  queue = [10, 41, 14, 80, 50, 58]
queue.poll() = 10  -->  queue = [14, 41, 58, 80, 50]
queue.poll() = 14  -->  queue = [41, 50, 58, 80]
queue.poll() = 41  -->  queue = [50, 80, 58]
queue.poll() = 50  -->  queue = [58, 80]
queue.poll() = 58  -->  queue = [80]
queue.poll() = 80  -->  queue = []
```

#### Q91. What will this code print, assuming it is inside the main method of a class?

`System.out.println("hello my friends".split(" ")[0]);`

- [ ] my
- [ ] hellomyfriends
- [x] hello
- [ ] friends

#### Explanation

The string `split()` method breaks a given string around matches of the given regular expression. After splitting
against the given regular expression, this method returns a string array.

```
Input String: 016-78967
Regular Expression: -
Output : {"016", "78967"}
```

#### Q92. You have an instance of type Map<String, Integer> named instruments containing the following key-value pairs: guitar=1200, cello=3000, and drum=2000. If you add the new key-value pair cello=4500 to the Map using the put method, how many elements do you have in the Map when you call instruments.size()?

- [ ] 2
- [ ] When calling the put method, Java will throw an exception
- [ ] 4
- [x] 3

#### Explanation

A `Map` contains values on the basis of key, i.e. key and value pair. Each key and value pair is known as an entry.
A `Map` contains unique keys.

A `Map` doesn't allow duplicate keys, but you can have duplicate values. `HashMap` and `LinkedHashMap` allow null keys
and values, but `TreeMap` doesn't allow any null key or value.

```java
import java.util.*;

public class HashMapExample2 {
    public static void main(String[] args) {
        HashMap<Integer, String> map = new HashMap<Integer, String>();//Creating HashMap    
        map.put(1, "Mango");
        map.put(2, "Apple");
        map.put(3, "Banana");
        map.put(1, "Grapes"); //trying duplicate key

        System.out.println("Iterating Hashmap...");
        for (Map.Entry m : map.entrySet()) {
            System.out.println(m.getKey() + " " + m.getValue());
        }
    }
}  
```

```
Output:

Iterating Hashmap...
1 Grapes
2 Apple
3 Banana
```

#### Q93. Which class acts as root class for Java Exception hierarchy?

- [ ] Clonable
- [x] Throwable
- [ ] Object
- [ ] Serializable

#### Explanation

The `Throwable` class is the superclass of every error and exception in the Java language. Only objects that are one of
the subclasses this class are thrown by any “Java Virtual Machine” or may be thrown by the Java `throw` statement.

For the motives of checking of exceptions during compile-time, `Throwable` and any subclass of Throwable which is not
also a subclass of either Error or RuntimeException are considered as checked exceptions.

Throwable class is the root class of Java Exception Hierarchy and is inherited by two subclasses:

1. Exception
2. Error

![](src/java/java-exceptions-classes.png)

#### Q94. Which class does not implement the java.util.Collection interface?

- [ ] java.util.Vector
- [ ] java.util.ArrayList
- [ ] java.util.HashSet
- [x] java.util.HashMap

#### Explanation

The `Collection` interface is the root interface of the Java collections' framework.

There is no direct implementation of this interface. However, it is implemented through its subinterfaces like `List`
, `Set`, and `Queue`.

For example, the `ArrayList` class implements the `List` interface which is a subinterface of the `Collection`
Interface.

![](src/java/java-collection-interface.jpg)

**Note**: `HashMap` class implements `Map` interface.

#### Q95. You have a variable of named `employees` of type `List<Employee>` containing multiple entries. The `Employee` type has a method `getName()` that returns te employee name. Which statement properly extracts a list of employee names?

- [ ] `employees.collect(employee -> employee.getName());`
- [ ] `employees.filter(Employee::getName).collect(Collectors.toUnmodifiableList());`
- [x] `employees.stream().map(Employee::getName).collect(Collectors.toList());`
- [ ] `employees.stream().collect((e) -> e.getName());`

#### Explanation

Stream `map(Function mapper)` returns a stream consisting of the results of applying the given function to the elements
of
this stream.

Stream `map(Function mapper)` is an intermediate operation. These operations are always lazy. Intermediate operations
are
invoked on a Stream instance, and after they finish their processing, they give a Stream instance as output.

Example:

```java
import java.util.*;
import java.util.stream.Collectors;

class GFG {

    // Driver code
    public static void main(String[] args) {

        System.out.println("The stream after applying "
                + "the function is : ");

        // Creating a list of Integers
        List<String> list = Arrays.asList("geeks", "gfg", "g", "e", "e", "k", "s");

        // Using Stream map(Function mapper) to
        // convert the Strings in stream to
        // UpperCase form
        List<String> answer = list.stream().map(String::toUpperCase).
                collect(Collectors.toList());

        // displaying the new stream of UpperCase Strings
        System.out.println(answer);
    }
}
```

#### Q96. This code does not compile. What needs to be changed so that it does?

```java
public enum Direction {
    EAST("E"),
    WEST("W"),
    NORTH("N"),
    SOUTH("S");
    private final String shortCode;

    public String getShortCode() {
        return shortCode;
    }
}
```

- [x] Add a constructor that accepts a `String` parameter and assigns it to the field `shortCode`.
- [ ] Remove the `final` keyword for the field `shortCode`.
- [ ] All enums need to be defined on a single line of code.
- [ ] Add a setter method for the field `shortCode`.

#### Explanation

Java program to create an enum with strings. The given enum contains deployment environments and their respective URLs.
URLs are passed to **the enum constructor** for each enum constant.

```java
public enum Environment {
    PROD("https://prod.domain.com:1088/"),
    SIT("https://sit.domain.com:2019/"),
    CIT("https://cit.domain.com:8080/"),
    DEV("https://dev.domain.com:21323/");

    private String url;

    Environment(String envUrl) {
        this.url = envUrl;
    }

    public String getUrl() {
        return url;
    }
}
```

#### Q97. Which language feature ensures that objects implementing the `AutoCloseable` interface are closed when it completes?

- [ ] try-catch-finally
- [ ] try-finally-close
- [x] try-with-resources
- [ ] try-catch-close

#### Explanation

A `Closeable` is a source or destination of the data that needs to be closed.

The `close()` method is invoked when we need to release resources that are being held by objects such as open files. It
is one of the important interfaces to stream classes.

The `Closeable` interface extends `AutoCloseable` interface therefore any class that implements `Closeable` also
implements `AutoCloseable`.

![](src/java/java-hierarchy-of-closeable-interface.png)

`AutoCloseable` was specially introduced to work with try-with-resources statements.

Since `Closeable` implements `AutoCloseable`, therefore any class that implements `Closeable` also
implements `AutoCloseable` interface and can use the
try-with resources to close the files.

```java
try(FileInputStream fin=new FileInputStream(input)){
// Some code here
        }
```

#### Q98. What code should go in line 3?

```java
class Main {
    public static void main(String[] args) {
        array[0] = new int[]{1, 2, 3};
        array[1] = new int[]{4, 5, 6};
        array[2] = new int[]{7, 8, 9};
        for (int i = 0; i < 3; i++)
            System.out.print(array[i][1]); //prints 258
    }
}
```

- [ ] `int[][] array = new int[][];`
- [x] `int[][] array = new int[3][3];`
- [ ] `int[][] array = new int[2][2];`
- [ ] `int[][] array = [][];`

#### Explanation

`Multidimensional` Arrays can be defined in simple words as array of arrays.

Data in multidimensional arrays are stored in tabular form (in row major order).

Examples:

```
Two dimensional array:
int[][] twoD_arr = new int[10][20];

Three dimensional array:
int[][][] threeD_arr = new int[10][20][30];
```

#### Q99. Is this an example of method overloading or overriding?

```java
class Car {
    public void accelerate() {
    }
}

class Lambo extends Car {
    public void accelerate(int speedLimit) {
    }

    public void accelerate() {
    }
}
```

- [ ] neither
- [x] both
- [ ] overloading
- [ ] overriding

#### Explanation

When two or more methods in the same class have the same name but different parameters, it’s called `Overloading`.

When the method signature (name and parameters) are the same in the superclass and the child class, it’s
called `Overriding`.

##### Overriding vs Overloading

1. `Overriding` implements Runtime Polymorphism whereas `Overloading` implements Compile time polymorphism.
2. The method `Overriding` occurs between superclass and subclass.
   `Overloading` occurs between the methods in the same class.
3. `Overriding` methods have the same signature i.e. same name and method arguments.
   `Overloaded` method names are the same but the parameters are different.

#### Q100. Which choice is the best data type for working with money in Java?

- [ ] float
- [ ] String
- [ ] double
- [x] BigDecimal

#### Explanation

BigDecimal represents a signed decimal number of arbitrary precision with an associated scale. BigDecimal provides full
control over the precision and rounding of the number value. Virtually, it's possible to calculate the value of pi to 2
billion decimal places using BigDecimal, with available physical memory being the only limit.

That’s the reason why we should always prefer BigDecimal or BigInteger for financial calculations.

#### Q101. Which statement about constructors is not ture?

- [ ] A class can have multiple constructors with a different parameter list.
- [ ] You can call another constructor with `this` or `super`.
- [ ] A constructor does not define a return value.
- [x] Every class must explicitly define a constructor without parameters.

#### Explanation

In Java, a constructor is a block of codes similar to the method. It is called when an instance of the class is created.
At the time of calling constructor, memory for the object is allocated in the memory.

Constructor is a special type of method which is used to initialize the object.

There are three rules defined for the constructor.

1. Constructor name must be the same as its class name
2. A Constructor must have no explicit return type
3. A Java constructor cannot be abstract, static, final, and synchronized

Example:

```java
public class Foo {
    private int x;

    public Foo() {
        this(1);
    }

    public Foo(int x) {
        this.x = x;
    }
}
```

Every time an object is created using the new() keyword, at least one constructor is called.

It calls a default constructor if there is no constructor available in the class. In such case, Java compiler provides a
default constructor by default.

So shouldn't explicitly define a constructor without parameters.

#### Q102. What language feature allows types to be parameters on classes, interfaces, and methods in order to reuse the same code for different data types?

- [ ] Regular Expressions
- [ ] Reflection
- [x] Generics
- [ ] Concurrency

#### Explanation

Java Generic methods and generic classes enable programmers to specify, with a single method declaration, a set of
related methods, or with a single class declaration, a set of related types, respectively.

Generics also provide compile-time type safety that allows programmers to catch invalid types at compile time.

Using Java Generic concept, we might write a generic method for sorting an array of objects, then invoke the generic
method with Integer arrays, Double arrays, String arrays and so on, to sort the array elements.

Following example illustrates how we can print an array of different type using a single Generic method:

```java
public class GenericMethodTest {
    // generic method printArray
    public static <E> void printArray(E[] inputArray) {
        for (E element : inputArray) {
            System.out.printf("%s ", element);
        }
        System.out.println();
    }

    public static void main(String[] args) {

        Integer[] intArray = {1, 2, 3, 4, 5};
        Double[] doubleArray = {1.1, 2.2, 3.3, 4.4};
        Character[] charArray = {'H', 'E', 'L', 'L', 'O'};

        System.out.println("Array integerArray contains:");
        printArray(intArray);   // pass an Integer array

        System.out.println("\nArray doubleArray contains:");
        printArray(doubleArray);   // pass a Double array

        System.out.println("\nArray characterArray contains:");
        printArray(charArray);   // pass a Character array
    }
}
```

#### Q103. What will be printed?

```java
public class Berries {

    String berry = "blue";

    public static void main(String[] args) {
        new Berries().juicy("straw");
    }

    void juicy(String berry) {
        this.berry = "rasp";
        System.out.println(berry + "berry");
    }
}
```

- [ ] raspberry
- [x] strawberry
- [ ] blueberry
- [ ] rasp

#### Explanation

Every variable used in a programming language holds a scope. The scope tells the compiler about the segment within a
program where the variable is accessible or used.

Member variables are members of a class and hence declared inside a class but not inside any method or function.

Thus, we can address such variable scope as class scope or class-level scope. Programmers declare such variables within
the
class’s curly braces along with an access modifier. Programmers can use such variables anywhere within the Java
class but not outside it.

#### Q104. What is the value of `forestCount` after this code executes?

```
public class MyClass {
  Map<String, Integer> forestSpecies = new HashMap<>();
        forestSpecies.put("Amazon", 30000);
        forestSpecies.put("Congo", 10000);
        forestSpecies.put("Daintree", 15000);
        forestSpecies.put("Amazon", 40000);
  int forestCount = forestSpecies.size();
}
```

- [x] 3
- [ ] 4
- [ ] 2
- [ ] When calling the put method, Java will throw an exception

#### Explanation

A `Map` contains values on the basis of key, i.e. key and value pair. Each key and value pair is known as an entry.
A `Map` contains unique keys.

A `Map` doesn't allow duplicate keys, but you can have duplicate values. `HashMap` and `LinkedHashMap` allow null keys
and values, but `TreeMap` doesn't allow any null key or value.

```java
import java.util.*;

public class HashMapExample2 {
    public static void main(String[] args) {
        HashMap<Integer, String> map = new HashMap<Integer, String>();//Creating HashMap    
        map.put(1, "Mango");
        map.put(2, "Apple");
        map.put(3, "Banana");
        map.put(1, "Grapes"); //trying duplicate key

        System.out.println("Iterating Hashmap...");
        for (Map.Entry m : map.entrySet()) {
            System.out.println(m.getKey() + " " + m.getValue());
        }
    }
}  
```

```
Output:

Iterating Hashmap...
1 Grapes
2 Apple
3 Banana
```

#### Q105. What is a problem with this code?

```java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.List;

class Main {
    public static void main(String[] args) {
        List<String> list = new ArrayList<String>(Arrays.asList("a", "b", "c"));
        for (String value : list) {
            if (value.equals("a")) {
                list.remove(value);
            }
        }
        System.out.println(list); // outputs [b,c]
    }
}
```

- [ ] String should be compared using == method instead of equals.
- [x] Modifying a collection while iterating through it can throw a ConcurrentModificationException.
- [ ] The List interface does not allow an argument of type String to be passed to the remove method.
- [ ] ArrayList does not implement the List interface.

#### Explanation

The `ConcurrentModificationException` is a very common exception in Java that occurs usually while working with
Collections.

The `ConcurrentModificationException` is used to fail-fast when something being iterated on is modified.

This exception occurs when an object is attempted to be modified concurrently without permission. For example, if a
Collection is modified while a thread is traversing it using an Iterator, a ConcurrentModificationException is thrown
from the `Iterator.next()` method.

Here is an example of a `ConcurrentModificationException` thrown when attempting to remove an element from an ArrayList
using the `remove()` method while traversing it using an enhanced for loop:

```java
import java.util.ArrayList;
import java.util.List;

public class ConcurrentModificationExceptionExample {
    public static void main(String[] args) {
        List<String> list = new ArrayList<>();
        list.add("a");
        list.add("b");
        list.add("c");
        list.add("d");

        for (String elem : list) {
            if (elem.equals("a")) {
                list.remove(elem);
            }
        }
    }
}
```

Since the enhanced for loop uses an `Iterator` internally to traverse elements in a Collection, running the above code
causes a `ConcurrentModificationException` since the `remove()` method of the Collection is used instead of the
iterator:

```
Exception in thread "main" java.util.ConcurrentModificationException
at java.base/java.util.ArrayList$Itr.checkForComodification(ArrayList.java:1013)
at java.base/java.util.ArrayList$Itr.next(ArrayList.java:967)
at ConcurrentModificationExceptionExample.main(ConcurrentModificationExceptionExample.java:12)
```
