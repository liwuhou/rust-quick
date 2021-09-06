# 结构体生命周期注解

```rust
struct Spaceship<'a> {
    
// 该结构拥有该字符串的所有权
    
// 当该结构超出范围时。
    
// 该字符串数据将被丢弃并从堆中删除 
    name: String, 
//该结构并不拥有该字段所引用的数据
    
// 如果该结构仍然可以使用该引用，就会出现模糊不清的情况
    
// 需要添加明确的生命周期注解 
    nickname: &'a str,
}
//将生命期注释为impl。
impl<'a, 'b> Spaceship<'a> {
    
//因为寿命消除规则#3。
    
// 不需要明确的生命期注解
    
// 输出的寿命将作为&self参数的寿命。
    fn send_transmission(&self, msg: &str) -> (&str, &str) {
        println!("Transmitting message: {}", msg);
        (&self.name, self.nickname)
    } 
// 在这里，因为输出寿命与&self输入寿命不同。
    
// 需要明确的寿命注解 
    fn test_send_transmission(&'a self, msg: &'b str) -> &'b str {
        println!("Transmitting message: {}", msg);
        msg
    }
}
fn main() {
    let saucer = Spaceship {
        name: String::from("TR95 MCC Enterprise 9"),
        nickname: "TR95",
    }; 
    let sender = saucer.send_transmission("All aboard!");
    println!("sender is {}", sender.1); 
    let test_msg = saucer.test_send_transmission("this is a test");
    println!("test_msg is {}", test_msg);
}
```
输出
```
Transmitting message: All aboard!
sender is TR95
Transmitting message: this is a test
test_msg is this is a test
```