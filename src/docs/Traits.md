# 特性
```rust

// 特质。

// 用于定义特定数据类型功能的抽象方法
// 方法的集合

// 代表完成某些任务所需的一组行为
// 数据类型可以实现一个特征。

// 该类型实现了这些特定的方法，因此这些方法可以在它身上使用。
// 泛型使用特质来指定未知数据类型的能力。

// 特质作为一种约束，可以接受哪些具体类型。

// 只要这些具体类型实现了这组方法
// 与TypeScript和其他支持经典OOP的语言中的接口相似。
// Rust带有默认的通用特征（参见std::prelude）。
// 你可以定义你的自定义特征
struct Car {
    model: String,
    brand: String,
    velocity: u16, 
// km/h
}
struct Plane {
    name: String,
    nick_name: String,
    velocity: u16, 
// km/h
    crew: u8,
    passengers: u16,
    ceiling: u32,
}
// 自定义特质 
trait Serialization {
    
// 方法签名
    fn describe(&self) -> String;
}
// 实现一个特定的特性
impl Serialization for Car {
    fn describe(&self) -> String {
        
// format! 宏返回格式化的字符串 
    format!(
            "{} from {} going at {} km/h.",
            self.model, self.brand, self.velocity
        )
    }
}
// 为其他类型实现特性
impl Serialization for Plane {
    fn describe(&self) -> String {
        format!(
            "{} ({}) going at {} km/h with a crew of {} and up to {} passengers at {} m above.",
            self.name, self.nick_name, self.velocity, self.crew, self.passengers, self.ceiling
        )
    }
}
fn main() {
    let gle_class_coupe = Car {
        model: String::from("GLE-Class Coupe"),
        brand: String::from("Mercedes-Benz"),
        velocity: 280,
    };
     let g6 = Plane {
        name: String::from("Gulfstream G650 "),
        nick_name: String::from("G6"),
        velocity: 956,
        crew: 4,
        passengers: 19,
        ceiling: 15545,
    };
     println!("{}", gle_class_coupe.describe());
    println!("{}", g6.describe());
}
```

输出

```
GLE-Class Coupe from Mercedes-Benz going at 280 km/h.
Gulfstream G650  (G6) going at 956 km/h with a crew of 4 and up to 19 passengers at 15545 m above.
```