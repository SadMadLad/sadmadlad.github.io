---
categories: [Programming, Rust]
tag: [Rust, Programming, Variables, Notes, Data Types]
---

### Nature
Variables in Rust by default are immutable. So, when you write `let x = 32;`, the variable `x` is immutable and cannot be changed later (you can shadow it though). 

### Mutable Variables
If you want to declare a variable to be mutable, you need to declare it with a `mut` keyword, like `let mut x = 32;`.

### Constants
Constants, just like immutable variables, cannot be modified. However, there are some differences:

| Variables | Constants |
| - | - |
| Variables do not require annotation by default | [Type Annotation](#annotation) is a must for constants |
| Can be shadowed | Cannot be shadowed |
| Not always uppercase | Always uppercase |

## Data Types

Rust is [statically typed](#statically-typed-language) and must know the types during the compile time. There are two types of data types in Rust:

### Scalar Types
Scalar types represent a single value. The four primary scalar types are:
* **Integer**: Number without a fractional component. [Here are the some of the types of integers that can be declared in Rust](https://doc.rust-lang.org/book/ch03-02-data-types.html#integer-types). `isize` and `usize` types are typically used when indexing some sort of collection. You can write the string literals in following ways:

  | Literal | Example |
  | - | - |
  | Decimal | `98_222` |
  | Hex | `0xff` |
  | Octal | `0o1234` |
  | Binary | `0b0000_1111` |
  | Byte (`u8` only) | `b'A'` |

* **Floating Point Numbers**: Numbers with the fractional component. Typically, there are `f32` and `f64` (for more precision).

* **Booleans**: Only available values are `true` or `false`. Typically used for conditionals for [flow control](#flow-control).

* **Character Type**: A character type means a single unicode entity. Typically wrapped in single quote (like `A`), unlike strings which are wrapped in double quotes.

### Compound Types

Compound types are used to group up multiple elements into single data structure. Two primitive compound types are:

#### Tuples

Tuples generally group up multiple elements of multiple types into a single compound type. *Tuples cannot grow or shrink once declared*.

```rust
let my_tuple: (i32, char) = (100, 'A');
let (a, b) = my_tuple // Destructure
let c = my_tuple.0 // Accessing first element
```

#### Arrays

Arrays have fixed length that have all of their elements of the same data type. If you are unsure if the collection can grow, you should [vector](#vector) instead of an array.

```rust
let arr_one = [1, 2, 3]
let arr_two: [i32; 5] = [1, 2, 3, 4, 5] // Initializing an array of 5 i32 elements.
let arr_three: [3; 5] // Initializing an array of 5 3s ([3, 3, 3, 3, 3])
```


## Terms and Definitions

**Type Annotation**: Declaring a type of a variable. 
{: #annotation }

**Statically Typed Language**: A statically typed language must know the type of all the variables during run type.
{: #statically-typed-language }

**Collection**: Here, colllection means some type of data structure with many elements to it, like arrays, strings etc.
{: #collection }

**Flow Control**: Control of the execution of instructions in a programs, using `booleans`, `if-else`, `switch` statements etc.
{: #flow-control }

**Vector**: A vector is a flexible data structure that is stored on heap and can be grown or shrinked on the go.
{: #vector }


