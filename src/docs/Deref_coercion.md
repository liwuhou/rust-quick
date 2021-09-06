# Deref 解构

注意。

- 传递一个借来的字符串引用（&String）与传递一个字符串片断（&str）是不一样的。
- 借用的字符串引用指向堆栈中的字符串，而堆栈又拥有并指向堆中的数据
- slice只存储一个指向堆数据的指针和长度信息。它并不跟踪容量，因为它并不拥有堆上的任何东西。
- 由于字符串引用包含了作为一个片断的所有信息（指向堆数据的指针+长度），Rust允许在预期有字符串片断的地方使用字符串引用。
- 这种便利被称为 deref coercion。
```rust
fn main() {
    let message = String::from("lorem ipsum");

    // 注意到一个字符串引用被作为参数传入 
    let first_word = get_first_word(&message);
    println!("first_word is \"{}\"", first_word);
}
// 注意到预期的参数是字符串类型的slice (&str)。
fn get_first_word(msg: &str) -> &str {
    let bytes: &[u8] = msg.as_bytes();
    for (index, &item) in bytes.iter().enumerate() {
        if item == b' ' {
            return &msg[..index];
        }
    }
    &msg
}
```

- 当然，当使用字符串片时，deref coercion不起作用，因为字符串引用是预期的（因为缺少属性）。
- 当编写代码时，在不需要数据所有权的情况下，最好使用字符串片。