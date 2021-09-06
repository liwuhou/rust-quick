# 语句和表达式

```rust
fn main() {
    // 语句执行一个动作而不返回一个值 
    // 语句以分号结尾：a = 6。
     // 表达式评估为一个结果值 
     // 表达式不以分号结束。3 + 4，评估结果为7
      // 在表达式中加入分号可以将其转化为一个语句。
      // 表达式可以作为语句的一部分使用： let total = r + c;\n\t{}\n\t{}"。
       // 其中 "r + c "是一个表达式，"let total = r + c; "是一个语句。
       println!("expression 4 + 5 evaluates to: {}", 4 + 5);
}
```
输出
```
expression 4 + 5 evaluates to: 9
```