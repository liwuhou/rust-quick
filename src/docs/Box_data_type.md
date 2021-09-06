# 封箱数据类型

```rust
// Box<T>用于在堆上而不是在栈上存储数据
// 它由堆栈上的一个指针组成
// 指向堆上的一个内存块
// 该内存块已被分配得足够大，可以容纳<T>数据。
// 盒子被认为是智能指针
// 提供了比引用更多的功能。
// 盒子<T>对它所指向的数据有所有权
// 当Box<T>超出范围时，会将堆中的内存删除。
// Box数据类型被用来存储一个在编译时无法知道大小的类型
// 但仍然需要一个尺寸
// 例如：递归类型
// 递归类型的例子：一个结构体包括另一个相同类型的结构体作为它的一个字段（想想迭代器--比如在JavaScript中）。
// 在编译时，你不知道层的深度，因此不知道整个结构的大小。
// 盒子的另一个用途是转移数据的所有权，而不是在堆栈中复制它。
// 避免复制大量的堆栈数据
// 通过将数据转移到堆中，可能会提高性能（因为有指针），可以更容易地转移数据。
use std::mem;
#[derive(Debug)]
struct Team {
    name: String,
    size: u8,
    capacity: f64,
    domain: String,
}
fn main() {
    // 记住结构体是在堆栈上的
    // 除了长度可变的字段（例如：String）会留在堆上。
    let lions = Team {
        name: String::from("The lions"),
        size: 7,
        capacity: 11.5,
        domain: String::from("Authentication"),
    }; 
    println!("lions is {:?}", lions); 
    // mem::size_of_val()给出了给定参考值所指向的字节大小。
    println!(
      "lions size is on stack {} bytes",
      mem::size_of_val(&lions)
    ); 
    // 这不是一个复制操作，所有权被转移了。
    // 狮子变量失去了对该结构的所有权 
    // 狮子变量不能再被使用了 
    // 结构实例被转移到盒子分配的堆位置上。
    // boxed_lions变量成为该结构的新主人
    //通过住在堆栈上的盒子智能指针，成为结构的新主人。
    let boxed_lions: Box<Team> = Box::new(lions); 
    println!("boxed_lions is {:?}", boxed_lions); 
    //打印盒子指针的大小（字节）。
    println!(
        "boxed_lions size is on stack {} bytes",
        mem::size_of_val(&boxed_lions)
    ); 
    //打印结构实例的字节大小 
    // 需要向mem::size_of_val()传递一个被解除引用的盒子指针（WTF...）的引用。
    // 在盒子指针前使用解除引用操作符 "*"。
    //引用一个指针将代表被指向的位置/数据。
    // &*boxed_lions是对堆上数据的引用，而不是对堆上指针的引用。
    println!(
        "boxed_lions team size is on heap {} bytes",
        mem::size_of_val(&*boxed_lions)
    ); 
    //将结构实例移回堆栈中
    //通过取消引用盒子的指针来实现 
    let unboxed_lions: Team = *boxed_lions; 
    println!("unboxed_lions is {:?}", unboxed_lions); 
    println!(
        "unboxed_lions team size is on stack {} bytes",
        mem::size_of_val(&unboxed_lions)
    );
}
```
输出
```
lions is Team { name: "The lions", size: 7, capacity: 11.5, domain: "Authentication" }
lions size is on stack 64 bytes
boxed_lions is Team { name: "The lions", size: 7, capacity: 11.5, domain: "Authentication" }
boxed_lions size is on stack 8 bytes
boxed_lions team size is on heap 64 bytes
unboxed_lions is Team { name: "The lions", size: 7, capacity: 11.5, domain: "Authentication" }
unboxed_lions team size is on stack 64 bytes
```