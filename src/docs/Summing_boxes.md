# 封箱求和

```rust
use std::ops::Add;// restrict generic type T to concrete types that implement the Add trait (like u32, f64, etc.)fn sum_boxes<T: Add<Output = T>>(b1: Box<T>, b2: Box<T>) -> Box<T> {
    let unboxed_b1 = *b1;
    let unboxed_b2 = *b2;
    let sum = unboxed_b1 + unboxed_b2;
    Box::new(sum)
}fn main() {
    let box1 = Box::new(11);
    let box2 = Box::new(44);
    let sum_box = sum_boxes(box1, box2);
    assert_eq!(*sum_box, 55); let box1 = Box::new(1.1);
    let box2 = Box::new(4.4);
    let sum_box = sum_boxes(box1, box2);
    assert_eq!(*sum_box, 5.5); let box1 = Box::new(1.1f32);
    let box2 = Box::new(4.4f32);
    let sum_box = sum_boxes(box1, box2);
    assert_eq!(*sum_box, 5.5f32); let box1 = Box::new(11u8);
    let box2 = Box::new(44u8);
    let sum_box = sum_boxes(box1, box2);
    assert_eq!(*sum_box, 55u8); let box1 = Box::new(11u16);
    let box2 = Box::new(44u16);
    let sum_box = sum_boxes(box1, box2);
    assert_eq!(*sum_box, 55u16); println!("tests passed!");
}
```
输出
```
test passed!
```

Compact version
```rust
use std::ops::Add;fn sum_boxes<T: Add<Output = T>>(b1: Box<T>, b2: Box<T>) -> Box<T> {
    Box::new(*b1 + *b2)
}fn main() {
    assert_eq!(*sum_boxes(Box::new(11), Box::new(44)), 55); assert_eq!(*sum_boxes(Box::new(1.1), Box::new(4.4)), 5.5); assert_eq!(*sum_boxes(Box::new(1.1f32), Box::new(4.4f32)), 5.5f32); assert_eq!(*sum_boxes(Box::new(11u8), Box::new(44u8)), 55u8); assert_eq!(*sum_boxes(Box::new(11u16), Box::new(44u16)), 55u16); println!("tests passed!");
}
```
More complex generic type restriction
```rust
use std::ops::{Add, MulAssign};// remove the Copy trait restriction and see what happens
// more on this laterfn sum_boxes<T: Add<Output = T> + MulAssign + Copy>(
    mut b1: Box<T>,
    b2: Box<T>
) -> Box<T> {
    *b1 *= *b2;
    Box::new(*b1 + *b2)
}fn main() {
    let box1 = Box::new(11);
    let box2 = Box::new(44);
    assert_eq!(*sum_boxes(box1, box2), 528); let box1 = Box::new(1.1);
    let box2 = Box::new(4.4);
    assert_eq!(*sum_boxes(box1, box2), 9.240000000000002); let box1 = Box::new(1.1f32);
    let box2 = Box::new(4.4f32);
    assert_eq!(*sum_boxes(box1, box2), 9.24f32); let box1 = Box::new(11u16);
    let box2 = Box::new(44u16);
    assert_eq!(*sum_boxes(box1, box2), 528u16); println!("tests passed!");
}
```