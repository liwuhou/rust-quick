# 字数统计

创建一个名为 "lorem.txt "的文件，内容如下。

```text
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis porta velit quis mattis bibendum. Fusce sed nulla eget arcu lacinia placerat ac eget dui. Nam a ante tellus. Aliquam varius tincidunt nisi a efficitur. Donec non malesuada odio. Donec vitae arcu eu magna efficitur pulvinar. Proin feugiat, erat et congue aliquet, ipsum turpis volutpat ante, a ullamcorper magna elit nec libero. Maecenas lacus magna, gravida id tristique at, lobortis sit amet libero.Donec vel nunc ac sapien tempus vehicula. Aenean vulputate quam eget felis elementum suscipit. Aliquam vehicula odio dui, id varius lectus gravida consequat. Maecenas sit amet dolor erat. Duis rhoncus mollis nulla. Etiam pellentesque arcu sed pretium fermentum. Phasellus metus velit, dapibus eu pellentesque eu, pulvinar eu nunc. In posuere massa non elementum varius. Donec et vehicula urna, id dignissim ex.Nunc vitae sem volutpat, malesuada odio vel, ornare arcu. Nunc dictum tincidunt turpis, sed tristique tellus hendrerit at. In ac tempor lacus. Pellentesque tempus velit eu pharetra consectetur. Integer ultricies sem sem, a tincidunt urna tempus quis. Nullam porttitor turpis ut lacus mollis dignissim nec vel ipsum. Integer volutpat quam et enim pellentesque, ut imperdiet nibh faucibus. Vestibulum varius, libero eget porta congue, enim risus porttitor lacus, at pretium mauris ligula sit amet ligula.Donec at pharetra elit. Sed nulla dui, consectetur sollicitudin magna a, consequat maximus erat. Maecenas ultricies libero orci, a cursus justo blandit non. Vivamus non fringilla ante. In cursus finibus elit quis cursus. Maecenas at arcu id ex consectetur eleifend. Aenean nec purus eget odio commodo ullamcorper. Integer maximus quis turpis id finibus. Etiam mi nunc, fringilla eget diam non, gravida blandit nisl. Curabitur finibus bibendum consequat. Nunc eleifend aliquam risus a iaculis.Nullam id lacus sem. Suspendisse a nunc facilisis, rutrum purus aliquet, pulvinar libero. Etiam ornare, enim at egestas varius, mi justo feugiat purus, eget congue nisi nibh vitae mauris. Integer malesuada, diam et placerat mollis, purus nulla molestie lacus, in egestas nisl lacus et odio. Fusce feugiat odio eget justo lacinia placerat. In rutrum et quam sed gravida. Vivamus vel blandit metus, sed imperdiet turpis. Sed facilisis ipsum ipsum, egestas mattis dolor tempus at. Morbi eu scelerisque ante.
```

源代码

```rust
use std::collections::HashMap;
use std::env;
use std::fmt;
use std::fs;#[derive(Debug)]
struct MostCommonWord {
    value: String,
    occurrence: u32,
}impl fmt::Display for MostCommonWord {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        write!(
            f,
            "\"{}\" is the most common word with {} occurrences",
            self.value, self.occurrence
        )
    }
}
impl MostCommonWord {
    fn new(value: &str, occurrence: u32) -> MostCommonWord {
        MostCommonWord {
            value: value.to_string(),
            occurrence,
        }
    }
}
fn main() {
    if env::args().len() != 2 {
        println!("this program requires one argument");
        return;
    } 
    let filepath = match env::args().nth(1) {
        Some(text) => text,
        None => panic!("Failed to get file path"),
    }; 
    println!("filepath is {}", filepath);
      let file_content = match fs::read_to_string(filepath) {
        Ok(content) => content,
        Err(e) => panic!("Err: {}", e),
    }; 
    println!("file_content is:\n {}", file_content);
    let mut word_count: HashMap<String, u32> = HashMap::new();
    for word in file_content.split_whitespace() {
        let lowercase_word = word.to_lowercase(); 
        match word_count.get(&lowercase_word) {
            Some(count) => {
                let increment = *count + 1;
                word_count.insert(lowercase_word, increment);
            }
            None => {
                word_count.insert(lowercase_word, 1);
            }
        };
    }
    let mut most_common = MostCommonWord::new("", 0);
    let mut most_common_words = vec![]; 
    for (word, count) in &word_count {
        if most_common.occurrence < *count {
            most_common.value = word.to_string();
            most_common.occurrence = *count;
        }
    } 
    most_common_words.push(most_common);
    for (word, count) in &word_count {
        if most_common_words[0].value != word.to_string()
            && most_common_words[0].occurrence == *count
        {
            let other_most_common = MostCommonWord::new(word, *count);
            most_common_words.push(other_most_common);
        }
    }
    if most_common_words.len() > 1 {
        println!("The most common words in the text are;");
        for most_common in most_common_words {
            println!(
                "\"{}\" with {} occurrences",
                most_common.value, most_common.occurrence
            );
        }
    } else if most_common_words.len() == 1 {
        println!("{}", most_common_words[0]);
    }
}
```
输出
```bash
$ cargo run lorem.txt
"eget" is the most common word with 8 occurrences
```

替代实现

```rust
use std::env;
use std::fs;
use std::collections::HashMap;fn main() {
    // 读取文件并建立单个单词的向量
    let contents = match env::args().nth(1) {
        Some(f) => match fs::read_to_string(f) {
            Ok(s) => s.to_lowercase(),
            Err(e) => {
                eprintln!("Could not read file: {}", e);
                std::process::exit(1);
            }
        },
        None => {
            eprintln!("Program requires an argument: <file path>");
            std::process::exit(2);
        }
    }; 
    let all_words = contents.split_whitespace().collect::<Vec<&str>>(); 
    // 计算每个独特的词出现了多少次 
    let mut word_counts: HashMap<&str, u32> = HashMap::new(); 
    for word in all_words.iter() {
        *word_counts.entry(word).or_insert(1) += 1;
    }

    // 确定最常使用的单词
     let mut top_count = 0u32; 
     let mut top_words: Vec<&str> = Vec::new(); 
     for (&key, &val) in word_counts.iter() {
        if val > top_count {
            top_count = val;
            top_words.clear();
            top_words.push(key);
        } else if val == top_count {
            top_words.push(key);
        }
    } 
    // 显示结果
    println!("Top word(s) occurred {} times:", top_count);
    for word in top_words.iter() {
        println!("{}", word);
    }
}
```