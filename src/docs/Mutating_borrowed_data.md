# 改变借用数据

```rust
fn main() {
    // notice it is a mutable variable let mut rocket_fuel = String::from("MU-RF"); // notice we pass a mutable reference (&mut <TYPE>) let length = process_fuel(&mut rocket_fuel); println!("rocket_fuel is {}, length: {}", rocket_fuel, length);
}// notice the &mut in the parameter list
// we expect propellant to be a mutable reference to a Stringfn process_fuel(propellant: &mut String) -> usize {
    println!("Processing propellant {}", propellant); // mutating borrowed data propellant.push_str("333"); let length = propellant.len();
    length
}
```
Output
```
Processing propellant MU-RF
rocket_fuel is MU-RF333, lenght: 8
```