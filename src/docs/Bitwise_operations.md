# 位操作运算

```rust
/*
位操作：对单个比特而不是字节集进行操作。
- 二进制表示，一个字节的序列
- 为了便于阅读，允许使用下划线分隔符
- 默认情况下，二进制表示法被存储为i32
*/
fn main() {
    //通过添加后缀u8存储为u8

    let mut value = 0b1111_0101u8; 
    //将打印基数10（十进制）表示法

    println!("value is {}", value); 
    /*
    :08b
        0 -> 显示前导零
        8 -> 显示的比特数
        b -> 显示二进制表示法
    */
    println!("value is {:08b}", value); 
    // 比特式非：反转各个比特

    value = !value; 
    // 0000_1010
    println!("value is {:08b}", value); 
    // 比特式和：用于清除一个特定位的值值=值&0b1111_0111。
    // -> 0000_0010
    println!("value is {:08b}", value); 
    // 比特式和：用于检查特定位的值
    // 如果一个特定的位是0或1，对检查进程状态的寄存器的状态很有用

    println!("value is {:08b}", value & 0b0100_0000);
   // --> 0000_0000 
   // 位法OR：如果任一操作数为1，结果为1
    // 对设置一个特定位的值很有用

    value = value | 0b0100_0000; 
    // -> 0100_0010
    println!("value is {:08b}", value); 
    // 按位数XOR（排他性OR）。
   // 只有当位数不同时，结果为1，否则为0
   // 如果有不同的位，可以设置为0

   value = value ^ 0b0101_0101; 
   // -> 0001_0111
   println!("value is {:08b}", value); 
   ////////////////////////////
   // 位移运算符
   //////////////////////////// 
   // 将比特模式向左或向右移动若干比特
   // 并用零回填移位的位空间 
   // 左移4位

   value = value << 4; 
   // -> 0111_0000
   println!("value is {:08b}", value); 
   // 右移3位

   value = value >> 3; 
   // -> 0000_1110
   println!("value is {:08b}", value);
}
```
输出
```
value is 245
value is 11110101
value is 00001010
value is 00000010
value is 00000000
value is 01000010
value is 00010111
value is 01110000
value is 00001110
```