# 不能恢复的错误


// two types of runtime errors in Rust
// Recoverable (ex: file not found error)
// Unrecoverable (ex: index out of array bounds)// most languages do not distinguish between these errors
// and use Exceptions to handle all of them// Rust does not have traditional Exceptions:// Rust uses the Result<T, E> enum type for recoverable errors// Rust uses panics for unrecoverable errorsfn main() {
    // panic! macro
    // immediately terminates the program
    // and provides feedback to caller of program // panic!("Something went wrong."); let countdown: [i32; 4] = [3, 2, 1, 0];
    for left in countdown.iter() {
        println!("T-minus {}", left); // the program will panic when diving by zero let q = 1 / left;
        println!("q is {}", q);
    }
}

Output

T-minus 3
q is 0
T-minus 2
q is 0
T-minus 1
q is 1
T-minus 0
thread 'main' panicked at 'attempt to divide by zero', /home/<USER>/.rustup/toolchains/stable-x86_64-unknown-linux-gnu/lib/rustlib/src/rust/library/core/src/ops/arith.rs:474:1
note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace
