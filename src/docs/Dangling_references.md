# 未知引用

```rust
fn main() {
    let everything = create_something(); 
    // "everything "是一个陈旧的引用，指向什么都没有。
    // 程序将无法编译 
    println!("everything is {}", everything);
}
// notice the return type
fn create_something() -> &String {
    let new_thing = String::from("new in town"); 
    // 这是一个悬空的引用，因为。
    因为: // new_thing在函数结束时已经超出了范围。
    // 返回对该变量的引用是没有意义的
    // 因为数据已经从内存中删除了，因为它不再属于一个变量了。
    &new_thing
}
```
输出
```
程序将无法编译，因为存在悬空引用。解决办法是对创建的字符串而不是对它的引用。
```

```rust
fn main() {
    let everything = create_something();
    println!("everything is {}", everything);
}
fn create_something() -> String {
    let new_thing = String::from("new in town");
    new_thing
}
```

输出
```
everything is new in town
```