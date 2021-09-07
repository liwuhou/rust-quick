# 所有权

```rust
fn main() {
    /*需要清理不再需要的已分配内存块
    在C/C++中：malloc()和free()用于手动管理内存。
    另一种方法是垃圾收集，它是自动的 */ /*
    Rust使用OWNERSHIP系统。
       - 变量负责释放自己的资源
       - 每个值在同一时间只能由一个变量拥有
       - 当拥有的变量超出范围时，该值就会被丢弃。
       - 有一些方法可以将一个值的所有权从一个变量转移到另一个变量。
    */ 
    let outer_planet: String;
    let outer_galaxy: String;
    let outer_planet_position: i32; 
    // 内部代码块范围 
    {
        let inner_planet = String::from("Mercury");
        println!("inner_planet is {}", inner_planet); 
        /*
        因为所有权规定每个值/数据只有一个所有者。
         - inner_planet将不再指向堆上的String值。
         - 在Rust中，将所有权从一个变量转移到另一个变量被称为 "移动"。
         - 这意味着在Rust中没有存储在堆上的数据的浅层拷贝。
            (浅层拷贝=多个变量指向内存中的相同数据)
        */ 
        // 转移所有权
        outer_planet = inner_planet; 
        // 在转移字符串数据的所有权后，不能再使用inner_planet变量了
        // println! ("inner_planet is {}", inner_planet); 
        // => 会出现panic
        let mut inner_galaxy = String::from("Milky Way");
        println!("inner_galaxy is {}", inner_galaxy); 
        //重复存储在堆上的数据，创建一个字符串数据的深度拷贝

        outer_galaxy = inner_galaxy.clone(); 
        inner_galaxy.clear();
        println!("inner_galaxy is now: {}", inner_galaxy);
        println!("outer_galaxy is {}", outer_galaxy); 
        // 整数数据类型住在堆栈中。
        let mut inner_planet_position = 1;
        println!("inner_planet_position is {}", inner_planet_position);
        /*
        为 outer_planet_position 创建一个整数数据的副本。
        - 所有权受到尊重（没有浅层拷贝--每次每个值只有一个变量）--通常STACK-ONLY数据类型（即固定大小）被隐式拷贝
            当包含它们的变量被分配给另一个变量时 - 存储在堆栈中的数据类型实现了允许它们被复制而不是移动的特性
        */ 
        outer_planet_position = inner_planet_position;
        inner_planet_position += 4; 
        println!("inner_planet_position is {}", inner_planet_position); 
        println!("outer_planet_position is {}", outer_planet_position); 
    } 
    println!("\nouter_planet is {}", outer_planet);
    println!("outer_galaxy is {}", outer_galaxy);
    println!("outer_planet_position is {}", outer_planet_position);
}
```
输出
```
inner_planet is Mercury
inner_galaxy is Milky Way
inner_galaxy is now:
outer_galaxy is Milky Way
inner_planet_position is 1
inner_planet_position is 5
outer_planet_position is 1
```
更多案例:
```rust
fn main() {
    let mut arr_1: [u8; 2] = [33, 66]; 
    // ////////////////
    // 固定长度的类型（存储在堆栈中）被COPIED。
    // //////////////// 
    let arr_2 = arr_1;
    println!("arr_1 is {:?}", arr_1);
    arr_1 = [1, 2];
    println!("arr_1 is now {:?}", arr_1);
    println!("arr_2 is {:?}", arr_2); 
    // ////////////////
    // 可变长度类型的值将所有权转移到新的变量上
    // //////////////// 
    let vec_1 = vec![3, 4];
    let vec_2 = vec_1; 
    //不能再使用所有权已被 "转移 "的变量了 
    // 
    println!("vec_1 is {:?}", vec_1); 
    // => wll panic println! ("vec_2 is {:?}", vec_2); 
    // 借用一个变量所拥有的值而不移动所有权。
    // 使用对该值的引用 
    let vec_4 = vec![5, 6, 7]; 
    //用一个引用来借取值（&<NAME>）。
    let vec_5 = &vec_4;
    println!("vec_4 is {:?}", vec_4);
    println!("vec_5 is {:?}", vec_5);
}
```

输出
```
输出
arr_1 is [33, 66]
arr_1 is now [1, 2]
arr_2 is [33, 66]
vec_2 is [3, 4]
vec_4 is [5, 6, 7]
vec_5 is [5, 6, 7]
```