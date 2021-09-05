# 多条件判断If else if

```rust
fn main() {
    let x = 2;
    let y = 5; if x > y {
        println!("x is greater than  y");
    } else if x < y {
        println!("x is less than y");
    } else {
        println!("x is equal to y");
    }
}
```
Output
```
x is less than y
```