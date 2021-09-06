# 特性界限
```rust
// when working with generics we can use traits
// in order to stipulate which functionalities the concrete types must implement// trait bounds force a generic type to implement specific traits// trait bounds guarantee a generic type will have the necessary behaviorsuse core::fmt::Debug;
use std::any;// To be able to print an item it must implement the Display trait
// but because not all type implement it, we will use the Debug trait
// which is more commonly implemented by defaultfn print_type<T: Debug>(it: T) {
    // type_name() returns the name of a type as a string slice
    // by passing the type to the turbofish operator (::<MY_TYPE>) println!("{:?} is a {}", it, any::type_name::<T>());
}fn main() {
    print_type(1);
    print_type(1.2);
    print_type([12, 34]);
}
```
Output
```
1 is a i32
1.2 is a f64
[12, 34] is a [i32; 2]

```