# 元组

```rust

fn main() {
    //用于分组混合数据类型的相关项目
    //最多可以有12个混合类型的值
    // 如果增加更多的值，它将不再是一个元组类型。
    let a_tuple: (&str, u8, char) = ("ok", 0, 'd');
    let first_item = a_tuple.0;
    println!("first_item is {}", first_item); 
    // 使元组可变 
    let mut b_tuple = ("ok", 0);
    b_tuple.0 = "ko";
    b_tuple.1 += 1;
    println!("b_tuple.1 is {}", b_tuple.1);
     // 解构一个元组 
     let c_tuple = ("en", "US", 1);
    let (language, country, code) = c_tuple;
    println!(
        "language is: {}\ncountry is: {}\ncode is: {}",
        language, country, code
    )
}
```
输出
```
first_item is ok
b_tuple.1 is 1
language is: en
country is: US
code is: 1
```