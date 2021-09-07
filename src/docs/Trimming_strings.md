# 裁剪字符串

```rust

fn main() {
    let test1 = "This is test1.        ";
    assert_eq!(trim_space(&test1), "This is test1."); let test2 = "        This is test2.";
    assert_eq!(trim_space(&test2), "This is test2."); let test3 = "        This is test3.               ";
    assert_eq!(trim_space(&test3), "This is test3."); let test4 = "This is test4.";
    assert_eq!(trim_space(&test4), "This is test4."); let test5 = "        ";
    assert_eq!(trim_space(&test5), ""); let test6 = "";
    assert_eq!(trim_space(&test6), ""); let test7 = "    😸   ";
    assert_eq!(trim_space(&test7), "😸"); let test8 = "     😸😸 test8.   ";
    assert_eq!(trim_space(&test8), "😸😸 test8."); let test9 = "     😸😸 test9. 😸😸   ";
    assert_eq!(trim_space(&test9), "😸😸 test9. 😸😸"); 
    // 注意：Rust中的字符串有一个trim()方法 
    let test10 = " 😸This is the last test😸.😸      ";
    let trimmed_message = test10.trim();
    assert_eq!(trimmed_message, "😸This is the last test😸.😸");
}
fn trim_space(s: &str) -> &str {
    let bytes = s.as_bytes();
    let mut result = ""; 
    //通过寻找第一个非空格字符来修剪前面的空格 
    // 遍历字符串片段的字节表示法
    // 我们这样做是因为我们使用了中间的字符串片断 
    for (index, &item) in bytes.iter().enumerate() {
        if item != b' ' {
            result = &s[index..];
            break;
        }
    } 
    let bytes = result.as_bytes(); 
    //通过查找最后一个非空格字符来修剪尾部的空格 
    for t in bytes.iter().enumerate() {
        let index = t.0;
        let reverse_index = result.len() - index;
        if bytes[reverse_index - 1] != b' ' {
            result = &result[..reverse_index];
            break;
        }
    } 
    result
}
```
其他解决方案:
```rust
fn trim_space(s: &str) -> &str {
    let mut start = 0;
    let mut end = 0; 
    // 遍历字符串片断的字符 
    for (index, character) in s.chars().enumerate() {
        if character != ' ' {
            start = index;
            break;
        }
    } 
    for (index, character) in s.chars().rev().enumerate() {
        if character != ' ' {
            end = s.len() - index;
            break;
        }
    } 
    &s[start..end]
}
```