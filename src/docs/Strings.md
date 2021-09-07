# 字符串

Rust has two kinds of string types.

```rust

fn main() {
    
// 两种类型的字符串表示。

    
// - 字符串：硬编码到可执行文件中。
    
// 这些是不可改变的，在编译前必须知道。

    
// - 字符串类型：在堆上分配的数据，\n/tmutable，在运行时动态生成。
// 存储在堆上的字符串字面意义 
// String::from() 从一个字符串字面内容中创建一个字符串类型。
//序列[m,a,r,s]将被存储在堆中。
// 为了访问存储在堆中的字符串，程序在堆中持有一个指针（消息变量）。
// 栈上的指针包括第一个字符的内存地址、字符串的长度和容量，这样你就知道在堆上为它分配了多少内存。
let mut message = String::from("Jupiter");
    println!("message is {}", message); 
//将字符串附加到原始的字符串上 
// 如果需要的内存大于容量，指针地址以及长度和容量就会更新，以反映内存中的新位置。
 message.push_str(" is smoke and mirrors");
    println!("message is {}", message); 
// 推送一个字符
    message.push('!');
    println!("message is {}", message); 
// 获取长度
   println!("message lenght is {}", message.len()); 
// 获得以字节为单位的容量
   println!("message capacity is {}", message.capacity()); 
// 检查是否为空
  println!("Is empty: {}", message.is_empty()); 
// 字符串搜索
  println!("Contains smoke: {}", message.contains("smoke")); 
// 替换字符串
  println!("message is {}", message.replace("smoke","gaz")); 
// 循环处理字符串中的单词（用空白处分割）。
  for word in message.split_whitespace() {
    println!("word is {}", word);
  } 
//创建有容量的字符串
 let mut s = String::with_capacity(4); 
// 4个字节的容量
  println!("s capacity is  {} bytes", s.capacity()); 
// 消耗的是1个字节
  
// 拉丁字母通常有1个字节的大小
  
// 记住Unicode支持4字节的字符
  s.push('Q'); s.push('W'); 
// 消耗了1个字节
  s.push_str("er"); 
// 消耗了2个字节 
//超过了字符串的容量（自动增加并在内存中重新分配）。
s.push('T'); 
// 消耗1个字节
  println!("s capacity is  now {} bytes", s.capacity());
}
```
输出
```
message is Jupiter
message is Jupiter is smoke and mirrors
message is Jupiter is smoke and mirrors!
message lenght is 29
message capacity is 56
Is empty: false
Contains smoke: true
message is Jupiter is gaz and mirrors!
word is Jupiter
word is is
word is smoke
word is and
word is mirrors!
s capacity is  4 bytes
s capacity is  now 8 bytes
```