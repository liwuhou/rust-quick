# 数据结构

- 用来分组混合数据类型的多个相关项目
- 元素被命名（与图元不同，图元是有顺序的
- 两种结构（常规结构和元组结构

```rust
// tuple结构
// 用于存储没有命名字段的混合数据集合
// 用于区分为特定的类型
// （不是普通的元组）结构 Signal(u8, bool, String)。
// 常规结构
// 结构名称被大写
//像JavaScript和OOP中的类一样
struct Car {
    // 结构中的字段
    model: String,
    year: String,
    used: bool,
}
// 方法：与结构相关的函数/子程序
// 方法是在结构的上下文中定义的。
// 方法的第一个参数是对一个结构实例的引用
impl Car {
    // construct car
    fn new(m: &str, y: &str) -> Car {
        Car {
            model: m.to_string(),
            year: y.to_string(),
            used: false,
        }
    } 
    // self等同于JavaScript中的 "this"。
    fn serialize(&self) -> String {
        format!(
            "model: {} - year: {} - used: {}",
            self.model, self.year, self.used
        )
    } 
    // 变更状态
    fn marked_used(&mut self) {
        self.used = true;
    }
}
struct Position {
  latitude: f64,
  longitude: f64
}
fn print_signal(s: &Signal) {
    println!("s1 is {}, {}, {}", s.0, s.1, s.2);
}
fn main() {
    let mut pos_1 = Position {
        latitude: 27.299112,
        longitude: 95.387110,
    }; 
    println!(
      "pos_1 is {:.3}, {:.3}",
      pos_1.latitude,
      pos_1.longitude
    ); 
    pos_1.latitude = 23.1111;
    println!(
      "pos_1 is now {:.3}, {:.3}",
      pos_1.latitude,
      pos_1.longitude
    ); 
    let mut s1 = Signal(0, true, String::from("ok")); 
    // 元组结构的字段可以像普通元组的值一样被访问。
    // 使用它们的索引
    // 记住元组结构没有命名的字段 
    print_signal(&s1); 
    s1.0 = 23;
    s1.1 = false;
    s1.2 = String::from("NETERR"); 
    println!("s1 is now {}, {}, {}", s1.0, s1.1, s1.2); 
    let car_1 = Car::new("QBC", "2133");
    println!("car_1 is a {} of {}", car_1.model, car_1.year); 
    let is_used = if car_1.used == true {
        "used"
    } else {
        "brand new"
    };
    println!("car_1 is {}", is_used);
    println!("car_1 is {}", car_1.serialize()); 
    let mut car_2 = Car::new("ZZ7", "2042");
    println!("car_2 is a {}", car_2.serialize()); 
    car_2.marked_used();
    println!("car_2 is now {}", car_2.serialize());
}
```

输出
```
pos_1 is 27.299, 95.387
pos_1 is now 23.111, 95.387
s1 is 0, true, ok
s1 is now 23, false, NETERR
car_1 is a QBC of 2133
car_1 is brand new
car_1 is model: QBC - year: 2133 - used: false
car_2 is a model: ZZ7 - year: 2042 - used: false
car_2 is now model: ZZ7 - year: 2042 - used: true
```

更多结构的示例：
```rust
// 需要使用debug和clone traits
// 能够用调试运算符打印结构体的实例
// 能够克隆该结构的一个实例。
// 以后会有更多关于特质的内容
#[derive(Debug, Clone)]
struct Spaceship {
    name: String,
    crew: u8,
    propellant: f64,
}
// methods are defined within a impl block
impl Spaceship {
    fn get_name(&self) -> &str {
      //用借贷运算符将字符串转换为字符串片断 
      &self.name
    } 
    fn add_fuel(&mut self, gallons: f64) {
        self.propellant += gallons;
    } 
    // 这是一个关联函数
    // 与结构数据类型相关联
    // 与方法类似，但没有&self引用
    // 用于与该结构相关的一般函数。
    // 而不是一个特定的实例
    //（就像面向对象中的类静态方法）。
    // 通常用于构建结构体的实例 
    fn new(name: &str) -> Spaceship {
      Spaceship {
        name: String::from(name),
        crew: 11,          // 默认值，所有实例都一样
        propellant: 0.0    // 默认值，所有实例都一样
      }
    }
}
fn main() {
    let mut spaceship1 = Spaceship {
        name: String::from("spaceship1"),
        crew: 123,
        propellant: 1234567.654,
    }; 
    //访问字段值 
    println!("spaceship1 has {} members.", spaceship1.crew); 
    spaceship1.crew = 99; 
    println!(
        "After attack, spaceship1 has now {} members.",
        spaceship1.crew
    ); 
    println!("spaceship1 is {:?}", spaceship1); 
    // 默认情况下，结构数据被存储在 STACK 上。
    // 如果结构包含HEAP存储的数据（如字符串）。
    // 指针存储在STACK上，数据存储在HEAP上。
    // 从其他实例的字段中创建结构实例
    //（就像JS中的spread operator，但是是两个点而不是三个点）。
    // 这就是所谓的结构更新语法
    // 它允许创建新的实例
    // 通过复制现有实例的字段值来创建新实例
    //（除了在新实例中明确设置的字段）。
    let spaceship2 = Spaceship {
        name: String::from("Galactos"),
        ..spaceship1
    }; 
    println!("spaceship2 is {:?} members.", spaceship2); 
    // 在修改复制的结构实例时
    // 不会影响复制后的新实例。
    //（与保留的JavaScript引用不同。
    // 当用数组传播对象时......) 
    spaceship1.name = String::from("Battlestar"); 
    spaceship1.crew = 78; 
    assert_eq!(spaceship2.crew, 99); 
    println!("spaceship1 is {:?}", spaceship1); 
    println!("spaceship2 is {:?}", spaceship2); 
    // 要复制所有字段，甚至是基于堆的字段。
    // 你需要创建一个结构实例的副本。
    // 否则，当使用结构更新语法时，会转移基于堆的数据的所有权
    // 这意味着你不能再使用复制的实例中的相关字段。
    let mut spaceship3 = Spaceship {
        //需要手动实现克隆特性
        //在结构定义中（见上文）。
        ..spaceship1.clone()
    }; 
    println!("spaceship3 is {:?}", spaceship3); 
    let name = spaceship3.get_name(); 
    println!("name is {}", name); 
    println!("spaceship3 propellant is {}", spaceship3.propellant);

    spaceship3.add_fuel(4567.113);

    println!(
      "After going to space refuel station, spaceship3 propellant is now {}",
      spaceship3.propellant
    ); 
    //要调用一个指定的函数，请使用路径操作符（::）。
    let spaceship4 = Spaceship::new("Serenity"); 
    assert_eq!(spaceship4.crew, 11);
}
```