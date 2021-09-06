# 字符

```rust
fn main() {
    // Unicode scalar value stored using 4 bytes (32 bits)
    // contrary to C like languages that store it in 1 byte
    let letter: char = 'z';
    let number_char = '9';
    let finger = '\u{261D}'; println!("letter is {}", letter);
    println!("number_char is {}", number_char);
    println!("finger is {}", finger);
}
```
Output
```
letter is z
number_char is 9
finger is ☝
```