# 切片

```rust

fn main() {
// 切片：用于引用一个集合（array等）的连续部分（子集），而不占用这些元素的所有权。
// 常用的有：字符串分片 dt type : &str
    
// 字符串是一个片断
    
// 数据在可执行的二进制文件中是硬编码的，程序使用一个字符串片断来访问它 
// 从字符串数据中创建一个字符串片断 
// 句子变量也有一个指向内存中字符串数据开头的指针，作为其长度和容量的信息。
 let sentence = String::from("This is a sequence of words.");
    println!("sentence is {}", sentence); 
// last_word变量有一个指向字符串数据部分的偏移量/起始索引的指针，以及分片的长度
    
// 像往常一样，切片的结束索引被排除在结果之外（在大多数编程语言中，在对集合进行切片时很常见）。
let last_word = &sentence[22..22 + 5];          
// [start..end_excluded]
    println!("last_word is \"{}\"", last_word); 
//从偏移索引到集合结束的切片（这里是字符串数据）。
let last_part: &str = &sentence[22..];
    println!("last_part is \"{}\"", last_part); 
//从集合的开始到结束的索引进行切片 
let without_last_word = &sentence[..22];
    println!("without_last_word is \"{}\"", without_last_word); 
// 字符串片的长度是以字节数为单位的（usize数据类型）。
    
// 不是以字符数为单位 
let slice_length: usize = last_part.len();
    println!("slice_length is {} bytes", slice_length); 
// 当创建一个字符串片断时，范围索引必须出现在有效的UTF-8字符边界上。
    
// 记住，UTF-8字符可以占用多个字节。
    
// 这就是说，分片范围索引必须是字符的边界。
    
// 如果你的索引在一个字符的中间，程序会惊慌失措。
    
// 所以当从带有特殊字符或表情符号的字符串中创建字符串片断时要小心。
// 是的，这是一些低级别的东西，我们通常不会在日常的Node.js中处理。
}
```
输出
```
sentence is This is a sequence of words.
last_word is "words"
last_part is "words."
without_last_word is "This is a sequence of "
slice_length is 6 bytes
```