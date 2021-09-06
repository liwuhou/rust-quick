# 枚举方法
```rust
#[derive(Debug)]
enum Shape {
    Triangle(f64, f64, f64), // 边 a, b, c
    Rectangle(f64, f64),     // 宽, 高
    Circle(f64),             // 半径
}
impl Shape {
    fn get_perimeter(&self) -> f64 {
        // 不需要解除对自变量的引用
        // 编译器将自动引用/解除引用匹配表达式中的模式
        // match *self { 
        match self {
            Shape::Rectangle(width, height) => (width + height) * 2.0,
            Shape::Triangle(a, b, c) => a + b + c,
            Shape::Circle(radius) => radius * 2.0 * std::f64::consts::PI,
        }
    }
}
fn main() {
    let a_shape = Shape::Triangle(1.1, 2.2, 3.3);
    println!("a_shape is {:?}", a_shape);
    println!("a_shape perimeter is {}", a_shape.get_perimeter()); 
    let a_shape = Shape::Rectangle(1.3, 5.7);
    println!("a_shape is {:?}", a_shape);
    println!("a_shape perimeter is {}", a_shape.get_perimeter()); 
    let a_shape = Shape::Circle(1.13);
    println!("a_shape is {:?}", a_shape);
    println!("a_shape perimeter is {:.2}", a_shape.get_perimeter());
}
```
输出
```

a_shape is Triangle(1.1, 2.2, 3.3)
a_shape perimeter is 6.6
a_shape is Rectangle(1.3, 5.7)
a_shape perimeter is 14
a_shape is Circle(1.13)
a_shape perimeter is 7.10
```