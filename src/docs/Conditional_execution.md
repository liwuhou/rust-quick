# 条件执行

```rust

fn main() {
    let x = 5;
    if x == 5 {
        println!("x is 5");
    } 
    // 如果表达式（相当于JS/Node.js中的三元运算符）。
    let x_odd = if x % 2 == 0 { "odd" } else { "even" };
    println!("x_odd is {}", x_odd);
}
```
输出
```
x is 5
x_odd is even
```