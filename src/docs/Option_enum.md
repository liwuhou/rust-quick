# 可选枚举

```rust
// 在许多语言中。
// 当在非空值的上下文中使用空值时，会发生错误。
// Rust没有一个传统的空值
// 相反，Rust使用一个名为Option的通用枚举。
// 的通用枚举，它可以有两种变体。
// 枚举Option<T> {
// Some(T)。
// None
// }
// 1) Some: 表示有一个值
// 2) None : 表示没有值
// Option枚举被包含在前缀中
fn main() {
    // 实例化一个选项枚举
    let someone: Option<i32> = Some(1);
    println!("someone is {:?}", someone);
     let something: Option<&str> = Some("thing");
    println!("something is {:?}", something); 
    let nothing: Option<i32> = None;
    println!("nothing is {:?}", nothing); 
    let countdown = [5, 4, 3, 2, 1]; 
    //在切片上使用get()来获取一个选项枚举。
    // 对指定索引处的值的一个引用
    let item = countdown.get(5);
    println!("item is {:?}", item); 
    let item = countdown.get(0);
    println!("item is {:?}", item);
     let item = countdown.get(2);
    let item = item.unwrap_or(&0) + 1;
    println!("item is {:?}", item); 
    let item = countdown.get(20); 
    // unwrap_or(&default_value)。
    // 如果变量是Option::Some，返回存储的数据
    // 如果变量是Option::None，则使用传递的参数。
    // 注意，该参数是一个引用 
    let item = item.unwrap_or(&0) + 1;
    println!("item is {:?}", item);
}
```
输出
```
someone is Some(1)
something is Some("thing")
nothing is None
item is None
item is Some(5)
item is 4
item is 1
```