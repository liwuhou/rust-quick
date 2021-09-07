# 命令行参数
```rust
use std::env;
fn main() {
    // 检查所需的参数数量
     if env::args().len() <= 2 {
        println!("this program requires at least two arguments");
        return;
    }
     // args()返回传递给程序可执行二进制文件的参数的迭代器
    // 使用enumerate()来获取输入参数和它们的索引
    // 第一个参数是可执行路径（但不一定）。
    for (index, arg) in env::args().enumerate() {
        println!("argument {} is {}", index, arg);
    }
     //获得特定索引的参数 
    let arg2 = env::args().nth(2).unwrap();
    println!("\narg2 is {}", arg2);
}
```

输出
```
> cargo run toto "titi.txt" --flag -targument 0 is target/debug/command_line_args
argument 1 is toto
argument 2 is titi.txt
argument 3 is --flag
argument 4 is -targ2 is titi.txt
```