# 未知引用

```rust
fn main() {
    let everything = create_something(); // "everything" is a stale reference pointing to nothing
    // the program will not compile println!("everything is {}", everything);
}// notice the return typefn create_something() -> &String {
    let new_thing = String::from("new in town"); // this is a dangling reference because:
    // new_thing goes out of scope at the end of the function
    // returning a reference to that variable does not make sense
    // because the data will have been dropped from memory because not owned anymore by a variable &new_thing
}
```
输出

program will not compile because of dangling reference. The solution is to the created string instead of a reference to it:
```rust
fn main() {
    let everything = create_something();
    println!("everything is {}", everything);
}fn create_something() -> String {
    let new_thing = String::from("new in town");
    new_thing
}
```

输出
```
everything is new in town
```