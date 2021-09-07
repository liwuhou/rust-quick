# 形状工厂

```rust

struct Rectangle {
    width: f64,
    height: f64,
}
struct Circle {
    radius: f64,
}
impl Rectangle {
    fn new(width: f64, height: f64) -> Rectangle {
        // 注意这个速记符号
        // 在创建结构体的实例时
        // 因为方法参数的名称与结构字段的名称相同 
        Rectangle { width, height }
    } 
    fn get_area(&self) -> f64 {
        self.height * self.width
    } 
    fn scale(&mut self, scalar: f64) {
        self.width *= scalar;
        self.height *= scalar;
    }
}
impl Circle {
    fn new(radius: f64) -> Circle {
        Circle { radius }
    } 
    fn get_area(&self) -> f64 {
        std::f64::consts::PI * self.radius * self.radius
    } 
    fn get_diameter(&self) -> f64 {
        self.radius * 2.0
    }
}
fn main() {
    let mut rect = Rectangle::new(1.2, 3.4);
    assert_eq!(rect.get_area(), 4.08); 
    rect.scale(0.5);
    assert_eq!(rect.get_area(), 1.02); 
    let expected = 16.0 * std::f64::consts::PI;
    assert_eq!(circ.get_area(), expected); 
    println!("Test passed!");
}
```

输出
```
Test passed!
```