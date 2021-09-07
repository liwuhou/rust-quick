# 自文件中读取内容


- 在你的项目文件夹中创建一个 fruits.txt 文件，内容如下。
```
apple
avocado
banana
cherry
orange
mango
coconut
pear
lemon
```
---

```rust
use std::fs;
use std::path::Path;fn main() {
    let path = Path::new("./fruits.txt"); 
    let contents = fs::read_to_string(path)
                      .expect("Failed to read file."); 
    println!("contents is: {}", contents); 
    //处理每一行
    for line in contents.lines() {
        println!("line is {}", line);
    } 
    // 读取文件为字节
    let contents: Vec<u8> = fs::read(path)
                               .expect("Failed to read file."); 
    println!("\ncontents is: {:?}", contents);
}
```
输出
```
contents is: apple
avocado
banana
cherry
orange
mango
coconut
pear
lemonline is apple
line is avocado
line is banana
line is cherry
line is orange
line is mango
line is coconut
line is pear
line is lemoncontents is: [97, 112, 112, 108, 101, 10, 97, 118, 111, 99, 97, 100, 111, 10, 98, 97, 110, 97, 110, 97, 10, 99, 104, 101, 114, 114, 121, 10, 111, 114, 97, 109, 103, 101, 10, 109, 97, 110, 103, 111, 10, 99, 111, 99, 111, 110, 117, 116, 10, 112, 101, 97, 114, 10, 108, 101, 109, 111, 110, 10]
```