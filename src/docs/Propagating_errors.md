# 传播的错误

```rust
use std::fs;
use std::io;
fn read_and_combine(f1: &str, f2: &str) -> Result<String, io::Error> {
    let mut s1 = match fs::read_to_string(f1) {
        Ok(s) => s,
        //将错误传播给调用者
        Err(e) => return Err(e),
    }; 
    // Rust提供了一种用于传播错误的速记语法
    // 移除匹配表达式
    // 并在结果枚举后面加上一个问号（?）。
    // 这等同于上面的语法
    //"？"只能用于返回结果枚举的函数。
    let s2 = fs::read_to_string(f2)?; 
    s1.push('\n');
    s1.push_str(&s2);
    Ok(s1)
}
fn main() {
    match read_and_combine("file1.txt", "file2.txt") {
        Ok(text_result) => println!("result is:\n{}", text_result),
        Err(e) => println!("Got error: {}", e),
    };
}
```
输出
```

Got error: No such file or directory (os error 2)
```