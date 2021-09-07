# Crates

- 源代码文件的收集
- crates注册仓库。 [crates.io](https://crates.io/)
    (相当于[npmjs.com](https://www.npmjs.com/)的Node.js模块)
- 两种类型。
    - 二进制crate
    包含用于编译执行程序的源代码
    - 库crate
    包含用于执行其他程序的代码
- 要使用第三方程序箱，请在Cargo.toml文件的[dependencies]部分添加crate的名称和版本（外部crate）。
```yml
[package]
name = "crates"
version = "0.1.0"
authors = ["Florian GOTO <<you@example.com>>"]
edition = "2018"
# 在<https://doc.rust-lang.org/cargo/reference/manifest.html>[dependencies]看到更多的键和它们的定义。
# 添加随机数生成工具箱
rand = "0.8.3"
```
-   Cargo will automatically download the crates in the [dependencies] section along with their own dependencies before compiling
-   to use the downloaded crate
```rust
use rand;
fn main() {
  let random_number = rand::random::<u8>();
  println!("random_number is {}", random_number);
}
```
输出
```
random_number is 97
```

- 如果你使用一个板块的特定函数，请在use语句中直接指定它（编译器会警告你与本地定义的代码发生名称冲突）。

```rust
// 只导入 rand 软件的 random() 函数 rand::random。
// 从rand crate prelude中导入所有内容
 use rand::prelude::*;
 fn main() {
  let random_number = random::<u8>();
  println!("random_number is {}", random_number);
}
//不能在同一范围内有一个名为随机的局部函数

// 由于名称冲突，如果添加以下代码，程序将无法编译
 fn random() -> u8 {

//   123

 }
```