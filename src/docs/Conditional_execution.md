# 条件执行

```rust

fn main() {
    let x = 5;
    if x == 5 {
        println!("x is 5");
    } 
    // if expressions (equivalent of ternary operator in JS/Node.js) 
    let x_odd = if x % 2 == 0 { "odd" } else { "even" };
    println!("x_odd is {}", x_odd);
}
```
Output
```
x is 5
x_odd is even
```