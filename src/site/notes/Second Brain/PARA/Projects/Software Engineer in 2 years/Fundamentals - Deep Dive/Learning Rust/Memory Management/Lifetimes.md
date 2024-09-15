---
{"dg-publish":true,"dg-path":"Projects/Software Engineer in 2 years/Fundamentals - Deep Dive/Learning Rust/Memory Management/Lifetimes.md","permalink":"/projects/software-engineer-in-2-years/fundamentals-deep-dive/learning-rust/memory-management/lifetimes/","noteIcon":"","updated":"2024-09-14T21:14:52.472-07:00"}
---


>[!compass] Lifetime - the span of the program which a specific place of data is valid.

![Screenshot 2024-09-14 at 5.07.58 PM.png](/img/user/Second%20Brain/PARA/Projects/Software%20Engineer%20in%202%20years/Fundamentals%20-%20Deep%20Dive/Learning%20Rust/Memory%20Management/attachments/Screenshot%202024-09-14%20at%205.07.58%20PM.png)

The [[Second Brain/PARA/Projects/Software Engineer in 2 years/Fundamentals - Deep Dive/Learning Rust/Memory Management/Borrow Checker\|Borrow Checker]] evaluates the lifetimes of values in order to make sure the [[Second Brain/PARA/Projects/Software Engineer in 2 years/Fundamentals - Deep Dive/Learning Rust/Memory Management/Borrowing\|Borrowing]] rules are not being broken.

the goal is to check if:

>[!activity] The references lifetime does not outlive the owner value's lifetime (the original)

Last Example:

```rust
fn main() {
	let s1 = String:from("hello world");
	let s2 = String:from("hello world again");

	let result: &str = longest(s1.as_str(), s2.as_str());

	println!("The longest string is {}", result);
}

// ERROR: missing lifetime specifier
fn longest(a: &str, b: &str) -> &str {
	if a.len() > b.len() {
		a
	} else {
		b
	}
}
```

### Concrete vs Generic Lifetimes
---
**concrete** == the span of code where the ownership is valid and that the compiler infers. 

but **generic** lifetimes are a type of generic that inform the compiler how references to data should be related to each other and ensuring that data lives long enough to be accessed.

take these for example

### Concrete Lifetimes
```rust
fn get_static_str() -> &'static str {
	"I live forever!" 
	// This string lives for the entire duration of the program
}

fm main() {
	let s: &'static str = get_static_str();
	println!("{}", s);
}
```

### Generic lifetime
---
```rust
fn get_str_with_lifetime<'a>(input: &'a str) -> &'a str {
	input 
	// the returned reference has the same lifetime as the input
}

fn main() {
	let input = String::from("hello");
	let result = get_str_with_lifetime(&input);
	println!("{}", result);
	// safe because input and result have the same lifetime.
}
```

Here, `'a` is a **generic lifetime**. It doesn't specify how long the reference will live; it only guarantees that `result` will not outlive `input`.

In short:

- **Concrete lifetimes** are explicit (like `'static`).
- **Generic lifetimes** allow for flexibility in how long references can live while ensuring safety.


