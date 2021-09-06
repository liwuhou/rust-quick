# 转让所有权（存储在堆上的数据)

```rust
fn main() {
    let rocket_fuel = String::from("MU-RF");
    process_fuel(rocket_fuel); // the ownership of the string has moved to propellant variable,

    // the following code will panic because rocket_fuel ownership is done so you can no longuer use the variable // println!("rocket_fuel is {}", rocket_fuel);
}/*
    - because propellant is String so lives on the HEAP
    - data stored on heap when passed as argument to function,
    - the function local variable gets a pointer to the data passed
    - and therefore the local function variable gets ownership of the data.
*/
fn process_fuel(propellant: String) {
    // propellant takes ownership of the String data stored on the heap println!("Processing propellant {}", propellant);
}
```
输出
```
Processing propellant MU-RF
```

> Note: A thing to remember as a Node.js developer is that variables associated to mutable-length data (aka stored on the heap) do NOT contain the data itself but a pointer to that data in memory. The pointer is a reference to the data but NOT the data itself either, it describes the data and how it can be retrieved.

To keep the ownership of the string by the rocket_fuel variable, you can clone the data:
```rust
fn main() {
    let rocket_fuel = String::from("MU-RF"); // ownership of the string his kept by rocket_fuel variable, // a clone/copy of the string data is passed as argument process_fuel( rocket_fuel.clone() );

    // no panic because rocket_fuel stills own the string data println!("rocket_fuel is {}", rocket_fuel);
}
fn process_fuel(propellant: String) {
    // propellant takes ownership of the String data clone // mutations on the clone of course will not affect the original data (but remember that you will need to declare mut in function signature) println!("Processing propellant {}", propellant);
}
```
Ouput
```
Processing propellant MU-RF
rocket_fuel is MU-RF
```
If you do not want to copy the data and need the original variable to keep ownership of the data, then you can pass ownership back when the function is done:
```rust
fn main() {
    let mut rocket_fuel = String::from("MU-RF"); // of course, you can declare again without mut rocket_fuel = process_fuel(rocket_fuel); println!("rocket_fuel is {}", rocket_fuel);
}// notice the mut on the parameter declaration, to be able to mutate the data passed inside the function scope// notice the String return type and the last line without a semicolonfn process_fuel(mut propellant: String) -> String {
    println!("Processing propellant {}", propellant);

    propellant.push_str("-super");

    propellant
}
```
Ouput
```
Processing propellant MU-RF
rocket_fuel is MU-RF-super
```