# 静态生命周期
```rust
// '静态寿命
// 表示在程序的整个持续时间内都可以引用。
// 例如：一个字符串字头被存储在程序的二进制文件中。
// 所以它永远不会消失
// 数据从开始到结束都是可用的
// 所有的字符串字头都有一个静态寿命。
// let literal: &'static str = "I am a string slice";
// 将永远不会失效，并且比其他寿命长。
// '静态寿命是一个特性的约束
// 确保数据类型只包含 "静态元素"。
// 这样，接收者就可以抓住它
// 并一直使用它，因为他们知道它将永远不会失效。
// <T: Display + 'static>
fn get_toto<'a>() -> &'a str {
    "toto here"
}
fn main() {
  let toto: &'static str = get_toto();
  println!("toto is {}", toto);
}
```

输出
```
toto is toto here
```