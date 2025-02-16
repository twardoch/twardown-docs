---
this_file: twardown-docs/examples/basic.md
title: Basic Twardown Example
author: Adam Twardoch
date: 2024-03-24
---

# Basic Twardown Example

This document demonstrates the basic features of Twardown Markdown.

## Text Formatting

You can use **bold**, *italic*, or ***both***. You can also use `inline code` or add [links](https://example.com).

## Lists

### Unordered Lists
- First item
- Second item
  - Nested item
  - Another nested item
- Third item

### Ordered Lists
1. First step
2. Second step
   1. Substep A
   2. Substep B
3. Third step

### Task Lists
- [ ] Write documentation
- [x] Set up repository
- [ ] Implement features
  - [x] Core functionality
  - [ ] Extensions
  - [ ] Tests

## Code Blocks

```python
def hello_world():
    """Print a greeting"""
    print("Hello, Twardown!")
```

```javascript
function helloWorld() {
  // Print a greeting
  console.log("Hello, Twardown!");
}
```

## Tables

| Feature    | Status | Notes                    |
|------------|--------|--------------------------|
| Basic MD   | ✅     | All CommonMark features |
| Tables     | ✅     | With alignment support  |
| Task Lists | ✅     | Nested lists supported  |

## Blockquotes

> This is a blockquote
> 
> It can span multiple lines
>
> > And can be nested

## Thematic Breaks

Above this line
***
Below this line

## Special Features

### Magic Records
The magic record at the top of this file (`this_file: examples/basic.md`) helps track the file's location in the project.

### Frontmatter
This file includes YAML frontmatter with title, author, and date information.

## Extended Syntax

Term 1
: Definition 1

Term 2
: Definition 2
: Additional definition

~~Strikethrough text~~

- [x] Task with ==highlighted== text
- [ ] Task with ^superscript^ text
- [x] Task with ~subscript~ text
