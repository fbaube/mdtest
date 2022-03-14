# mdtest

tinkering with GFM 

```package doc
// Real is just another name for float64.
type Real float64
package doc_test
// Use Real like a general floating type:
func ExampleReal() {
    var x Real = 1.23
}
```

Also a special comment can be used to designate what the output
of the example will be (ALTHO note that this is not yet runnable !) 

```
package doc
// Absolute value.
func Abs(x Real) Real {
}
package doc_test
func ExampleAbs_positive() {
    Abs(1.23)
    // Output: 1.23
}
func ExampleAbs_negative() {
    Abs(-1.23)
    // Output: 1.23
}
```

Hi, <font face="serif"><big>some</big></font> text.

| Name     | Character |
| ---      | :--:      |
| Backtick | `         |
| Pipe     | \|        |

| Docu | Docu |
| ---  | ---  |
| [on Github](http://github.com/fbaube/mdtest/docs/Test.md) | [on pkg-dev](http://example.com) |

example_test.go in the stringutil directory:

```package stringutil_test

import (
    "fmt"
    "golang.org/x/example/stringutil"
)
func ExampleReverse() {
    fmt.Println(stringutil.Reverse("hello"))
    // Output: olleh
}
```

If we remove the output comment entirely then the example function
is compiled but not executed. Examples without output comments are
useful for demonstrating code that cannot run as unit tests, such
as that which accesses the network, while guaranteeing the example
at least compiles.

Example function names

Godoc uses a naming convention to associate an example function
with a package-level identifier.

````
func ExampleFoo()     // documents the Foo function or type
func ExampleBar_Qux() // documents the Qux method of type Bar
func Example()        // documents the package as a whole
Following this convention, godoc displays the ExampleReverse example alongside the documentation for the Reverse function.
```

Multiple examples can be provided for a given identifier by using a
suffix beginning with an underscore followed by a lowercase letter.
Each of these examples documents the Reverse function:

```
func ExampleReverse()
func ExampleReverse_second()
func ExampleReverse_third()
```

Larger examples

Sometimes we need more than just a function to write a good example.

To achieve this we can use a “whole file example.” A whole file
example is a file that ends in _test.go and contains exactly one
example function, no test or benchmark functions, and at least
one other package-level declaration. When displaying such examples
godoc will show the entire file.

A package can contain multiple whole file examples; one example per file.

