# 转让所有权（存储在堆上的数据)

```rust
fn main() {
    let rocket_fuel = String::from("MU-RF");
    process_fuel(rocket_fuel); 
    //字符串的所有权已经转移到了推进剂变量上。

    // 下面的代码会出现恐慌，因为火箭燃料的所有权已经被剥夺，所以你不能再使用这个变量。
    println!("rocket_fuel is {}", rocket_fuel);
}
/*
    - 因为推进剂是字符串，所以存在于HEAP中。
    - 当作为参数传递给函数时，数据存储在堆中。
    - 函数的局部变量得到一个指向所传递数据的指针
    - 因此，本地函数变量获得了数据的所有权。
*/
fn process_fuel(propellant: String) {
    //推进器对存储在堆上的字符串数据拥有所有权 
    println!("Processing propellant {}", propellant);
}
```
输出
```
Processing propellant MU-RF
```

> 注意：作为一个Node.js开发者，需要记住的是，与可变长度数据相关的变量（又称存储在堆上的变量）并不包含数据本身，而是一个指向内存中数据的指针。指针是对数据的引用，但也不是数据本身，它描述了数据以及如何检索它。

为了保持Rocket_fuel变量对该字符串的所有权，你可以克隆该数据。
```rust
fn main() {
    let rocket_fuel = String::from("MU-RF"); 
    //字符串的所有权由rocket_fuel变量保存。
    //字符串数据的克隆/拷贝作为参数被传递。
    process_fuel( rocket_fuel.clone() );

    // 没有panic，因为Rocket_fuel仍然拥有字符串数据。
    println!("rocket_fuel is {}", rocket_fuel);
}
fn process_fuel(propellant: String) {
    // 推进器对克隆的字符串数据拥有所有权 
    // 克隆上的突变当然不会影响原始数据（但请记住，你需要在函数签名中声明突变）。
    println!("Processing propellant {}", propellant);
}
```
输出
```
Processing propellant MU-RF
rocket_fuel is MU-RF
```
如果你不想复制数据，需要原始变量保持数据的所有权，那么你可以在函数完成后将所有权传回。
```rust
fn main() {
    let mut rocket_fuel = String::from("MU-RF"); 
    // 当然，你可以再次声明，而不需要Mut 
    rocket_fuel = process_fuel(rocket_fuel); 
    println!("rocket_fuel is {}", rocket_fuel);
}
// 注意参数声明中的 mut，以便能够对函数范围内传递的数据进行变异。
// 注意字符串的返回类型和最后一行没有分号。
fn process_fuel(mut propellant: String) -> String {
    println!("Processing propellant {}", propellant);

    propellant.push_str("-super");

    propellant
}
```
输出
```
Processing propellant MU-RF
rocket_fuel is MU-RF-super
```