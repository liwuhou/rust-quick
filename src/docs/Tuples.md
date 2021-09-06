# 元组

```rust

fn main() {
    // used to group related items of mixed data types
    // can have max 12 mixed type values
    // adding more values and it will no longer be a tuple type 
    let a_tuple: (&str, u8, char) = ("ok", 0, 'd');
    let first_item = a_tuple.0;
    println!("first_item is {}", first_item); 
    // mutate a tuple let mut b_tuple = ("ok", 0);
    b_tuple.0 = "ko";
    b_tuple.1 += 1;
    println!("b_tuple.1 is {}", b_tuple.1);
     // destructure a tuple 
     let c_tuple = ("en", "US", 1);
    let (language, country, code) = c_tuple;
    println!(
        "language is: {}\ncountry is: {}\ncode is: {}",
        language, country, code
    )
}
```
Output
```
first_item is ok
b_tuple.1 is 1
language is: en
country is: US
code is: 1
```