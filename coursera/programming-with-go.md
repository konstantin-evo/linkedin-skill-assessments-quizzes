## Getting Started with Go

[Link to course](https://www.coursera.org/learn/golang-getting-started)

<a name="link-top"></a>

---

### Table of Contents

<ol>
  <li>
    <a href="#module-1">Getting Started with Go</a>
      <ul>
        <li>
          <a href="#getting-started-with-go">Getting Started with Go</a>
        </li>
      </ul>
      <ul>
        <li>
          <a href="#basic-data-types">Basic Data types</a>
        </li>
      </ul>
      <ul>
        <li>
          <a href="#composite-data-types">Composite Data types</a>
        </li>
      </ul>
  </li>
  <li>
    <a href="#module-2">Functions, Methods, and Interfaces in Go</a>
      <ul>
        <li>
          <a href="#function-and-organization">Function and organization</a>
        </li>
      </ul>
      <ul>
        <li>
          <a href="#function-types">Function types</a>
        </li>
      </ul>
      <ul>
        <li>
          <a href="#object-orientation-in-go">Object orientation in Go</a>
        </li>
      </ul>
  </li>
</ol>

---

#### Module 1

#### Getting Started with Go

#### Q1. What does a compiler do?

1. [x] Generates executable machine code from source code in a high-level language
2. [ ] Automatically formats source code in a readable way
3. [ ] Combines multiple files into a single program
4. [ ] Tests the basic functionality of the code

#### Explanation

A compiler is a software tool that translates source code written in a high-level programming language into executable
machine code or a lower-level representation that can be directly executed by a computer. It performs various tasks such
as lexical analysis, syntax analysis, semantic analysis, optimization, and code generation. The resulting output is
typically a standalone executable program or a library that can be run on the target platform.

#### Q2. What is the scope of a variable?

1. [ ] The variable declaration
2. [ ] The instructions where the variable is assigned a value
3. [x] Region of a program where the variable can be accessed
4. [ ] The set of values to which a variable can be assigned

#### Explanation

In Go (Golang), the scope of a variable refers to the region of a program where the variable can be accessed.

The scope of a variable in Go is determined by its declaration. It defines the parts of the program where the variable
is visible and can be referred to by its name. The scope can be limited to a specific block of code, a function, or
extend to the entire package, depending on how and where the variable is declared.

Here's an example to illustrate the scope of a variable in Go:

```go
package main

import "fmt"

func main() {
	// Variable with function-level scope
	var message string = "Hello"
	fmt.Println(message) // Output: Hello

	if true {
		// Variable with block-level scope
		var insideBlock string = "Inside Block"
		fmt.Println(insideBlock) // Output: Inside Block
	}

	// The variable insideBlock is not accessible outside the if block
	// fmt.Println(insideBlock) // Uncommenting this line will result in a compile-time error

	// Variable shadowing
	var message string = "Goodbye"
	fmt.Println(message) // Output: Goodbye
}
```

#### Q3. What is Garbage Collection?

1. [ ] Reorganization of source code to reduce the number of function calls
2. [x] Deallocation of objects which are no longer in use
3. [ ] Reorganization of source code to improve encapsulation and understandability
4. [ ] Deletion of unused segments of code

#### Explanation

Garbage Collection in Go refers to the automatic memory management process that deallocates and reclaims memory occupied
by objects that are no longer in use or reachable by the program. It is responsible for identifying and freeing memory
that is no longer needed, allowing the program to efficiently manage its memory resources.

Go's garbage collector works in the background and automatically handles memory management, relieving the developer from
manually allocating and deallocating memory. It tracks objects in memory, identifies those that are no longer reachable
through the program's execution flow, and then frees up the associated memory space for reuse.

#### Q4. What does an interpreter do?

1. [x] Converts instructions in a high-level language into machine code at runtime
2. [ ] Processes user inputs
3. [ ] Reads files in a given data format
4. [ ] Produces output data corresponding to each input region

#### Explanation

An interpreter is a program or software component that executes code written in a high-level programming language
directly without the need for prior compilation. Its primary function is to convert the instructions in a high-level
language into machine code or lower-level code and execute them on the fly.

**Note**: Go is a compiled programming language rather than an interpreted one. When you write Go code, it needs to be
compiled into machine code before it can be executed. This compilation step is performed using the Go compiler, commonly
known as "`go build`" or "`go run`" commands.

The advantage of compilation in Go is that it enables the production of highly efficient and performant code. The
compiled binary can take advantage of low-level optimizations and hardware-specific features. Additionally, the
compilation step helps catch errors and perform type checking before the program is executed, leading to improved
reliability and runtime efficiency.

#### Q5. True or False: Concurrency always results in some performance improvement.

1. [ ] True
2. [x] False

#### Explanation

False.

Concurrency in Go does not always guarantee performance improvement. While Go's concurrency features, such as goroutines
and channels, can help optimize performance in certain scenarios, the effectiveness of concurrency depends on the nature
of the task and how it can be parallelized.

Concurrency can improve performance in situations where tasks can be executed concurrently without dependencies and can
be parallelized effectively. In such cases, Go's lightweight goroutines and efficient scheduling can lead to improved
performance by utilizing multiple cores or processors.

However, there are cases where introducing concurrency can introduce additional overhead and complexity, resulting in
degraded performance. For example, if a task involves frequent synchronization or sharing of mutable data between
goroutines, the overhead of synchronization can outweigh the benefits of concurrency.

#### Q6. The type of variable determines which of the following aspects of that variable? (Select ALL that are correct.)

1. [x] Size in memory
2. [x] Operations that can be performed on the variable
3. [x] The data that can be contained in the object
4. [ ] The number of characters in the variable's name

#### Explanation

The type of variable in Go determines the size in memory it occupies, the operations that can be performed on it, and
the kind of data that can be stored in it.

The type defines the behavior and characteristics of a variable, including how it is stored, how it can be manipulated,
and the range of values it can hold. However, the type of variable does not determine the number of characters in its
name. The variable name is independent of its type and is used for identification and reference purposes.

Here's an example to illustrate how the type of variable determines the aspects mentioned:

```go
package main

import (
	"fmt"
)

func main() {
	var x int     // Variable x with type int
	var y float64 // Variable y with type float64
	var z string  // Variable z with type string

	fmt.Println("Size of x:", unsafe.Sizeof(x))
	fmt.Println("Size of y:", unsafe.Sizeof(y))
	fmt.Println("Size of z:", unsafe.Sizeof(z))

	x = 10
	y = 3.14
	z = "Hello, Go!"

	fmt.Println("x:", x)
	fmt.Println("y:", y)
	fmt.Println("z:", z)
}
```

In this example, we declare three variables with different types: x of type int, y of type float64, and z of type
string. The type of each variable determines the size in memory it occupies, the operations that can be performed on it,
and the data that can be stored in it.

The `Sizeof` function from the unsafe package is used to determine the size of each variable in memory. The output will
show the size of x, y, and z respectively.

Later in the code, we assign values to these variables and print their values. The type of each variable determines the
range of values it can hold and the operations that can be performed on it. For example, x can hold integer values, y
can hold floating-point numbers, and z can hold string values.

The example demonstrates how the type of variable influences its size, allowed operations, and the data it can contain
in Go.

#### Q7. What is the name of the package from which an executable program is generated?

1. [ ] fmt
2. [ ] os
3. [ ] init
4. [x] main

#### Explanation

The correct answer is "main".

In Go, an executable program is generated from the package named "main". The "main" package serves as the entry point of
the executable program. It must include a special function called "main", which is the starting point of the program
execution. When the program is run, the code inside the "main" function is executed.

Here's an example of a Go program with the main package:

```go
package main

import "fmt"

func main() {
	fmt.Println("Hello, Go!")
}
```

#### Q8. Which of the following is an example of a short variable declaration?

1. [x] x := 2.3
2. [ ] var x int =10
3. [ ] var x int
4. [ ] x=2.3

#### Explanation

The example `x := 2.3` represents a short variable declaration in Go. Short variable declaration allows you to declare
and initialize a variable using the `:=` syntax without explicitly specifying the variable's type. The type of the
variable is inferred from the value assigned to it.

In this case, `x` is being declared and initialized with the value `2.3`. The Go compiler will infer the type of `x`
as `float64` based on the value assigned to it.

<p align="right">(<a href="#table-of-contents">back to top</a>)</p>

---

#### Basic Data types

#### Q1. Which of the following expressions does NOT compute the average of two integers a and b?

1. [x] avg := 2 % (a + b)
2. [ ] avg := float64(a + b) / 2
3. [ ] avg := float64(a + b) / 2.0
4. [ ] avg := float64(float64(a + b) / 2.0)

#### Explanation

The expression `2 % (a + b)` computes the remainder when 2 is divided by the sum of a and b. It does not yield the
average of the two numbers.

#### Q2. What is printed when the following program is executed?

```go
func main() {
i, _ := strconv.Atoi("10")
y := i * 2
fmt.Println(y)
}
```

1. [ ] 1010
2. [ ] 10
3. [ ] 102
4. [x] 20

#### Explanation

1. The `strconv.Atoi()` function is used to convert the string "10" to an integer value and assign it to the
   variable `i`.
2. Since the conversion is successful, `i` will have the value 10.
3. The variable `y` is then assigned the result of multiplying `i` by 2, resulting in 20.
4. Finally, the `fmt.Println()` function is used to print the value of `y`, which is 20.

#### Q3. What is printed when the following program is executed?

```go
func main() {
s := strings.Replace("ianianian", "ni", "in", 2)
fmt.Println(s)
}
```

1. [ ] `ianianian`
2. [x] `iainainan`
3. [ ] `iainanian`
4. [ ] `nianiania`

#### Explanation

When the given program is executed, it will print the modified string after replacing the first two occurrences of "ni"
with "in" in the original string "`ianianian`".

Here's the output of the program:

```
iainainan
```

Explanation:

The `strings.Replace()` function is used to replace substrings within a string. In this case, the original string
is "`ianianian`".

1. The first argument to `strings.Replace()` is the original string.
2. The second argument is the substring to be replaced, which is "`ni`".
3. The third argument is the replacement substring, which is "`in`".
4. The fourth argument is the maximum number of replacements to be made. In this case, it is set to 2, so only the first
   two occurrences of "ni" will be replaced.
5. The modified string "`iainianian`" is then assigned to the variable `s`.
6. Finally, the `fmt.Println()` function is used to print the value of `s`, which is "iainianian" after replacing "ni"
   with "in" twice.

#### Q4. What is printed by this code?

```go
func main() {
  x := 7
  switch  {
    case  x>3:
      fmt.Printf("1")
    case  x>5:
      fmt.Printf("2")
    case  x==7:
      fmt.Printf("3")
    default: 
      fmt.Printf("4")
  }
}
```

#### Explanation

The code will print "1" because the value of `x` is 7, which satisfies the condition `x > 3`.

When a `switch` statement is used without an expression, it evaluates the truthiness of each case statement's condition
in order and executes the first one that evaluates to `true`.

#### Q5. What is printed by this code?

```go
func main() {
  var  xtemp int
  x1  :=  0
  x2 :=  1
  for  i :=0;  i<5;  i++ {
    xtemp  =  x2
    x2  =  x2 + x1
    x1 =  xtemp
  }
  fmt.Println(x2)
}
```

1. [ ] 5
2. [ ] 13
3. [x] 8
4. [ ] 4

#### Explanation

The code snippet provided will print `8`.

The code initializes three variables: `xtemp`, `x1`, and `x2`. Then, there is a for loop that iterates five times. In
each iteration, the value of `x2` is updated by adding `x1` to it, and the value of `x1` is updated to the previous
value of `x2`. Essentially, this code implements the Fibonacci sequence generation.

After the loop, the value of `x2` will be `8`, and that is what will be printed using `fmt.Println(x2)`.

| x | x1 | x2 | xtemp |
|---|----|----|-------|
| 0 | 1  | 1  | 1     |
| 1 | 1  | 2  | 1     |
| 2 | 2  | 3  | 2     |
| 3 | 3  | 5  | 3     |
| 4 | 5  | 8  | 5     |

#### Q6. True or False: This code compiles correctly.

```go
func main() {
  var  x int
  var  y *int
  z  :=  3
  y  = &z
  x  =  &y
}
```

#### Explanation

The code provided will not compile correctly.

The line `x = &y` will cause a compilation error because it is attempting to assign a pointer (`&y`) to a non-pointer
variable (`x`). This is a type mismatch, and Go does not allow such assignments between different types.

To fix the error, you can either change the type of `x` to be a pointer or assign the value of `y` (dereferencing the
pointer) to `x`. Here's an example of the corrected code:

```go
func main() {
  var x *int
  var y *int
  z := 3
  y = &z
  x = y
}
```

In this corrected code, `x` and `y` are both declared as pointers to integers (`*int`). The value of `y` (the address
of `z`) is assigned to `x` without any compilation errors.

#### Q7. Which integer type provides higher accuracy?

1. [ ] int16
2. [ ] int32
3. [ ] int
4. [x] All of these types provide the same accuracy

#### Explanation

In Go, all of these integer types (`int16`, `int32`, and `int`) have the same accuracy in terms of representing whole
numbers. The difference lies in the range of values they can represent.

- `int16` is a 16-bit signed integer type with a range of -32768 to 32767.
- `int32` is a 32-bit signed integer type with a range of -2147483648 to 2147483647.
- `int` is an implementation-defined integer type, which usually corresponds to the word size of the underlying
  architecture. It can be 32 bits or 64 bits.

While the accuracy, i.e., the ability to represent whole numbers, is the same for all these types, the choice of which
one to use depends on the range of values you need to work with. If you require a larger range, you can choose `int32`
or `int`, whereas if you have a narrower range, `int16` may suffice.

<p align="right">(<a href="#table-of-contents">back to top</a>)</p>

---

#### Composite Data types

#### Q1. What is printed when the following program is executed?

```go
func main() {
  x  :=  []int {4,  8,  5}
  y  :=  -1
  for  _,  elt  := range  x {
    if  elt > y {
      y  =  elt
    }
  }
  fmt.Print(y)
}
```

1. [ ] 4
2. [x] 8
3. [ ] 5
4. [ ] -1

#### Explanation

The program initializes `x` as a slice with the values `[4, 8, 5]` and `y` as -1.

The for loop iterates over the elements of `x` using the range syntax. In each iteration, the value of `elt` is set to
the current element being iterated.

Inside the loop, it checks if the current element (`elt`) is greater than the current value of `y`. If it is, `y` is
updated with the value of `elt`.

In this case, the loop will compare each element of `x` with `y` and update `y` if a larger value is found.

Here's the step-by-step execution:

1. `elt = 4`, `y = -1`. Since `4` is greater than `-1`, `y` is updated to `4`.
2. `elt = 8`, `y = 4`. Since `8` is greater than `4`, `y` is updated to `8`.
3. `elt = 5`, `y = 8`. Since `5` is not greater than `8`, `y` remains `8`.

After the loop completes, `y` will contain the maximum value from `x`, which is `8`. Therefore, the output of the
program will be `8`.

#### Q2. What is printed when the following program is executed?

```go
func main() {
  x  :=  [...]int {4,  8,  5}
  y  :=  x[0:2]
  z  :=  x[1:3]
  y[0]  =  1
  z[1]  =  3
  fmt.Print(x)
}
```

1. [ ] [1 3 8]
2. [x] [1 8 3]
3. [ ] [4 1 3]
4. [ ] [4 8 5]

#### Explanation

The program modifies the values of `y[0]` and `z[1]`. `y[0] = 1` assigns the value `1` to the first element
of `y`, which also corresponds to the first element of `x`. Similarly, `z[1] = 3` assigns the value `3` to the second
element of `z`, which corresponds to the third element of `x`.

Since `y` and `z` are slices that share the underlying array `x`, modifying the elements of the slices also modifies the
elements of `x`.

Therefore, the output of the program will be `[1 8 3]`, as the modifications made to the slices affect the corresponding
elements in the original array `x`.

#### Q3. What is printed when the following program is executed?

```go
func main() {
  x  :=  [...]int {1,  2,  3,  4,  5}
  y  :=  x[0:2]
  z  :=  x[1:4]
  fmt.Print(len(y),  cap(y),  len(z), cap(z))
}
```

1. [x] 2 5 3 4
2. [ ] 2 4 3 4
3. [ ] 2 3 3 4
4. [ ] 2 5 3 5

#### Explanation

The `len()` function returns the length of a slice, which is the number of elements in the slice, and the `cap()`
function returns the capacity of a slice, which is the maximum number of elements the slice can hold.

In this case, `len(y)` returns `2` because `y` has two elements (`[1, 2]`), `cap(y)` returns `5` because the underlying
array `x` has a capacity of `5`, `len(z)` returns `3` because `z` has three elements (`[2, 3, 4]`), and `cap(z)`
returns `4` because the underlying array `x` has a capacity of `4` from index 1 to index 4.

Therefore, the output of the program will be `2 5 3 4`, which represents the length and capacity of the `y` and `z`
slices, respectively.

#### Q4. What is printed when the following program is executed?

```go
func main() {
  x  :=  map[string]int {
    "ian": 1,  "harris": 2}
  for  i,  j :=  range  x {
    if  i == "harris" {
      fmt.Print(i,  j)
    }
  }
}
```

1. [ ] harris1
2. [ ] 1ian
3. [ ] 1harris
4. [x] harris2

#### Explanation

The program initializes a map `x` with key-value pairs: `"ian": 1` and `"harris": 2`.

The for loop iterates over the elements of the map `x` using the range syntax. In each iteration, the key is assigned to
the variable `i` and the corresponding value is assigned to the variable `j`.

Inside the loop, it checks if the current key `i` is equal to `"harris"`. If it is, it prints the key `i` and the
value `j`.

In this case, the loop will iterate over the elements of `x` and find that the key `"harris"` matches the condition.
Therefore, the `Print` statement will be executed, and it will print `"harris"` followed by the corresponding value `2`.

Therefore, the output of the program will be `harris2`.

#### Q5. What is printed when the following program is executed?

```go
type P struct  {
    x string
    y int
} 

func  main() {
  b  :=  P{"x",  -1}
  a  :=  [...]P{P{"a",  10},  
        P{"b",  2},
        P{"c",  3}}
  for  _,  z :=  range  a {
    if  z.y > b.y {
      b  =  z
    }
  }
  fmt.Println(b.x)
}
```

1. [ ] a
2. [ ] b
3. [ ] c
4. [ ] x

#### Explanation

The loop will compare the `y` field of each struct in `a` with the `y` field of `b` and update `b` if a larger value is
found.

Here's the step-by-step execution:

1. First iteration: `z = P{"a", 10}`, `b = P{"x", -1}`. Since `10` is greater than `-1`, `b` is updated to `P{"a", 10}`.
2. Second iteration: `z = P{"b", 2}`, `b = P{"a", 10}`. Since `2` is not greater than `10`, `b` remains unchanged.
3. Third iteration: `z = P{"c", 3}`, `b = P{"a", 10}`. Since `3` is not greater than `10`, `b` remains unchanged.

After the loop completes, `b` will contain the struct value that had the largest `y` field, which is `P{"a", 10}`.
Therefore, the output of the program will be `a`.

#### Q6. What is printed when the following program is executed?

```go
func main() {
  s  :=  make([]int,  0,  3)
  s  =  append(s,  100)
  fmt.Println(len(s),  cap(s))
}
```

1. [x] 1 3
2. [ ] 0 3
3. [ ] 1 1
4. [ ] 1 4

#### Explanation

The program starts by creating a slice `s` using the `make()` function with an initial length of `0` and a capacity
of `3`.

Next, it uses the `append()` function to add an element `100` to the slice `s`. The `append()` function appends the
element to the slice and returns the resulting slice. In this case, the `append()` operation modifies `s` to
become `[100]`.

Finally, the program prints the length and capacity of the slice `s` using the `len()` and `cap()` functions.

Since the length of `s` is `1` (it contains one element), and the capacity is `3` (the maximum number of elements the
slice can hold without reallocation), the output of the program will be `1 3`.

<p align="right">(<a href="#table-of-contents">back to top</a>)</p>

---

#### Module 2

#### Functions, Methods, and Interfaces in Go

---

#### Function and organization

#### Q1. Using functions in code  has which of the following impacts?

1. [ ] Improve code understandability
2. [ ] Facilitate code reuse
3. [ ] Support abstraction
4. [x] All of the above

#### Explanation

Using functions in code has multiple impacts, including improving code understandability, facilitating code reuse, and
supporting abstraction.

1. **Improve code understandability**: Functions allow you to break down complex tasks into smaller, more manageable
   units. By encapsulating a specific set of instructions within a function, you can make the code more readable and
   easier to comprehend. Functions also provide a natural way to document and communicate the purpose and behavior of a
   particular piece of code.
2. **Facilitate code reuse**: Functions can be written once and reused multiple times throughout the codebase. Instead
   of duplicating the same set of instructions at multiple places, you can define a function and call it wherever
   needed. This promotes code reuse, reduces redundancy, and helps maintain a modular and efficient codebase.
3. **Support abstraction**: Functions abstract away the implementation details and provide a higher-level interface for
   performing specific tasks. By defining functions with well-chosen names and clear parameters, you can hide the
   underlying complexity and make the code more understandable and manageable. Abstraction enables you to focus on the "
   what" rather than the "how" of a particular functionality.

#### Q2. Which of these statements is true?

1. [ ] A function can have only one return value.
2. [ ] A function cannot have more than two parameters.
3. [x] A function can have parameters of different types.
4. [ ] The type of the arguments do not need to be specified.

#### Explanation

In Go, a function can have parameters of different types. This allows you to pass in values of different data types to
the function when calling it.

Here's an example in Go:

```go
package main

import "fmt"

func greet(name string, age int) {
	fmt.Printf("Hello, %s! You are %d years old.\n", name, age)
}

func main() {
	greet("Alice", 25)
}
```

In this example, the `greet` function takes two parameters: `name`, which is of type `string`, and `age`, which is of
type `int`.

#### Q3. Let’s say that you are writing a function which takes a structure as an argument. What is a good reason to rewrite the function to take a pointer to the structure as an argument, instead of the structure itself?

1. [x] The function needs to modify the structure.
2. [ ] The function needs to read data inside the structure.
3. [ ] The function needs to copy the structure.
4. [ ] The structure uses very little space in memory.

#### Explanation

If a function needs to modify the structure, it is generally more efficient and practical to pass a pointer to the
structure as an argument, rather than the structure itself. When a pointer is passed, the function can directly access
and modify the original structure in memory, without the need to make a copy.

When a structure is passed by value (i.e., the structure itself is passed), a copy of the structure is made and passed
to the function. If the function modifies the structure, it will only affect the copy and not the original structure.

Here's an example in Go to illustrate passing a pointer to a structure:

```go
package main

import "fmt"

type Person struct {
	Name string
	Age  int
}

func modifyPerson(p *Person) {
	p.Age = 30
}

func main() {
	person := Person{Name: "Alice", Age: 25}

	fmt.Println("Before modification:", person)

	modifyPerson(&person)

	fmt.Println("After modification:", person)
}
```

In this example, the `modifyPerson` function takes a pointer to a `Person` structure as an argument. Inside the
function, the `Age` field of the structure is modified. When calling the function in the `main` function, we pass the
address of the `person` variable using the `&` operator (`&person`), which gives us a pointer to the structure.

As a result, the original `person` structure is modified, and we can see the changes reflected in the output.

#### Q4. Which of the features of functions listed below improve code understandability?

#### I. Low number of arguments

#### II Performs several distinct tasks

#### III. Low control-flow complexity

1. [x] I and II
2. [ ] I and III
3. [ ] II and III
4. [ ] I, II, and III

#### Explanation

The features of functions that improve code understandability are:

**I. Low number of arguments**: Functions with a low number of arguments are generally easier to understand and reason
about. Having a large number of arguments can make it more challenging to comprehend the function's purpose and
behavior. It is recommended to keep the number of arguments to a minimum, ideally no more than a handful, to enhance
code understandability.

**III. Low control-flow complexity**: Functions with a low control-flow complexity are easier to understand.
Control-flow complexity refers to the number of branches, loops, and conditional statements within a function. Functions
with a simpler control-flow structure tend to be more readable and less prone to errors. Breaking down complex functions
into smaller, more focused functions can help reduce control-flow complexity and improve code understandability.

#### Q5. What is a difference between passing a slice as an argument and passing an array as an argument?

1. [ ] Passing a slice passes a copy of all the data in the slice.
2. [ ] Passing an array is faster than passing a slice.
3. [ ] There is no difference.
4. [x] Passing an array passes a copy of the entire array.

#### Explanation

When you pass an array as an argument to a function, you are passing a copy of the entire array. This means that
modifications made to the elements of the array within the function will not affect the original array outside the
function.

**Note**: if the array is very large, passing a copy of the entire array can be less efficient in terms of
memory and performance compared to passing a slice.

When you pass a slice as an argument to a function, you are passing a reference to the underlying array that the slice
points to. This means that any modifications made to the elements of the slice within the function will be visible
outside the function as well.

Here's an example to illustrate the behavior of passing a slice and an array as arguments:

```go
package main

import "fmt"

func modifySlice(slice []int) {
	slice[0] = 10
}

func modifyArray(arr [3]int) {
	arr[0] = 20
}

func main() {
	slice := []int{1, 2, 3}
	array := [3]int{1, 2, 3}

	fmt.Println("Before modification:")
	fmt.Println("Slice:", slice)
	fmt.Println("Array:", array)

	modifySlice(slice)
	modifyArray(array)

	fmt.Println("After modification:")
	fmt.Println("Slice:", slice)
	fmt.Println("Array:", array)
}
```

In this example, the `modifySlice` function takes a slice as an argument and modifies the first element to 10.
The `modifyArray` function takes an array as an argument and modifies the first element to 20.

After calling both functions, you can observe that the modification to the slice is reflected outside the function,
while the modification to the array has no effect on the original array. This showcases the difference between passing a
slice (passing a reference to the underlying array) and passing an array (passing a copy of the entire array).

<p align="right">(<a href="#table-of-contents">back to top</a>)</p>

---

#### Function types

#### Q1. Is the highlighted assignment to f in the following code a legal variable assignment?

```go
package main

var f func(string) int

func test(x string) int {
	return len(x)
}

func main() {
	f = test
}
```

1. [x] Yes
2. [ ] No

#### Explanation

Yes, the highlighted assignment to `f` in the given code is a legal variable assignment.

The variable `f` is declared as a function type `func(string) int`, which means it can store a reference to a function
that takes a string as input and returns an integer. The function `test` matches this signature, as it takes a string
parameter `x` and returns an integer using the `len` function.

#### Q2. Which of the following statements correctly declares a function whose argument is another function which takes an integer as an argument and returns a string?

1. [ ] func fA(fB (int) string)
2. [x] func fA(fB func (int) string)
3. [ ] func fA(fB func (int)) string
4. [ ] func fA(fB func (string) int)

#### Explanation

The correct statement that declares a function whose argument is another function which takes an integer as an argument
and returns a string is:

```go
func fA(fB func (int) string)
```

This statement declares a function named `fA` with an argument `fB`, which is of type `func(int) string`. It specifies
that `fB` should be a function that takes an integer as an argument and returns a string. This is the correct syntax for
declaring a function that accepts another function as an argument with the specified signature.

#### Q3. What is an anonymous function?

1. [ ] A function with no return value
2. [ ] A function with multiple names
3. [x] A function with no name
4. [ ] A function with no arguments

#### Explanation

In Go, an anonymous function is a function that is defined without a name. It is created inline within an expression or
assigned to a variable directly. Anonymous functions are often used as closures or for immediate execution without the
need for a separate function declaration.

Here's an example of an anonymous function in Go:

```go
package main

import "fmt"

func main() {
	// Assigning an anonymous function to a variable
	add := func(a, b int) int {
		return a + b
	}

	result := add(3, 4)
	fmt.Println(result) // Output: 7

	// Using an anonymous function directly
	func(x int) {
		fmt.Println("Anonymous function with argument:", x)
	}(5) // Output: Anonymous function with argument: 5
}
```

In this example, the first anonymous function is assigned to the `add` variable and can be invoked later with arguments.
The second anonymous function is executed immediately with the argument `5`.

#### Q4. Which of the following statements correctly declares a function whose return value is another function which takes a string as an argument and returns an integer?

1. [ ] func fA(fB (int) string) func (string) int
2. [ ] func fA(fB func (int) string) {}
3. [ ] func fA(int) string {}
4. [x] func fA() fB func (string) int{}

#### Explanation

The correct statement that declares a function whose return value is another function which takes a string as an
argument and returns an integer is:

```go
func fA() fB func (string) int{}
```

This statement declares a function named `fA` with an empty parameter list `()`, and its return type
is `fB func(string) int`. This means `fA` returns a function `fB` that takes a string as an argument and returns an
integer.

#### Q5. What does the above code print on the screen?

```go
package main

import "fmt"

func fA() func() int {
	i := 0
	return func() int {
		i++
		return i
	}
}

func main() {
	fB := fA()
	fmt.Print(fB())
	fmt.Print(fB())
}
```

1. [x] 12
2. [ ] 11
3. [ ] 01
4. [ ] 1

#### Explanation

The above code will print "`01`".

The `fA` function returns an anonymous function that takes no arguments and returns an integer. Inside `fA`, there is a
variable `i` initialized to 0. The returned anonymous function increments `i` by 1 and returns its value.

In the `main` function, `fB` is assigned the result of calling `fA()`, which means `fB` now refers to the anonymous
function returned by `fA`.

The first `fmt.Print(fB())` statement calls the anonymous function, which increments `i` to 1 and returns it. It prints
the value of `i`, which is `1`.

The second `fmt.Print(fB())` statement again calls the anonymous function, and now `i` is incremented to 2 and returned.
It prints the updated value of `i`, which is `2`.

#### Q6. What symbols are used in a function declaration to indicate that it is a variadic function?

1. [ ] “->”
2. [x] ”...”
3. [ ] "---"
4. [ ] "[]"

#### Explanation

The ellipsis `...` is used in the function declaration to indicate that the function accepts a variable number of
arguments of the same type. It allows the function to accept zero or more arguments of the specified type.

For example:

```go
func sum(nums ...int) int {
total := 0
for _, num := range nums {
total += num
}
return total
}
```

In this example, the function `sum` is declared with `nums ...int`, where `nums` is a variadic parameter of type `int`.
It can accept any number of integers as arguments, including none.

#### Q7. What does this routine produce?

```go
package main

import "fmt"

func main() {
	i := 1
	fmt.Print(i)
	i++
	defer fmt.Print(i + 1)
	fmt.Print(i)

}
```

1. [ ] 132
2. [ ] 134
3. [ ] 234
4. [x] 123

#### Explanation

The routine produces the output "123".

Here's the breakdown of the code:

1. `i := 1`: Declare and initialize the variable `i` with a value of 1.
2. `fmt.Print(i)`: Print the value of `i`, which is 1. Output: "1".
3. `i++`: Increment the value of `i` by 1. Now `i` is 2.
4. `defer fmt.Print(i + 1)`: Defer the execution of `fmt.Print(i + 1)` until the surrounding function (`main`) returns.
   The current value of `i` is 2, so the deferred print statement will use `i + 1`, which is 3.
5. `fmt.Print(i)`: Print the value of `i`, which is still 2. Output: "2".
6. The function `main` returns, and the deferred statement `fmt.Print(i + 1)` is executed. The value of `i` is still 2,
   so `i + 1` is 3. Output: "3".

<p align="right">(<a href="#table-of-contents">back to top</a>)</p>

---

#### Object orientation in Go

#### Q1. What is the difference between an object and a class?

1. [ ] An object is a field of data inside a class.
2. [x] A class is a template and an object is an instance of that template.
3. [ ] An object is a particular kind of class.
4. [ ] An object typically contains more data fields than a class.

#### Explanation

In object-oriented programming, a class is a blueprint or template that defines the structure and behavior of objects.
It specifies the properties (data fields) and methods (functions) that objects of that class will have.

#### Q2. What is the difference between a struct in Go and a class in an object-oriented language?

1. [x] A struct contains only data while a class can also contain methods.
2. [ ] A class describes data fields but a struct does not.
3. [ ] A struct can only be created inside a class.
4. [ ] A struct cannot contain another struct.

#### Explanation

In Go, a struct is a composite data type that allows you to group together different data fields of different types. It
is similar to a class in an object-oriented language, but there are some key differences.

Here's an example in Go to illustrate the difference between a struct and a class in an object-oriented language:

```go
package main

import "fmt"

// Struct definition
type Person struct {
	Name string
	Age  int
}

// Method associated with the Person struct
func (p Person) SayHello() {
	fmt.Printf("Hello, my name is %s and I'm %d years old.\n", p.Name, p.Age)
}

func main() {
	// Creating an object (instance) of the Person struct
	person := Person{Name: "Alice", Age: 25}

	// Accessing the struct fields and calling the method
	fmt.Println(person.Name) // Output: Alice
	fmt.Println(person.Age)  // Output: 25
	person.SayHello()        // Output: Hello, my name is Alice and I'm 25 years old.
}
```

In this example, we have a struct called `Person`, which represents a person with a `Name` field of type string and
an `Age` field of type int. This is similar to defining a class in an object-oriented language.

The `Person` struct also has a method called `SayHello()`, which is associated with the `Person` struct. It can be
accessed and called on objects (instances) of the `Person` struct.

In the `main()` function, we create an object `person` of type `Person` and initialize its field values. We can access
and print the field values (`Name` and `Age`) directly. Additionally, we call the `SayHello()` method on the `person`
object, which prints a message using the struct's field values.

This example demonstrates how a struct in Go can contain data fields and methods, akin to a class in an object-oriented
language.

#### Q3. Which of the following refers to data hiding?

1. [ ] Instantiation
2. [ ] Polymorphism
3. [ ] Inheritance
4. [x] Encapsulation

#### Explanation

Encapsulation refers to the concept of hiding the internal implementation details of an object and exposing only the
necessary information or functionality to the outside world. It is a fundamental principle in object-oriented
programming that promotes data hiding and abstraction.

Here's an example in Go to illustrate encapsulation and data hiding:

```go
package main

import (
	"fmt"
)

// Struct definition
type Person struct {
	name string
	age  int
}

// Method to set the name of the person
func (p *Person) SetName(name string) {
	p.name = name
}

// Method to get the name of the person
func (p Person) GetName() string {
	return p.name
}

// Method to set the age of the person
func (p *Person) SetAge(age int) {
	p.age = age
}

// Method to get the age of the person
func (p Person) GetAge() int {
	return p.age
}

func main() {
	// Creating an object (instance) of the Person struct
	person := Person{}

	// Setting the name and age using the encapsulated methods
	person.SetName("Alice")
	person.SetAge(25)

	// Accessing the name and age using the encapsulated methods
	fmt.Println(person.GetName()) // Output: Alice
	fmt.Println(person.GetAge())  // Output: 25

	// Attempting to access the fields directly (data hiding)
	// This would result in a compilation error
	// fmt.Println(person.name)
	// fmt.Println(person.age)
}
```

In this example, we define a struct called `Person`, which represents a person with `name` and `age` as private fields.

The methods `SetName()` and `GetName()` are defined with receiver type as a pointer to `Person`, allowing us to modify
and retrieve the `name` field respectively. Similarly, the methods `SetAge()` and `GetAge()` are defined for modifying
and retrieving the `age` field.

In the `main()` function, we create an object `person` of type `Person`. We then use the encapsulated
methods `SetName()` and `SetAge()` to set the name and age of the person respectively. The encapsulated methods ensure
that direct access to the private fields is restricted.

Next, we use the encapsulated methods `GetName()` and `GetAge()` to retrieve the name and age of the person
respectively. These methods provide controlled access to the private fields while maintaining data hiding.

If we attempt to access the `name` and `age` fields directly using `person.name` or `person.age`, it would result in a
compilation error. This demonstrates how encapsulation helps in data hiding by preventing direct access to private
fields outside the struct.

Encapsulation allows for better control over the access and modification of data, providing encapsulated methods as a
means to interact with the private fields of a struct, ensuring data integrity and security.

#### Q4. How do you associate a method with an arbitrary data type on Go?

1. [x] Define the method so that its receiver type is the data type of interest.
2. [ ] Define the method inside the data type definition.
3. [ ] Include the name of the data type in the name of the method.
4. [ ] Define the data type and the method in the same file.

#### Explanation

In Go, a method is associated with a specific data type by defining the method with a receiver parameter of that data
type. By specifying the receiver type, the method becomes associated with that type.

For example, let's say we have a custom data type called `MyType`:

```go
type MyType struct {
// fields and data of MyType
}
```

To associate a method with this `MyType`, we define the method with a receiver parameter of `MyType`:

```go
func (m MyType) MyMethod() {
// method implementation
}
```

In this example, the `MyMethod()` method is associated with the `MyType` data type. The receiver parameter `(m MyType)`
indicates that this method can be called on instances of `MyType`.

We can then create an object of `MyType` and call the associated method:

```go
myObject := MyType{}
myObject.MyMethod() // Call the MyMethod() on myObject
```

The method `MyMethod()` is now associated with the `MyType` data type, and we can call it on objects (instances)
of `MyType`.

To summarize, in Go, you associate a method with an arbitrary data type by defining the method with a receiver parameter
that matches the data type of interest. This allows the method to be called on objects of that data type.

#### Q5. In Go, how do you hide variables or functions in a package, so that functions outside the package cannot access them?

1. [ ] Use the package keyword
2. [ ] Use the private keyword.
3. [x] Give the variable/function a name which starts with a lower-case letter
4. [ ] Define the variable/function inside the package.

#### Explanation

In Go, the visibility and accessibility of variables and functions are determined by their naming conventions. To hide
variables or functions in a package, you give them a name that starts with a lower-case letter.

In Go, naming conventions follow the concept of visibility based on the initial letter case:

1. Variables or functions starting with an upper-case letter are exported and accessible from outside the package.
2. Variables or functions starting with a lower-case letter are unexported and not accessible from outside the package.

Here's an example to illustrate this:

```go
package mypackage

var PublicVariable int = 10
var unexportedVariable int = 20

func PublicFunction() {
	// Function implementation
}

func unexportedFunction() {
	// Function implementation
}
```

In this example, `PublicVariable` and `PublicFunction` start with upper-case letters, making them exported and
accessible from outside the `mypackage` package.

On the other hand, `unexportedVariable` and `unexportedFunction` start with lower-case letters, indicating that they are
unexported and cannot be accessed from outside the `mypackage` package.

#### Q6. Say that you have defined a type `t` and you have declared an object of that type called t1. Assume that the type t is the receiver type for a method called Foo(). Which expression shows a proper invocation of the method Foo()?

1. [ ] Foo(t1)
2. [ ] Foo(t)
3. [ ] t1.Foo()
4. [ ] t.Foo(t1)

#### Explanation

In Go, when a method is associated with a type, it is invoked using the syntax `receiver.Method()`. Therefore, to
properly invoke the method `Foo()` with `t1` as the receiver object, the correct expression would be `t1.Foo()`.

Here's an example to illustrate this:

```go
package main

import "fmt"

type MyType struct {
	// fields and data of MyType
}

func (m MyType) Foo() {
	fmt.Println("Foo() method called")
}

func main() {
	t1 := MyType{}
	t1.Foo() // Proper invocation of the Foo() method using t1 as the receiver object
}
```

In this example, we define a type `MyType` with a method `Foo()`. Inside the `main()` function, we create an object `t1`
of type `MyType`. To invoke the `Foo()` method on `t1`, we use the expression `t1.Foo()`, where `t1` is the receiver
object and `Foo()` is the method being invoked.

#### Q7. Assume that the type t is the receiver type for a method called Foo(). Under what conditions would it be better to make the receiver type of Foo() a pointer to t, rather than itself?

#### I. When the receiver type t uses a large amount of memory.

#### II. When the method Foo() must modify the data in the object of the receiver type.

1. [ ] Only I
2. [ ] Only II
3. [x] Both I and II
4. [ ] Neither I nor II

#### Explanation

It is better to make the receiver type of the method `Foo()` a pointer to `t` instead of `t` itself when both conditions
I and II are met.

**Condition I**: When the receiver type `t` uses a large amount of memory.

When the receiver type `t` uses a large amount of memory, passing it as a value (non-pointer) to the method would
involve making a copy of the entire data structure. This can be inefficient in terms of memory usage, especially if the
data structure is large. By using a pointer receiver, only the memory address of the data structure is passed, rather
than making a copy of the entire structure. This can lead to more efficient memory utilization.

**Condition II**: When the method `Foo()` must modify the data in the object of the receiver type.

If the method `Foo()` needs to modify the data within the object of the receiver type `t`, using a pointer receiver
allows the method to directly modify the original object. When a non-pointer receiver is used, the method receives a
copy of the object, and any modifications made within the method would only affect the copy, not the original object. By
using a pointer receiver, the method can directly access and modify the original object's data.

By using a pointer receiver, we can address both memory efficiency concerns and the ability to modify the receiver
object's data.

<p align="right">(<a href="#table-of-contents">back to top</a>)</p>

---
