# 借用检查

```rust
// 借用检查器
// 比较作用域以确定所有借用是否有效
// 注释为"'a'"的变量的寿命（它的存活时间）。

// 变量的寿命与它的作用域有关
// Rust会分析变量所引用的值的范围/寿命。

// 使用借用检查器
fn main() {
    let fuel; 
// ========= START lifetime ('a) of fuel ========== 
    {
        let gasoil = String::from("gasoil"); 
// ===== START lifetime ('b) of gasoil ======= 
        fuel = &gasoil; 
        println!("fuel is {}", fuel);
    } 
// ========= END lifetime of gasoil ================
} 
// ========= END lifetime of fuel ================
```
借用检查器检测到的错误。

```rust
fn main() {
    let fuel; 
// ========= START 'a ================ 
    {

        let gasoil = String::from("gasoil"); 
// ===== START 'b ===== 
        fuel = &gasoil; 
    } 
// ========= END 'b ================

    
// fuel存储了一个借来的对gasoil的引用。
    
// gasoil的生命周期已经结束
    
// fuel包含一个悬空的引用，程序将无法编译 
    println!("fuel is {}", fuel);
} 
// ========= END 'a ================
```
通过延长gasoil的使用寿命来修复寿命错误。
```rust
fn main() {
    let fuel; 
// ========= START 'a ================ 
    let gasoil = String::from("gasoil"); 
// ======= START 'b ======== 
    {
        fuel = &gasoil;
    }

    println!("fuel is {}", fuel);
} 
// ========= END 'a and 'b ================

```
输出
```
fuel is gasoil
```