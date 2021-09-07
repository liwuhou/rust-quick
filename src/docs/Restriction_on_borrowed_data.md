# 借用的数据限制
一旦你为一个变量创建了一个可变的引用，你就不能在同一范围内为它创建其他引用。

这可以防止数据竞赛，因为当多个引用可以访问和变异相同的数据时，会发生数据竞赛。

在编写处理多线程并发执行的程序时，数据竞赛是一个常见的问题
（不管是什么编程语言---即使是使用Node.js的JavaScript[它应该是单线程的......但高级用例允许多处理和多线程......了解你的工具！] ）。]).

这种限制允许Rust在编译时防止数据竞赛。

总结一下（注意大括号表示不同的作用域）。
```rust
fn main() {
    
// IMMUTABLE引用 = 每个范围内你想要多少就有多少 
    {
        let something = String::from("a thing"); 
        let one_ref = &something;
        let another_ref = &something;
        let some_ither_ref = &something; 
        println!("{:?}", (one_ref, another_ref, some_ither_ref));
    } 
// MUTABLE引用 = 每个范围一个 
    {
        let mut something_changing = String::from("another thing"); 
        let the_one_and_only_ref = &mut something_changing; 
// 不能创建对 "something_changing "的其他引用。
        
// 不管是可变的还是不可变的 
// 以下情况会使程序惊慌失措
        
// 
        let trying_ref = &something_changing;
        
// 
        let trying_other_ref = &mut something_changing; 
        println!("It's only {}", the_one_and_only_ref);
    }
}
```
输出
```
("a thing", "a thing", "a thing")
It's only another thing
```