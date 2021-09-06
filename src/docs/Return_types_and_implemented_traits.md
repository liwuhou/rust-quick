# 返回类型和特性实现

```rust

use std::fmt::Display;
// 返回值必须实现 "Display "特质。
fn get_displayable() -> impl Display {
    1
}
fn main() {
    println!("Display: {}", get_displayable());
}
```

输出
```
Display: 1
```