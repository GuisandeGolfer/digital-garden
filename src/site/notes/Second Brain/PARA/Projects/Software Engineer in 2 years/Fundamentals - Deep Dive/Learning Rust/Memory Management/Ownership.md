---
{"dg-publish":true,"dg-path":"Projects/Software Engineer in 2 years/Fundamentals - Deep Dive/Learning Rust/Memory Management/Ownership.md","permalink":"/projects/software-engineer-in-2-years/fundamentals-deep-dive/learning-rust/memory-management/ownership/","noteIcon":"","updated":"2024-09-14T16:41:44.456-07:00"}
---


# Rules
---
>[!boxes] 1. each value in Rust has an owner.

```rust
fn main() {
	let s1 = String::from("Let's get Rusty");
}
```

the *value* is the heap-allocated string
the *owner* is the `s1` variable

>[!boxes] 2. There can only be one owner at a time

so if we do this: 

```rust
fn main() {
	let s1 = String::from("Let's get Rusty");
	let s2 = s1;

	println!("{s1}");
}
```

we get the error `borrow of moved value s1`

s2 becomes the *new owner* of s1's *value* and printing s1 is invalid

but if we clone s1 (make a new copy of the *value*)`let s2 = s1.clone();` 
This code would be valid.

passing *values* as arguments (moving a value) apply to rule 2 as well.

```rust
fn main() {
	let s1 = String::from("Let's get Rusty");
	let s2 = s1;
	print_string(s2);
}

fn print_string(s: String) {
	println!("{s}");
}
```

the argument `s` becomes the new owner of `s2`'s *value* which leads to **rule 3**

>[!boxes] 3. When the owner goes out of scope, the value will be dropped.

so after the `print_string` function finishes and the scope switches back to main(); the *value* owned by *s* gets dropped and cleaned up from memory (heap or stack)

There are ways to temporarily avoiding this ownership rule:

- using `.clone()` to make a copy (more memory) and passing that copy into the function.
- or have the function pass the value back in the return statement.

## References

instead of giving full ownership, we can pass a *reference* to the function.

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

---

This is called [[Second Brain/PARA/Projects/Software Engineer in 2 years/Fundamentals - Deep Dive/Learning Rust/Memory Management/Borrowing\|Borrowing]]








