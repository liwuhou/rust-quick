# 多重特质界限和where子句

```rust
use std::fmt::Display;
// multiple trait bounds are separated by a + operator

// PartialEq/From/Copy are part of the prelude of the std library so no import
//
 //fn compare_and_print<T: Display + PartialEq + From<U>, U: Display + PartialEq + Copy>(a: T, b: U) {
// the below function signature is equivalent to the above

// but more readable with the were clause to declare trait bounds
fn compare_and_print<T, U>(a: T, b: U)
where
    T: Display + PartialEq + From<U>,
    U: Display + PartialEq + Copy,
{
    
// 
T::from(b) => convert b to type T
    
// From trait allows for a type
    
// to define how to create itself from another type.
    
// ex: creating a string from string slice
    
//      
String::From("ttoto") if a == T::from(b) {
        println!("{} is equal to {}", a, b);
    } else {
        println!("{} is not equal to {}", a, b);
    }
}
fn main() {
    compare_and_print(22, 55);
    compare_and_print(2.2, 2.2);
}
```
Output
```
22 is not equal to 55
2.2 is equal to 2.2
```