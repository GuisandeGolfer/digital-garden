---
{"dg-publish":true,"dg-path":"Projects/Software Engineer in 2 years/Fundamentals - Deep Dive/Learning Rust/Memory Management/Borrowing.md","permalink":"/projects/software-engineer-in-2-years/fundamentals-deep-dive/learning-rust/memory-management/borrowing/","noteIcon":"","updated":"2024-09-14T17:07:04.721-07:00"}
---


Using references in Rust is called **Borrowing**.

Here is a simple example:

```rust
fn main() {
	let s1 = String::from("Let's get Rusty");
	print_string(&s1);
	print_string(&s1);
}

fn print_string(s: &str) {
	println!("{s}");
}
```

There are two **borrowing** rules:

> [!book] 1. at any given time, you can have either one mutable reference or any number of immutable references

example:

```rust
fn main() {
	let s1 = String::from("Let's get Rusty");
	let r1 = &s1;
	let r2 = &s1;
	print_string(r1);
}

fn print_string(s: &str) {
	println!("{s}");
}
```

**borrowing** is not violated here because these references (and original value) is immutable (no values were manipulated only read; not updated/written)

but if we do this instead (add the`mut` keyword for `s1`)

```rust
fn main() {
	let mut s1 = String::from("Let's get Rusty");
	let r1 = &s1;
	let r2 = &mut s1;
	// cannot borrow 's1' as mutable because it is also borrowed as immutable.
	print_string(r1);
}

fn print_string(s: &str) {
	println!("{s}");
}
```

if you get the next reference then you are understanding why this is important:

```rust
fn main() {
	let mut x = vec![1, 2, 3];

	let last = x.last().unwrap();

	x.push(4);

	println!("{:?}", last);
}
```

Why would this not work?

>[!caution]- Answer
>- because `.last()` takes ownership of the value of x due to the function pass of `.last().unwrap()`
>- so if the compiler did not catch our error
>- last could be pointing to a memory location that does not exist anywhere.

Correct Code:

```rust
fn main() {
	let mut x = vec![1, 2, 3];

	x.push(4);

	let last = x.last().unwrap();

	println!("{:?}", last);
}
```

This way there is only one mutable reference to x.

>[!boxes] 2. References must always be valid.

```rust
fn main() {
	let r;
	{
		let s = String::from("lets get rusty");

		r = &s;
	}
		// borrowed value (&s) does not live long enough.

	println!("{}", r);
}
```

since the `r` *owner* definition was dropped when leaving the inner scope.

the `println!` statement would not work due to no borrow / references existing on the heap / memory.

The `does not live long enough` is a Rust attribute called [[Second Brain/PARA/Projects/Software Engineer in 2 years/Fundamentals - Deep Dive/Learning Rust/Memory Management/Lifetimes\|Lifetimes]]
