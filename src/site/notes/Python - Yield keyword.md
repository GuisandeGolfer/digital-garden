---
{"dg-publish":true,"permalink":"/python-yield-keyword/","noteIcon":"","updated":"2024-08-26T21:39:20.362-07:00"}
---


# Python3 - Yield keyword
---

- take a text file that you may have.

and you want to read each line from the file:

```python

def fetch_lines(filename):
	with open(filename, "r") as file:
		lines = []
		for line in lines:
			lines.append(line)
		return lines

zen = fetch_lines("<file-name-here>.txt")
print(zen)
```

since we are storing the lines of the text file in `list = []`, we are storing those lines in the memory of our program (stack/heap)

but what if the file was million's of lines long?

then our program would crash.

### What if we just get one line at a time?

pull a line, do what we need to do, erase it from memory (the stack), and then move onto the next one.

That's where: 
>[!award] Python Generators come in...

you can change the code above to instead use the `yield` keyword.

```python

def fetch_lines(filename):
	with open(filename, "r") as file:
		# lines = []
		for line in lines:
			yield line
			# lines.append(line)
		# return lines

zen = fetch_lines("<file-name-here>.txt")
print(zen)
```

instead of printing out the whole array, it will print out
```bash
<generator object fetch_lines at 0x00000002789FDSE>
```

to get values out of this *generator object*, we say `next(zen)`

and we will get the next line.

- @ It's like a for-loop that is frozen in time, and we can control the actions of that frozen for-loop dynamically. 

---
## Now that we know what Yield does...How can you use `yield from`?
---

- example
```python
def generator():
	yield 1
	yield 2
	yield "hello world"

gen = generator()

next(gen)
next(gen)
next(gen)
```

you can pass an iterable or another generator to `yield from` to get the same type of results or effect

like so:

```python
def generator():
	yield 1
	yield 2
	yield 3

def other_generator():
	yield "goodbye"

	yield from generator()

	yield "hello again"


for item in other_generator():
	print(item)
```

This will print out:

```bash
goodbye
1
2
3
"hello again"
```

This is a good paradigm to use when you are handling an iterable where you don't know the end length and don't want your program's memory to expand rapidly if you get a very large sized iterable (think millions).

- ! You can even send information into subgenerators in order to do further data handling or exception Handling

- This is sometimes called "coroutine behavior"

once `yield` ends up on the value side of the assignment, it turns the generator into a coroutine and allows the generator to receive values (like done by `delegator`)

but when `yield` is on the left side; it sends the value out of the generator.

```python
def subgen():
	while True:
		x = yield
		yield x * 2


def delegator():
	yield from subgen()

g = delegator()

next(g) # prime the generator
g.send(3)
print(next(g)) # sends 3 to subgen, recieves 6
g.send(5)
print(next(g)) # sends 5 to subgen, recieves 10 
```

if you need a more verbose example:

```python
def verbose_subgen():
    while True:
        print("Waiting to receive...")
        x = yield
        print(f"Received: {x}")
        result = x * 2
        print(f"Sending back: {result}")
        yield result


g = verbose_subgen()
next(g)  # Prime the generator
print("Main: Sending 3")
g.send(3)
print(f"Main: Got back {next(g)}")
print("Main: Sending 5")
g.send(5)
print(f"Main: Got back {next(g)}")
```

You need to "prime" the generator in order for `verbose_subgen` to get to it's first yield statement.

if you don't you get this error.

```python
Traceback (most recent call last):
  File "/Users/diegoguisande/Desktop/PARA/Projects_1/fastAPI/./scratch.py", line 33, in <module>
    g.send(3)
TypeError: can't send non-None value to a just-started generator
```