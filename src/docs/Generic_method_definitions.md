# 泛型方法定义

```rust

#[derive(Debug)]
struct Rectangle<T> {
    width: T,
    height: T,
}#[derive(Debug)]
struct Shape<T, U> {
    width: T,
    height: U,
}// include the generic variable names after the impl keyword
// and after the struct identifier
// impl<T, U> tells the compiler that methods for generic struct definitionimpl<T, U> Shape<T, U> {
    fn get_width(&self) -> &T {
        // need to return a reference
        // because not know by which type <T> will be replaced with
        // remember ownership for fixed / mutable-length data type
        // returning a reference works for both without transfer of ownership &self.width
    }
}// implementing methods for a specific concrete type of Shape
// notice not putting generic types after impl keyword tells the compiler that these methods are for concrete struct defintitionimpl Shape<u8, u8> {
    fn get_perimeter(&self) -> u8 {
        (self.height + self.width) * 2
    }
}fn main() {
    let rect = Rectangle {
        width: 1.2,
        height: 3.4,
    }; println!("rect is {:?}", rect); let rect = Rectangle {
        width: 5,
        height: 11,
    }; println!("rect is {:?}", rect); let rect = Rectangle {
        width: 7u8,
        height: 23u8,
    }; println!("rect is {:?}", rect); let rect = Shape {
        width: 456u16,
        height: 78.54f32,
    }; println!("rect is {:?}", rect); println!("rect width is {:?}", rect.get_width()); let rect = Shape {
        width: 54u8,
        height: 32u8,
    }; // get_perimeter() method is defined on this instance of Shape
    // because the fields are both u8 data
    // otherwise this method would be not be found println!("rect perimter is {:?}", rect.get_perimeter());
}
```
输出
```
rect is Rectangle { width: 1.2, height: 3.4 }
rect is Rectangle { width: 5, height: 11 }
rect is Rectangle { width: 7, height: 23 }
rect is Shape { width: 456, height: 78.54 }
rect width is 456
rect perimter is 172
```