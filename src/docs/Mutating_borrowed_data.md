# 改变借用数据

```rust
fn main() {
    // 注意它是一个可变的变量 
    let mut rocket_fuel = String::from("MU-RF"); 
    // 注意我们传递了一个可变的引用（&mut <TYPE>）。
    let length = process_fuel(&mut rocket_fuel); 
    println!("rocket_fuel is {}, length: {}", rocket_fuel, length);
}
// 注意参数列表中的&mut
// 我们希望propellant是一个对String的可变引用
fn process_fuel(propellant: &mut String) -> usize {
    println!("Processing propellant {}", propellant); 
    //突变借来的数据 
    propellant.push_str("333"); 
    let length = propellant.len();
    length
}
```
输出
```
Processing propellant MU-RF
rocket_fuel is MU-RF333, lenght: 8
```