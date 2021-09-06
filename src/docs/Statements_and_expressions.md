# 语句和表达式

```rust
fn main() {
    // Statement performs an action without returning a value 
    // statements end with a semicolon: a = 6;
     // an expression evaluates to a resulting value 
     // expressions do NOT end with a semicolon: 3 + 4 which evaluates to 7
      // adding a semicolon to an expressions transforms it into an statement 
      // expressions are used as parts of statements: let total = r + c;\n\t{}\n\t{}",
       // where "r + c" is an expression and "let total = r + c;" is a statement 
       println!("expression 4 + 5 evaluates to: {}", 4 + 5);
}
```
Output
```
expression 4 + 5 evaluates to: 9
```