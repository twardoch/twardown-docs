---
this_file: twardown-docs/spec/index.md
---

# Twardown Markdown Specification

## Overview

Twardown is an opinionated Markdown flavor that combines the best features of various Markdown extensions into a cohesive, well-documented package. This specification defines the exact features and behaviors that make up the Twardown flavor.

## Design Principles

1. **Consistency**: Features should work the same way across different implementations
2. **Simplicity**: Prefer simple, clear syntax over complex alternatives
3. **Compatibility**: Maintain compatibility with CommonMark where possible
4. **Extensibility**: Provide clear extension points for custom functionality
5. **Performance**: Implementations should be efficient and scalable

## Core Features

### 1. Basic Markdown

Twardown includes all CommonMark features:

- Headings (ATX and Setext)
- Paragraphs and Line Breaks
- Lists (Ordered and Unordered)
- Code Blocks and Inline Code
- Links and Images
- Emphasis and Strong Emphasis
- Blockquotes
- Thematic Breaks

### 2. Extended Features

In addition to CommonMark, Twardown includes:

#### 2.1 Tables
- Supports GitHub-style tables
- Alignment options
- Header row required
- Example:
  ```markdown
  | Header 1 | Header 2 |
  |----------|----------|
  | Cell 1   | Cell 2   |
  ```

#### 2.2 Task Lists
- GitHub-style task lists
- Nested task lists supported
- Example:
  ```markdown
  - [ ] Unchecked task
  - [x] Checked task
    - [ ] Nested task
  ```

#### 2.3 Frontmatter
- YAML frontmatter for metadata
- Must start and end with `---` on its own line
- Example:
  ```markdown
  ---
  title: Document Title
  author: Name
  date: 2024-03-24
  ---
  ```

### 3. Special Features

Twardown adds several special features:

#### 3.1 Magic Records
- Special comments that maintain file metadata
- Must be placed at the top of the file
- Example:
  ```markdown
  ---
  this_file: path/to/file.md
  ---
  ```

## Implementation Requirements

1. Python Implementation
   - Must be compatible with Python-Markdown
   - Should provide extension mechanism
   - Must maintain type safety

2. JavaScript Implementation
   - Must be compatible with unified/remark
   - Should work with existing remark plugins
   - Must support ESM and CommonJS

## Extension Points

1. Custom Syntax
   - Implementations must provide way to add custom syntax
   - Must not conflict with core features

2. Rendering
   - Must support custom renderers
   - Should provide hooks for transformation

## Version History

- 0.1.0 (Current)
  - Initial specification
  - Core features defined
  - Basic extension points specified
