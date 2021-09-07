# 水果查找器


- 在你的项目文件夹中复制前几节的fruit.txt文件
- 我们将创建一个程序来寻找列表中的水果
- 如果一个水果在列表中，它将返回一条信息，说明它在列表中的位置
- 如果没有找到，则将其添加到列表中

```rust
use std::env;
use std::fs;
use std::io::prelude::*;
use std::path::Path;
fn main() {
    if env::args().len() != 3 {
        println!("This programs takes two arguments");
        std::process::exit(1);
    } 
    let file_path = env::args().nth(1).expect("Failed to get file path");
    let search_name = env::args().nth(2).expect("Failed to get search name");
    let path = Path::new(&file_path);
    let fruits = fs::read_to_string(path).expect("Failed to read file"); 
    for (index, fruit) in fruits.lines().enumerate() {
        if fruit == search_name {
            println!(
                "{} is the {}{} fruit in the list",
                search_name,
                index + 1,
                if index == 0 {
                    "st"
                } else if index == 1 {
                    "nd"
                } else if index == 2 {
                    "rd"
                } else {
                    "th"
                }
            );
            return;
        }
    } 
    println!("{} is not in the fruit list", search_name); 
    let mut file = fs::OpenOptions::new()
        .append(true)
        .open(path)
        .expect("Failed to open file."); 
    let mut new_fruit = search_name.clone(); 
    let fruits_bytes = fruits.as_bytes();
    if fruits_bytes[fruits_bytes.len() - 1] != b'\n' {
        // 在字符串的开头插入换行
        new_fruit.insert(0, '\n');
    }
    new_fruit.push('\n'); 
    file.write(new_fruit.as_bytes())
        .expect("Failed to write to file."); 
    println!("{} was added to fruit list", search_name);
}
```
输出
```
> cat fruits.txt
apple
avocado
banana
cherry
orange
mango
coconut
pear
lemon
lime
pineapple
papaya
grape
guava
kiwi
elderberry
raspberry
tomato> cargo run -q fruits.txt tomato
tomato is the 18th fruit in the list> cargo run -q fruits.txt avocado
avocado is the 2nd fruit in the list> cargo run -q fruits.txt peach
peach is not in the fruit list
peach was added to fruit listcargo run -q fruits.txt peach
peach is the 19th fruit in the list
```