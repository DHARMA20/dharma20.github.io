## TIL-Python `*args` and `**kwargs`

If you have done or read some coding you would have come across `*args`  and `**kwargs` . They are used while defining functions and its arguments.

```python
def display_info(*args, **kwargs):
	# code
	pass
```

What are those? Let's find out.

## Usage of `*args`

`*args` allows you to pass a **variable number of positional arguments** to a function. The arguments are collected into a **tuple**, which can be iterated over or used as needed.

- Use `*args` when you don't know how many positional arguments will be passed to the function.
- If no arguments are passed, `*args` will simply be an empty tuple.
- When using `*args` with regular parameters, the regular parameters must appear **before** `*args`.
- Use `*args` when you need to iterate through the arguments.

---
### Example

```python
def greet(greeting, *names):
    for name in names:
        print(f'{greeting}, {name}!')

greet('Hi', "Alice", "Bob", 'Charlie')

# Output
Hi, Alice!
Hi, Bob!
Hi, Charlie!
```

- Note that the `greeting` parameter is defined **before** `*names`.
- The variable `*args` can be replaced with any name; the only rule is to use an asterisk (`*`) before the variable name.


## Usage of `**kwargs`

`**kwargs` allows a function to accept a **variable number of keyword arguments**. These arguments are collected into a **dictionary**, where the keys are the argument names (strings) and the values are the corresponding values.

- Use `**kwargs` when you don't know how many keyword arguments will be passed to the function.
- If no arguments are passed, `**kwargs` will simply be an empty dictionary.
- When using `**kwargs` with regular parameters, the regular parameters must appear **before** `**kwargs`.
- If you are using both `*args` and `**kwargs` in a function, `*args` must come before `**kwargs` in the parameters list.
- Use `**kwargs` when the function should accept optional configuration parameters.

### Example

```python
def introduce(greeting, **kwargs):
    print(greeting)
    for key, value in kwargs.items():
        print(f"{key}: {value}")

introduce("Hello!", name="Alice", hobby="Painting")

# Output
Hello! 
name: Alice 
hobby: Painting
```
