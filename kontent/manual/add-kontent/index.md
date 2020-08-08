---
title: "Creating Content with Errorist"
date: 2020-07-27T17:15:38+02:00
description: A soft step-by-step tutorial covering the main features of Errorist mulilingual website theme.
draft: true
toc: true
weight: 300
---

This page will walk you through the steps necessary to add content to your website.

Though not a requirement, using `tree` command-line utility would be handy, if you get lost in
directory structure. To install it, use the default package manager on Linux or MacPorts on Mac.
`tree` shows the entire file hierarchy under specified directory – see the examples throughout this
tutorial.

## Create a Section and Your First Page

Hugo server is probably already running in your terminal. Open another terminal tab or window and
run:

```
hugo new -k page blog/test-page
```

This creates a 'Blogs' section (it should now appear in the top-left corner), and a 'page bundle', a directory
where your page lives. If you run `tree kontent/blog/test-page/`, it will show

```
kontent/blog/test-page/
├── index.md
└── index.ru.md
```

Two `index.*` files have been created, one for the default language (currently English) and Russian.
In subsequent sections we shall see how to customize this step.

Open `kontent/blog/test-page/index.md` in your editor. You will see some parameters between dashed
lines that describe your page. Together they are called 'front matter'. Let's set some of them, and
also add some content. The result should look like this:

```
---
title: Starting Out with Errorist
date: 2020-07-27T17:23:59+02:00
description: 'My first test page description'
draft: true
---

Once I save this file, my first page is created!
```

If you now click the 'Blogs' link (perhaps opening it in a new browser tab), you will get to the 'Blogs' section
front page, where your test page is listed with its `title` and `description` (you've set these in
the front matter). One more click, and you will see your page.

### Markdown and YAML

You probably know it already, but in case you don't: the content files, like `index.md` we've just
created, combine two formats. The front matter is written in [YAML](https://yaml.org/spec/1.2/spec.html). 
If you are completely new to YAML, here's [a very brief introduction.]({{< ref "yaml-tutorial" >}})

The rest of a content file is written in Markdown format. It is intended to be simple, and it is,
too. [GitHub Markdown Guide](https://guides.github.com/features/mastering-markdown/) is a
three-minute read.

If you are viewing this page on a Hugo server running on your computer, you can open the Markdown
file for this page (`kontent/manual/add-kontent/index.md`) and see how it maps to the web page you
are looking at right now.

### Set the Section Name and Description

We probably want our section name to be 'Blog', not 'Blogs', so let's sort that out. Create a
listing page for the section by running this command (mind the underscore):

```
hugo new blog/_index.md
```

Edit `kontent/blog/_index.md` to look like this:

```
---
title: "Blog"
date: 2020-07-27T17:49:45+02:00
description: My Personal blog with Errorist
draft: true
---
A few words as to what my blog is about.
```

Once you save the file, 'Blogs' will become 'Blog', and the section page will now display an
introduction text. This step should be repeated for each language used in your website, inserting
the language code as an additional file name suffix, so for Russian it would be `_index.ru.md`.

## Add the Main Image to a Page

Create a file `kontent/blog/test-page/main-img` and add a single line to it: `plain-blue`, either
using an editor or from command line:

```
echo 'plain-blue' >> kontent/blog/test-page/main-img
```

If you now open [http://localhost:1313/blog/test-page](http://localhost:1313/blog/test-page/), you
will see that an image `plain-blue` has been added to the page. Notice, it's got a caption already,
too. Where did it come from? Have a look into `kontent/images` directory:

```
kontent/images/
├── _index.md
└── plain-blue
    ├── example.png
    ├── index.md
    └── index.ru.md
```

This is where our sample image lives together with its captions and other metadata. The captions in
English and Russian are stored as content in `index.md` and `index.ru.md` files, respectively.
Here's the English one:

```
---
title: "Plain Blue"
date: 2020-07-27T18:37:21+02:00
draft: true
authors:
alt: alt tag of an example image
---
This is a caption for an example image
```

Essentially, we are looking at another page bundle, that just isn't rendered nor listed anywhere –
only included into another page. 

## Adding Content in Another Language

For that, let's edit `kontent/blog/test-page/index.ru.md` file in your page bundle.
If you haven't got a Cyrillic keyboard, as the case might be, here's a sample content you can
copy-and-paste:

```md
---
title: "Welcome to Errorist"
date: 2020-07-27T17:15:38+02:00
description: 
draft: true
toc: true
---
Царь Никита жил когда-то  
Праздно, весело, богато,  
Не творил добра, ни зла,  
И земля его цвела.  
Царь трудился понемногу,  
Кушал, пил, молился богу  
И от разных матерей  
Прижил сорок дочерей ...  
```

Your test page has got a 'Languages' navigation section and a link pointing to the Russian
version of your page. Not surprisingly, once you click it, you will see the Russian page you've just
created. The main image is already there, and notice – it has a Russian caption, too.

That's the benefit of using image bundles: image captions follow the image itself like ducklings
follow their mother-duck, so there never be a mismatch between an image and its caption.

## Creating an Image Bundle

Choose an image and some descriptive name for it. I shall use `myimage` in this example. Run

```
hugo new -k img images/myimage
```

This creates another directory under `kontent/images` which now looks like this:

```
kontent/images/
├── _index.md
├── myimage
│   ├── index.md
│   └── index.ru.md
└── plain-blue
    ├── example.png
    ├── index.md
    └── index.ru.md
```

Copy an image file into `kontent/images/myimage/` (the name of the file doesn't matter). Assuming
your image is `~/MyImages/random.jpg`,

```
cp ~/MyImages/random.jpg kontent/images/myimage/
```

Edit `kontent/images/myimage/index*.md` files to add captions, and our image bundle is ready. 

Let's link it to our test page now.

In the `kontent/blog/test-page/main-img` file, change `plain-blue` to `myimage`, and check the page
again: [http://localhost:1313/blog/test-page](http://localhost:1313/blog/test-page/). The image
supplied with the theme should now change to yours.

## Including Images in the Content of a Page

The general Markdown syntax is

```md
![alt text](src "title text")
```

where `src` is the URL of the image, relative or absolute. With Errorist, if `src` does not contain
a dot (has no 'extension'), the image bundle under `kontent/images` directory will be looked up
instead. The `"title text"` will override the one in the image bundle, and `alt text` will override
the `alt` value. While this might be occasionally useful, most of the time you'd use the texts from
the image bundle, and so reduce it to just

```md
![](src)
```

Create a couple of image bundles and try to experiment with them. What happens if you
refer to nonexistent image bundle? What if image bundle exists, but hasn't got any image?

If you still prefer to use 'loose' images, an absolute path like `/file.jpg` as `src` value would
point to `static/file.jpg`, while relative path `file.jpg` would point to a file in the page bundle 
directory. You will still need to write the captions, so you'll hardly manage to cut any corners
here.

## Clickable Tabs

Errorist theme has been created with foreign language students in mind to let them (b)log their
learning process.

Clickable tabs allow you, among other things, to include your grammar exercises,
showing either the original task or your solution, or the correct solution, or the solution with
corrections, but one at a time. This is useful should you wish to revisit a particular topic in the
future. 

{{< tabs_bq "homework" >}}

So let's create one. In a page bundle, create a directory `myhomework` (the name is arbitrary):

```
mkdir kontent/blog/test-page/homework
```

In this directory create four files as shown in the following code snippets. Here, the names
_are_ important. If you are experiencing the 'writer's block', here's example contents for the said
files:

`kontent/blog/test-page/homework/10_task.txt`:

```md
Señor Rodriguez ... católico, pero ... muerto. 
Señor Díaz ... vivo, pero hoy no ... católico.
```

`kontent/blog/test-page/homework/20_mysolution.txt`:

```md
Señor Rodriguez es católico, pero es muerto. 
Señor Díaz está vivo, pero hoy no es católico.
```

`kontent/blog/test-page/homework/30_solution.txt`:

```md
Señor Rodriguez era católico, pero está muerto. 
Señor Díaz está vivo, pero hoy no está católico.
```


`kontent/blog/test-page/homework/40_corrections.txt`:

```md
Señor Rodriguez ~~es~~ **era** católico, pero ~~es~~ **está** muerto. 
Señor Díaz está vivo, pero hoy no ~~es~~ **está** católico.
```

The `~~` is markdown that will be converted into `<del>` HTML tag, and `**` will become the `<strong>` tag.

Back to our tabs. Your page bundle structure will now look like this:

```
kontent/blog/test-page
├── homework
│   ├── 10_task.txt
│   ├── 20_mysolution.txt
│   ├── 30_solution.txt
│   └── 40_corrections.txt
├── index.md
├── index.ru.md
└── main-img
```

Add the following at the bottom of `kontent/blog/test-page/index.md`
`kontent/blog/test-page/index.ru.md` files:

```
{{</* tabs_bq "homework" */>}}
```

If you look at your test page now, you will see the clickable tabs at the bottom, showing our
fictional homework exercise.

The number at the beginning of a tab file name is for sorting, so that `10_task.txt` appears before
`40_corrections.txt`. The name of a tab is the file name stripped of its `number_` prefix and `.txt`
suffix, so `10_task.txt` becomes `task`. Then, if your localization file (more on that in a moment) contains the tab name as a
key, the translation for that key will be displayed. The entries for 'task', 'mysolution',
'solution' and 'corrections' are already included.

If you were creating a new language-learning blog post from scratch, you could create a page bundle
of this particular kind like this:

``` 
hugo new -k langblog blog/señores-vivos-y-muertos
```

If editing tab files by hand feels a grueling task, you are not alone. Consider managing your homework
using Git and GitHub. If you do, you can just pipe different commits and `wdiffs` of your exercises
into tabs files.

## Featuring an Article on the Front Page

It's time to put your best foot forward. In a page bundle directory, edit the
`kontent/blog/test-page/index.md` file, adding `exposures` parameter to the front matter:

```
---
title: Starting Out with Errorist
date: 2020-07-27T17:23:59+02:00
description: 'My first test page description'
draft: true
exposures:
- major
---
```

If you check the front page of your site at [http://localhost:1313](http://localhost:1313), you
will notice that the main image for your test page now appears at the top together with what is
supposed to be a summary, but is in fact just 70 characters of the page squashed without any respect
to the original formatting. To fix the issue, create a file called `summary.md` (the name is
important), and write the summary for your page into it. Looks better, doesn't it?

To get a summary for the Russian page, too, you should create a `summary.ru.md`.

If you set `exposures` parameter to `minor`, your test page will be listed in the right column of
the front page.

## Adding Links 

The Markdown syntax for links is

```
[Visible Text](http://example.com "title")
```

where 'Visible Text' is the text displayed on the page, and the optional 'title' is
the text that appears when you hover mouse cursor over it, but do not click yet.

To refer to the page of your website, you should use a _shortcode_ in place of URL:

```
[Visible Text]({{</* ref "/page#anchor" */>}} "title")
```

The path is relative to the domain, so if your site is `http://example.com`, the above code will be
rendered as `http://example.com/page#anchor`. The shortcode will throw exception, if this page
doesn't exist – so you are guaranteed against dead links at your own site at least.

Do not use trailing `/` when using the shortcode – it will result in an error.

## Configure Your Project

Now that you know how things work, remove whatever you've created while going through the tutorial.

```
git clean -f *
```

### Configure the Authors

Open `data/authors.yaml`, read the comments, and configure one or more authors by example. It's
YAML format, so keep an eye on indentation.

Once configured, the authors can be referred to from the front matter of their articles like this:

```
authors:
- mmustermann
- tatkins
```

Notice, it is a list, as an article may have more authors than one.

### Configure the Languages

Open `config/_default/languages.yaml`, read the comments, and configure to your needs.

### Adjust Internationalization (I18N for Short)

If you've added new languages, you will also need to add translation files, one per new language.
Create `i18n` directory in your project root, and copy the English translations file to be used as a
template (for German in this example):

```
mkdir i18n
cp themes/errorist/i18n/en.yaml i18n/de.yaml
```

Open `i18n/de.yaml` and change English translations to German.

### Adjust Archetypes

If there were changes in supported languages, you will need to add/remove `index*.md` files
accordingly. That is, for each `index.md` file under `archetypes` directory in your project, you
will need an `index.<LANG>.md` file for each language you support. To remove these files for Russian
(if you are not going to use Russian), run

```
find archetypes -name 'index.ru.md' -exec rm '{}' \;
```

Your project is now configured. Create some content you want to publish.

## Clean Up

```
# Re-create kontent/_index.md
rm kontent/_index.md
hugo new _index.md

# Remove test image bundle
rm -r kontent/images/plain-blue

# Remove the manual
rm -r kontent/manual
```

Restart Hugo server.

## Build Your Site

Once you are done creating the initial content you want to publish, you should change the front
matter parameter `draft` to `false` on everything that you are going to publish, including the image
bundles. To double check, run

```
# To see if you haven't forgot anything
grep -rl 'draft: true' kontent/*
```

Stop Hugo server, and then start it without the `-D` option. Now you will see only pages that are
going to be published. Double-check if everything looks the way it is supposed to.

If you now run 
```
hugo
```

your site will be built in the `public` directory under your project root. This
can be changed by setting the `publishDir:` in `config/_default/config.yaml` to something else.
Personally, I prefer to have it _outside_ the project directory, because it's generated content and
shouldn't be included in a source repository.

## Set up a Repository on GitHub and Publish Your Site

Create an [account on GitHub](https://github.com), if you haven't done so yet.

Create a repository named `<YOUR GITHUB USERNAME>.github.io`. 

Build your site locally, and change into whatever you have configured for your `publishDir`.

Initialize a git repository there, add the files, and commit:

```
git init
git add .
git commit -m 'initial commit'
```

Add your GitHub repository as a remote, and push it to GitHub:

```
git remote add origin <YOUR GITHUB REPOSITORY URL>
git push -u origin master
```

Your website will shortly be accessible at `http://<YOUR GITHUB USERNAME>.github.io`.

If you ego demands a domain of your own, register one and [follow the GitHub
manual](https://docs.github.com/en/github/working-with-github-pages/managing-a-custom-domain-for-your-github-pages-site).

## The Source Repository

Remove the original git remote (where you've cloned the bootstrapping project from):

```
git remote remove origin
```

Decide where do you want to keep the repository with source files of your project. Should that be
GitHub, create a repository there and add it as a remote. Unless you use a paid account, ask
yourself, whether you want the _source_ of your project, including drafts, to be publicly available.
This is very individual, of course.

That was it. This tutorial doesn't cover all the details, but your site should be functional now.
For details, refer to README file.
