# 借用的数据限制
Once you create a mutable reference to a variable, you cannot create other references to it within that same scope.

This prevents data races which occur when multiple references can access and mutate the same data.

Data races are a common problem when writing programs handling multiple threads that execute concurrently (no matter the programming language --- even JavaScript with Node.js [ which is supposed to be single threaded...but advanced use cases allow for multiprocessing and multi-threading...know your tools! ]).

This restriction allows Rust to prevent data races at compile time.

To sum up (notice the curly braces denoting different scopes):
```rust
fn main() {
    
// IMMUTABLE references = as many as you want per scope 
{
        let something = String::from("a thing"); let one_ref = &something;
        let another_ref = &something;
        let some_ither_ref = &something; println!("{:?}", (one_ref, another_ref, some_ither_ref));
    } 
// MUTABLE references = ONE per scope 
{
        let mut something_changing = String::from("another thing"); let the_one_and_only_ref = &mut something_changing; 
// CANNOT create other references to "something_changing"
        
// NO MATTER if mutable or immutable 
// the following will make the program panic
        
// 
let trying_ref = &something_changing;
        
// 
let trying_other_ref = &mut something_changing; 
println!("It's only {}", the_one_and_only_ref);
    }
}
```
输出
```
("a thing", "a thing", "a thing")
It's only another thing
```