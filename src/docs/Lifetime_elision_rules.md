# 生命周期剥离规则

```rust

// 寿命消除规则
// 编译器分析引用寿命的一套规则。

// 描述了不需要明确的寿命注释的情况
// 如果有任何不明确的地方，就需要明确的寿命注释。
// 目前，有3条寿命消除规则。
// #1

// 每个作为参考的输入参数都被分配了自己的生命周期
// 
//fn get_first_word<'a>(s: &'a str) -> &str {
// 寿命只适用于作为引用的参数。

// 非引用参数不需要它们
// fn get_first_word<'a>(s: &'a str, t: i32) -> &str {
// fn get_first_word<'a, 'b>(s: &'a str, t: &'b str) -> &str {

// fn get_first_word<'a, 'b, 'c>(s: &'a str, t: &'b str, u: &'c str) -> &str {
// #2

// 如果只有一个输入寿命。

// 将其分配给所有的输出寿命

// （输出寿命必须与输入寿命之一相匹配）。
//符合删除的条件，因此可以省略寿命。

// fn get_first_word<'a>(s: &'a str) -> &'a str {

// ==>``fn get_first_word(s: &str) -> &str {
// #3

// 如果有一个&self或&mut self输入参数。

// 它的寿命将被分配给所有的输出寿命
// fn do_stuff(&self, input: &str) -> &str {

// rule #1 ==> fn do_stuff<'a,'b>(&'a self, input: &'b str) -> &str {

// rule #3 ==> fn do_stuff<'a,'b>(&'a self, input: &'b str) -> &'a str {
// 这些删除规则是为编译器准备的

// 但知道什么时候可以省略寿命是很好的。
fn main() {
    let message = String::from("Hi there");
    let first_word = get_first_word(&message);
    println!("first_word is {}", first_word);
}
fn get_first_word(s: &str) -> &str {
    let bytes = s.as_bytes(); 
    for (index, &item) in bytes.iter().enumerate() {
        if item == b' ' {
            return &s[..index]; 
// 有空格
        }
    } 
    &s 
// 无空格，所以输入的字符串是一个完整的单词
}
```
输出
```
first_word is Hi
```
