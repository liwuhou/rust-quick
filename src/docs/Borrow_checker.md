# 借用检查

```rust
// borrow checker
// compares scopes to determine whether all borrows are valid
// lifetime (how long it is alive) of variables annotated like " 'a "

// the lifetime of a variable is related to its scope
// Rust analyses the scope / lifetime of the values referenced by a variable

// using the borrow checker
fn main() {
    let fuel; 
// ========= START lifetime ('a) of fuel ========== 
    {
        let gasoil = String::from("gasoil"); 
// ===== START lifetime ('b) of gasoil ======= 
        fuel = &gasoil; 
        println!("fuel is {}", fuel);
    } 
// ========= END lifetime of gasoil ================
} 
// ========= END lifetime of fuel ================
```
Error detected by the borrow checker:

```rust
fn main() {
    let fuel; 
// ========= START 'a ================ 
    {

        let gasoil = String::from("gasoil"); 
// ===== START 'b ===== 
        fuel = &gasoil; 
    } 
// ========= END 'b ================

    
// fuel stores a borrowed reference to gasoil
    
// gasoil lifetime is done
    
// fuel contains a dangling reference, the program will not compile 
    println!("fuel is {}", fuel);
} 
// ========= END 'a ================
```
Fixing the lifetime error by extending the lifetime of gasoil:
```rust
fn main() {
    let fuel; 
// ========= START 'a ================ 
let gasoil = String::from("gasoil"); 
// ======= START 'b ======== 
{
        fuel = &gasoil;
    }

    println!("fuel is {}", fuel);} 
// ========= END 'a and 'b ================

```
Output
```
fuel is gasoil
```