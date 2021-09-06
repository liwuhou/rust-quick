# 猜数游戏错误处理重构


use rand::prelude::*;
use std::io;fn main() {
    guess_with_infinite_retry();
}fn guess_with_infinite_retry() {
    let secret_number = thread_rng().gen_range(1..101);
    let mut invalid_numberretry_limit = 0;
    println!("Guess a number between 1 and 100:"); loop {
        let mut buffer = String::new(); let guess = match io::stdin().read_line(&mut buffer) {
            Ok(_) => match buffer.trim().parse::<u32>() {
                Ok(number) => number,
                Err(e) => {
                    invalid_numberretry_limit += 1;
                    if invalid_numberretry_limit == 3 {
                        panic!("Too many invalid numbers entered");
                    } println!("Failed to parse guess: {}", e);
                    println!("Please enter a valid number:");
                    continue;
                }
            },
            Err(e) => {
                println!("Failed to read line: {}", e);
                continue;
            }
        }; if guess < secret_number {
            println!("guess too low, guess higher:");
        } else if guess > secret_number {
            println!("guess too high, guess lower:");
        } else {
            println!("you found it!");
            break;
        }
    }
}

Output

Guess a number between 1 and 100:Failed to parse guess: cannot parse integer from empty string
Please enter a valid number:Failed to parse guess: cannot parse integer from empty string
Please enter a valid number:thread 'main' panicked at 'Too many invalid numbers entered', src/main.rs:19:25
note: run with `RUST_BACKTRACE=1` environment variable to display a backtrace

Or

Guess a number between 1 and 100:
44
guess too low, guess higher:
77
guess too low, guess higher:
99
guess too high, guess lower:
88
guess too high, guess lower:
80
you found it!