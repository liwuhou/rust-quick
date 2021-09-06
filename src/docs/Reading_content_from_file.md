# 自文件中读取内容


-   create a fruits.txt file in your project folder with the following content:
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
    let path = Path::new("./fruits.txt"); let contents = fs::read_to_string(path)
                      .expect("Failed to read file."); println!("contents is: {}", contents); // process individual lines for line in contents.lines() {
        println!("line is {}", line);
    } // read file as bytes let contents: Vec<u8> = fs::read(path)
                               .expect("Failed to read file."); println!("\ncontents is: {:?}", contents);
}
```
Output
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