# While 循环

```rust
fn main() {
    let mut count = 0;
    let letters: [char; 5] = ['a', 'b', 'c', 'd', 'e']; while count < letters.len() {
        println!("letter[{}] is {}", count, letters[count]);
        count += 1;
    }// contrary to loop expressions, the break statement in while loop cannot return a value
}
```
Output
```
letter[0] is a
letter[1] is b
letter[2] is c
letter[3] is d
letter[4] is e
```