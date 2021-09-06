# 定位枚举

```rust
use std::fmt;
enum Location {
    Unknown,
    Anonymous,
    Known(f64, f64), 
    // 纬度、经度
}
impl fmt::Display for Location {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        match self {
            Location::Anonymous => write!(f, "Location is anonymous"),
            Location::Unknown => write!(f, "Location is unknown"),
            Location::Known(latitude, longitude) => {
                write!(f, "latitude: {} longitude: {}", latitude, longitude)
            }
        }
    }
}
fn main() {
    let address = Location::Anonymous;
    println!("address is {}", address);
    let address = Location::Unknown;
    println!("address is {}", address);
    let address = Location::Known(123.4, 456.7);
    println!("address is {}", address);
}
```
输出
```

address is Location is anonymous
address is Location is unknown
address is latitude: 123.4 longitude: 456.7
```