# 哈希表数据类型
```rust
// 保存数据为 键值对 格式
// 根据key，可以找到对应的值
// 键 -> 值 单向映射
// Rust 用一个hash方法检测如何存储数据
// 键，值可以是不同的数据类型
// 所有的键必须是一样的数据类型
// 所有的值必须是同样的数据类型
// 每个键只有一个值
//你需要导入一个类型，更新 哈希表的时候:
// #1. 覆写已有的键值对
// #2. 插入一个新的值，当键值对不存在的时候
// #3. 修改已有的值，基于它当前的值
use std::collections::HashMap;
fn main() {
    let mut missions = HashMap::new(); 
    missions.insert("Toto", 23);
     // HashMap<&str, i32>
    missions.insert("Toto", 33); 
    // #1 update missions.insert("Titi", 45);
    missions.insert("Tata", 67); missions.entry("Tutu").or_insert(77); 
    // #2 update 
    // #3 update 
    let tyty = missions.entry("Titi").or_insert(0);
    *tyty += 1; 
    println!("missions is {:?}", missions.clone()); 
    let toto_missions = match missions.get("Toto") {
        Some(value) => value,
        None => &0,
    }; 
    println!("Toto_missions is {}", toto_missions);
}
```
输出
```
missions is {"Tata": 67, "Titi": 46, "Toto": 33, "Tutu": 77}
Toto_missions is 33
```