# 返回类型和特质的动态分派

```rust
use std::fmt::Display;
// [dynamic dispatch](https:
//doc.rust-lang.org/stable/rust-by-example/trait/dyn.html)
// when the retun type cannot be known until runtime

// notice the [dyn](https:
//doc.rust-lang.org/std/keyword.dyn.html)  keyword and the use of a Box pointers
// Returns a value that implements the Display trait,

// but we do not know which one at compile time.
fn get_dynamic_displayable(a: bool) -> Box<dyn Display> {
    if a {
        
        returns u32 Box::new(1)
    } else {
        
     returns string slice Box::new("one")
    }
}
fn main() {
    println!("Display: {}", get_dynamic_displayable(false));
}
```
Output
```
Display: one
```