# 矢量

```rust
fn main() {
    
// 具有相同数据类型的元素的集合
    
// 元素是按顺序排列的 
// 数组有一个固定的大小，在编译时必须知道。
    
// 因为数组的数据是存储在堆栈中的 
// 向量可以动态地增长和缩小
    
// 通过添加/删除项目来实现
    
// 矢量数据被存储在堆内存中
    
// 因此你需要处理[所有权]和[借用]。
// 向量 = 可变大小的数组 
let mut letters: Vec<char> = vec!['a', 'b', 'c'];
    println!("letters are {:?}", letters); 
    let first_letter = letters[0];
    println!("first_letter is {}", first_letter); 
//为向量添加值 
letters.push('d');
    letters.push('e');
    letters.push('f');
    println!("letters are {:?}", letters); 
// 删除最后一个值 
letters.pop();
    println!("letters are {:?}", letters); 
    let mut numbers: Vec<i32> = vec![11, 22, 44];
    numbers[2] = 33;
    println!("numbers is {}", numbers[2]); 
    let words: Vec<&str>;
    words = vec!["ok"; 2]; 
    println!("words are {:?}", words); 
    let mut ints = vec![22, 33, 44, 55, 66, 77];
    let length: usize = ints.len();
    println!("length is {}", length); 
    let mem_size_byte = std::mem::size_of_val(&ints);
    println!("mem_size_byte is {}", mem_size_byte); 
// 从矢量中切出一片
let mut slice: &[i32] = &ints;
    println!("slice is {:?}", slice); slice = &ints[2..5];
    println!("slice is {:?}", slice); 
// 在向量上进行迭代
 for it in ints.iter() {
        println!("it is {}", it);
    } 
// 迭代时对向量项目进行变异 
for it in ints.iter_mut() {
        
// 解除对指针的引用，以获得和设置值（*it）。
        *it *= *it;
    }
    println!("ints is {:?}", ints);
}
```
输出
```
letters are ['a', 'b', 'c']
first_letter is a
letters are ['a', 'b', 'c', 'd', 'e', 'f']
letters are ['a', 'b', 'c', 'd', 'e']
numbers is 33
words is ["ok", "ok"]
length is 6
mem_size_byte is 24
slice is [22, 33, 44, 55, 66, 77]
slice is [44, 55, 66]
it is 22
it is 33
it is 44
it is 55
it is 66
it is 77
ints is [484, 1089, 1936, 3025, 4356, 5929]
```