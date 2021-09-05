# 布尔运算和二进制代数

```rust
fn main() {
    let a = true;
    let b = false;
    println!("a is {}\nb is {}", a, b); 
    println!("NOT a is {}", !a);
    println!("a AND b is {}", a & b);
    println!("a OR b is {}", a | b);
    println!("a XOR b is {}", a ^ b); 
    // boolean casted to integer begets 0 or 1 println!("a XOR b is {}", (a ^ b) as i32); 
    // 1 
    let c = (a ^ b) | (a & b);
    println!("c is {}", c); 
    // short-circuiting logical operations:
    // right operand not evaluated 
    let d = true || (a & b);
    println!("d is {}", d); 
    // the panic macro is not evaluated,
    // so the process ends with status 0 (OK, no error)
    // panics exit the program immediately (like throwing error in Node.js)
    let e = false && panic!();
    println!("e is {}", e);
}
```

Output

```
a is true
b is false
NOT a is false
a AND b is false
a OR b is true
a XOR b is true
a XOR b is 1
c is true
d is true
e is false
```