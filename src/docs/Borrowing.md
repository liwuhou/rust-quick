# 借用

All this stuff about ownership is great but what if you don't need to transfer ownership, you just need the data:
```rust
fn main() {
    
// 借用：在不取得所有权的情况下访问数据 
//创建一个你想借用的变量的引用
    
// 使用借用操作符"&"。
let rocket_fuel = String::from("MU-RF"); 
// 注意借用操作符来创建一个引用
    
// 该函数期望的是一个引用，而不是一个值 
let length = process_fuel(&rocket_fuel); 
println!("rocket_fuel is {}, length: {}", rocket_fuel,length);
}
// 注意参数类型中的借用操作符

// 我们希望propellant是对一个字符串的引用。

// 而不是一个字符串值(/pointer to it...)
fn process_fuel(propellant: &String) -> usize {
    
// propellant是指向字符串数据的变量的一个引用，用来借用数据。
// 再说一遍，这里没有SHALLOW COPY，因为propellant借用了指针，它确实包含了指针本身（假设它是一个指向另一个指针的指针...）。
println!("Processing propellant {}", propellant);
    let length = propellant.len();
    length 
//当推进剂变量在函数结束时超出范围。
    
// 字符串数据仍然在堆中，因为它仍然属于原始变量（火箭燃料）。
    }
```
输出
```

Processing propellant MU-RF
rocket_fuel is MU-RF, lenght: 5

In Rust, data will most often be passed by reference (borrowed)than by value (ownership transfer). But you still need to know which variable really owns the data.
```