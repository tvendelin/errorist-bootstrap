---
title: "Configure Errorist – the Short Version"
date: 2020-08-02T20:36:26+02:00
description: The quickest possible way to set up Errorist mulilingual website theme.
draft: true
weight: 200
---

It is strongly advisable to go through a [quick hands-on tutorial]({{< ref "add-kontent" >}}).
Errorist core features require a particular content structure, and the tutorial is the quickest way
to grasp it. Errorist will, of course, work with any setup as far as the core functionality of Hugo
is concerned, but it will also be limited to just that.

## Configure the Authors

Open `data/authors.yaml`, read the comments, and configure one or more authors by example. It's
YAML format, so keep an eye on indentation.

## Configure the Languages

Open `config/_default/languages.yaml`, read the comments, and configure to your needs. You might
want to this step later, though, after you've tried things out.

## Adjust Internationalization (I18N for Short)

If you've added new languages, you will also need to add translation files, one per new language.
Create `i18n` directory in your project root, and copy the English translations file to be used as a
template (for German in this example):

```
mkdir i18n
cp themes/errorist/i18n/en.yaml i18n/de.yaml
```

Open `i18n/de.yaml` and change English translations to German.

## Adjust Archetypes

If there were changes in supported languages, you will need to add/remove `index*.md` files
accordingly. That is, for each `index.md` file under `archetypes` directory in your project, you
will need an `index.<LANG>.md` file for each language you support. To remove these files for Russian
(if you are not going to use Russian), run

```
find archetypes -name 'index.ru.md' -exec rm '{}' \;
```

## Adjust `_index.*md` Files in the Image Bundle Directory

If there were changes in supported languages, you will need to add/remove `kontent/images/_index*.md` files
accordingly. By default the only language-specific part is the file name itself, so mere copying
will do.

## Clean up Tutorials and Examples

```
# Re-create kontent/_index.md
rm kontent/_index.md
hugo new _index.md

# Remove test image bundle
rm -r kontent/images/plain-blue

# Remove the manual
rm -r kontent/manual

# Remove the Git remote (and maybe add yours later)
git remote remove origin
```

You are ready to create content and publish your website.
