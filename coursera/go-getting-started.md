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
