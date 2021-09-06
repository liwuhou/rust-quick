# 打印输出


在Rust中，你使用所谓的[宏](https://en.wikipedia.org/wiki/Macro_(computer_science))来打印到控制台。Rust中的宏有一个标识符，后面是一个感叹号（！）。println！宏是非常灵活的。

```rust
fn main() { 
   // 字符串内插
   println!("Adding {} and {} gives {}", 22, 33, 22 + 33);
   // 位置参数 
   println!(
        "Ypur name is {0}. Welcome to {1}. Nice to meet you {0}",
        "Goto", "Rust"
   );
    // 变量命名
     println!(
        "{language} is very popular. It was created in {year}",
        language = "Rust",
        year = 2010
   );
   // 占位符特征（使用位置参数以避免重复）。
   println!("{0}, in binary: {0:b}, in hexadecimal: {0:x}", 11);
    // 调试特性（对打印任何东西都非常有用）。
     // 如果你试图直接打印数组，你会得到一个错误。
  // 因为数组不是一个字符串或数字类型。
   println!("{:?}", [11, 22, 33]);
  }
```
运行命令查看输出结果：
```
cargo run
```
你会看到（连同代码的编译信息---Rust是一种编译的语言）。
```
Adding 22 and 33 gives 55
Ypur name is Goto. Welcome to Rust. Nice to meet you Goto
Rust is very popular. It was created in 2010
Decimal: 11      Binary: 1011    Hexadecimal: b
[11, 22, 33]
```
在Rust中，你必须在行尾使用分号（;），除非它是一个返回东西的函数的最后一行（后面会详细介绍）。