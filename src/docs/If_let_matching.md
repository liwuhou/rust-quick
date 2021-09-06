# if let 匹配
```rust
 
// if let 格式
// 用于只匹配一个值
fn main() {
    let number = Some(1); 
// 注意这个写法：
    
// if let PATTERN = VALUE {} 
    if let Some(1) = number {
        println!("You are the one");
    }
}
```

输出

```

You are the one
```