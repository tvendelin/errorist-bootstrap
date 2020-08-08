---
title: "Markdown by Example"
date: 2020-08-07T09:02:22+02:00
description: 'Markdown basic syntax by example: header, paragraph, list, link, image, table.'
draft: true
weight: 500
---

The example below shows how content of your pages should be written to have headers, paragraphs,
etc. If you scroll down you will see what the resulting web page will look like.

```md
Whatever you publish with Hugo and Errorist – the articles, blog posts, etc. –
are written using a plain text editor. The special parts of you texts –
headings, lists, links, images, blockquotes – are marked up with a simple
notation called Markdown. For example, once I put an empty line after this text,
it will be interpreted as the end of paragraph.

Notice you can read everything almost as easily as on a webpage that is created
based on your Markdown writings. To mark a text as a header, prepend it with a
pound and a space:

# The Main Header (H1 in HTML)

To create up to five levels of subheaders you just need to add more pound signs.
This is the next level of a subheader:

## Two Pound Signs Make a Second-Level Header

To add _emphasis_ to some part of a text, put it between underscores, and to
make it **bold**, put it between two asterisks on each side.

To block-quote some text, like your grammar exercise, prepend each paragraph
with `>` sign:

>When illustrating grammar concepts, you might want to highlight some ~~common
misspellings~~, and the **correct spelling** as well. You can put the misspelled
text between two tilde characters on both sides, and it will appear red and
crossed out.  Marking text as **bold** within a blockquote will make it green,
bold and italic. The latter is just styling in Errorist.

>To continue a blockquote over a paragraph boundary, use the `>` sign at the
beginning of the next paragraph.

[This is a link to Google](http://google.com).

![mysterious person](https://gravatar.com/avatar?d=mp&s=200 "Adding an image is
also simple")

Here is an ordered list of Errorist priorities:
1. Easy and robust multilingual content management.
1. Minimum code in Markdown files.
1. Minimalist design

Unordered list of formats used in a page:
- Markdown
- YAML

Even tables are doable:

|City       |   Population|
|:----------|------------:|
|Tokyo      |9 273 000 000|
|Montabaur  |       12 486|

Colon on the left means the column is aligned left, colon on the right aligns
the column right. Delimiters (`|`) do not need to align, but you can align them
for better readability.

This is not a complete list of what can be done with Markup, but it is enough to
get started.
```

Whatever you publish with Hugo and Errorist – the articles, blog posts, etc. – are written using a
plain text editor. The special parts of you texts – headings, lists, links, images, block quotes –
are marked up with a simple notation called Markdown. For example, once I put an empty line after
this text, it will be interpreted as the end of paragraph.

Notice you can read everything almost as easily as on a web page that is created based on your
Markdown writings. To mark a text as a header, prepend it with a pound and a space:

# The Main Header (H1 in HTML)

To create up to five levels of subheads you just need to add more pound signs. This is the next
level of a subhead:

## Two Pound Signs Make a Second-Level Header

To add _emphasis_ to some part of a text, put it between underscores, and to make it **bold**, put
it between two asterisks on each side.

To block-quote some text, like your grammar exercise, prepend each paragraph with `>` sign:

>When illustrating grammar concepts, you might want to highlight some ~~common misspellings~~,
and the **correct spelling** as well. You can put the misspelled text between two tilde characters
on both sides, and it will appear red and crossed out. Marking text as **bold** within a block quote
will make it green, bold and italic. The latter is just styling in Errorist.

>To continue a block quote over a paragraph boundary, use the `>` sign at the
beginning of the next paragraph.

[This is a link to Google](http://google.com).

![mysterious person](https://gravatar.com/avatar?d=mp&s=200 "Adding an image is also simple")

Here is an ordered list of Errorist priorities:
1. Easy and robust multilingual content management.
1. Minimum code in Markdown files.
1. Minimalist design

Unordered list of formats used in a page:
- Markdown
- YAML

Even tables are doable:

|City       |   Population|
|:----------|------------:|
|Tokyo      |9 273 000 000|
|Montabaur  |       12 486|

Colon on the left means the column is aligned left, colon on the right
aligns the column right. Delimiters (`|`) do not need to align, but you can align them for better
readability.

This is not a complete list of what can be done with Markup, but it is enough to get started.
