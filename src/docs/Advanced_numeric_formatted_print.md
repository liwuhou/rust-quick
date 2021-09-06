# 高级数字格式化打印

```rust
fn main() {
    let x = 246.92385;
    let y = 24.69;
    let z = x / y;

    // print line macro with 3 decimal point precision
    // 打印浮点数，带有小数点后3位精度
    println!("z is {:.3}", z);

    // 共9位数，前置用空格补位
    println!("z is {:9.3}", z);

    //用0补位
    println!("z is {:09.3}", z);
    println!("z is {:09.3}\nx is {}", z, x);
 
    // 换行
    print!("y is {:09.3}\n x is {}\n", y, x); 
    // 位置占位 
    println!("z is {0:05.1} and x is {1:.2}. \nx is also {1}", z, x)
}
```

输出
```
z is 10.001
z is    10.001
z is 00010.001
z is 00010.001
x is 246.92385
y is 00024.690
 x is 246.92385
z is 010.0 and x is 246.92.
x is also 246.92385
```