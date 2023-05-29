## Getting Started with Go

[Link to course](https://www.coursera.org/learn/golang-getting-started)

<a name="link-top"></a>

---

### Table of Contents

<ol>
  <li>
    <a href="#module-1">Module 1</a>
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
