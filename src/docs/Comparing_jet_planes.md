# 对比飞机

```rust

use std::cmp::*;
use std::fmt;struct Jet {
    name: String,
    velocity: f64, // km/h
}// custom implementation of the [Display](https://doc.rust-lang.org/std/fmt/trait.Display.html#required-methods) traitimpl fmt::Display for Jet {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        write!(f, "{}, flying at {} km/h", self.name, self.velocity)
    }
}// custom implementation of the [PartialOrd](https://doc.rust-lang.org/std/cmp/trait.PartialOrd.html#how-can-i-implement-partialord) traitimpl PartialOrd for Jet {
    fn partial_cmp(&self, other: &Self) -> Option<Ordering> {
        self.velocity.partial_cmp(&other.velocity)
    }
}// custom implementation of the [PartialEq](https://doc.rust-lang.org/std/cmp/trait.PartialEq.html#how-can-i-implement-partialeq) traitimpl PartialEq for Jet {
    fn eq(&self, other: &Self) -> bool {
        self.velocity == other.velocity
    }
}fn main() {
    let g6 = Jet {
        name: String::from("Gulfstream G650"),
        velocity: 956.0,
    }; let g7 = Jet {
        name: String::from("Gulfstream G700"),
        velocity: 937.0,
    }; println!("G6 jet is {}", g6); println!("Does G6 velocity equal to G7's: {}", g6.eq(&g7)); println!("Is G6 faster than G7: {}", g6.gt(&g7));
}
```
输出
```
G6 jet is Gulfstream G650, flying at 956 km/h
Does G6 velocity equal to G7's: false
Is G6 faster than G7: true

```