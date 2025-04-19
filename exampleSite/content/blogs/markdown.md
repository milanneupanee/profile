---
title: "Markdown Syntax"
date:  2025-04-17T22:53:58+05:30
draft: false
github_link: "https://github.com/milanneupanee/markdown"
author: "Gurusabarish"
tags:
  - Markdown syntax
  - Sample
  - example
image: /images/post.jpg
description: ""
toc:
---

## Paragraph
Markdown is a lightweight markup language widely used to format text using a plain-text editor. It's simple, easy to learn, and allows writers to create rich text content such as headings, lists, links, images, and code blocks without needing complex tools. Markdown is especially popular among developers, writers, and technical bloggers because of its clean syntax and compatibility with many content management systems.

Originally created by John Gruber, Markdown is often used in platforms like GitHub, Reddit, and static site generators like Hugo and Jekyll. Its main advantage lies in readability—Markdown-formatted files can be read as-is without rendering, making collaboration and documentation seamless across teams.

## Blockquote
A blockquote in Markdown is used to highlight and format quoted text, typically from another source or to emphasize a key statement. It's created by placing a greater-than symbol (`>`) at the beginning of a line. Blockquotes can span multiple lines and can be nested for layered quoting. This feature is especially useful in documentation, articles, or notes where citing or spotlighting important content is essential, offering both visual distinction and semantic clarity in the rendered output.


### Blockquote without attribution

> Blockquotes are used to highlight a section of text, such as a quote, note, or important information.  
> You can include Markdown formatting like **bold**, *italic*, or even lists inside them.  
> They help emphasize content and make it stand out visually.


### Blockquote with attribution

> Don't communicate by sharing memory, share memory by communicating.</p>
> — <cite>Rob Pike[^1]</cite>

[^1]: The above quote is excerpted from Rob Pike's [talk](https://www.youtube.com/watch?v=PAAkCSZUG1c) during Gopherfest, November 18, 2015.

## Tables

Tables aren't part of the core Markdown spec, but Hugo supports supports them out-of-the-box.

| Name  | Age |
| ----- | --- |
| Bob   | 27  |
| Alice | 23  |

### Inline Markdown within tables

| Inline&nbsp;&nbsp;&nbsp; | Markdown&nbsp;&nbsp;&nbsp; | In&nbsp;&nbsp;&nbsp;                | Table  |
| ------------------------ | -------------------------- | ----------------------------------- | ------ |
| _italics_                | **bold**                   | ~~strikethrough~~&nbsp;&nbsp;&nbsp; | `code` |

## Code Blocks

### Code block with backticks

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <title>Example HTML5 Document</title>
  </head>
  <body>
    <p>Test</p>
  </body>
</html>
```

### Code block indented with four spaces

    <!DOCTYPE html>
    <html lang="en">
    <head>
      <meta charset="UTF-8">
      <title>Example HTML5 Document</title>
    </head>
    <body>
      <p>Test</p>
    </body>
    </html>

### Code block with Hugo's internal highlight shortcode

{{< highlight html >}}

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Example HTML5 Document</title>
</head>
<body>
  <p>Test</p>
</body>
</html>
{{< /highlight >}}

## List Types

### Ordered List

1. First item
2. Second item
3. Third item

### Unordered List

- List item
- Another item
- And another item

### Nested list

- Item
  1. First Sub-item
  2. Second Sub-item

## Headings

The following HTML `<h1>`—`<h6>` elements represent six levels of section headings. `<h1>` is the highest section level while `<h6>` is the lowest.

# H1

## H2

### H3

#### H4

##### H5

###### H6

## Other Elements — abbr, sub, sup, kbd, mark

<abbr title="Graphics Interchange Format">GIF</abbr> is a bitmap image format.

H<sub>2</sub>O

X<sup>n</sup> + Y<sup>n</sup> = Z<sup>n</sup>

Press <kbd><kbd>CTRL</kbd>+<kbd>ALT</kbd>+<kbd>Delete</kbd></kbd> to end the session.

Most <mark>salamanders</mark> are nocturnal, and hunt for insects, worms, and other small creatures.

## Summury
| Feature             | Syntax Example                            | Description                                                |
|---------------------|-------------------------------------------|------------------------------------------------------------|
| Heading             | `# Heading 1` to `###### Heading 6`       | Creates headings from h1 to h6                             |
| Bold                | `**bold text**` or `__bold text__`        | Makes the text bold                                        |
| Italic              | `*italic text*` or `_italic text_`        | Makes the text italic                                      |
| Strikethrough       | `~~strikethrough~~`                       | Shows text with a line through it                          |
| Blockquote          | `> This is a quote`                       | Indents text as a quote                                    |
| Ordered List        | `1. Item one`                             | Numbered list                                              |
| Unordered List      | `- Item` or `* Item`                      | Bulleted list                                              |
| Inline Code         | `` `code` ``                              | Shows inline code                                          |
| Code Block          | <pre>```python<br>print("Hello")<br>```</pre> | Code block with optional syntax highlighting               |
| Link                | `[Link text](https://example.com)`        | Creates a hyperlink                                        |
| Image               | `![Alt text](image-url.jpg)`              | Embeds an image                                            |
| Horizontal Rule     | `---` or `***`                            | Creates a horizontal line                                  |
| Table               | `| Head | Head |`                         | Formats content in table form                             |
| Task List           | `- [x] Task done` / `- [ ] Task not done` | To-do checkboxes                                           |
| Footnote            | `[^1]` and `[^1]: Footnote content`       | Adds footnotes with references                            |
| Emoji               | `:smile:`                                 | Renders emoji (if enabled)                                 |
| HTML                | `<div>Text</div>`                         | Raw HTML can be embedded                                   |
| Escape Character    | `\*escaped\*`                             | Escapes Markdown formatting characters                     |

