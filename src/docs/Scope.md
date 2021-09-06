# 范围
```rust


fn main() {
    let planet = "Dunya";
    if true {
        let planet = "Jupiter";
        println!("planet is {}", planet);
    } 
    println!("planet is {}", planet);
}
```

Output
```
planet is Jupiter
planet is Dunya
```