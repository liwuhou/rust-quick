# 借用

All this stuff about ownership is great but what if you don't need to transfer ownership, you just need the data:
```rust
fn main() {
    
// BORROWING: access data without taking ownership 
// create a reference to the variable you want to borrow
    
// using borrow operator "&" 
let rocket_fuel = String::from("MU-RF"); 
// notice the borrow operator to create a reference
    
// the function expects a reference, not a value 
let length = process_fuel(&rocket_fuel); 
println!("rocket_fuel is {}, length: {}", rocket_fuel,length);
}
// notice the borrow operator in parameter type

// we expect propellant to be a reference to a string,

// not a string value (/pointer to it...)
fn process_fuel(propellant: &String) -> usize {
    
// propellant is a reference to the variable that points to the string data, to borrow the data 
// again, NO SHALLOW COPY here because propellant borrows the pointer, it does contain the pointer itself (let's say that it's a pointer to another pointer...) 
println!("Processing propellant {}", propellant);
    let length = propellant.len();
    length 
// when the propellant variable goes out of scope at the end of the function,
    
// the string data is still on the heap because it remains owned by the original variable (rocket_fuel) 
    }
```
Output
```

Processing propellant MU-RF
rocket_fuel is MU-RF, lenght: 5

In Rust, data will most often be passed by reference (borrowed)than by value (ownership transfer). But you still need to know which variable really owns the data.
```