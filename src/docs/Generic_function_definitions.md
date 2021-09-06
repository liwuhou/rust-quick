# 泛型函数定义

```rust


//限制通用类型

//限于那些实现了特质的类型，这些类型的值可以进行排序比较（PartialOrd）。

// PartialOrd特性包含在std crate prelude中（不需要全路径）。

// 否则，编译器怎么会知道具体类型是否可以使用>进行比较？
fn get_biggest<T: PartialOrd>(n1: T, n2: T) -> T {
    if n1 > n2 {
        n1
    } else {
        n2
    }
}
fn main() {
    println!("biggest is {}", get_biggest(23u8, 121u8));
    println!("biggest is {}", get_biggest(12345, 121));
    println!("biggest is {}", get_biggest(123.45, 1.21));
}
```
输出
```
biggest is 121
biggest is 12345
biggest is 123.45
```