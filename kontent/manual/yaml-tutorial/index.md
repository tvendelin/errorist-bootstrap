---
title: "YAML – the Very Basics"
date: 2020-08-04T14:51:02+02:00
description: A very brief introduction to YAML
draft: true
weight: 600
---

This is grossly simplified introduction to [YAML](https://yaml.org/spec/1.2/spec.html#id2759963).
The complete official documentation is [available here](https://yaml.org/spec/1.2/spec.html#id2759963). 
However, you will only need a small subset of it to configure your Hugo project and the 'front matter' of
your Markdown files. This little tutorial provides a starting point.

YAML is a format for representing data structure in a human-readable way. 
YAML's block collections use indentation for scope and begin each entry on its own line.
Block sequences indicate each entry with a dash and space ('- '). Mappings
use a colon and space (': ') to mark each key: value pair. Comments begin with `#`. 

Here is an excerpt from `config/_default/config.yaml` with simple scalar-to-scalar mapping. The
quotes are optional, the space after the colon is not: `title:"My site"` would result in an error.

```
baseURL: "https://example.org"
title: "My site"
theme: "errorist"
```

You can nest one mapping into another:

```
highlight:
    codeFences: true
    noClasses: false

```

Here, the key `highlight` holds two mappings as its value. Indentation is important. If you remove
it, this would become three same-level mappings, `highlight` holding now an empty value. This is
probable the most common source of misconfigurations and associated confusion.

Finally, you can map a sequence of scalars:

```
tags:
- git
- hugo
- seo
```    

Here, the `tag` key holds a sequence of scalars (`git`, `hugo`, `seo`). Mind the space after dash:
`-git` would be an error.

A dash counts for indentation. From [YAML specs](http://www.yaml.org/spec/1.2/spec.html#id2799784): 
>Since people perceive the “-” indicator as indentation, nested block sequences may be indented by
>one less space.

This is enough, I believe, to get most of the tasks done as far as a your website project is
concerned. Should that not be the case, read the [YAML docs](https://yaml.org/spec/1.2/spec.html).
