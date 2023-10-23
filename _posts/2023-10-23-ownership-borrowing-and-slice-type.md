---
title: 'Ownership, Borrowing and Slice Type'
categories: [Programming, Rust]
tag: [Rust, Programming, Conceptual, Notes]
---

Rust inherently has no garbage collector. Instead, it relies on an important concept of **ownership**.

> Before moving onto ownership, it is important to discuss the difference between **heap** and **stack**. **Stack** is organized memory in which data is pushed and popped from the stack. It follows the *LIFO* (Last In First Out) sequence. Stack is *faster* and data types like integers, characters are stored on it. **Heap** is less organized when it comes to storing data. It is *slower* than stack. When it comes to storing data in heap, it needs to know how much space does it need to free up before storing the variable on the go, which is why it is slower. It needs to keep the pointer for memory too. Storing data types like vectors requires heaps.
{: .prompt-tip }

Following are the rules of ownership in Rust:
* Each value has an owner.
* The can only be one owner at a time.
* When the owner goes out of scope, the value will be dropped.

```rust
{ // w is not valid
  let w = "world"; // w is valid
} // w is not valid
```

The string literal (declared like `let x = "hello";`) is hardcoded and cannot be mutated. This cannot be modified. If you want a mutable string, you would need to declare it using `String::from`.

```rust
let mut x = String::from("hello");
x.push_str(", world")!
```

When you use allocated variables, they are *borrowed* between the variables. For example:

```rust
let x = String::from("hello");
let y = x;

println!("{}", x); // Wrong. x is already borrowed by y
// If you want to use x too, you would have to clone it like this:
let y = x.clone();
```

The values passed to functions are also dropped in the function (as they go out of the scope).

```rust
fn takes_ownership(s: String) {
  println!("{}", s);
}

fn main() {
  let x = String::from("hello");
  takes_ownership(x);

  // x has gone out of scope and become invalid.
}
```

## References

If we want to pass a value to a function, but do not want it to drop out of scope, we can pass a **reference** to the function instead of the whole value. A **reference** is the pointer to the value. **Reference by default are immutable**.

```rust
fn main() {
  let s = String::from("Hello");
  let r = &s;
  println!("{}", length(r))
}

fn length(s: &String) -> i32 {
  s.len()
}
```

Some rules for references:

* One value can have multiple *immutable* references, but only one mutable reference.
* Mutable reference go out of scope.
* You cannot have an immutable reference and mutable reference to the same value at the same time.
* Mutable reference allows you to change the value of the variable.

## The Slice Type

The Slice Type allows us to reference a contiguous sequence of elements in a collection. As it is a reference, it does not have ownership. Here is an example:

```rust
let string: String = String::from("Hello World");

// Getting the slices
println!("{}", &string[0..4]);
println!("{}", &string[..3]);
println!("{}", &string[7..]);

// The above slices are of the &str type.
```

> By default, string literals (like `Hello World!`) are of type `&str`.
{: .prompt-tip }
