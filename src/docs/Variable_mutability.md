# 变量可变性

```rust
fn main() {
    let car = "Mitsubishi";
    println!("car is a {}", car); 
    // code block, has its own scope 
    {
        // varable shadowing
        let car = 1;
        println!("car is a {}", car);
    } 
    println!("car is a {}", car);
}
```
Output
```
car is a Mitsubishi
car is a 1
car is a Mitsubishi
```