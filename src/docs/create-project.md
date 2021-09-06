# 创建一个Rust项目



你可以用[Rust playground](https://play.rust-lang.org/?version=nightly&mode=debug&edition=2018)在线运行本文中的所有代码（当然，除了文件访问等本地的东西）。

安装完Rust后，用Cargo（Rust软件包管理器）创建一个新项目。
```rust
cargo new <PROJECT_NAME>。
```
这将在你的当前目录下创建一个新的文件夹。

或者，让你的当前目录成为项目文件夹。
```
cargo init
```
源文件位于src/文件夹中。当然，进入点是main.rs文件及其主函数（fn关键字）。
```rust
fn main() {
    println! ("Hello, world!");
}
```