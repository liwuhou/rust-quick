# 数组

```rust

fn main() {
    // fixed length and single typed
    // stored in contiguous memory locations
    // Contiguous means that elements are laid out so that every element is the same distance from its neighbors. 
    let letters = ['a', 'b', 'c'];
     // type: [char; 3]
    let first_letter = letters[0];
    println!("first_letter is {}", first_letter); // to modify elements in array, it must be mutable 
    let mut numbers = [11, 22, 44]; 
    // type is [i32; 3]
    numbers[2] = 33;
    println!("numbers is {}", numbers[2]);
     // empty array declaration (memory allocated)
      let words: [&str; 2];
    words = ["ok"; 2]; 
    // repeat expression, equivalent to ["ok", "ok"]
    println!("words is {:?}", words); /*
    length of usize is based on number of bytes needed to reference memory in your target architecture:
    - for 32 bit compilation target -> usize is 4 bytes
    - for 64 bit compilation target -> usize is 8 bytes
    */ 
    let ints = [22; 5];
    let length: usize = ints.len();
    println!("length is {}", length);
     // get size in memory (mem module of the std crate) 
     let mem_size_byte = std::mem::size_of_val(&ints);
    println!("mem_size_byte is {}", mem_size_byte); 
    // get slice from array
    let mut slice: &[i32] = &ints;
    println!("slice is {:?}", slice);

    slice = &ints[3..5];
    println!("slice is {:?}", slice);
}
```

Output
```
first_letter is a
numbers is 33
words is ["ok", "ok"]
length is 5
mem_size_byte is 20
slice is [22, 22, 22, 22, 22]
slice is [22, 22]
```