# 打印输出


In Rust, you use what is called a [macro](https://en.wikipedia.org/wiki/Macro_(computer_science)) to print to the console. Macros in Rust have an identifier followed by an exclamation mark (!). The println! macro is very flexible:
```rust
fn main() { // string interpolation 
println!("Adding {} and {} gives {}", 22, 33, 22 + 33);
// positional arguments 
println!(
        "Ypur name is {0}. Welcome to {1}. Nice to meet you {0}",
        "Goto", "Rust"
   );
    // named arguments
     println!(
        "{language} is very popular. It was created in {year}",
        language = "Rust",
        year = 2010
   );
   // placeholder traits (using positional argument to avoid repeat) 
   println!("{0}, in binary: {0:b}, in hexadecimal: {0:x}", 11);
    // debug trait (very useful to print anything)
     // if you try to print the array directly, you will get an error
  // because an array is not a string or number type
   println!("{:?}", [11, 22, 33]);
  }
```
To see the output, run:
```
cargo run
```
you will see (along info about compilation of the code --- Rust is a compiled language):
```
Adding 22 and 33 gives 55
Ypur name is Goto. Welcome to Rust. Nice to meet you Goto
Rust is very popular. It was created in 2010
Decimal: 11      Binary: 1011    Hexadecimal: b
[11, 22, 33]
```
In Rust, you must use semicolons (;) at the end of a line unless it is the last line of a function that returns something (more on that later).