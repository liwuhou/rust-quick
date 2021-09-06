# 返回类型和特质的动态分派

```rust
use std::fmt::Display;
// [动态调度](https://doc.rust-lang.org/stable/rust-by-example/trait/dyn.html)
// 当运行时才知道retun的类型时

// 注意 [dyn](https://doc.rust-lang.org/std/keyword.dyn.html) 关键字和盒式指针的使用
// 返回一个实现了显示特性的值。

// 但我们在编译时不知道是哪一个。
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
输出
```
Display: one
```