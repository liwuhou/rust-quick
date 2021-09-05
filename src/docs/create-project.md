# 创建一个Rust项目

You can run all the code in this article online (except local stuff like file access, of course) with the [Rust playground](https://play.rust-lang.org/?version=nightly&mode=debug&edition=2018).

After installing Rust, create a new project with Cargo (the Rust package manager):
```rust
cargo new <PROJECT_NAME>
```
This will create a new folder in your current directory.

Alternatively, to make your current directory the project folder:
```
cargo init
```
The source is located in the src/ folder. Of course, the entry point is the main.rs file with its main function (fn keyword).
```rust
fn main() {
    println!("Hello, world!");
}
```