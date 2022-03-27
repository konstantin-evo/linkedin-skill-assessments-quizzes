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

```java
1:

class Main {
2:

    public static void main(String[] args) {
        3:int[] array = {1, 2, 3, 4};
        4:for (int i = 0; i < array.size(); i++) {
            5:System.out.print(array[i]);
            6:}
        7:}
8:
}
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

```java
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

```java
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

