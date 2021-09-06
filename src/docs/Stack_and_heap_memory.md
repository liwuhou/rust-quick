# 堆内存和栈内存

```rust

fn main() {
    println!("=== STACK ====\n");
    println!("- values stored in sequential order of insertion");
    println!("- data added in LIFO (last in first out)");
    println!("- stores variables - pushing values on the stack");
    println!("- also holds info for function execution");
    println!(
        "- stack have very fast access because no guessing where to put data, it will be on top"
    );
    println!("- stacks are limited in size");
    println!("- all data in stack must have a known fixed size\n");
    func1();
    println!("func1 done");
    println!("pop variable y off the stack");
    println!("pop variable z off the stack\n");println!("\n\n=== HEAP ====\n");
    println!("- adding data to heap, search for large enough place in memory to store data");
    println!("- marks memory spot as being used (allocating) and put data in it");
    println!("- accessing data in heap is more complex than the stack because the stack allocates anywhere in available memory");
    println!("- slower than stack");
    println!("- dynamically add and remove data");
    println!("\n\n=== POINTER ====\n");
    println!("- data type that stores a memory address");
    println!("- pointers have a fixed size so can be stored on the stack");
    println!("- adding and accessing data on the heap is done through pointers (addresses in memory)");
}
fn func1() {
    println!("func1 executing...");
    let y = 3.11;
    println!("push variable y = {} onto the stack", y);
    let z = 5;
    println!("push variable z = {} onto the stack", z);
    func2();
    println!("func2 done");
    println!("pop variable arr off the stack");
}
fn func2() {
    println!("func2 executing...");
    let arr = [2, 3, 4];
    println!("push variable arr = {:?} onto the stack", arr);
}
```
Output
```
=== STACK ====- 
values stored in sequential order of insertion
- data added in LIFO (last in first out)
- stores variables - pushing values on the stack
- also holds info for function execution
- stack have very fast access because no guessing where to put data, it will be on top
- stacks are limited in size
- all data in stack must have a known fixed sizefunc1 executing...
push variable y = 3.11 onto the stack
push variable z = 5 onto the stack
func2 executing...
push variable arr = [2, 3, 4] onto the stack
func2 done
pop variable arr off the stack
func1 done
pop variable y off the stack
pop variable z off the stack=== HEAP ====- adding data to heap, search for large enough place in memory to store data
- marks memory spot as being used (allocating) and put data in it
- accessing data in heap is more complex than the stack because the stack allocates anywhere in available memory
- slower than stack
- dynamically add and remove data=== POINTER ====- data type that stores a memory address
- pointers have a fixed size so can be stored on the stack
- adding and accessing data on the heap is done through pointers (addresses in memory)
```
