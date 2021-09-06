# 切片为参数

```rust

fn main() {
    let message = String::from("lorem ipsum"); 
    let first_word = get_first_word(&message);
    println!("first_word is \"{}\"", first_word); 
    let first_word_too = get_first_word_too(&message[6..]);
    println!("first_word_too is \"{}\"", first_word_too);
}
// ======= passing the entire string as input ===========
fn get_first_word(msg: &String) -> &str {
    // create a slice of bytes (&[u8] data type) from string data 
    let bytes: &[u8] = msg.as_bytes(); 
    // iterate through byte sequence one byte at a time
    // use enumerate() to get the index when iterating
     for (index, &item) in bytes.iter().enumerate() {
        // find first space and return everything before as a string slice
         // b' ' is the byte representation of a blank space
        // remember that we are iterating on a sequence of bytes, NOT characters
       // we do that because the index for a string slice is in terms of bytes 
       if item == b' ' {
            return &msg[..index];
       }
    } 
    // no blank space found, return entire message &msg
}
// ======= passing a string slice as input ===========
fn get_first_word_too(msg: &str) -> &str {
    let bytes: &[u8] = msg.as_bytes(); 
    for (index, &item) in bytes.iter().enumerate() {
        if item == b' ' {
            return &msg[..index];
        }
    } 
    &msg
}
```
Output
```
first_word is "lorem"
first_word_too is "ipsum"
```