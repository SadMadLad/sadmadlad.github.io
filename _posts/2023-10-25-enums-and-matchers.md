---
categories: [Programming, Rust]
tag: [Rust, Programming, Enums, Notes]
---

Enums are quite important for Rust. Enums are usually used to group up structs and for pattern matching. Here is an example:

```rust
enum Graphs {
  Point(f32, f32),
  Line(f32, f32),
  Origin,
  Angle { degrees: f32 },
}

fn main() {
  let g = Graph::Angle { degrees: 40.0 };
  
  println!("{:#?}", g)
}
```

## The `Option<T>` and `None` enums

Rust itself has no `null` and uses the enum type `Option<T>`. It consists of two types, one is `Some<T>`, that signifies presence of some value, and the other is `None`, which is something like `null`.

```rust
fn main() {
  let some: Option<i32> = Some(32);
  let none: Option<i32> = None;
}

fn somebody<T>(e: Option<T>) {
  match e {
    Some(x) => {println!("Some value");}
    None => {println!("None");}
  }
}
```

## Pattern Matching

The `match` is powerful operator in Rust to compare against different enum values.

```rust
#[derive(Debug)]
enum Graph {
  Point(f32, f32),
  Line(f32, f32),
  Origin,
  Angle { degrees: f32 },
}

fn main() {
  let a = Graph::Point(10.0, 10.0);
  let b = Graph::Line(8.0, 9.0);
  let c = Graph::Origin;
  let d = Graph::Angle{ degrees: 40.0 };
  
  let a = matcher(a);
  let b = matcher(b);
  let c = matcher(c);
  let d = matcher(d);
  
  println!("{}, {}, {}, {}", a, b, c, d);
}

fn matcher(e: Graph) -> String {
  match e {
    Graph::Point(x, y) => String::from("Pointing x, y"),
    Graph::Origin => String::from("Origin"),
    Graph::Angle { degrees }  => String::from("Degrees"),
    _ => String::from("Not found"),
  }
}
```

The `if let` is a shortcut to destructure and handle the value instead of writing `match` for all the types.

```rust
fn main() {
    let some: Option<i32> = Some(32);
    
    if let Some(i) = some {
        println!("Matched {:?}!", i);
    }
}
```

