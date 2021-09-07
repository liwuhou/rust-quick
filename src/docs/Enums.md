# 枚举
```rust

//定义了一个具有多种可能变体的数据类型
enum Controller {
    Turbo,
    Up,
    Down,
    Left,
    Right,
    X,
    Y,
    A,
    B,
}
fn push_button_notify(c: &Controller) {
    
// 模式匹配（相当于JavaScript中的switch）。
    match c {
        Controller::Turbo => println!("Turbo button pushed."),
        Controller::Up => println!("Up button pushed."),
        Controller::Down => println!("Down button pushed."),
        Controller::Left => println!("Left button pushed."),
        Controller::Right => println!("Right button pushed."),
        Controller::Y => println!("Y button pushed."),
        Controller::X => println!("X button pushed."),
        Controller::A => println!("A button pushed."),
        Controller::B => println!("B button pushed."),
    }
}
fn main() {
    let secret_push_combo = [
        Controller::Up,
        Controller::Left,
        Controller::A,
        Controller::Turbo,
        Controller::Y,
        Controller::B,
        Controller::Turbo,
        Controller::Down,
        Controller::Right,
        Controller::X,
    ];
     for push in secret_push_combo.iter() {
        push_button_notify(push);
    }
}
```
输出
```
Up button pushed.
Left button pushed.
A button pushed.
Turbo button pushed.
Y button pushed.
B button pushed.
Turbo button pushed.
Down button pushed.
Right button pushed.
X button pushed.
```