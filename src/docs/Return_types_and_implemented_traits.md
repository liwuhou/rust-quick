# 返回类型和特性实现

```rust

use std::fmt::Display;// the return value must implement the Display traitfn get_displayable() -> impl Display {
    1
}fn main() {
    println!("Display: {}", get_displayable());
}
```

输出
```
Display: 1
```