# 参考

Material for MkDocs 包含了许多很棒的特性，使技术写作成为一种快乐的活动。
文档的这一部分解释了如何设置页面，并展示了所有可以直接从 Markdown 文件中使用的可用样本。

## 配置

### 内置元插件

[:octicons-heart-fill-24:{ .mdx-heart } Sponsors only][insiders]{ .mdx-insiders } ·
[:octicons-tag-24: insiders-4.21.0][insiders] ·
:octicons-cpu-24: Plugin ·
:octicons-beaker-24: Experimental

内置的元插件允许 **设置每个文件夹的前面内容**，这是特别方便的，以确保文件夹中的所有页面使用特定的模板或标签。
将以下代码行添加到 `mkdocs.yml`:

```yaml
plugins:
  - meta
```

> 如果你需要使用[Insiders]和不使用[内置插件]构建文档，请参考[内置插件]一节，了解共享配置如何帮助实现这一目标。

有以下配置选项:

[`meta_file`](#+meta.meta_file){ #+meta.meta_file }

: :octicons-milestone-24: 默认: `**/.meta.yml` – 这个选项指定插件应该查找的元文件的名称。默认设置假设元文件名为`.meta.yml`:

    ``` yaml
    plugins:
      - meta:
          meta_file: '**/.meta.yml' # (1)!
    ```

    1.  注意，强烈建议用`.`作为元文件的前缀，否则它们将包含在构建输出中。

[内置博客插件]: ../setup/setting-up-a-blog.md#built-in-blog-plugin
[内置插件]: ../insiders/getting-started.md#built-in-plugins

## 使用

### 设置页面标题

每个页面都有一个指定的标题，在导航侧栏中使用，用于[社交卡片]和其他地方。
MkDocs 尝试在[四步过程]中自动确定页面的标题，标题也可以显式地设置前置事项 `title` 属性:

```yaml
---
title: Lorem ipsum dolor sit amet # (1)!
---
# Document title
```

1. 这一行将生成页面的 HTML 文档[`head`][head]内的[`title`][title] 设置为给定值。
   请注意，通过[`site_name`][site_name]设置的站点标题后面加了一个破折号。

[社交卡片]: ../setup/setting-up-social-cards.md
[四步过程]: https://www.mkdocs.org/user-guide/writing-your-docs/#meta-data
[title]: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/title
[head]: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/head
[site_name]: https://www.mkdocs.org/user-guide/configuration/#site_name

### 设置页面描述

Markdown 文件可以包括添加到页面`meta`标签的描述，也可以用于[社交卡片]。
如果作者没有明确定义 Markdown 文件的描述，在`mkdocs.yml`中设置[`site_description`][site_description] 作为回退值是个好主意:

```yaml
---
description: Nullam urna elit, malesuada eget finibus ut, ac tortor. # (1)!
---
# Document title
```

1.  这一行将包含当前页面文档`head`中的描述的`meta` 标记设置为所提供的值。

[site_description]: https://www.mkdocs.org/user-guide/configuration/#site_description

### 设置页面图标

[:octicons-heart-fill-24:{ .mdx-heart } Sponsors only][insiders]{ .mdx-insiders } ·
[:octicons-tag-24: insiders-4.5.0][insiders] ·
:octicons-beaker-24: Experimental

An icon can be assigned to each page, which is then rendered as part of the
navigation sidebar, as well as [navigation tabs], if enabled. Use the front
matter `icon` property to reference an icon, adding the following lines at the
top of a Markdown file:

```yaml
---
icon: material/emoticon-happy # (1)!
---
# Document title
```

1.  Enter a few keywords to find the perfect icon using our [icon search] and
    click on the shortcode to copy it to your clipboard:

    <div class="mdx-iconsearch" data-mdx-component="iconsearch">
      <input class="md-input md-input--stretch mdx-iconsearch__input" placeholder="Search icon" data-mdx-component="iconsearch-query" value="emoticon happy" />
      <div class="mdx-iconsearch-result" data-mdx-component="iconsearch-result" data-mdx-mode="file">
        <div class="mdx-iconsearch-result__meta"></div>
        <ol class="mdx-iconsearch-result__list"></ol>
      </div>
    </div>

[insiders]: ../insiders/index.md
[icon search]: icons-emojis.md#search
[navigation tabs]: ../setup/setting-up-navigation.md#navigation-tabs

### 设置页面状态

[:octicons-heart-fill-24:{ .mdx-heart } Sponsors only][insiders]{ .mdx-insiders } ·
[:octicons-tag-24: insiders-4.22.0][insiders] ·
:octicons-beaker-24: Experimental

可以为每个页面分配状态，然后将其显示为导航侧栏的一部分。
首先，通过向`mkdocs.yml`添加以下内容，将状态标识符与描述关联起来:

```yaml
extra:
  status:
    <identifier>: <description> # (1)!
```

1.  The identifier can only include alphanumeric characters, as well as dashes
    and underscores. For example, if you have a status `Recently added`, you can
    set `new` as an identifier:

    ```yaml
    extra:
      status:
        new: Recently added
    ```

The page status can now be set with the front matter `status` property. For
example, you can mark a page as `new` with the following lines at the top of a
Markdown file:

```yaml
---
status: new
---
# Document title
```

The following status identifiers are currently supported:

- :material-alert-decagram: – `new`
- :material-trash-can: – `deprecated`

### 设置页面副标题

[:octicons-heart-fill-24:{ .mdx-heart } Sponsors only][insiders]{ .mdx-insiders } ·
[:octicons-tag-24: insiders-4.25.0][insiders] ·
:octicons-beaker-24: Experimental

Each page can define a subtitle, which is then rendered below the title as part
of the navigation sidebar by using the front matter `subtitle` property, and
adding the following lines:

```yaml
---
subtitle: Nullam urna elit, malesuada eget finibus ut, ac tortor
---
# Document title
```

### 设置页面模板

If you're using [theme extension] and created a new page template in the
`overrides` directory, you can enable it for a specific page. Add the following
lines at the top of a Markdown file:

```yaml
---
template: custom.html
---
# Document title
```

??? question "How to set a page template for an entire folder?"

    With the help of the [built-in meta plugin], you can set a custom template
    for an entire section and all nested pages, by creating a `.meta.yml` file
    in the corresponding folder with the following content:

    ``` yaml
    template: custom.html
    ```

[theme extension]: ../customization.md#extending-the-theme
[built-in meta plugin]: #built-in-meta-plugin

## 定制

### 在模板中使用元数据

#### 在所有页面上

In order to add custom `meta` tags to your document, you can [extend the theme
][theme extension] and [override the `extrahead` block][overriding blocks],
e.g. to add indexing policies for search engines via the `robots` property:

```html
{% extends "base.html" %} {% block extrahead %}
<meta property="robots" content="noindex, nofollow" />
{% endblock %}
```

[overriding blocks]: ../customization.md#overriding-blocks

#### 在一页纸上

If you want to set a `meta` tag on a single page, or want to set different
values for different pages, you can use the `page.meta` object inside your
template override, e.g.:

```html
{% extends "base.html" %} {% block extrahead %} {% if page and page.meta and
page.meta.robots %}
<meta property="robots" content="{{ page.meta.robots }}" />
{% else %}
<meta property="robots" content="index, follow" />
{% endif %} {% endblock %}
```

You can now use `robots` exactly like [`title`][title] and
[`description`][description] to set values. Note that in this case, the
template defines an `else` branch, which would set a default if none was given.

[title]: #setting-the-page-title
[description]: #setting-the-page-description
