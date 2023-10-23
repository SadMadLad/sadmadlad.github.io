---
categories: [Programming, Rust]
tag: [Rust, Programming, Control Flow, Notes]
---

Rust provides `if-else`, `loop`, `while` and `for` to control the execution of instructions.

## If-Else

Rust provides with `if-else` statements for conditional execution of instructions. *The condition for the `if-else` statement should always be a boolean*. This is important because unlike other programming languages like Ruby and JavaScript, statements like `if number { ... }` do not work. Furthermore, you can write `if-else` statements in a single line as well.

```rust
let a = 10;
if a > 8 {
  println!("This is greater than 8");
} else if a == 10 {
  println!("This is equal to 10");
} else {
  println!("None of the above conditions are true");
}

// The following would not work.

let b = 2;
if b {
  println!("This is not going to work")
}
```

While writing `if-else` in one line, make sure to keep the type of the variable same in both the `if` and the `else` blocks. For example:

```rust
let number = if true { 5 } else { 6 }; // This is fine.
let number = if true { 5 } else { '6' }; // This is wrong.
```

## Loops

### `loop`
Rust has a keyword `loop` that continuously runs unless explicitly broken using the keyword `break`. You can also name your loops using `'` (like this `'counting_up: loop { ... }`), and breaking specific loops. Below is an example.

```rust
let mut x = 10;
'outside_loop: loop {
  x += 1
  loop {
    x += 2
    if x > 20 {
      break;
    }
    if x > 40 {
      break 'outside_loop;
    }
  }
}
```

### `while`
The `while` works just like it does other programming languages.

```rust
let mut x = 0;

while x > 10 {
  x+= 1;
}
```

### `for`
Similar to Python, the `for` keyword allows us to loop over collections.

```rust
let arr = [1, 2, 3, 4, 5];

for i in arr {
  println!("This is {i}")
}
```
