# 变量
```rust
fn main() {
    // 变量在默认情况下是不可变的
    //存储在堆上（后面会有更多的介绍）。
    let pc = "Inspirion XYZ";
    println!("pc is {}", pc); 
    // 可变的变量
    let mut age = 1;
    println!("age is {}", age);
    age = 2;
    println!("age is {}", age); 
    // 常量（必须是大写字母和明确的类型定义）。
     const BRAND: &str = "Dell";
    println!("brand is {}", BRAND); 
    // 多重赋值（元组解构）。
    // 在文章后面有更多关于元组的内容
     let (status, code) = ("OK", 200);
    println!("status: {}, code: {}", status, code);
}
```
输出
```
pc is Inspirion XYZ
age is 1
age is 2
brand is Dell
status: OK, code: 200
```