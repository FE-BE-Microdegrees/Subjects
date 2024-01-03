# Markdown

- [Markdown](#markdown)
  - [Learning Outcomes](#learning-outcomes)
  - [What is Markdown?](#what-is-markdown)
  - [Pros of Markdown:](#pros-of-markdown)
  - [Cons of Markdown:](#cons-of-markdown)
  - [When to Use Markdown:](#when-to-use-markdown)
  - [Basic Markdown Syntax:](#basic-markdown-syntax)
    - [Headings:](#headings)
    - [Emphasis:](#emphasis)
    - [Lists:](#lists)
      - [Unordered:](#unordered)
      - [Ordered:](#ordered)
    - [Links:](#links)
    - [Images:](#images)
    - [Blockquotes:](#blockquotes)
    - [Inline Code:](#inline-code)
    - [Code Blocks:](#code-blocks)
    - [Horizontal Rule:](#horizontal-rule)
    - [Tables:](#tables)
    - [Task Lists:](#task-lists)
  - [Excercises](#excercises)

## Learning Outcomes

After completing this topic, you'll be able to:

- describe what Markdown is and why it's useful;
- identify the pros and cons of Markdown;
- use Markdown to format text;
- use Markdown for documentation, blogging, and other purposes.
- use Markdown in Github.

## What is Markdown?

Markdown is a lightweight markup language with plain-text formatting syntax. It was created by John Gruber in 2004. The main goal behind Markdown was to make it easy for people to write and format text in a way that's readable and can be converted to HTML (or other output formats).

## Pros of Markdown:

- **Simplicity:** Markdown is easy to learn and use. Its syntax is intuitive, which means even non-developers can get started quickly.
  
- **Readability:** Markdown documents are plain text, so they're readable even without being converted to another format. The syntax doesn't obstruct the content.
  
- **Portability:** Being plain-text files, Markdown documents are OS-agnostic and can be opened with any text editor.

- **Flexible Output:** Markdown can be converted to a variety of formats including HTML, PDF, and even Word or LaTeX, using converters like Pandoc.

- **Widespread Use:** It's supported on many platforms such as GitHub, Reddit, Stack Exchange, and many content management systems.

- **Version Control Friendly:** Being plain text, Markdown works seamlessly with version control systems like Git.

- **No Need for Specialized Software:** You can write Markdown in any text editor.

## Cons of Markdown:

- **Limited Styling:** While Markdown can handle basic formatting with ease, it's not suitable for documents that require complex styles or layouts.

- **Inconsistencies:** There are several flavors of Markdown, and not all tools support every feature. For example, the way GitHub processes Markdown can be slightly different from other platforms.

- **Learning Curve:** While Markdown is simpler than most markup languages, there's still a learning curve for those unfamiliar.

- **Not Ideal for Larger Documents:** While you can certainly use Markdown for larger documents, it might not be as manageable or structured as other formats designed for that purpose.

- **No Built-in Preview:** Unless you're using a specialized Markdown editor, there's no way to preview the formatted output without converting it.

## When to Use Markdown:

- **Documentation:** Many open-source projects use Markdown for their README files and documentation because of its simplicity and GitHub's built-in support.

- **Blogging:** Many blogging platforms and static site generators support Markdown because of its readability and ease of use.

- **Notetaking:** Markdown is great for taking structured notes. There are several note-taking apps that support Markdown formatting.

- **Online Discussions:** Platforms like Reddit and Stack Exchange use Markdown for text formatting in comments and posts.

- **Writing Books:** Some authors use Markdown for writing books, especially technical books, because of its simplicity and flexibility in producing output formats.

- **Presentations:** With tools like Reveal.js, you can even create slide presentations using Markdown.

- **Learning materials:** Markdown is great for creating learning materials like tutorials, cheat sheets, and more. It's easy to write and read, and can be converted to a variety of formats. If something changes in the source material, you only need to update the Markdown file and re-generate the output.

In conclusion, Markdown is an excellent choice for projects that require basic formatting without the overhead of more complex markup languages. Its simplicity and readability are its main strengths, but for more complex layouts or extensive styling, other formats might be more suitable.

## Basic Markdown Syntax:

Here's a quick reference to basic Markdown syntax:

### Headings:

```markdown
# H1
## H2
### H3
#### H4
##### H5
###### H6
```

### Emphasis:

```markdown
*italic* or _italic_
**bold** or __bold__
**_italic and bold_** or *__italic and bold__*
~~strikethrough~~
```

### Lists:

#### Unordered:

```markdown
* Item 1
* Item 2
  * Subitem 2.1
  * Subitem 2.2
```

or 

```markdown
- Item 1
- Item 2
  - Subitem 2.1
  - Subitem 2.2
```

#### Ordered:

```markdown
1. First item
2. Second item
   1. Subitem 2.1
   2. Subitem 2.2
```

### Links:

```markdown
[Google](https://www.google.com)
```

### Images:

```markdown
![Alt text](url_to_image)
```

### Blockquotes:

```markdown
> This is a blockquote.
```

### Inline Code:

```markdown
Here is `inline code`.
```

### Code Blocks:

Using three backticks:

<pre>
```
function example() {
  console.log("example");
}
```
</pre>

Or with syntax highlighting:

<pre>
```javascript
function example() {
  console.log("example");
}
```
</pre>

### Horizontal Rule:

```markdown
---
```

or 

```markdown
***
```

### Tables:

```markdown
| Header 1 | Header 2 |
| -------- | -------- |
| Cell1    | Cell2    |
| Cell3    | Cell4    |
```

### Task Lists:

```markdown
- [x] Task 1 (completed)
- [ ] Task 2 (not completed)
```

Remember, different platforms or flavors of Markdown might have additional features or slight variations, but the above covers the basic and commonly-used syntax.

Read more from [Markdown Guide](https://www.markdownguide.org/).

## Excercises

- Create `README.md` file into your repository and write a short introduction about yourself using Markdown syntax.
- Make sure to use at least 3 different Markdown syntaxes (e.g. headings, lists, links, images, etc.).
- Commit and push your changes to your repository.
- Check your repository on GitHub and make sure that your `README.md` file is rendered properly.
