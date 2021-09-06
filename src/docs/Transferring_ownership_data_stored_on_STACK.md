# 转让所有权（存储在STACK上的数据）

```rust
fn main() {
    let rocket_fuel = 1;
    process_fuel(rocket_fuel);
    println!("rocket_fuel is {}", rocket_fuel);
}
/*
    - because propellant is i32 so lives on the stack,
    the value passed as argument is COPIED jn fn scope
    - to be able to modify the copy inside the function scope, use the mut keyword
*/
fn process_fuel(mut propellant: i32) {
    // the copy is modified 
    propellant += 2;
    println!("Processing propellant {}", propellant);
}
```
输出
```
Processing propellant 3
rocket_fuel is 1
```