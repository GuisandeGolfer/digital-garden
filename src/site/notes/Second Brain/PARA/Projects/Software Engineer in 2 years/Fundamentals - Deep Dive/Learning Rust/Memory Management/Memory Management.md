---
{"dg-publish":true,"dg-path":"Projects/Software Engineer in 2 years/Fundamentals - Deep Dive/Learning Rust/Memory Management/Memory Management.md","permalink":"/projects/software-engineer-in-2-years/fundamentals-deep-dive/learning-rust/memory-management/memory-management/","noteIcon":"","updated":"2024-09-14T17:08:28.720-07:00"}
---


- **[[Second Brain/PARA/Projects/Software Engineer in 2 years/Fundamentals - Deep Dive/Learning Rust/Memory Management/Memory Management\|Memory Management]]**
	- **attachments**

	- [[Second Brain/PARA/Projects/Software Engineer in 2 years/Fundamentals - Deep Dive/Learning Rust/Memory Management/Borrow Checker\|Borrow Checker]]
	- [[Second Brain/PARA/Projects/Software Engineer in 2 years/Fundamentals - Deep Dive/Learning Rust/Memory Management/Borrowing\|Borrowing]]
	- [[Second Brain/PARA/Projects/Software Engineer in 2 years/Fundamentals - Deep Dive/Learning Rust/Memory Management/Lifetimes\|Lifetimes]]
	- [[Second Brain/PARA/Projects/Software Engineer in 2 years/Fundamentals - Deep Dive/Learning Rust/Memory Management/Memory Management\|Memory Management]]
	- [[Second Brain/PARA/Projects/Software Engineer in 2 years/Fundamentals - Deep Dive/Learning Rust/Memory Management/Ownership\|Ownership]]



Normally managing memory on the heap comes from two ways:

1. a garbage collector doing it for you or
	1. too much runtime overhead
2. using malloc / free to do it yourself
	1. too error prone

>[!book] The Rust "Borrow Checker" (inside compiler) enforces rules at compile that makes violating memory safety impossible
>- These are [[Second Brain/PARA/Projects/Software Engineer in 2 years/Fundamentals - Deep Dive/Learning Rust/Memory Management/Ownership\|Ownership]] and [[Second Brain/PARA/Projects/Software Engineer in 2 years/Fundamentals - Deep Dive/Learning Rust/Memory Management/Borrowing\|Borrowing]]

