# 切片为参数

```rust

fn main() {
    let message = String::from("lorem ipsum"); 
    let first_word = get_first_word(&message);
    println!("first_word is \"{}\"", first_word); 
    let first_word_too = get_first_word_too(&message[6..]);
    println!("first_word_too is \"{}\"", first_word_too);
}
// ======= 将整个字符串作为输入传递 ===========
fn get_first_word(msg: &String) -> &str {
    //从字符串数据中创建一个字节片（&[u8] 数据类型）。
    let bytes: &[u8] = msg.as_bytes(); 
    // 在字节序列中一个一个地迭代。
    // 迭代时使用enumerate()来获取索引
     for (index, &item) in bytes.iter().enumerate() {
        // 找到第一个空格，并将之前的所有内容作为一个字符串片断返回
         // b''是一个空格的字节表示。
        // 记住，我们是在迭代一个字节序列，而不是字符。
       // 我们这样做是因为字符串片断的索引是以字节为单位的。
       if item == b' ' {
            return &msg[..index];
       }
    } 
    // 没有发现空白处，返回整个信息 &msg
}
// ======= 传递一个字符串片断作为输入 ===========
fn get_first_word_too(msg: &str) -> &str {
    let bytes: &[u8] = msg.as_bytes(); 
    for (index, &item) in bytes.iter().enumerate() {
        if item == b' ' {
            return &msg[..index];
        }
    } 
    &msg
}
```
输出
```
first_word is "lorem"
first_word_too is "ipsum"
```