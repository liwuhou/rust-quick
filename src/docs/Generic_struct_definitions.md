# 泛型数据结构体定义

```rust
// 具体数据类型或其他属性的抽象代名词
// 可以与结构、函数、方法等一起使用，以帮助消除重复的代码
// 赋予数据类型以灵活性
// 用<T>定义（T：通用类型变量
// 通用变量的名称是任意的，可以是<Toto>。
// 类似于TypeScrypt中的泛型
#[derive(Debug)]
struct Rectangle<T> {
    width: T,
    height: T,
}
//多种通用类型
#[derive(Debug)]
struct Shape<T, U> {
    width: T,
    height: U,
}
fn main() {
    //用f64数据创建矩形 
    let rect = Rectangle {
        width: 1.2,
        height: 3.4,
    }; 
    println!("rect is {:?}", rect); 
    // 用u32数据创建矩形 
    let rect = Rectangle {
        width: 5,
        height: 11,
    }; 
    println!("rect is {:?}", rect); 
    // 用u8数据创建矩形
    //注意我们在数字后面加上了u8的后缀。
    let rect = Rectangle {
        width: 7u8,
        height: 23u8,
    }; 
    println!("rect is {:?}", rect); 
    // 用u16和f32数据创建形状 
    let rect = Shape {
        width: 456u16,
        height: 78.54f32,
    }; 
    println!("rect is {:?}", rect);
}
```
输出
```
rect is Rectangle { width: 1.2, height: 3.4 }
rect is Rectangle { width: 5, height: 11 }
rect is Rectangle { width: 7, height: 23 }
rect is Shape { width: 456, height: 78.54 }
```

- 泛型是一种零成本的抽象=在不降低运行时性能的情况下更容易编程
- Rust编译器对泛型使用单态化=用具体的数据类型代替占位符
- 在编译时，代码将包括具体的数据类型，而不是泛型抽象=如果你用f64数据创建一个矩形，编译后的代码将有一个带有f64字段的矩形的结构定义，以及与创建结构实例时同样多的具体类型定义。
- 源代码将使用通用数据类型，但编译后的代码将有具体的数据类型，因此不会影响运行时的性能（无需猜测数据类型）。