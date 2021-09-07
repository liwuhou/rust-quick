# While 循环

```rust
fn main() {
    let mut count = 0;
    let letters: [char; 5] = ['a', 'b', 'c', 'd', 'e']; 
    while count < letters.len() {
        println!("letter[{}] is {}", count, letters[count]);
        count += 1;
    }
    // 与循环表达式相反，while循环中的break语句不能返回一个值。
}
```
输出
```
letter[0] is a
letter[1] is b
letter[2] is c
letter[3] is d
letter[4] is e
```