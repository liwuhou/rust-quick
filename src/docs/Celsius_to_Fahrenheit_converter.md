# 摄氏度转换为华氏度

```rust
fn main() {
    let (celsius, farenheit) = to_farenheit(40.0);
    println!("{} celsius is {} farenheit", celsius, farenheit);
    assert_eq!(farenheit, 104.0); 
    // 如果断言失败，将不执行
    println!("test passed");
}
fn to_farenheit(celsius: f32) -> (f32, f32) {
    let farenheit = (1.8 * celsius) + 32.0; 
    // 返回语句（没有分号）
    (celsius, farenheit)
}
```