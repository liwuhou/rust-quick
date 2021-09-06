# 字符

```rust
fn main() {
  //Unicode标量值使用4个字节（32位）存储。
    // 与C语言相反，C语言将其存储在1个字节中
    let letter: char = 'z';
    let number_char = '9';
    let finger = '\u{261D}'; println!("letter is {}", letter);
    println!("number_char is {}", number_char);
    println!("finger is {}", finger);
}
```
输出
```
letter is z
number_char is 9
finger is ☝
```