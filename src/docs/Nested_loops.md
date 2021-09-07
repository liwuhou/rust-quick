# 嵌套循环

```rust

fn main() {
    let mut matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]; 
    // 从矩阵中读取 
    for row in matrix.iter() {
        for number in row.iter() {
            print!("{}\t", number);
        }
        println!("");
    } 
    println!("======================="); 
    // 修改可变矩阵的值
    // iter_mut()返回可变的引用 
    for row in matrix.iter_mut() {
        for number in row.iter_mut() {
            //用星号解除引用，以获得值本身 
            *number += 20;
            print!("{}\t", number);
        }
        println!("");
    }
}
```
输出
```
1 2 3
4 5 6
7 8 9
=======================
21 22 23
24 25 26
27 28 29
```