# Deref 解构

Notes:

-   passing a borrowed reference to a string (&String) is not the same as passing a string slice (&str)
-   a borrowed string reference points to a string on the stack which in turn owns and points to the data on the heap
-   a slice only stores a pointer to the heap data along with length information. It does not keep track of the capacity because it does not own anything on the heap.
-   since a string reference contains all the info to function as a slice (pointer to heap data + length), Rust allows to use a string reference where a string slice is expected
-   this convenience is called deref coercion:
```rust
fn main() {
    let message = String::from("lorem ipsum");

    // notice that a string reference is passed as argument 
    let first_word = get_first_word(&message);
    println!("first_word is \"{}\"", first_word);
}
// notice that the expected argument is of type string slice (&str)
fn get_first_word(msg: &str) -> &str {
    let bytes: &[u8] = msg.as_bytes();
    for (index, &item) in bytes.iter().enumerate() {
        if item == b' ' {
            return &msg[..index];
        }
    }
    &msg
}
```

-   of course, deref coercion does not work when using a string slice where a string reference is expected (because of the missing properties)
-   when writing code, prefer using string slices in cases where ownership of the data is not required