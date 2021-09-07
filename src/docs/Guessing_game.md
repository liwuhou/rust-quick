# 猜数游戏

```rust
use rand::Rng;
use std::io;
fn main() {
    println!("Guess a number");
    println!("Please enter your guess:"); 
    let secret_number = rand::thread_rng().gen_range(1, 101);
    println!("The secret number is {}", secret_number); 
    // ":: "用于给定类型的关联函数（相当于OOP中的静态方法--以后会有更多的介绍）。
    // String::new() 创建一个String类型的空字符串（可增长的UTF-8编码文本）。
    let mut guess = String::new(); 
    /*
        std::io::stdin，如果你不使用文件顶部的导入的话
        std::io::stdin() 返回一个std::io::stdin类型的实例
    */ 
    io::stdin()
        .read_line(&mut guess)
        .expect("Failed to read line"); 
        println!("You guess: {}", guess);
}
```