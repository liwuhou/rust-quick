# 扩展匹配模式

```rust
fn main() {
    let number = 123u8; 
    // 匹配表达式根据情况返回数值
    // 匹配臂从上到下依次评估 
    let result: &str = match number {
        // 匹配臂
        0 => "zero", 
        // 匹配臂
        1 => "one", 
        // 匹配臂
        2 => "two", 
        // 通配符模式(默认情况下)
        // 用下划线符号（_）表示
        // 应该最后使用。
        // 否则，将不会对下面的部分进行评估。
        // 当你不想明确地定义所有可能的匹配臂时，这一点很有用。
        // （或者仅仅是因为存在大量或无限的可能性）。
        // 注意代码块，当超过一行的时候 
        _ => {
            println!("{} did not match any arm", number);
            "unmatched"
        }
    }; 
    println!("result is {}", result);
}
```
输出
```

123 did not match any arm
result is unmatched
```