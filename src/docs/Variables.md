# 变量
```rust
fn main() {
    // variables are immutable by default
    // stored on the heap (more on that later) 
    let pc = "Inspirion XYZ";
    println!("pc is {}", pc); // mutable variables 
    let mut age = 1;
    println!("age is {}", age);
    age = 2;
    println!("age is {}", age); // constants (must be uppercase and explicit type definition)
     const BRAND: &str = "Dell";
    println!("brand is {}", BRAND); // multiple assignment (tuple destructuring)
    // more on tuples later in the article
     let (status, code) = ("OK", 200);
    println!("status: {}, code: {}", status, code);
}
```
Output
```
pc is Inspirion XYZ
age is 1
age is 2
brand is Dell
status: OK, code: 200
```