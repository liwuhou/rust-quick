# 默认特性实现

```rust

struct Car {
    model: String,
    brand: String,
    velocity: u16, // km/h
}
struct Plane {
    name: String,
    nick_name: String,
    velocity: u16, // km/h
    crew: u8,
    passengers: u16,
    ceiling: u32,
}
trait Serialization {
    // 默认的特质实现
    // 以避免为每个使用该特质的类型实现它。
    fn describe(&self) -> String {
        String::from("some kind of vehicle.")
    }
}
impl Serialization for Car {
    //为汽车结构提供具体的特质实现
    // 覆盖默认实现 
    fn describe(&self) -> String {
        format!(
            "{} from {} going at {} km/h.",
            self.model, self.brand, self.velocity
        )
    }
}
//将使用默认的特质实现，因为没有特定的特质。
impl Serialization for Plane {}
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
some kind of vehicle.
```