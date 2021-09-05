# 基本数据类型

```rust
fn main() {
    // default integer numeric type is i32 
    let num1 = 123;
    println!("{} - type: {}", num1, get_type(&num1)); // default floating point numeric type is f64 let num2 = 1.23;
    println!("{} - type: {}", num2, get_type(&num2)); // explicit typing 
    let num3: i8 = 23;
    println!("{} - type: {}", num3, get_type(&num3)); // max values // std is the standard library/crate,
    // it gives access to a rich variety of features,
    // here we use the type modules (i32, i16, etc.) and properties
    let max_i32 = i32::MAX;
    let max_i16 = i16::MAX;
    println!("max value for i32 is {}", max_i32);
    println!("max value for i16 is {}", max_i16); // boolean 
    let is_rust_fun: bool = true;
    println!(
        "is_rust_fun is {} - type: {}",
        is_rust_fun,
        get_type(&is_rust_fun)
    );
    let is_greater = 23 > 5;
    println!(
        "is_greater is {} - type: {}",
        is_greater,
        get_type(&is_greater)
    );
     // characters (unicode - up to 4 bytes length) let smiley = '😈';
    println!("smiley is {} - type: {}", smiley, get_type(&smiley));
}
// helper function to print types
fn get_type<T>(_: &T) -> &str {
    std::any::type_name::<T>()
}
```
Output
```
123 - type: i32
1.23 - type: f64
23 - type: i8
max value for i32 is 2147483647
max value for i16 is 32767
is_rust_fun is true - type: bool
is_greater is true - type: bool
smiley is 😈 - type: char
```