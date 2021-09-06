# 布尔运算和二进制代数

```rust
fn main() {
    let a = true;
    let b = false;
    println!("a is {}\nb is {}", a, b); 
    println!("NOT a is {}", !a);
    println!("a AND b is {}", a & b);
    println!("a OR b is {}", a | b);
    println!("a XOR b is {}", a ^ b); 
    // 布尔值转为整数后会产生0或1。
    println!("a XOR b is {}", (a ^ b) as i32); 
    // 1 
    let c = (a ^ b) | (a & b);
    println!("c is {}", c); 
    // 短路的逻辑操作。
    // 右边的操作数没有被评估 
    let d = true || (a & b);
    println!("d is {}", d);    
     // panic宏没有被评估。
    // 所以进程以状态0结束（OK，无错误）。
    // panic会立即退出程序（就像在Node.js中抛出错误）。
    let e = false && panic!();
    println!("e is {}", e);
}
```

输出

```
a is true
b is false
NOT a is false
a AND b is false
a OR b is true
a XOR b is true
a XOR b is 1
c is true
d is true
e is false
```