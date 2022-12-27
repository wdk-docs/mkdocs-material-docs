---
icon: material/tooltip-plus
status: new
---

# Abbreviations

Technical documentation often incurs the usage of many acronyms, which may
need additional explanation, especially for new user of your project. For these
matters, Material for MkDocs uses a combination of Markdown extensions to
enable site-wide glossaries.

## Configuration

This configuration enables abbreviations and allows to build a simple
project-wide glossary, sourcing definitions from a central location. Add the
following line to `mkdocs.yml`:

```yaml
markdown_extensions:
  - abbr
  - attr_list
  - pymdownx.snippets
```

See additional configuration options:

- [Abbreviations]
- [Attribute Lists]
- [Snippets]

  [abbreviations]: ../setup/extensions/python-markdown.md#abbreviations
  [attribute lists]: ../setup/extensions/python-markdown.md#attribute-lists
  [snippets]: ../setup/extensions/python-markdown-extensions.md#snippets

### Improved tooltips

[:octicons-heart-fill-24:{ .mdx-heart } Sponsors only][insiders]{ .mdx-insiders } ·
[:octicons-tag-24: insiders-4.15.0][insiders] ·
:octicons-beaker-24: Experimental

When improved tooltips are enabled, Material for MkDocs replaces the browser's
rendering logic for `title` attribute with beautiful little tooltips.
Add the following lines to `mkdocs.yml`:

```yaml
theme:
  features:
    - content.tooltips
```

Now, tooltips will be rendered for the following elements:

- **Content** – elements with a `title`, permalinks and copy-to-clipboard button
- **Header** – home button, header title, color palette switch and repository link
- **Navigation** – links that are shortened with ellipsis, i.e. `...`

[insiders]: ../insiders/index.md

## Usage

### Adding tooltips

The [Markdown syntax] allows to specify a `title` for each link, which will
render as a beautiful tooltip when [improved tooltips] are enabled. Add a
tooltip to a link with the following lines:

```markdown title="Link with tooltip, inline syntax"
[Hover me](https://example.com "I'm a tooltip!")
```

<div class="result" markdown>

[Hover me](https://example.com "I'm a tooltip!")

</div>

Tooltips can also be added to link references:

```markdown title="Link with tooltip, reference syntax"
[Hover me][example]

[example]: https://example.com "I'm a tooltip!"
```

<div class="result" markdown>

[Hover me](https://example.com "I'm a tooltip!")

</div>

For all other elements, a `title` can be added by using the [Attribute Lists]
extension:

```markdown title="Icon with tooltip"
:material-information-outline:{ title="Important information" }
```

<div class="result" markdown>

:material-information-outline:{ title="Important information" }

</div>

[markdown syntax]: https://daringfireball.net/projects/markdown/syntax#link
[improved tooltips]: #improved-tooltips

### Adding abbreviations

Abbreviations can be defined by using a special syntax similar to URLs and
[footnotes], starting with a `*` and immediately followed by the term or
acronym to be associated in square brackets:

```markdown title="Text with abbreviations"
The HTML specification is maintained by the W3C.

_[HTML]: Hyper Text Markup Language
_[W3C]: World Wide Web Consortium
```

<div class="result" markdown>

The HTML specification is maintained by the W3C.

_[HTML]: Hyper Text Markup Language
_[W3C]: World Wide Web Consortium

</div>

[footnotes]: footnotes.md

### Adding a glossary

[Snippets]扩展可以通过移动专用文件[^1]中的所有缩略语来实现一个简单的术语表，并[auto-append]该文件到具有以下配置的所有页面:

[^1]: 强烈建议将包含缩写的 Markdown 文件放在`docs` 文件夹之外(这里使用了一个名为`includes`的文件夹)，否则 MkDocs 可能会抱怨未引用的文件。

=== ":octicons-file-code-16: `includes/abbreviations.md`"

    ```` markdown
    *[HTML]: Hyper Text Markup Language
    *[W3C]: World Wide Web Consortium
    ````

=== ":octicons-file-code-16: `mkdocs.yml`"

    ```` yaml
    markdown_extensions:
      - pymdownx.snippets:
          auto_append:
            - includes/abbreviations.md
    ````

[auto-append]: https://facelessuser.github.io/pymdown-extensions/extensions/snippets/#auto-append-snippets
