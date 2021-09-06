# 匹配选项

```rust
fn main() {
    let countdown = [5, 4, 3, 2, 1]; 
    let item = countdown.get(5);
    println!("item is {:?}", item); 
    let item = countdown.get(0);
    println!("item is {:?}", item); 
    let item = countdown.get(3); 
    // 使用匹配表达式来返回值
    let item = match item {
        Some(value) => value + 1,
        None => 0,
    };
    println!("item is {:?}", item); 
    let item = countdown.get(20);
    let item = match item {
        Some(value) => value + 1,
        None => 0,
    };
    println!("item is {:?}", item);
}
```
输出
```

item is None
item is Some(5)
item is 3
item is 0
```