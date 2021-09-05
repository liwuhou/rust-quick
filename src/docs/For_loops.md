# For循环

```rust
fn main() {
    let message = ['m', 'e', 's', 's', 'a', 'g', 'e']; 
    /* Iterator
    - implements logic to iterate over each item in a collection
    - next() method returns the next item in a sequence
      */
    for item in message.iter() {
        println!("current item is {}", item);
    } 
    println!(""); 
// To also get the indexes when iterating
    
// enumerate() returns a tuple with index/item_reference pair
    
// To get the item use &item
    
// because the iterator gives back a reference (&<NAME>)
    
// Adding the & (borrow operator) allows you to
    
// borrow the variable without
    
// taking ownership (see borrowing section)
    
// - then when you use the variable in the for loop scope, you access the value 
for (index, &item) in message.iter().enumerate() {
        println!("item {} is {}", index, item);
        if item == 'e' {
            break;
        }
    }
     println!(""); 
// iterating over a range of numbers
    
// excludes the end value of the range
 for number in 0..5 {
        println!("number is {}", number);
    }
}
```
Output
```
current item is m
current item is e
current item is s
current item is s
current item is a
current item is g
current item is eitem 0 is m
item 1 is enumber is 0
number is 1
number is 2
number is 3
number is 4
```