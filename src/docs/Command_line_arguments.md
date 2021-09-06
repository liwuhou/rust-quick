# 命令行参数
```rust
use std::env;
fn main() {
    // check for required number of arguments
     if env::args().len() <= 2 {
        println!("this program requires at least two arguments");
        return;
    }
     // args() returns an iterator over arguments passed to the program executable binary file
    // use enumerate() to get input args and their index
    // first argument is the executable path (but not always) 
    for (index, arg) in env::args().enumerate() {
        println!("argument {} is {}", index, arg);
    }
     // get argument at specific index 
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