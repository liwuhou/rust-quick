# 算术运算

```rust
fn main() {
    // 相同的数据类型才能运算
    let a = 11;
    let b = 33;
    let c = a + b;
    println!("c is {}", c);
     let d = c - b;
    println!("d is {}", d);
     let e = a * d;
    println!("e is {}", e); 
    // 先转换成相同的数据类型再运算，记得可能会有精度损失  
    let f = c as f32 / 4.5;
    println!("f is {}", f);

     // 操作优先权控制

    let g = 43.5432 % (a as f64 * e as f64);
    println!("g is {}", g);
}
```

输出
```
c is 44
d is 11
e is 121
f is 9.777778
g is 43.5432

```