# 所有权

```rust
fn main() {
    /* need to clean up allocated memory blocks no longer needed
    in C/C++: malloc() and free() for manual memory mngt
    other approach is garbage collection which is automatic */ /*
    Rust uses OWNERSHIP ystem:
       - variables are responsible for freeing their own resources
       - every value is owned by only one variable at a time
       - when owning variable goes out of scope the value is dropped
       - there are ways to transfer ownership of a value from one variable to another
    */ 
    let outer_planet: String;
    let outer_galaxy: String;
    let outer_planet_position: i32; 
    // inner code block scope 
    {
        let inner_planet = String::from("Mercury");
        println!("inner_planet is {}", inner_planet); 
        /*
        because ownership mandates only one owner per value/data,
         - inner_planet will no longer point to the String value on the heap
         - transferring ownership from one variable to another is called a "move" in Rust
         - this means that NO shallow copy of data STORED ON THE HEAP in Rust
            (shallow copy = several variables pointing to same data in memory)
        */ 
        // transferring ownership
        outer_planet = inner_planet; 
        // can no longer use inner_planet variable after the move of ownership of string data
        // println!("inner_planet is {}", inner_planet); 
        // => will panic 
        let mut inner_galaxy = String::from("Milky Way");
        println!("inner_galaxy is {}", inner_galaxy); 
        // to duplicate data stored on the heap, creates a deep copy of the String data

        outer_galaxy = inner_galaxy.clone(); 
        inner_galaxy.clear();
        println!("inner_galaxy is now: {}", inner_galaxy);
        println!("outer_galaxy is {}", outer_galaxy); 
        // integer data types live on the stack 
        let mut inner_planet_position = 1;
        println!("inner_planet_position is {}", inner_planet_position);
        /*
        a copy of the integer data is created for the outer_planet_position
        - ownership is respected (no shallow copy - only one variable per value at a time) - generally STACK-ONLY data types (ie fixed size) are implicitly copied
            when variable containing them is assigned to another variable - data types stored om stack implement the trait that allow them to be copied rather than moved
        */ 
        outer_planet_position = inner_planet_position;
        inner_planet_position += 4; 
        println!("inner_planet_position is {}", inner_planet_position); 
        println!("outer_planet_position is {}", outer_planet_position); 
    } 
    println!("\nouter_planet is {}", outer_planet);
    println!("outer_galaxy is {}", outer_galaxy);
    println!("outer_planet_position is {}", outer_planet_position);
}
```
Output
```
inner_planet is Mercury
inner_galaxy is Milky Way
inner_galaxy is now:
outer_galaxy is Milky Way
inner_planet_position is 1
inner_planet_position is 5
outer_planet_position is 1
```
More examples:
```rust
fn main() {
    let mut arr_1: [u8; 2] = [33, 66]; 
    // ////////////////
    // fixed-length types (stored on the stack) are COPIED
    // //////////////// 
    let arr_2 = arr_1;
    println!("arr_1 is {:?}", arr_1);
    arr_1 = [1, 2];
    println!("arr_1 is now {:?}", arr_1);
    println!("arr_2 is {:?}", arr_2); 
    // ////////////////
    // mutable-length type values move the ownership to new variable
    // //////////////// 
    let vec_1 = vec![3, 4];
    let vec_2 = vec_1; 
    // can no longer use the variable which ownership has been "moved" 
    // println!("vec_1 is {:?}", vec_1); 
    // => wll panic println!("vec_2 is {:?}", vec_2); 
    // to borrow value owned by a variable without moving ownership,
    // use a reference to that value let vec_4 = vec![5, 6, 7]; 
    // borrowing value using a reference (&<NAME>) 
    let vec_5 = &vec_4;
    println!("vec_4 is {:?}", vec_4);
    println!("vec_5 is {:?}", vec_5);
}
```

Output
```
Output
arr_1 is [33, 66]
arr_1 is now [1, 2]
arr_2 is [33, 66]
vec_2 is [3, 4]
vec_4 is [5, 6, 7]
vec_5 is [5, 6, 7]
```