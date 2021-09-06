# 基本数据类型

```rust
fn main() {
    // 默认整数的精度数据类型是32位: i32 
    let num1 = 123;
    println!("{} - type: {}", num1, get_type(&num1)); 
    // 默认浮点数的精度为64位： f64
    let num2 = 1.23;
    println!("{} - type: {}", num2, get_type(&num2)); 
    // 显示声明 类型 
    let num3: i8 = 23;
    println!("{} - type: {}", num3, get_type(&num3)); 
    // 最大值
     // std是标准库/rate。
    // 它提供了丰富的功能。
    // 这里我们使用类型模块（i32、i16等）和属性。
    let max_i32 = i32::MAX;
    let max_i16 = i16::MAX;
    println!("max value for i32 is {}", max_i32);
    println!("max value for i16 is {}", max_i16); 
    // 布尔值 
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
     //字符（unicode - 最多四个字节的长度）。
    let smiley = '😈';
    println!("smiley is {} - type: {}", smiley, get_type(&smiley));
}
// 用于打印类型的辅助函数
fn get_type<T>(_: &T) -> &str {
    std::any::type_name::<T>()
}
```
输出
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