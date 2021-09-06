# 多生命周期注解

```rust
// 注意这里，尽管返回类型与一个参数有相同的寿命
// 我们必须为另一个参数注解另一个生命周期
// 即使从未返回
// 以避免任何混淆
// 记住，这里的代码很简单
// 但输入和返回的值可能来自于一个已编译的库。
// 编译器不能接触到源代码。
fn get_longest_name<'a, 'b>(x: &'a str, y: &'b str) -> &'a str {
    if x.len() > y.len() {
        x
    } else {
        x
    }
}
fn main() {
    let result;
    // START 'a
    let name1 = String::from("Deep Space 9"); {
        // START 'b
        let name2 = String::from("Voyager");
        result = get_longest_name(&name1, &name2);
    } // END 'b
    println!("result is {}", result);
} // END 'a
```
输出
```
result is Deep Space 9
```