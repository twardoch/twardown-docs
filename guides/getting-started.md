---
this_file: twardown-docs/guides/getting-started.md
---

# Getting Started with Twardown

This guide will help you get started with Twardown in both Python and JavaScript environments.

## What is Twardown?

Twardown is an opinionated Markdown flavor that provides a consistent writing experience across different platforms and tools. Instead of manually configuring multiple Markdown plugins and extensions, Twardown gives you a carefully curated set of features that work well together.

## Installation

### Python

```bash
# Using uv (recommended)
uv pip install twardown-py

# Using pip
pip install twardown-py
```

### JavaScript

```bash
# Using npm
npm install twardown-js

# Using yarn
yarn add twardown-js

# Using pnpm
pnpm add twardown-js
```

## Basic Usage

### Python

```python
from markdown import Markdown
from twardown_py import TwardownExtension

# Create a Markdown instance with Twardown
md = Markdown(extensions=[TwardownExtension()])

# Convert markdown to HTML
html = md.convert("""
---
title: My Document
---

# Hello World

- [ ] Task 1
- [x] Task 2
""")
```

### JavaScript

```javascript
import { unified } from 'unified'
import remarkParse from 'remark-parse'
import remarkTwardown from 'twardown-js'
import remarkHtml from 'remark-html'

const processor = unified()
  .use(remarkParse)
  .use(remarkTwardown)
  .use(remarkHtml)

const markdown = `
---
title: My Document
---

# Hello World

- [ ] Task 1
- [x] Task 2
`

const result = await processor.process(markdown)
console.log(result.toString())
```

## Features

Twardown includes all CommonMark features plus:

1. Tables
   ```markdown
   | Header 1 | Header 2 |
   |----------|----------|
   | Cell 1   | Cell 2   |
   ```

2. Task Lists
   ```markdown
   - [ ] Unchecked task
   - [x] Checked task
     - [ ] Nested task
   ```

3. Frontmatter
   ```markdown
   ---
   title: Document Title
   author: Name
   date: 2024-03-24
   ---
   ```

4. Magic Records
   ```markdown
   ---
   this_file: path/to/file.md
   ---
   ```

## Editor Setup

### VSCode

1. Install the recommended extensions:
   - unifiedjs.vscode-remark
   - yzhang.markdown-all-in-one

2. Add Twardown configuration to your settings.json:
   ```json
   {
     "markdown.extension.toc.levels": "2..6",
     "markdown.extension.toc.orderedList": false
   }
   ```

## Next Steps

- Read the [full specification](../spec/index.md)
- Check out the [examples](../examples/basic.md)
- Learn about [extension points](../spec/index.md#extension-points)

## Getting Help

- Check the [troubleshooting guide](./troubleshooting.md)
- File issues on GitHub
- Join the community discussions
