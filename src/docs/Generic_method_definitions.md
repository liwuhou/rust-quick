# 泛型方法定义

```rust

#[derive(Debug)]
struct Rectangle<T> {
    width: T,
    height: T,
}
#[derive(Debug)]
struct Shape<T, U> {
    width: T,
    height: U,
}
// 在 impl 关键字之后包括通用变量名称
// 和结构标识符之后
// impl<T, U>告诉编译器，通用结构定义的方法
impl<T, U> Shape<T, U> {
    fn get_width(&self) -> &T {
        // 需要返回一个引用
        // 因为不知道<T>将被替换成哪种类型。
        //记住固定/可变长度数据类型的所有权
        //返回一个引用，对这两种类型都有效，无需转移所有权 &self.width
    }
}
//为特定的具体类型的Shape实现方法
// 注意不要把通用类型放在 impl 关键字后面，这告诉编译器这些方法是为具体的结构定义服务的。
impl Shape<u8, u8> {
    fn get_perimeter(&self) -> u8 {
        (self.height + self.width) * 2
    }
}
fn main() {
    let rect = Rectangle {
        width: 1.2,
        height: 3.4,
    }; 
    println!("rect is {:?}", rect); 
    let rect = Rectangle {
        width: 5,
        height: 11,
    }; 
    println!("rect is {:?}", rect); 
    let rect = Rectangle {
        width: 7u8,
        height: 23u8,
    }; 
    println!("rect is {:?}", rect); 
    let rect = Shape {
        width: 456u16,
        height: 78.54f32,
    }; 
    println!("rect is {:?}", rect); 
    println!("rect width is {:?}", rect.get_width()); 
    let rect = Shape {
        width: 54u8,
        height: 32u8,
    }; 
    // get_perimeter()方法是在Shape的这个实例上定义的。
    // 因为这两个字段都是u8数据
    // 否则这个方法将无法被找到 
    println!("rect perimter is {:?}", rect.get_perimeter());
}
```
输出
```
rect is Rectangle { width: 1.2, height: 3.4 }
rect is Rectangle { width: 5, height: 11 }
rect is Rectangle { width: 7, height: 23 }
rect is Shape { width: 456, height: 78.54 }
rect width is 456
rect perimter is 172
```