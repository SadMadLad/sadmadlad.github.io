---
categories: [Programming, Rust]
tag: [Rust, Programming, Structures, Notes]
---

A struct is declared with a `struct` keyword, followed by its name and a list of attributes and their types.

```rust
struct User {
  active: bool,
  sign_in_count: u32,
  name: String
}

fn build_user(active: bool, sign_in_count: u32, name: String) -> User {
  User { active, sign_in_count, name }
}

fn main() {
  let s: String = String::from("Hello World");

  let user: User = User {
    active: false,
    sign_in_count: 32,
    name: s 
  };

  println!("{}", user.active);
}
```

### Tuple Structs

Tuple structs are basically named tuples.

```rust
struct Point(f32, f32, f32);

fn main() {
  let point: Point = Point(10.0, 10.0, 10.0);
  println!("{}", point.0);
}
```

### Adding functionality to Structs

We can add more functionality to structs using derived traits. For example, structs by default cannot be printed directly using the macro `println!`. But adding the trait `#[derive(Debug)]` on the top of the declaration of a struct, you can print it in `println!` using `{:?}` (or `{:#?}` for prettier output).

```rust
#[derive(Debug)]
struct Person { name: String, age: u8 }

fn main() {
  let person: Person = Person { name: String::from("Name"), age: 10 };

  println!("{:#?}", person);
}
```
> `dbg!` can also be used to print, but `dbg!` takes the ownership while `println!` takes the reference.
{: .prompt-tip }

> In `#[derive(Debug)]`, the `derive` is an **attribute** and `Debug` is a **trait**.`
{: .prompt-tip }

### Defining methods

Methods for a struct can be declared using the `impl` signature. Typically, the methods use `&self` as an argument. However, we can also declare methods that do not use `&self` as the argument (`String::from` is an example). We can declare multiple `impl` for a single struct.

```rust
#[derive(Debug)]
struct Point(i32, i32, i32);

impl Point {
    fn avg(&self) -> i32 { (self.0 + self.1 + self.2) / 3 }
    fn new(x: i32, y: i32, z: i32) -> Self { Self(x, y, z) } 
}

fn main() {
    let p: Point = Point::new(1, 2, 3);
    
    println!("{:#?} {}", p, p.avg());
}
```

> `&self` is a shorthand for `self: &Self`.
{: .prompt-tip }
