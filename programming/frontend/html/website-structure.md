# Website Structure

## Semantic Wrappers

- `<main>` is for content unique to this page. Use `<main>` only once per page, and put it directly inside `<body>`. Ideally this shouldn't be nested within other elements.
- `<article>` encloses a block of related content that makes sense on its own without the rest of the page (e.g., a single blog post).
- `<section>` is similar to `<article>`, but it is more for grouping together a single part of the page that constitutes one single piece of functionality (e.g., a mini map, or a set of article headlines and summaries). It's considered best practice to begin each section with a heading (e.g. `<h1>`); also note that you can break `<article>`s up into different `<section>`s, or `<section>`s up into different `<article>`s, depending on the context.
- `<aside>` contains content that is not directly related to the main content but can provide additional information indirectly related to it (glossary entries, author biography, related links, etc.).
- `<header>` represents a group of introductory content. If it is a child of `<body>` it defines the global header of a webpage, but if it's a child of an `<article>` or `<section>` it defines a specific header for that section (try not to confuse this with titles and headings).
- `<nav>` contains the main navigation functionality for the page. Secondary links, etc., would not go in the navigation.
- `<footer>` represents a group of end content for a page.

## Non-semantic Wrappers

- `<span>`
- `<div>`

## Line Breaks and Horizontal Rules

- `<br>`: line breaks.
- `<hr>`: create a horizontal rule in the document that denotes a thematic change in the text (such as a change in topic or scene). Visually it just looks like a horizontal line.

Both doesn't require closing tags.

## Preserve Formatting

If you want your text to follow the exact format of how it is written in the HTML document. In these cases, you can use the preformatted tag `<pre>`.

```
<pre>
  function testFunction( strText ){
    alert (strText)
  }
</pre>
```

Function will keep the format instead of compressing into 1 line.

## Nonbreaking Spaces

If you do not want the client browser to break text, you should use a nonbreaking space entity `&nbsp;` instead of a normal space.

`<p>An example of this technique appears in the movie "12&nbsp;Angry&nbsp;Men."</p>`

"12 Angry Men" will not be split across 2 lines.

## Planning for a Website

1. List features common to most (if not all) pages.
2. Draw a rough sketch of the page appearance.
3. Make one long list of all desired features.
4. Sort all features into groups or pages.
5. Sketch a rough sitemap. Bubble each page and draw lines to show the typical workflow between pages.

## Resource
- [Introduction to HTML](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML)

[Back](../../../README.md)
