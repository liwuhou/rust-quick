# 函数方法

```rust

fn main() {
    be_polite(); 
// inferred types for y and z are the ones used as parameters of add()
    
// to be clear, if you do not declare a specific type for variables, these variables will assume the type of the arguments of the function where first used 
// remember, by the default inferred type is i32 for integers 
let y = 12;
    let z = 34; 
// now y and z are considered u8 type because this is how they are first used as function arguments 
add(y, z); 
// passing later y and z to another fn with different param types will panic
    
guess_number(z) 
// -> expects a i32 not a u8
    
// need for explicit cast: guess_number(y as i32)
}
fn be_polite() {
    println!("Greetings, pleased to meet you.");
    guess_number(25)
}
fn guess_number(number: i32) {
    println!("Indeed, {} is the correct answer", number)
}
fn add(a: u8, b: u8) {
    let sum = a + b;
    println!("sum is {}", sum)
}
```
Output
```

Greetings, pleased to meet you.
Indeed, 25 is the correct answer
sum is 46
Indeed, 12 is the correct answer
```