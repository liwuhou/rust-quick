# Crates

-   collection of source code files
-   crates registry: [crates.io](https://crates.io/)
    (equivalent to [npmjs.com](https://www.npmjs.com/) for Node.js modules)
-   two kinds:
    - binary crates
    contain the source code to compile to execute the program
    - library crates
    contain code for other programs to execute
-   to use third-party crates, add the crate name and version in the Cargo.toml file in the [dependencies] section (external crates):
```yml
[package]
name = "crates"
version = "0.1.0"
authors = ["Florian GOTO <<you@example.com>>"]
edition = "2018"# See more keys and their definitions at <https:
//doc.rust-lang.org/cargo/reference/manifest.html>[dependencies]
# add the random number generation crate
rand = "0.8.3"
```
-   Cargo will automatically download the crates in the [dependencies] section along with their own dependencies before compiling
-   to use the downloaded crate
```rust
use rand;
fn main() {
  let random_number = rand::random::<u8>();
  println!("random_number is {}", random_number);
}
```
输出
```
random_number is 97
```

-   if you use a specific function of a crate, specify it directly in the use statement (the compiler will warn you about name collisions with locally defined code):

```rust
// import only the random() function of the rand crateuse rand::random;
// import everything from the rand crate prelude

 use rand::prelude::*;
 fn main() {
  let random_number = random::<u8>();
  println!("random_number is {}", random_number);
}
// cannot have a local function named random in the same scope

// the program will not compile if the following code is added because of the name collision
 fn random() -> u8 {

//   123

 }
```