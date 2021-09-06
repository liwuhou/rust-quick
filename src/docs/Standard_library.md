# 标准库

-   documentation: <https://doc.rust-lang.org/std/>

```rust

// the use statement is used to import crates/libraries
// it brings a module path into the scope of a program// some modules of the standard library are not part of the Rust language itself
// (meaning, you need to import them - like the "fs" module in Node.js - otherwise the compiler will not know what they mean)// the standard library is available to all programs by default// the [prelude](https://doc.rust-lang.org/std/prelude/index.html)  is a list of things that are automatically imported into every Rust program
// it does not import the entire std library (only the most common standard modules)// if a module is not included into the prelude, you need to manually import ituse std::thread;fn main() {
    let child = thread::spawn(move || 2 + 2);
    let res = child.join(); println!("res is {}", res.unwrap());
}
```

输出
```

res is 4
```