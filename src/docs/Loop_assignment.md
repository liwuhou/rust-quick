# 循环赋值

```rust
fn main() {
    let mut count = 0;
     // 无限循环 
     loop {
        if count == 10 {
            break;
        }
        count += 1;
        println!("count is {}", count);
    }
     println!("\nAfter first loop.\n");
     //从循环表达式中返回一个值 
     let result = loop {
        if count == 15 {
            // 用break语句返回一个值 
            break count * 20;
        }
        count += 1;
        println!("count is {}", count);
    }; 
    println!("\nAfter second loop, result is {}", result);
}
```

输出
```
count is 1
count is 2
count is 3
count is 4
count is 5
count is 6
count is 7
count is 8
count is 9
count is 10After first loop.count is 11
count is 12
count is 13
count is 14
count is 15After second loop, result is 300
```