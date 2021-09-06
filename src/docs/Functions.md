# 函数方法

```rust

fn main() {
    be_polite(); 
// y和z的推断类型是作为add()的参数使用的类型。
    
// 如果你没有声明变量的具体类型，那么这些变量将假定为第一次使用的函数的参数类型。
// 记住，默认的推断类型是整数的i32。
    let y = 12;
    let z = 34; 
// 现在y和z被认为是u8类型，因为这就是它们第一次作为函数参数使用的方式 
    add(y, z); 
// 稍后将y和z传给另一个参数类型不同的fn，会引起panic
    
guess_number(z) 
// --> 希望是一个i32而不是一个u8
    
// 需要明确的转换。
guess_number(y as i32)
}
fn be_polite() {
    println!("Greetings, pleased to meet you.");
    guess_number(25)
}
fn guess_number(number: i32) {
    println!("Indeed, {} is the correct answer", number)
}
fn add(a: u8, b: u8) {
    let sum = a + b;
    println!("sum is {}", sum)
}
```
输出
```

Greetings, pleased to meet you.
Indeed, 25 is the correct answer
sum is 46
Indeed, 12 is the correct answer
```