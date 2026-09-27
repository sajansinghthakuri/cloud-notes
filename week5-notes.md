# Week 5 – Python I: Core Language

**Date:** September 27, 2026

## Goal

Build fluency with Python fundamentals and develop the ability to use Python for automation, scripting, and future Cloud/DevOps work.

The goal of this week was not to learn frameworks or cloud-specific Python libraries, but to become comfortable with the language itself.

---

## Overview

After completing the initial Linux fundamentals, I moved into the programming section of my Cloud Engineering roadmap.

This week focused entirely on Python fundamentals.

I worked through Python's core syntax, built-in data types, data structures, control flow, comprehensions, functions, and commonly used built-in functions.

I also practiced writing small automation-oriented programs rather than learning Python only through isolated syntax examples.

The main objective was to make Python fundamentals familiar enough that I can use them naturally when working on automation and infrastructure-related tasks.

---

## Python Environment

I started by understanding the Python development environment.

### Topics Covered

* `python3`
* `pip`
* Virtual environments
* `venv`
* Python interpreter
* Python scripts
* PEP 8
* VS Code Python extension

### Virtual Environments

A virtual environment creates an isolated Python environment for a project.

Example:

```bash
python3 -m venv .venv
```

Activate on Linux/macOS:

```bash
source .venv/bin/activate
```

The main reason for using a virtual environment is to keep project dependencies isolated.

This becomes especially important when working on multiple Python projects that may require different package versions.

---

## Variables & Data Types

I practiced Python's basic built-in data types.

### Common Types

```python
int
float
str
bool
None
```

Example:

```python
server_count = 5
cpu_usage = 72.5
server_name = "web-server-01"
is_healthy = True
error_message = None
```

### Checking Types

```python
type(server_count)
```

Python is dynamically typed, meaning I don't need to declare the variable type explicitly.

---

## Type Casting

I learned how to convert values between compatible types.

```python
server_count = int("5")
cpu_usage = float("72.5")
server_id = str(101)
```

Common conversion functions:

```python
int()
float()
str()
bool()
```

Casting is useful when processing user input, command output, configuration values, and data received from external systems.

---

## Strings & f-Strings

Strings are used heavily in automation and scripting.

Example:

```python
server = "web-01"
status = "healthy"

message = f"{server} is {status}"
```

Output:

```text
web-01 is healthy
```

I also practiced common string methods such as:

```python
.lower()
.upper()
.strip()
.replace()
.split()
.startswith()
.endswith()
```

---

## Operators & Truthiness

I practiced:

### Arithmetic Operators

```text
+
-
*
/
%
**
//
```

### Comparison Operators

```text
==
!=
>
<
>=
<=
```

### Logical Operators

```text
and
or
not
```

Python also has the concept of truthiness.

Values such as these are considered false:

```python
False
None
0
""
[]
{}
set()
```

Most other values are considered true.

---

## `is` vs `==`

One important Python distinction I learned:

```python
==
```

checks whether two values are equal.

```python
is
```

checks whether two references point to the same object.

Example:

```python
a = [1, 2, 3]
b = [1, 2, 3]

print(a == b)
print(a is b)
```

Output:

```text
True
False
```

A common rule is to use `is` when checking identity, especially:

```python
value is None
```

rather than:

```python
value == None
```

---

## Data Structures

I worked with Python's four major built-in collection types:

| Data Structure | Main Use                      |
| -------------- | ----------------------------- |
| List           | Ordered, mutable collection   |
| Tuple          | Ordered, immutable collection |
| Dictionary     | Key-value data                |
| Set            | Unique values                 |

### List

```python
servers = ["web-01", "web-02", "db-01"]
```

Lists are useful when order matters and values may change.

### Tuple

```python
server = ("web-01", "10.0.0.10")
```

Tuples are useful for fixed collections of values.

### Dictionary

```python
server = {
    "name": "web-01",
    "ip": "10.0.0.10",
    "status": "healthy"
}
```

Dictionaries are especially important for automation and API work because JSON data is commonly represented as nested dictionaries and lists in Python.

### Set

```python
regions = {"us-east-1", "us-west-2", "us-east-1"}
```

Output:

```python
{"us-east-1", "us-west-2"}
```

Sets automatically remove duplicate values.

---

## Data Structure Time Complexity

I also learned why choosing the correct data structure matters.

Common average-case operations:

| Operation       | List | Dictionary |  Set |
| --------------- | ---: | ---------: | ---: |
| Access by index | O(1) |          — |    — |
| Search          | O(n) |       O(1) | O(1) |
| Insert          | O(n) |       O(1) | O(1) |
| Delete          | O(n) |       O(1) | O(1) |

The exact complexity can depend on the operation and implementation, but understanding the general behavior helps when writing scalable automation.

---

## Slicing

Slicing allows me to extract part of a sequence.

```python
servers = ["web-01", "web-02", "web-03", "db-01"]

print(servers[1:3])
```

Output:

```text
['web-02', 'web-03']
```

General syntax:

```python
sequence[start:stop:step]
```

The `stop` position is not included.

---

## Unpacking

Python allows values to be assigned to multiple variables.

```python
server = ("web-01", "10.0.0.10")

name, ip = server
```

This makes code easier to read when working with structured data.

---

## `enumerate()`

Instead of manually maintaining a counter:

```python
servers = ["web-01", "web-02", "web-03"]

for index, server in enumerate(servers):
    print(index, server)
```

Output:

```text
0 web-01
1 web-02
2 web-03
```

`enumerate()` is useful whenever I need both the index and the value.

---

## `zip()`

`zip()` allows multiple iterables to be processed together.

```python
servers = ["web-01", "web-02"]
statuses = ["healthy", "unhealthy"]

for server, status in zip(servers, statuses):
    print(server, status)
```

Output:

```text
web-01 healthy
web-02 unhealthy
```

This is useful when related data is stored in separate sequences.

---

## `sorted()` with `key`

I practiced sorting data using a custom key.

Example:

```python
servers = [
    {"name": "web-01", "cpu": 80},
    {"name": "web-02", "cpu": 45},
    {"name": "web-03", "cpu": 65},
]

servers = sorted(servers, key=lambda server: server["cpu"])
```

This is useful when processing structured data such as server information, monitoring results, or API responses.

---

## Control Flow

I practiced the main Python control-flow structures.

### `if / elif / else`

```python
if cpu_usage > 80:
    print("High CPU usage")
elif cpu_usage > 60:
    print("Moderate CPU usage")
else:
    print("Normal CPU usage")
```

### `for`

```python
for server in servers:
    print(server)
```

### `while`

```python
attempts = 0

while attempts < 3:
    print("Checking server...")
    attempts += 1
```

### `break`

Stops a loop early.

```python
for server in servers:
    if server == "db-01":
        break
```

### `continue`

Skips the current iteration.

```python
for server in servers:
    if server == "db-01":
        continue

    print(server)
```

### `range()`

```python
for number in range(5):
    print(number)
```

Output:

```text
0
1
2
3
4
```

---

## Comprehensions

I learned list, dictionary, and set comprehensions.

### List Comprehension

```python
healthy_servers = [
    server for server in servers
    if server["status"] == "healthy"
]
```

### Dictionary Comprehension

```python
server_status = {
    server["name"]: server["status"]
    for server in servers
}
```

### Set Comprehension

```python
regions = {
    server["region"]
    for server in servers
}
```

Comprehensions can make simple transformations concise.

However, a normal loop can be more readable when the logic becomes complex.

The goal is not to replace every loop with a comprehension.

---

## Functions

Functions allow reusable logic to be separated from the rest of the program.

Example:

```python
def check_server_status(server):
    return server["status"] == "healthy"
```

Calling the function:

```python
result = check_server_status(server)
```

Functions help make automation scripts easier to read, test, maintain, and reuse.

---

## Function Parameters

I practiced:

* Positional parameters
* Default parameters
* Keyword arguments
* `*args`
* `**kwargs`

Example:

```python
def connect(server, port=22):
    print(f"Connecting to {server}:{port}")
```

Default values allow a function to provide sensible behavior when an argument is not supplied.

---

## `*args` and `**kwargs`

`*args` collects additional positional arguments.

```python
def show_servers(*servers):
    for server in servers:
        print(server)
```

`**kwargs` collects additional keyword arguments.

```python
def configure_server(**settings):
    print(settings)
```

These features are useful when designing flexible functions.

---

## Scope

I learned about variable scope and the difference between local and global variables.

Example:

```python
server = "web-01"

def show_server():
    server = "db-01"
    print(server)

show_server()
print(server)
```

Output:

```text
db-01
web-01
```

The variable inside the function is local to that function.

Understanding scope helps prevent unexpected changes to program state.

---

## Type Hints

I practiced adding type information to functions.

```python
def add_servers(current: int, new: int) -> int:
    return current + new
```

Type hints make code easier to understand and help development tools identify potential mistakes.

They do not automatically enforce types at runtime.

---

## Docstrings

I learned to document what a function does using a docstring.

```python
def check_server(status: str) -> bool:
    """Return True when the server status is healthy."""
    return status == "healthy"
```

Docstrings are useful when revisiting code later or working with other developers.

---

## Important Built-ins

I practiced several Python built-in functions that are especially useful in automation.

```python
len()
sum()
min()
max()
any()
all()
sorted()
reversed()
map()
filter()
```

Examples:

```python
len(servers)

sum(cpu_values)

max(cpu_values)

min(cpu_values)

any(statuses)

all(statuses)
```

Knowing these functions reduces the need to write unnecessary loops.

---

## Mutable Default Arguments

One Python behavior I learned to be careful with is mutable default arguments.

Avoid:

```python
def add_server(server, servers=[]):
    servers.append(server)
    return servers
```

The default list is created once and reused between calls.

A safer approach is:

```python
def add_server(server, servers=None):
    if servers is None:
        servers = []

    servers.append(server)
    return servers
```

This is an important Python gotcha because it can produce unexpected state across function calls.

---

## Hands-on Practice

During this week I practiced Python using Cloud/DevOps-oriented examples.

Some of the exercises included:

* Working with server names
* Checking server health
* Filtering healthy servers
* Managing server dictionaries
* Finding unique regions
* Iterating through nested dictionaries
* Using lists, tuples, dictionaries, and sets
* Converting loops into comprehensions
* Writing reusable functions
* Adding type hints and docstrings
* Working with virtual environments
* Practicing Python syntax and built-in functions

I also organized my Python learning material separately in my `python-fundamentals` repository.

The purpose of that repository is to keep structured Python learning content separate from my professional Python projects.

---

## Key Takeaways

A few things stood out to me during this week:

1. Python's built-in data structures are extremely important for automation.
2. Dictionaries and lists will be especially useful when working with APIs and JSON.
3. Choosing the right data structure can affect performance.
4. Functions make automation code reusable and easier to maintain.
5. Type hints and docstrings improve code readability.
6. Comprehensions are useful, but readability is more important than making code shorter.
7. Python has several small behaviors and gotchas that are important to understand.
8. Writing Python for automation requires more than knowing syntax—it requires understanding how to structure the code.

---

## Challenges

The areas that required the most attention were:

* Understanding the differences between Python data structures
* Remembering time complexity
* Working with nested dictionaries
* Understanding `is` vs `==`
* Using comprehensions without making code difficult to read
* Understanding function scope
* Understanding `*args` and `**kwargs`
* Remembering the mutable default argument behavior
* Choosing between a simple loop and a comprehension

Repeated practice was much more useful than simply reading the syntax.

---

## Reflection

Completing Python I gave me a much stronger foundation for the programming side of my Cloud Engineering roadmap.

Python is particularly important for my long-term goals because I want to use it for automation, infrastructure tooling, API interaction, monitoring, and other Cloud/DevOps tasks.

At the same time, I still have two earlier roadmap sections to complete:

* **Week 3 — Linux II**
* **Week 4 — Networking**

Because I had to pause my learning journey for a period of time, I decided to continue progressing with Python while covering those missed topics alongside my current learning.

This allows me to maintain momentum without abandoning the Linux and networking fundamentals that are essential for Cloud Engineering.

---

## Next Week

### Week 6 — Python II: Files, Errors, Modules, OOP & Testing

Planned topics:

* Reading and writing files
* File paths
* Exception handling
* Custom exceptions
* Modules and imports
* Python packages
* Object-oriented programming
* Classes and objects
* Inheritance
* Composition
* Testing with `pytest`
* Writing maintainable Python code

Alongside this, I will continue working through the missed **Linux II and Networking** material.

---

## Roadmap Progress

Completed:

* Week 0 – Foundations
* Week 1 – Computer Fundamentals & Virtualization
* Week 2 – Linux I
* Week 5 – Python I

Currently continuing:

* Week 6 – Python II
* Week 3 – Linux II *(being covered alongside current learning)*
* Week 4 – Networking *(being covered alongside current learning)*

The roadmap order has changed, but the learning goals have not.

**Keep learning. Keep building. Keep documenting.**
