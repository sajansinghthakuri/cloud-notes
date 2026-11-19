# Week 6 – Python II: Files, Errors, Modules, OOP & Testing

## Goal

Move from writing simple Python scripts to building maintainable, reusable, and tested tools.

This week focused on file handling, error handling, modules, object-oriented programming, testing, and development tools. The main objective was to apply these concepts by building a practical **File Organizer CLI**.

---

## Overview

This week was about writing Python code that is closer to real-world software development.

I explored how Python handles files and directories, how to manage errors, how to organize code into modules, and how object-oriented programming helps structure larger applications.

I also worked with `pytest`, `ruff`, and `argparse` to make Python applications easier to test, maintain, and use.

---

## 1. File Handling

File handling allows Python programs to read, create, modify, and manage files.

### Opening Files

Python uses the built-in `open()` function.

Common file modes:

| Mode | Description |
|---|---|
| `r` | Read |
| `w` | Write (overwrites existing content) |
| `a` | Append |
| `x` | Create a new file |
| `b` | Binary mode |
| `t` | Text mode (default) |

### Context Managers

The `with` statement automatically closes files after use.

```python
with open("notes.txt", "r") as file:
    content = file.read()
    print(content)
```

### Reading Files

```python
file.read()       # Read entire file
file.readline()   # Read one line
file.readlines()  # Read all lines into a list
```

Reading line by line is generally more memory-efficient for large files.

### Writing and Appending

```python
with open("notes.txt", "w") as file:
    file.write("Learning Python file handling.")

with open("notes.txt", "a") as file:
    file.write("\nLearning Python II.")
```

---

## 2. pathlib

`pathlib` provides an object-oriented way to work with filesystem paths.

It is generally preferable to manually constructing paths with `os.path`.

### Common Operations

```python
from pathlib import Path

path = Path("documents")

path.exists()       # Check whether path exists
path.is_file()      # Check whether it is a file
path.is_dir()       # Check whether it is a directory
path.name           # Filename
path.stem           # Filename without extension
path.suffix         # File extension
path.parent         # Parent directory
```

### Creating Directories

```python
Path("reports/2026").mkdir(parents=True, exist_ok=True)
```

### Finding Files

```python
# Find files in the current directory
for file in Path(".").glob("*.txt"):
    print(file)

# Find files recursively
for file in Path(".").rglob("*.log"):
    print(file)
```

### Why pathlib Matters

- Cleaner path handling.
- Cross-platform compatibility.
- Easier directory traversal.
- Convenient file and directory operations.

---

## 3. Python Standard Library

The standard library provides built-in modules for common programming tasks.

| Module | Purpose |
|---|---|
| `os` | Operating system interactions |
| `shutil` | File and directory operations |
| `sys` | Python interpreter and system information |
| `datetime` | Date and time operations |
| `argparse` | Command-line argument parsing |
| `pathlib` | Filesystem path management |

These modules are especially useful for system administration and automation.

---

## 4. Data Formats: CSV, JSON & YAML

Different data formats are commonly used in cloud engineering and DevOps.

### CSV

CSV (Comma-Separated Values) is commonly used for tabular data.

```python
import csv

with open("servers.csv", "r", newline="") as file:
    reader = csv.DictReader(file)

    for row in reader:
        print(row)
```

### JSON

JSON (JavaScript Object Notation) is widely used in APIs, configuration files, and cloud services.

```python
import json

data = {
    "name": "web-server",
    "status": "running"
}

# Write JSON
with open("server.json", "w") as file:
    json.dump(data, file, indent=4)

# Read JSON
with open("server.json", "r") as file:
    loaded_data = json.load(file)
```

Important methods:

- `json.load()` – Read JSON from a file.
- `json.dump()` – Write JSON to a file.
- `json.loads()` – Parse a JSON string.
- `json.dumps()` – Convert Python objects into a JSON string.

### YAML

YAML is commonly used for human-readable configuration files, especially in Docker, Kubernetes, and CI/CD.

Install PyYAML:

```bash
pip install pyyaml
```

Example:

```yaml
server:
  name: web-server
  port: 8080
  status: running
```

Read YAML:

```python
import yaml

with open("config.yaml", "r") as file:
    config = yaml.safe_load(file)

print(config)
```

**Key difference:**

- CSV: Tabular data.
- JSON: Structured data and API communication.
- YAML: Human-readable configuration.

---

## 5. Exception Handling

Exceptions allow programs to handle errors without unexpectedly terminating.

### Basic Exception Handling

```python
try:
    number = int(input("Enter a number: "))
    print(100 / number)

except ValueError:
    print("Please enter a valid number.")

except ZeroDivisionError:
    print("Cannot divide by zero.")
```

### Exception Handling Blocks

| Block | Purpose |
|---|---|
| `try` | Code that might raise an exception |
| `except` | Handles specific exceptions |
| `else` | Executes when no exception occurs |
| `finally` | Executes whether an exception occurs or not |

### Raising Exceptions

```python
def validate_file(filename):
    if not filename:
        raise ValueError("Filename cannot be empty.")

    return filename
```

### Custom Exceptions

```python
class FileOrganizerError(Exception):
    """Base exception for file organizer errors."""


class UnsupportedFileError(FileOrganizerError):
    """Raised when a file type is unsupported."""
```

**Important:** Catch specific exceptions instead of using bare `except:` clauses. This makes errors easier to identify and troubleshoot.

---

## 6. Logging

Logging records application events, warnings, and errors.

Unlike `print()`, logging provides severity levels, timestamps, handlers, and configurable output destinations.

### Logging Levels

| Level | Purpose |
|---|---|
| DEBUG | Detailed diagnostic information |
| INFO | Normal application events |
| WARNING | Unexpected situations |
| ERROR | Operation failures |
| CRITICAL | Serious application failures |

### Basic Logging

```python
import logging

logging.basicConfig(
    level=logging.INFO,
    format="%(asctime)s - %(levelname)s - %(message)s"
)

logging.info("Application started.")
logging.warning("Configuration file not found.")
logging.error("File operation failed.")
```

### Important Components

- Logger: Generates log messages.
- Handler: Determines where logs are sent.
- Formatter: Controls log message format.
- Level: Determines which messages are recorded.

Logging is particularly useful when developing automation tools and troubleshooting production applications.

---

## 7. Modules and Packages

Modules help organize Python code into reusable files.

### Module

A Python file containing functions, classes, or variables.

Example:

```text
project/
├── main.py
└── utilities.py
```

Import a module:

```python
import utilities
```

Or import a specific function:

```python
from utilities import calculate_size
```

### Packages

A package organizes related Python modules into directories.

Example:

```text
file_organizer/
├── __init__.py
├── config.py
├── organizer.py
└── logging_config.py
```

### Main Entry Point

```python
if __name__ == "__main__":
    main()
```

This ensures that `main()` runs when the file is executed directly, rather than when it is imported as a module.

### requirements.txt

Used to document external Python dependencies.

Example:

```text
PyYAML
pytest
ruff
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## 8. Object-Oriented Programming (OOP)

OOP organizes code around objects and classes.

### Classes and Objects

A class defines the structure and behavior of objects.

```python
class Server:
    def __init__(self, name, status):
        self.name = name
        self.status = status

    def display(self):
        print(self.name, self.status)


server = Server("web-server", "running")
server.display()
```

### Important Concepts

| Concept | Description |
|---|---|
| Class | Blueprint for creating objects |
| Object | Instance of a class |
| `__init__` | Initializes an object |
| Instance attribute | Belongs to an individual object |
| Class attribute | Shared through the class |
| Method | Function defined inside a class |
| Inheritance | Allows a class to reuse another class's behavior |
| Encapsulation | Organizes and controls access to object data |

### Special Methods

- `__str__()` – Human-readable string representation.
- `__repr__()` – Developer-oriented representation.

### Properties

`@property` allows a method to be accessed like an attribute.

```python
class Server:
    def __init__(self, cpu):
        self._cpu = cpu

    @property
    def cpu(self):
        return self._cpu
```

### Dataclasses

Dataclasses reduce repetitive code when creating classes primarily used to store data.

```python
from dataclasses import dataclass

@dataclass
class Server:
    name: str
    cpu: int
    memory: int
```

Python automatically generates useful methods such as `__init__()` and `__repr__()`.

---

## 9. Testing with pytest

Testing helps verify that functions behave as expected.

### Installation

```bash
pip install pytest
```

### Basic Test

Example function:

```python
def add(a, b):
    return a + b
```

Test:

```python
def test_add():
    assert add(2, 3) == 5
```

Run tests:

```bash
python -m pytest
```

### Important pytest Features

| Feature | Purpose |
|---|---|
| `assert` | Checks expected results |
| Fixtures | Provide reusable test setup |
| `@pytest.mark.parametrize` | Runs tests with multiple inputs |
| `tmp_path` | Creates temporary directories for file tests |

### Example: Testing with tmp_path

```python
def test_create_file(tmp_path):
    file = tmp_path / "notes.txt"

    file.write_text("Hello Python")

    assert file.exists()
    assert file.read_text() == "Hello Python"
```

`tmp_path` is especially useful when testing file-handling applications because tests don't need to modify real user files.

---

## 10. Python Development Tools

### Ruff

Ruff is a fast Python linter and formatter.

Check code:

```bash
ruff check .
```

Automatically fix supported issues:

```bash
ruff check . --fix
```

Format code:

```bash
ruff format .
```

### mypy

mypy checks Python type annotations.

Example:

```python
def calculate_size(size: int) -> int:
    return size * 1024
```

Run:

```bash
mypy .
```

**Why these tools matter:**

- Ruff helps maintain consistent code quality.
- mypy helps identify type-related problems.
- pytest verifies application behavior.

---

# 11. Hands-on Project: File Organizer CLI

**Repository:** `python-projects/file-organizer-cli`

The main practical assignment this week was building a command-line application that organizes files into structured folders automatically.

### Project Objective

Build a Python CLI tool that scans a directory and organizes files based on selected rules.

### Features Implemented

- Command-line interface using `argparse`.
- File organization by extension, date, and size.
- Dry-run mode to preview changes without modifying files.
- Recursive directory scanning.
- Filename collision handling.
- JSON configuration for custom extension-to-folder mappings.
- Logging to console and a log file.
- Exception handling with meaningful error messages.
- Automated tests using pytest.
- Code quality checks using Ruff.

### CLI Arguments

| Argument | Purpose |
|---|---|
| `--source` | Source directory |
| `--dest` | Destination directory |
| `--rule` | Organization rule |
| `--dry-run` | Preview changes without modifying files |
| `--recursive` | Include subdirectories |
| `--verbose` | Display detailed output |

### Example Usage

Preview file organization:

```bash
python main.py --source ./downloads --dest ./organized --rule extension --dry-run
```

Organize files:

```bash
python main.py --source ./downloads --dest ./organized --rule extension
```

Organize recursively:

```bash
python main.py --source ./downloads --dest ./organized --rule date --recursive
```

### Project Structure

```text
file-organizer-cli/
├── main.py
├── config.json
├── requirements.txt
├── README.md
├── file_organizer/
│   ├── __init__.py
│   ├── config.py
│   ├── logging_config.py
│   └── organizer.py
└── tests/
    ├── test_config.py
    └── test_organizer.py
```

### Project Validation

The completed project passed the following checks:

- **pytest:** 20 tests passed.
- **Ruff:** All checks passed.
- **CLI:** Help output and command-line arguments verified.

This project gave me practical experience combining file handling, OOP, exception handling, logging, testing, and command-line interfaces into one application.

---

# Key Takeaways

- `pathlib` makes filesystem operations cleaner and easier to maintain.
- Context managers help manage files safely.
- CSV, JSON, and YAML serve different purposes in automation and infrastructure.
- Proper exception handling makes applications more reliable.
- Logging provides better visibility than using `print()` for application diagnostics.
- Modules and packages make larger projects easier to organize.
- OOP helps structure reusable code.
- pytest helps catch bugs before applications are used.
- Ruff and mypy improve code quality and maintainability.
- `argparse` makes Python scripts usable as command-line tools.

---

# Reflection

This week was a significant step forward in my Python learning.

Previously, I was mainly focused on understanding Python syntax and writing smaller scripts. This week, I started applying those concepts to a complete application.

Building the File Organizer CLI helped me understand why project structure, error handling, logging, and testing matter in real-world development.

I also learned that writing code is only one part of building a reliable tool. Making it understandable, testable, and easy for someone else to use is equally important.

I'm looking forward to applying these skills to more automation tasks as I continue toward cloud engineering.

---

# Next Week

**Week 7 – Python III: APIs, JSON, and Automation**

Topics:

- HTTP fundamentals and API communication
- Python `requests` library
- GET, POST, PUT, and DELETE
- API authentication
- Environment variables and secret management
- JSON parsing and validation
- Pagination, rate limits, and retries
- Network error handling
- System automation using Python
- Scheduling and notifications
