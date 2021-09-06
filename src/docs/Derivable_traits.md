# 可衍生的特性
```rust
// 默认情况下，新结构不实现任何特质
// 你作为程序员给它提供它所需要的特质
// 可派生特质为常见特质提供了默认的实现方式
//提供了对基本功能的访问
// 而不需要实现自定义特征
//当派生特性时，编译器会生成默认代码。
// 编译器会生成所需方法的默认代码。
// 可派生特质是（随着语言的发展会有变化）。
// Eq
// PartialEq
// Ord
// PartialOrd
// Clone
// Copy
// Hash
// Default - 创建一个数据类型的新实例 
// Debug - 提供一个格式化的debug字符串 
// 衍生性状。 #[ derive( trait_a, trait_b, ...) ] 。
// PartialEq的默认实现要求两个结构的所有字段都相等，以返回true
// (检查文档 std::cmp::PartialEq)
// PartialOrd的默认实现是对字段的值进行比较。
// 按照定义的顺序解析字段，并且
// 一旦找到可以比较的字段。
// 将返回比较的结果
// 而不去看其他字段（查看文档 std::cmp::PartialOrd）。
#[derive(PartialEq, PartialOrd, Debug)]
struct Car {
    model: String,
    brand: String,
    velocity: u16, // km/h
}
fn main() {
    let gle_class_coupe = Car {
        model: String::from("GLE-Class Coupe"),
        brand: String::from("Mercedes-Benz"),
        velocity: 280,
    }; 
    let gle_class = Car {
        model: String::from("GLE-Class"),
        brand: String::from("Mercedes-Benz"),
        velocity: 218,
    };
     //由于派生的PartialEq特性而被允许。
     println!("Are the cars equal: {}", gle_class_coupe == gle_class);
      //由于派生的PartialOrd特性而被允许。
    //在这里，名称字段被比较以断定哪一个更大
     println!(
        "Is the coupe greater then the SUV: {}",
        gle_class_coupe > gle_class
    );
     //因为派生的Debug特性而被允许 
     println!("{:?}", gle_class);
}
```
输出
```
Are the cars equal: false
Is the coupe greater then the SUV: true
Car { model: "GLE-Class", brand: "Mercedes-Benz", velocity: 218 }
```