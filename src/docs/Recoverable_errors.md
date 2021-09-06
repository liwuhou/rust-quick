# 可恢复的错误


// recoverable errors// errors that do not cause the program to fail
// and can be corrected// Rust uses the Result<T,E> enum type to handle recoverable errors// enum Result<T, E> {
//     Ok(T),
//     Err(E),
// }// the Ok variant stores the value of the successful operation
// the Err variant stores the value of the error// the Result enum is included in the preludeuse std::fs;
use std::io;fn main() {
    // read_to_string() returns a Result<T, E> enum // create a file named file.txt in the root of the project folder:
    // $ echo 42 > file.txt let content: Result<String, io::Error> = fs::read_to_string("file.txt"); // avoid the unwrap() method
    // because will panic if this is the Err variant of the Result enum println!("content is {:?}", content.unwrap()); // for custom error message, use expect()
    // not the best way to handle recoverable errors let content: Result<String, io::Error> = fs::read_to_string("file-x.txt"); println!("content is {:?}", content.expect("failed reading file"));
}

Output

content is "42\n"
thread 'main' panicked at 'failed reading file: Os { code: 2, kind: NotFound, message: "No such file or directory" }', src/main.rs:35:41
