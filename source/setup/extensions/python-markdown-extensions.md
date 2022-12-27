# Python Markdown Extensions

The [Python Markdown Extensions] package is an excellent collection of
additional extensions perfectly suited for advanced technical writing. Material
for MkDocs lists this package as an explicit dependency, so it's automatically
installed with a supported version.

[python markdown extensions]: https://facelessuser.github.io/pymdown-extensions/

## Supported extensions

In general, all extensions that are part of [Python Markdown Extensions] should
work with Material for MkDocs. The following list includes all extensions that
are natively supported, meaning they work without any further adjustments.

### Arithmatex

[:octicons-tag-24: 1.0.0][arithmatex support] ·
[:octicons-workflow-24: Extension][arithmatex]

The [Arithmatex] extension allows for rendering of block and inline block
equations and integrates seamlessly with [MathJax][^1] – a library for
mathematical typesetting. Enable it via `mkdocs.yml`:

[^1]:
    Other libraries like [KaTeX] are also supported and can be integrated with
    some additional effort. See the [Arithmatex documentation on KaTeX] for
    further guidance, as this is beyond the scope of Material for MkDocs.

```yaml
markdown_extensions:
  - pymdownx.arithmatex:
      generic: true
```

Besides enabling the extension in `mkdocs.yml`, a MathJax configuration and
the JavaScript runtime need to be included, which can be done with a few lines
of [additional JavaScript]:

=== ":octicons-file-code-16: `docs/javascripts/mathjax.js`"

    ``` js
    window.MathJax = {
      tex: {
        inlineMath: [["\\(", "\\)"]],
        displayMath: [["\\[", "\\]"]],
        processEscapes: true,
        processEnvironments: true
      },
      options: {
        ignoreHtmlClass: ".*|",
        processHtmlClass: "arithmatex"
      }
    };

    document$.subscribe(() => {
      MathJax.typesetPromise()
    })
    ```

=== ":octicons-file-code-16: `mkdocs.yml`"

    ``` yaml
    extra_javascript:
      - javascripts/mathjax.js
      - https://polyfill.io/v3/polyfill.min.js?features=es6
      - https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js
    ```

The other configuration options of this extension are not officially supported
by Material for MkDocs, which is why they may yield unexpected results. Use
them at your own risk.

See reference for usage:

- [Using block syntax]
- [Using inline block syntax]

  [arithmatex]: https://facelessuser.github.io/pymdown-extensions/extensions/arithmatex/
  [arithmatex support]: https://github.com/squidfunk/mkdocs-material/releases/tag/1.0.0
  [arithmatex documentation on katex]: https://facelessuser.github.io/pymdown-extensions/extensions/arithmatex/#loading-katex
  [mathjax]: https://www.mathjax.org/
  [katex]: https://github.com/Khan/KaTeX
  [additional javascript]: ../../customization.md#additional-javascript
  [using block syntax]: ../../reference/mathjax.md#using-block-syntax
  [using inline block syntax]: ../../reference/mathjax.md#using-inline-block-syntax

### BetterEm

[:octicons-tag-24: 0.1.0][betterem support] ·
[:octicons-workflow-24: Extension][betterem]

The [BetterEm] extension improves the detection of Markup to emphasize text
in Markdown using special characters, i.e. for `**bold**` and `_italic_`
formatting. Enable it via `mkdocs.yml`:

```yaml
markdown_extensions:
  - pymdownx.betterem
```

The configuration options of this extension are not specific to Material for
MkDocs, as they only impact the Markdown parsing stage. See the [BetterEm
documentation][betterem] for more information.

[betterem]: https://facelessuser.github.io/pymdown-extensions/extensions/betterem/
[betterem support]: https://github.com/squidfunk/mkdocs-material/releases/tag/0.1.0

### Caret, Mark & Tilde

[:octicons-tag-24: 1.0.0][caret support] ·
[:octicons-workflow-24: Extension][caret]

The [Caret], [Mark] and [Tilde] extensions add the ability to highlight text
and define sub- and superscript using a simple syntax. Enable them together
via `mkdocs.yml`:

```yaml
markdown_extensions:
  - pymdownx.caret
  - pymdownx.mark
  - pymdownx.tilde
```

The configuration options of this extension are not specific to Material for
MkDocs, as they only impact the Markdown parsing stage. See the [Caret], [Mark]
and [Tilde documentation][tilde] for guidance.

See reference for usage:

- [Highlighting text]
- [Sub- and superscripts]

  [caret]: https://facelessuser.github.io/pymdown-extensions/extensions/caret/
  [caret support]: https://github.com/squidfunk/mkdocs-material/releases/tag/1.0.0
  [mark]: https://facelessuser.github.io/pymdown-extensions/extensions/mark/
  [tilde]: https://facelessuser.github.io/pymdown-extensions/extensions/tilde/
  [highlighting text]: ../../reference/formatting.md#highlighting-text
  [sub- and superscripts]: ../../reference/formatting.md#sub-and-superscripts

### Critic

[:octicons-tag-24: 1.0.0][critic support] ·
[:octicons-workflow-24: Extension][critic]

The [Critic] extension allows for the usage of [Critic Markup] to highlight
added, deleted or updated sections in a document, i.e. for tracking changes in
Markdown syntax. Enable it via `mkdocs.yml`:

```yaml
markdown_extensions:
  - pymdownx.critic
```

The following configuration options are supported:

[`mode`](#+pymdownx.critic.mode){ #+pymdownx.critic.mode }

: :octicons-milestone-24: Default: `view` – This option defines how the markup
should be parsed, i.e. whether to just `view` all suggested changes, or
alternatively `accept` or `reject` them:

    === "View changes"

        ``` yaml
        markdown_extensions:
          - pymdownx.critic:
              mode: view
        ```

    === "Accept changes"

        ``` yaml
        markdown_extensions:
          - pymdownx.critic:
              mode: accept
        ```

    === "Reject changes"

        ``` yaml
        markdown_extensions:
          - pymdownx.critic:
              mode: reject
        ```

See reference for usage:

- [Highlighting changes]

  [critic]: https://facelessuser.github.io/pymdown-extensions/extensions/critic/
  [critic support]: https://github.com/squidfunk/mkdocs-material/releases/tag/1.0.0
  [critic markup]: https://github.com/CriticMarkup/CriticMarkup-toolkit
  [highlighting changes]: ../../reference/formatting.md#highlighting-changes

### Details

[:octicons-tag-24: 1.9.0][details support] ·
[:octicons-workflow-24: Extension][details]

The [Details] extension supercharges the [Admonition] extension, making the
resulting _call-outs_ collapsible, allowing them to be opened and closed by the
user. Enable it via `mkdocs.yml`:

```yaml
markdown_extensions:
  - pymdownx.details
```

No configuration options are available. See reference for usage:

- [Collapsible blocks]

  [details]: https://facelessuser.github.io/pymdown-extensions/extensions/details/
  [details support]: https://github.com/squidfunk/mkdocs-material/releases/tag/1.9.0
  [admonition]: python-markdown.md#admonition
  [collapsible blocks]: ../../reference/admonitions.md#collapsible-blocks

### Emoji

[:octicons-tag-24: 1.0.0][emoji support] ·
[:octicons-workflow-24: Extension][emoji]

The [Emoji] extension automatically inlines bundled and custom icons and emojis
in `*.svg` file format into the resulting HTML page. Enable it via `mkdocs.yml`:

```yaml
markdown_extensions:
  - pymdownx.emoji:
      emoji_index: !!python/name:materialx.emoji.twemoji # (1)!


      emoji_generator: !!python/name:materialx.emoji.to_svg
```

1.  [Python Markdown Extensions] uses the `pymdownx` namespace, but in order to
    support the inlining of icons, the `materialx` namespace must be used, as it
    extends the functionality of `pymdownx`.

The following configuration options are supported:

[`emoji_index`](#+pymdownx.emoji.emoji_index){ #+pymdownx.emoji.emoji_index }

: :octicons-milestone-24: Default: `emojione` – This option defines which set
of emojis is used for rendering. Note that the use of `emojione` is not
recommended due to [restrictions in licensing][emoji index]:

    ``` yaml
    markdown_extensions:
      - pymdownx.emoji:
          emoji_index: !!python/name:materialx.emoji.twemoji
    ```

[`emoji_generator`](#+pymdownx.emoji.emoji_generator){ #+pymdownx.emoji.emoji_generator }

: :octicons-milestone-24: Default: `to_png` – This option defines how the
resolved emoji or icon shortcode is render. Note that icons can only be
used together with the `to_svg` configuration:

    ``` yaml
    markdown_extensions:
      - pymdownx.emoji:
          emoji_generator: !!python/name:materialx.emoji.to_svg
    ```

[`options.custom_icons`](#+pymdownx.emoji.options.custom_icons){ #+pymdownx.emoji.options.custom_icons }

: :octicons-milestone-24: Default: _none_ – This option allows to list folders
with additional icon sets to be used in Markdown or `mkdocs.yml`, which is
explained in more detail in the [icon customization guide]:

    ``` yaml
    markdown_extensions:
      - pymdownx.emoji:
          emoji_index: !!python/name:materialx.emoji.twemoji
          emoji_generator: !!python/name:materialx.emoji.to_svg
          options:
            custom_icons:
              - overrides/.icons
    ```

The other configuration options of this extension are not officially supported
by Material for MkDocs, which is why they may yield unexpected results. Use
them at your own risk.

See reference for usage:

- [Using emojis]
- [Using icons]
- [Using icons in templates]

  [emoji]: https://facelessuser.github.io/pymdown-extensions/extensions/emoji/
  [emoji support]: https://github.com/squidfunk/mkdocs-material/releases/tag/1.0.0
  [emoji index]: https://facelessuser.github.io/pymdown-extensions/extensions/emoji/#default-emoji-indexes
  [icon customization guide]: ../changing-the-logo-and-icons.md#additional-icons
  [using emojis]: ../../reference/icons-emojis.md#using-emojis
  [using icons]: ../../reference/icons-emojis.md#using-icons
  [using icons in templates]: ../../reference/icons-emojis.md#using-icons-in-templates

### Highlight

[:octicons-tag-24: 5.0.0][highlight support] ·
[:octicons-workflow-24: Extension][highlight] ·
:octicons-zap-24: Supersedes [CodeHilite]

The [Highlight] extension adds support for syntax highlighting of code blocks
(with the help of [SuperFences][pymdownx.superfences]) and inline code blocks
(with the help of [InlineHilite][pymdownx.inlinehilite]). Enable it via
`mkdocs.yml`:

```yaml
markdown_extensions:
  - pymdownx.highlight:
      anchor_linenums: true
  - pymdownx.superfences # (1)!
```

1.  [Highlight] is used by the [SuperFences][pymdownx.superfences] extension to
    perform syntax highlighting on code blocks, not the other way round, which
    is why this extension also needs to be enabled.

The following configuration options are supported:

[`use_pygments`](#+pymdownx.highlight.use_pygments){ #+pymdownx.highlight.use_pygments }

: :octicons-milestone-24: Default: `true` – This option allows to control
whether highlighting should be carried out during build time using
[Pygments] or in the browser with a JavaScript syntax highlighter:

    === "Pygments"

        ``` yaml
        markdown_extensions:
          - pymdownx.highlight:
              use_pygments: true
          - pymdownx.superfences
        ```

    === "JavaScript"

        ``` yaml
        markdown_extensions:
          - pymdownx.highlight:
              use_pygments: false
        ```

        As an example, [Highlight.js], a JavaScript syntax highlighter, can be
        integrated with some [additional JavaScript] and an [additional style
        sheet] in `mkdocs.yml`:

        === ":octicons-file-code-16: `docs/javascripts/highlight.js`"

            ``` js
            document$.subscribe(() => {
              hljs.highlightAll()
            })
            ```

        === ":octicons-file-code-16: `mkdocs.yml`"

            ``` yaml
            extra_javascript:
              - https://cdnjs.cloudflare.com/ajax/libs/highlight.js/10.7.2/highlight.min.js
              - javascripts/highlight.js
            extra_css:
              - https://cdnjs.cloudflare.com/ajax/libs/highlight.js/10.7.2/styles/default.min.css
            ```

        Note that [Highlight.js] has no affiliation with the
        [Highlight][pymdownx.highlight] extension.

    All following configuration options are only compatible with build-time
    syntax highlighting using [Pygments], so they don't apply if `use_pygments`
    is set to `false`.

[`auto_title`](#+pymdownx.highlight.auto_title){ #+pymdownx.highlight.auto_title }

: :octicons-milestone-24: Default: `false` – This option will automatically
add a [title] to all code blocks that shows the name of the language being
used, e.g. `Python` is printed for a `py` block:

    ``` yaml
    markdown_extensions:
      - pymdownx.highlight:
          auto_title: true
    ```

[`linenums`](#+pymdownx.highlight.linenums){ #+pymdownx.highlight.linenums }

: :octicons-milestone-24: Default: `false` – This option will add line numbers
to _all_ code blocks. If you wish to add line numbers to _some_, but not all
code blocks, consult the section on [adding line numbers][adding line numbers] in the code block reference, which also contains some tips on
working with line numbers:

    ``` yaml
    markdown_extensions:
      - pymdownx.highlight:
          linenums: true
    ```

[`linenums_style`](#+pymdownx.highlight.linenums_style){ #+pymdownx.highlight.linenums_style }

: :octicons-milestone-24: Default: `table` – The [Highlight] extension
provides three ways to add line numbers, two of which are supported by
Material for MkDocs. While `table` wraps a code block in a `<table>`
element, `pymdownx-inline` renders line numbers as part of the line itself:

    ``` yaml
    markdown_extensions:
      - pymdownx.highlight:
          linenums_style: pymdownx-inline
    ```

    Note that `inline` will put line numbers next to the actual code, which
    means that they will be included when selecting text with the cursor or
    copying a code block to the clipboard. Thus, the usage of either `table`
    or `pymdownx-inline` is recommended.

[`anchor_linenums`](#+pymdownx.highlight.anchor_linenums){ #+pymdownx.highlight.anchor_linenums }

: [:octicons-tag-24: 8.1.0][anchor_linenums support] · :octicons-milestone-24:
Default: `false` – If a code blocks contains line numbers, enabling this
setting will wrap them with anchor links, so they can be hyperlinked and
shared more easily:

    ``` yaml
    markdown_extensions:
      - pymdownx.highlight:
          anchor_linenums: true
    ```

The other configuration options of this extension are not officially supported
by Material for MkDocs, which is why they may yield unexpected results. Use
them at your own risk.

See reference for usage:

- [Using code blocks]
- [Adding a title]
- [Adding line numbers]
- [Highlighting specific lines]
- [Custom syntax theme]

  [highlight]: https://facelessuser.github.io/pymdown-extensions/extensions/highlight/
  [highlight support]: https://github.com/squidfunk/mkdocs-material/releases/tag/5.0.0
  [codehilite]: python-markdown.md#codehilite
  [pymdownx.superfences]: #superfences
  [pymdownx.inlinehilite]: #inlinehilite
  [pygments]: https://pygments.org
  [additional style sheet]: ../../customization.md#additional-css
  [highlight.js]: https://highlightjs.org/
  [title]: ../../reference/code-blocks.md#adding-a-title
  [anchor_linenums support]: https://github.com/squidfunk/mkdocs-material/releases/tag/8.1.0
  [adding line numbers]: ../../reference/code-blocks.md#adding-line-numbers
  [using code blocks]: ../../reference/code-blocks.md#usage
  [adding a title]: ../../reference/code-blocks.md#adding-a-title
  [highlighting specific lines]: ../../reference/code-blocks.md#highlighting-specific-lines
  [custom syntax theme]: ../../reference/code-blocks.md#custom-syntax-theme

### InlineHilite

[:octicons-tag-24: 5.0.0][inlinehilite support] ·
[:octicons-workflow-24: Extension][inlinehilite]

The [InlineHilite] extension add support for syntax highlighting of inline code
blocks. It's built on top of the [Highlight][pymdownx.highlight] extension, from
which it sources its configuration. Enable it via `mkdocs.yml`:

```yaml
markdown_extensions:
  - pymdownx.highlight
  - pymdownx.inlinehilite
```

The configuration options of this extension are not specific to Material for
MkDocs, as they only impact the Markdown parsing stage. The only exception is
the [`css_class`][inlinehilite options] option, which must not be changed. See the
[InlineHilite documentation][inlinehilite] for guidance.

See reference for usage:

- [Highlighting inline code blocks]

  [inlinehilite]: https://facelessuser.github.io/pymdown-extensions/extensions/inlinehilite/
  [inlinehilite support]: https://github.com/squidfunk/mkdocs-material/releases/tag/5.0.0
  [inlinehilite options]: https://facelessuser.github.io/pymdown-extensions/extensions/inlinehilite/#options
  [pymdownx.highlight]: #highlight
  [highlighting inline code blocks]: ../../reference/code-blocks.md#highlighting-inline-code-blocks

### Keys

[:octicons-tag-24: 1.0.0][keys support] ·
[:octicons-workflow-24: Extension][keys]

The [Keys] extension adds a simple syntax to allow for the rendering of keyboard
keys and combinations, e.g. ++ctrl+alt+del++. Enable it via `mkdocs.yml`:

```yaml
markdown_extensions:
  - pymdownx.keys
```

The configuration options of this extension are not specific to Material for
MkDocs, as they only impact the Markdown parsing stage. The only exception is
the [`class`][keys options] option, which must not be changed. See the
[Keys documentation][keys] for more information.

See reference for usage:

- [Adding keyboard keys]

  [keys]: https://facelessuser.github.io/pymdown-extensions/extensions/keys/
  [keys support]: https://github.com/squidfunk/mkdocs-material/releases/tag/1.0.0
  [keys options]: https://facelessuser.github.io/pymdown-extensions/extensions/keys/#options
  [adding keyboard keys]: ../../reference/formatting.md#adding-keyboard-keys

### SmartSymbols

[:octicons-tag-24: 0.1.0][smartsymbols support] ·
[:octicons-workflow-24: Extension][smartsymbols]

The [SmartSymbols] extension converts some sequences of characters into their
corresponding symbols, e.h. copyright symbols or fractions. Enable it via
`mkdocs.yml`:

```yaml
markdown_extensions:
  - pymdownx.smartsymbols
```

The configuration options of this extension are not specific to Material for
MkDocs, as they only impact the Markdown parsing stage. See the [SmartSymbols
documentation][smartsymbols] for guidance.

[smartsymbols]: https://facelessuser.github.io/pymdown-extensions/extensions/smartsymbols/
[smartsymbols support]: https://github.com/squidfunk/mkdocs-material/releases/tag/0.1.0

### Snippets

[:octicons-tag-24: 0.1.0][snippets support] ·
[:octicons-workflow-24: Extension][snippets]

[Snippets]扩展通过使用简单的语法将任意文件的内容嵌入到文档中，包括其他文档或源文件。
通过`mkdocs.yml`启用它:

```yaml
markdown_extensions:
  - pymdownx.snippets
```

这个扩展的配置选项不是特定于 Material for MkDocs，因为它们只影响 Markdown 解析阶段。
更多信息请参见[Snippets 文档][snippets]。

用法参考:

- [Adding a glossary]
- [Embedding external files]

  [snippets]: https://facelessuser.github.io/pymdown-extensions/extensions/snippets/
  [snippets support]: https://github.com/squidfunk/mkdocs-material/releases/tag/0.1.0
  [adding a glossary]: ../../reference/tooltips.md#adding-a-glossary
  [embedding external files]: ../../reference/code-blocks.md#embedding-external-files

### SuperFences

[:octicons-tag-24: 0.1.0][superfences support] ·
[:octicons-workflow-24: Extension][superfences] ·
:octicons-zap-24: Supersedes [Fenced Code Blocks]

The [SuperFences] extension allows for arbitrary nesting of code and content
blocks inside each other, including admonitions, tabs, lists and all other
elements. Enable it via `mkdocs.yml`:

```yaml
markdown_extensions:
  - pymdownx.superfences
```

The following configuration options are supported:

[`custom_fences`](#+pymdownx.superfences.custom_fences){ #+pymdownx.superfences.custom_fences }

: :octicons-milestone-24: Default: _none_ – This option allows to define a
handler for custom fences, e.g. to preserve the definitions of [Mermaid.js]
diagrams to be interpreted in the browser:

    ``` yaml
    markdown_extensions:
      - pymdownx.superfences:
          custom_fences:
            - name: mermaid
              class: mermaid
              format: !!python/name:pymdownx.superfences.fence_code_format
    ```

    Note that this will primarily prevent syntax highlighting from being
    applied. See the reference on [diagrams] to learn how Mermaid.js is
    integrated with Material for MkDocs.

The other configuration options of this extension are not officially supported
by Material for MkDocs, which is why they may yield unexpected results. Use
them at your own risk.

See reference for usage:

- [Using annotations]
- [Using code blocks]
- [Using content tabs]
- [Using flowcharts]
- [Using sequence diagrams]
- [Using state diagrams]
- [Using class diagrams]
- [Using entity-relationship diagrams]

  [superfences]: https://facelessuser.github.io/pymdown-extensions/extensions/superfences/
  [superfences support]: https://github.com/squidfunk/mkdocs-material/releases/tag/0.1.0
  [fenced code blocks]: python-markdown.md#fenced-code-blocks
  [mermaid.js]: https://mermaid-js.github.io/mermaid/
  [diagrams]: ../../reference/diagrams.md
  [using annotations]: ../../reference/annotations.md#usage
  [using content tabs]: ../../reference/content-tabs.md#usage
  [using flowcharts]: ../../reference/diagrams.md#using-flowcharts
  [using sequence diagrams]: ../../reference/diagrams.md#using-sequence-diagrams
  [using state diagrams]: ../../reference/diagrams.md#using-state-diagrams
  [using class diagrams]: ../../reference/diagrams.md#using-class-diagrams
  [using entity-relationship diagrams]: ../../reference/diagrams.md#using-entity-relationship-diagrams

### Tabbed

[:octicons-tag-24: 5.0.0][tabbed support] ·
[:octicons-workflow-24: Extension][tabbed]

The [Tabbed] extension allows the usage of content tabs, a simple way to group
related content and code blocks under accessible tabs. Enable it via
`mkdocs.yml`:

```yaml
markdown_extensions:
  - pymdownx.tabbed:
      alternate_style: true
```

The following configuration options are supported:

[`alternate_style`](#+pymdownx.tabbed.alternate_style){ #+pymdownx.tabbed.alternate_style }

: [:octicons-tag-24: 7.3.1][tabbed alternate support] ·
:octicons-milestone-24: Default: `false` · :octicons-alert-24: **Required**
– This option enables the content tabs [alternate style], which has
[better behavior on mobile viewports], and is the only supported style:

    ``` yaml
    markdown_extensions:
      - pymdownx.tabbed:
          alternate_style: true
    ```

[`slugify`](#+pymdownx.tabbed.slugify){ #+pymdownx.tabbed.slugify }

: :octicons-milestone-24: Default: `headerid.slugify` – This option allows for
customization of the slug function. For some languages, the default may not
produce good and readable identifiers – consider using another slug function
like for example those from [Python Markdown Extensions][slugs]:

    === "Unicode"

        ``` yaml
        markdown_extensions:
          - pymdownx.tabbed:
              slugify: !!python/object/apply:pymdownx.slugs.slugify
                kwds:
                  case: lower
        ```

    === "Unicode, case-sensitive"

        ``` yaml
        markdown_extensions:
          - pymdownx.tabbed:
              slugify: !!python/object/apply:pymdownx.slugs.slugify
        ```

The other configuration options of this extension are not officially supported
by Material for MkDocs, which is why they may yield unexpected results. Use
them at your own risk.

See reference for usage:

- [Grouping code blocks]
- [Grouping other content]
- [Embedded content]

  [tabbed]: https://facelessuser.github.io/pymdown-extensions/extensions/tabbed/
  [tabbed support]: https://github.com/squidfunk/mkdocs-material/releases/tag/5.0.0
  [tabbed alternate support]: https://github.com/squidfunk/mkdocs-material/releases/tag/7.3.1
  [alternate style]: https://facelessuser.github.io/pymdown-extensions/extensions/tabbed/#alternate-style
  [better behavior on mobile viewports]: https://twitter.com/squidfunk/status/1424740370596958214
  [grouping code blocks]: ../../reference/content-tabs.md#grouping-code-blocks
  [grouping other content]: ../../reference/content-tabs.md#grouping-other-content
  [embedded content]: ../../reference/content-tabs.md#embedded-content
  [slugs]: https://facelessuser.github.io/pymdown-extensions/extras/slugs/

### Tasklist

[:octicons-tag-24: 1.0.0][tasklist support] ·
[:octicons-workflow-24: Extension][tasklist]

The [Tasklist] extension allows for the usage of [GitHub Flavored Markdown]
inspired [task lists][tasklist specification], following the same syntactical
conventions. Enable it via `mkdocs.yml`:

```yaml
markdown_extensions:
  - pymdownx.tasklist:
      custom_checkbox: true
```

The following configuration options are supported:

[`custom_checkbox`](#+pymdownx.tasklist.custom_checkbox){ #+pymdownx.tasklist.custom_checkbox }

: :octicons-milestone-24: Default: `false` · This option toggles the rendering
style of checkboxes, replacing native checkbox styles with beautiful icons,
and is therefore recommended:

    ``` yaml
    markdown_extensions:
      - pymdownx.tasklist:
          custom_checkbox: true
    ```

[`clickable_checkbox`](#+pymdownx.tasklist.clickable_checkbox){ #+pymdownx.tasklist.clickable_checkbox }

: :octicons-milestone-24: Default: `false` · This option toggles whether
checkboxes are clickable. As the state is not persisted, the use of this
option is _rather discouraged_ from a user experience perspective:

    ``` yaml
    markdown_extensions:
      - pymdownx.tasklist:
          clickable_checkbox: true
    ```

The other configuration options of this extension are not officially supported
by Material for MkDocs, which is why they may yield unexpected results. Use
them at your own risk.

See reference for usage:

- [Using task lists]

  [tasklist]: https://facelessuser.github.io/pymdown-extensions/extensions/tasklist/
  [tasklist support]: https://github.com/squidfunk/mkdocs-material/releases/tag/1.0.0
  [github flavored markdown]: https://github.github.com/gfm/
  [tasklist specification]: https://github.github.com/gfm/#task-list-items-extension-
  [using task lists]: ../../reference/lists.md#using-task-lists
