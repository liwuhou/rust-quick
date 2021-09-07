# 标准库

-   文档: <https://doc.rust-lang.org/std/>

```rust

// 使用声明是用来导入模块/库的。
// 它把一个模块的路径带入程序的范围内
// 标准库中的一些模块并不是Rust语言本身的一部分。
// 意思是说，你需要导入它们--比如Node.js中的 "fs "模块--否则编译器将不知道它们是什么。
// 否则编译器将不知道它们的含义)
// 所有程序都默认使用标准库
// [prelude](https://doc.rust-lang.org/std/prelude/index.html)是每个Rust程序都会自动导入的东西的列表。
// 它并没有导入整个标准库（只有最常见的标准模块）。
// 如果一个模块没有被包含在预演中，你需要手动将其导入。
import ituse std::thread;
fn main() {
    let child = thread::spawn(move || 2 + 2);
    let res = child.join(); 
    println!("res is {}", res.unwrap());
}
```

输出
```

res is 4
```