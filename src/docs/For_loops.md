# For循环

```rust
fn main() {
    let message = ['m', 'e', 's', 's', 'a', 'g', 'e']; 
    /* 迭代器
    - 实现了对一个集合中的每个项目进行迭代的逻辑。
    - next()方法返回一个序列中的下一个项目。
      */
    for item in message.iter() {
        println!("current item is {}", item);
    } 
    println!(""); 
// 迭代时也要获得索引
    
// enumerate()返回一个带有索引/项目_引用对的元组。
    
// 要获得项目，使用&item
    
// 因为迭代器会返回一个引用（&<NAME>）。
    
// 添加&（借用操作符）可以让你
    
// 借用该变量而不
    
// 取得所有权（参见借用部分）。
    
// 然后当你在for循环范围内使用该变量时，你就可以访问该值了 
for (index, &item) in message.iter().enumerate() {
        println!("item {} is {}", index, item);
        if item == 'e' {
            break;
        }
    }
     println!(""); 
// 在一个数字范围上进行迭代
    
// 排除该范围的终值
 for number in 0..5 {
        println!("number is {}", number);
    }
}
```
输出
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