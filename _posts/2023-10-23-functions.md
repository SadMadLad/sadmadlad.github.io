---
categories: [Programming, Rust]
tag: [Rust, Programming, Functions, Notes]
---

Functions in Rust are declared with the `fn` keyword, followed by the name of the function and then a paranthesis which includes the arguments/inputs of a function. Then, you can declare the return type of the function with an arrow `->`. Lastly, the body of the function is declared in a body


```rust
fn foo(i: u32) -> u32 {
  i
}
```
To understand the use of semicolons in rust and why there was no semicolon in the above function, we must know the difference between a statement and an expression.

**Statement**: A statement performs some sort of instruction but does not return anything.

**Expression**: An expression evaluates and returns a value.

The following example demonstrates the difference between a statement and an expression:

```rust
  fn main() {
    let x = (let y = 10); // Wrong because the let does not return a value, and is a statement.

    let y = 10;
    let x = {
      y + 1
    } // Correct because the block results in a value at the end.
  }
```
