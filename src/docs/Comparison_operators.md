# 比较运算

```rust

/*
 * 只能比较相同类型的变量
*/
fn main() {
    let a = 11;
    let b = 88; 
    println!("a is {}\nb is {}", a, b); 
    println!("a EQUAL TO b is {}", a == b);
     println!("a NOT EQUAL TO b is {}", a != b);
      println!("a GREATER THAN b is {}", a > b); 
      println!("a GREATER THAN OR EQUAL TO b is {}", a >= b); 
      println!("a LESS THAN b is {}", a < b); 
      println!("a LESS THAN OR EQUAL TO b is {}", a <= b);
       let c = true;
    let d = false; 
    println!("\nc is {}\nd is {}", c, d);
    println!("c EQUAL TO d is {}", c == d);
    println!("c NOT EQUAL TO d is {}", c != d);
    println!("c GREATER THAN d is {}", c > d);
    println!("c GREATER THAN OR EQUAL TO d is {}", c >= d);
    println!("c LESS THAN d is {}", c < d);
    println!("c LESS THAN OR EQUAL TO d is {}", c <= d);
}
```
输出
```
a is 11
b is 88
a EQUAL TO b is false
a NOT EQUAL TO b is true
a GREATER THAN b is false
a GREATER THAN OR EQUAL TO b is false
a LESS THAN b is true
a LESS THAN OR EQUAL TO b is truec is true
d is false
c EQUAL TO d is false
c NOT EQUAL TO d is true
c GREATER THAN d is true
c GREATER THAN OR EQUAL TO d is true
c LESS THAN d is false
c LESS THAN OR EQUAL TO d is false
```