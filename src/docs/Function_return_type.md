# 函数返回类型

```rust
fn main() {
    let result = square(3);
    println!("result is {}", result); 
    let result_tuple = triple(33);
    let (input, result1) = result_tuple;
    println!("result_tuple is {:?}", result_tuple);
    
// {:?} ==> debug 格式化 
println!("input {} evaluates to {}", input, result1); 
let nothing: () = does_not_return();
    println!("nothing (union data type) is {:?}", nothing)
}
fn square(number: i32) -> i32 {
    println!("processing square({})", number); 
// 返回一个数值的表达式 number * number
    
// "return number * number; "也是有效的语法。
}
// 用元组实现多返回
fn triple(number: i32) -> (i32, i32) {
    println!("tripling the number: {}", number);
    let input = number;
    let result = number * 3;
    (input, result)
}
// 联盟数据类型

// 当fn返回的值没有意义时使用

// 用空()表示

// 它是可选的
fn does_not_return() -> () {
    println!("ain't returning nuthing!")
}
```

输出
```
processing square(3)
result is 9
tripling the number: 33
result_tuple is (33, 99)
input 33 evaluates to 99
ain't returning nuthing!
nothing (union data type) is ()
```