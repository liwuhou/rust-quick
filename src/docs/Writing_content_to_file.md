# 向文件中写入内容

-  新建一个名为 fruits.txt的纯文本文件，内容如下：记得放在项目的目录下面。 
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

```rust
use std::fs;
use std::path;
// 导入写 特性，它位于Prelude 类里面，更多的特性在后面
use std::io::prelude::*;
fn main() {
    let path = path::Path::new("./file.txt"); 
    let mut contents = String::new();
    contents.push_str("this is line 1\n");
    contents.push_str("this is line 2\n");
    contents.push_str("this is line 3\n"); 
// === 写/替换文件 
content === fs::write(path, contents)
       .expect("Failed to write to file."); 
// === 追加内容到文件  === 
let path = path::Path::new("./fruits.txt"); 
// 初始化一个新的fs模块的 OpenOptions 选项

let mut file = fs::OpenOptions::new()
        .append(true)
        .open(path)
        .expect("Failed to open file."); 
// 使用已导入的Wrie特性 
// 期望参数是一个字节的数组
// 注意字符串数据类型前面加b，表示转换成一个字节数组

file.write(b"\nolive\n")
        .expect("Failed to write to file.");
}
```