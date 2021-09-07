# 转让所有权（存储在STACK上的数据）

```rust
fn main() {
    let rocket_fuel = 1;
    process_fuel(rocket_fuel);
    println!("rocket_fuel is {}", rocket_fuel);
}
/*
    - 因为推进剂是i32的，所以住在堆栈上。
    作为参数传递的值在fn范围内被复制。
    - 为了能够修改函数范围内的拷贝，请使用mut关键字
*/
fn process_fuel(mut propellant: i32) {
    //副本被修改 
    propellant += 2;
    println!("Processing propellant {}", propellant);
}
```
输出
```
Processing propellant 3
rocket_fuel is 1
```