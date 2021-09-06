# 不能恢复的错误

```rust
// Rust中的两类运行时错误
// 可恢复的（例如：未找到文件错误）。
// 不可恢复的（例如：索引超出了数组的界限）。
// 大多数语言对这些错误不加区分
// 并使用异常来处理所有这些错误
// Rust没有传统的Exceptions。
// Rust使用Result<T, E>枚举类型来处理可恢复错误。
// Rust使用panics来处理不可恢复的错误。
fn main() {
    // panic! 宏
    // 立即终止程序
    // 并向程序的调用者提供反馈 
    // panic!("Something went wrong."); 
    let countdown: [i32; 4] = [3, 2, 1, 0];
    for left in countdown.iter() {
        println!("T-minus {}", left); 
         // 当除值为零时，程序会panic q = 1 / left;
        println!("q is {}", q);
    }
}
```
输出
```

T-minus 3
q is 0
T-minus 2
q is 0
T-minus 1
q is 1
T-minus 0
thread 'main' panicked at 'attempt to divide by zero', /home/<USER>/.rustup/toolchains/stable-x86_64-unknown-linux-gnu/lib/rustlib/src/rust/library/core/src/ops/arith.rs:474:1
```
注意：使用`RUST_BACKTRACE=1`环境变量运行，以显示回溯。
