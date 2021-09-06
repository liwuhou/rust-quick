# 多重特质界限和where子句

```rust
use std::fmt::Display;
// 多个特质边界用+运算符隔开

// PartialEq/From/Copy是std库前奏的一部分，所以没有导入。
//
 //fn compare_and_print<T: Display + PartialEq + From<U>, U: Display + PartialEq + Copy>(a: T, b: U) {
// 下面的函数签名与上面的函数签名是等价的

// 但用were子句来声明特质的边界，更具有可读性
fn compare_and_print<T, U>(a: T, b: U)
where
    T: Display + PartialEq + From<U>,
    U: Display + PartialEq + Copy,
{
    
// 
T::from(b) => convert b to type T
    
// From trait允许一个类型
    
// 来定义如何从另一个类型创建自己。
    
// 例如：从字符串片断中创建一个字符串。
    
//      
String::From("ttoto") if a == T::from(b) {
        println!("{} is equal to {}", a, b);
    } else {
        println!("{} is not equal to {}", a, b);
    }
}
fn main() {
    compare_and_print(22, 55);
    compare_and_print(2.2, 2.2);
}
```
输出
```
22 is not equal to 55
2.2 is equal to 2.2
```