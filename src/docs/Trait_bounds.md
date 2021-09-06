# 特性界限
```rust
// 当使用泛型时，我们可以使用特质。
// 来规定具体类型必须实现哪些功能。
// 特质的界限迫使泛型必须实现特定的特质。
// 特质边界保证了泛型将拥有必要的行为，使用core::fmt::Debug。
use std::any;
// 为了能够打印一个项目，它必须实现 "显示 "特质。
// 但由于不是所有的类型都实现了它，我们将使用Debug特性
// 这是更常见的默认实现方式
fn print_type<T: Debug>(it: T) {
    // type_name()将一个类型的名称作为一个字符串片断返回
    //通过将类型传递给turbofish操作符（::<MY_TYPE>）来实现。
    println!("{:?} is a {}", it, any::type_name::<T>());
}
fn main() {
    print_type(1);
    print_type(1.2);
    print_type([12, 34]);
}
```
输出
```
1 is a i32
1.2 is a f64
[12, 34] is a [i32; 2]

```