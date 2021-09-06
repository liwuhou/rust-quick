# 闭包
```rust
fn main() {
    
    // 闭包是匿名函数，可以访问包围范围内的变量。
    // 长形式
    let double = |n1: u8| -> u8 { n1 * 2 }; 
    // 短形式
    let triple = |n1| n1 * 3; 
    const DAYS_IN_YEAR: u16 = 365; 
    //从封闭的作用域引用变量
    let quadruple_than_add_number_days_in_year = |n1: i32| n1 * 4 + (DAYS_IN_YEAR as i32);
    const FACTOR: i32 = 22;
    let multiple_by_22 = |x| FACTOR * x; 
    println!("{}", double(11));
    println!("{}", triple(99));
    println!("{}", quadruple_than_add_number_days_in_year(44));
    println!("{}", multiple_by_22(5));
}
```
输出
```
22
297
541
110
```