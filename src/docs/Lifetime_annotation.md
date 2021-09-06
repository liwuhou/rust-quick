# 生命周期注解

```rust
// 定义一个通用的寿命 'a
// 明确地定义参数的通用寿命
//被称为生命周期注解
// 必须以撇号（'x'）开头。
//惯例是使用单个小写字母（'a, 'b, 'c)
// 但你可以自由地命名它（'a_lifetime, 'toto)
// 注意寿命注释
//在借贷操作符后面有一个空格，然后是类型。
// 在这个例子中，通过对返回类型的注解。
// 我们告诉编译器，返回的值与参数的寿命相同。
// 如果有不同的生存期，编译器将选择最小的生存期。
// 编译器将选择最小的 通过注释参数的寿命，
//我们告诉编译器返回的值与参数的寿命相同。
// 我们给借贷检查器提供信息来验证返回的引用。
fn get_longest_name<'a>(x: &'a str, y: &'a str) -> &'a str {
    if x.len() > y.len() {
        x
    } else {
        y
    }
}
fn main() {
    let result;
    let name1 = String::from("Deep Space 9");
    let name2 = String::from("Voyager");
    result = get_longest_name(&name1, &name2);
    println!("result is {}", result);
}
```

输出
```
result is Deep Space 9
```