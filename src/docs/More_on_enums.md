# 更多枚举值

```rust
#[derive(Debug)]
enum Shape {
    //用枚举存储数据，定义参数数据类型
    Triangle(f64, f64, f64), 
// 边 a, b, c
    Rectangle(f64, f64),     
// 长, 宽
    Circle(f64),             
// 半径
}
fn main() {
    let a_shape = Shape::Triangle(1.1, 2.2, 3.3);
    println!("a_shape is {:?}", a_shape); 
    let a_shape = Shape::Rectangle(1.3, 5.7);
    println!("a_shape is {:?}", a_shape);
    let a_shape = Shape::Circle(1.13);
    println!("a_shape is {:?}", a_shape); 
// 匹配运算符
    
// 将一个值与一系列模式进行比较
    
// 来决定执行哪段代码
    
// 与其他语言中的switch语句相似 
// 匹配表达式用于控制程序的流程 
    match a_shape {
        
// 枚举所有可能的值 
// 捕获存储的数据
        
// 使用一个位置参数名（a, b, c）。
        
//当匹配时要执行的逻辑是在"=>"之后。
        Shape::Triangle(a, b, c) => println!(
            "a_shape is a triangle with sides a = {}, b = {}, c = {}",
            a, b, c
        ),
        Shape::Rectangle(width, height) => println!(
            "a_shape is a rectangle with width = {} and height = {}",
            width, height
        ),
        Shape::Circle(radius) => println!("a_shape is a circle with radius {}", radius),
    }
}
```

输出
```
a_shape is Triangle(1.1, 2.2, 3.3)
a_shape is Rectangle(1.3, 5.7)
a_shape is Circle(1.13)
a_shape is a circle with radius 1.13
```