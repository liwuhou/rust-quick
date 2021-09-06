# 数组

```rust

fn main() {
    // 固定长度和单一类型的
    //存储在连续的内存位置
    // 毗连是指元素的排列方式，使每个元素与相邻元素有相同的距离。
    let letters = ['a', 'b', 'c'];
     // 类型: [char; 3]
    let first_letter = letters[0];
    println!("first_letter is {}", first_letter); 
    // 要修改一个元素，必须设置为可变 
    let mut numbers = [11, 22, 44]; 
    // 类型：[i32; 3]
    numbers[2] = 33;
    println!("numbers is {}", numbers[2]);
     // 空数组定义 （分配内存)
    let words: [&str; 2];
    words = ["ok"; 2]; 
    // 重复表达式，相当于 ["ok", "ok"]
    println!("words is {:?}", words); 
    /*
    usize的长度是基于你的目标架构中引用内存所需的字节数。
    - 对于32位的编译目标 -> usize是4字节
    - 对于64位的编译目标 -> usize是8字节。
    */ 
    let ints = [22; 5];
    let length: usize = ints.len();
    println!("length is {}", length);    
     //获得内存中的大小（std crate的mem模块）。
     let mem_size_byte = std::mem::size_of_val(&ints);
    println!("mem_size_byte is {}", mem_size_byte); 
    //从数组中获取切片
    let mut slice: &[i32] = &ints;
    println!("slice is {:?}", slice);

    slice = &ints[3..5];
    println!("slice is {:?}", slice);
}
```

输出
```
first_letter is a
numbers is 33
words is ["ok", "ok"]
length is 5
mem_size_byte is 20
slice is [22, 22, 22, 22, 22]
slice is [22, 22]
```