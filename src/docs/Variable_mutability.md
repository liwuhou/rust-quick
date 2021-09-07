# 变量可变性

```rust
fn main() {
    let car = "Mitsubishi";
    println!("car is a {}", car); 
    //代码块，有自己的范围 
    {
        // 变量遮罩，这里的car就跟上面的可以不一样
        let car = 1;
        println!("car is a {}", car);
    } 
    println!("car is a {}", car);
}
```
输出
```
car is a Mitsubishi
car is a 1
car is a Mitsubishi
```