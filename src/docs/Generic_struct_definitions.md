# 泛型数据结构体定义

```rust
// abstract stand-ins for concrete data types or other properties// can be used with structs, functions, methods, etc. to help eliminate duplicate code// gives flexibility to data types// defined with <T> (T: generic type variable)
// the name of the generic variable is arbitrary, could be <Toto>
// similar to generics in TypeScrypt#[derive(Debug)]
struct Rectangle<T> {
    width: T,
    height: T,
}// multiple generic types#[derive(Debug)]
struct Shape<T, U> {
    width: T,
    height: U,
}fn main() {
    // creating rectangle with f64 data let rect = Rectangle {
        width: 1.2,
        height: 3.4,
    }; println!("rect is {:?}", rect); // creating rectangle with u32 data let rect = Rectangle {
        width: 5,
        height: 11,
    }; println!("rect is {:?}", rect); // creating rectangle with u8 data
    // notice we add u8 as a suffix to the number let rect = Rectangle {
        width: 7u8,
        height: 23u8,
    }; println!("rect is {:?}", rect); // creating shape with u16 and f32 data let rect = Shape {
        width: 456u16,
        height: 78.54f32,
    }; println!("rect is {:?}", rect);
}
```
Output
```
rect is Rectangle { width: 1.2, height: 3.4 }
rect is Rectangle { width: 5, height: 11 }
rect is Rectangle { width: 7, height: 23 }
rect is Shape { width: 456, height: 78.54 }
```

-   Generics are a zero cost abstraction = easier programming without slowing down runtime performance
-   The Rust compiler uses monomorphization for generics = replaces placeholders with concrete data types
-   At compile time, the code will include the concrete data types, not the generic abstraction = if you create a Rectangle with f64 data, the compiled code will have a struct definition for a Rectangle with f64 fields and as many concrete type definitions as the ones when creating struct instances.
-   The source code will use generic data types but the compiled code will have the concrete data types thus not impacting runtime performance (no guess work about data types).