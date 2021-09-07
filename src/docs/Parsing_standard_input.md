# 解析标准输入

```rust

// 读取命令行的输入值
std::io;
fn main() {
  let mut buffer = String::new();
  println!("Enter your name:"); 
// ===== 访问stdin流 ===== 
// read_line()函数将用输入的字符串更新缓冲区。
  
// read_line()函数阻止程序的执行，直到有人在命令行上输入东西为止 
  let read_line_result = io::stdin().read_line(&mut buffer);
  println!("read_line_result is {:?}", read_line_result); 
  println!("Welcome to Rust, {}", buffer); 
// ===== 解析输入字符串 ======== 
// 清除之前输入的缓冲区
  buffer.clear(); 
  println!("Enter the year when you started learning Rust:"); 
  let read_line_result = io::stdin().read_line(&mut buffer);
  println!("read_line_result is {:?}", read_line_result); 
// 需要对输入的字符串进行修剪，因为在结尾处包含一个换行。
  
// 注意Turbofish操作符（::<i32>）表示要从输入字符串中解析的数据类型（这里是一个i32整数）。
// parse()返回一个结果枚举。
  
// 结果枚举允许处理错误（后面会有更多介绍
  
// 使用unwrap函数来提取值 
  let start_year = buffer.trim().parse::<i32>().unwrap();
  println!("You started your Rust journey in {}", start_year); 
//不使用turbofish操作符，将目标类型表示为变量类型 
  let start_year: i32 = buffer.trim().parse().unwrap();
  println!("You will be an expert in {}", start_year + 5);
}
```
输出 (> 后面表示命令行输入)
```
Enter your name:
> Florian
read_line_result is Ok(8)
Welcome to Rust, FlorianEnter the year when you started learning Rust:
> 2021
read_line_result is Ok(6)
You started your Rust journey in 2021
You will be an expert in 2026
```