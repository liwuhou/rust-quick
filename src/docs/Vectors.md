# 矢量

```rust
fn main() {
    
// collection of elements with the same data type
    
// elements are sorted in order 
// arrays have a fixed size that must be known at compile time
    
// because array data is stored on the stack 
// vectors can dynamically grow and shrink
    
// by adding / removing items
    
// vector data is stored in heap memory
    
// therefore you need to handle [ownership] and [borrowing]
// vectors = mutable size arrays 
let mut letters: Vec<char> = vec!['a', 'b', 'c'];
    println!("letters are {:?}", letters); 
    let first_letter = letters[0];
    println!("first_letter is {}", first_letter); 
// add value to vector 
letters.push('d');
    letters.push('e');
    letters.push('f');
    println!("letters are {:?}", letters); 
// remove last value 
letters.pop();
    println!("letters are {:?}", letters); 
    let mut numbers: Vec<i32> = vec![11, 22, 44];
    numbers[2] = 33;
    println!("numbers is {}", numbers[2]); 
    let words: Vec<&str>;
    words = vec!["ok"; 2]; 
    println!("words are {:?}", words); 
    let mut ints = vec![22, 33, 44, 55, 66, 77];
    let length: usize = ints.len();
    println!("length is {}", length); 
    let mem_size_byte = std::mem::size_of_val(&ints);
    println!("mem_size_byte is {}", mem_size_byte); 
// slice from vector 
let mut slice: &[i32] = &ints;
    println!("slice is {:?}", slice); slice = &ints[2..5];
    println!("slice is {:?}", slice); 
// iterate over vector
 for it in ints.iter() {
        println!("it is {}", it);
    } 
// mutate vector items while iterating 
for it in ints.iter_mut() {
        
// dereference the pointer to get and set value (*it)
        *it *= *it;
    }
    println!("ints is {:?}", ints);
}
```
Output
```
letters are ['a', 'b', 'c']
first_letter is a
letters are ['a', 'b', 'c', 'd', 'e', 'f']
letters are ['a', 'b', 'c', 'd', 'e']
numbers is 33
words is ["ok", "ok"]
length is 6
mem_size_byte is 24
slice is [22, 33, 44, 55, 66, 77]
slice is [44, 55, 66]
it is 22
it is 33
it is 44
it is 55
it is 66
it is 77
ints is [484, 1089, 1936, 3025, 4356, 5929]
```