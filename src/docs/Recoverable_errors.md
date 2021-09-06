# 可恢复的错误

```rust
// 可恢复的错误
// 不会导致程序失败的错误
// 并且可以被纠正的错误
// Rust使用Result<T,E>枚举类型来处理可恢复错误
// enum Result<T, E> {
// Ok(T),
// Err(E),
// }
// Ok变量存储的是成功操作的值
// Err变体存储错误的值
// 结果枚举被包含在前奏中，使用std::fs;
use std::io;
fn main() {
    // read_to_string() 返回一个 Result<T, E> 枚举。
    // 在项目文件夹的根部创建一个名为file.txt的文件。
    // $ echo 42 > file.txt 
    let content: Result<String, io::Error> = fs::read_to_string("file.txt")。
    // 避免使用unwrap()方法
    // 因为如果这是 Result 枚举的 Err 变体，会引起panic 
    println!("content is {:?}", content.unwrap() )。
    // 对于自定义的错误信息，使用 expect()
    // 这不是处理可恢复错误的最好方法。
    let content: Result<String, io::Error> = fs::read_to_string("file-x.txt"); 
    println!("content is {:?}", content.expect("failed reading file"));
}
```

输出
```

content is "42\n"
thread 'main' panicked at 'failed reading file: Os { code: 2, kind: NotFound, message: "No such file or directory" }', src/main.rs:35:41
```