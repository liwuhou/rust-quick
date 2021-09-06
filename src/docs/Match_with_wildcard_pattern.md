# 扩展匹配模式


fn main() {
    let number = 123u8; // match expression returning values based on case
    // match arms are evaluated sequentially from top to bottom let result: &str = match number {
        // match arm
        0 => "zero", // match arm
        1 => "one", // match arm
        2 => "two", // wildcard pattern (default case)
        // represented by an underscore symbol (_)
        // should be used last,
        // otherwise the following arms will not be evaluated.
        // useful when you don't want to define all possible match arms explicitly
        // (or simply because there is a high or infinite number of possibilities) // notice the code block when more than one line _ => {
            println!("{} did not match any arm", number);
            "unmatched"
        }
    }; println!("result is {}", result);
}

Output

123 did not match any arm
result is unmatched
