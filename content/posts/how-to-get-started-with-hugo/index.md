---
title: "How To Get Started With Hugo"
date: 2021-05-01T14:24:23+02:00
# weight: 1
# aliases: ["/first"]
tags: ["tech", "tutorials", "get started", "hugo", "how to"]
categories: ["tech", "tutorials", "hugo"]
author: "Phuc Tran" # multiple authors: ["Me", "You"]
showToc: true
TocOpen: true
draft: false
hidemeta: false
comments: false
description: "Quick Start for Hugo - World's fastest static site generator"
disableHLJS: true # to disable highlightjs
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
# cover:
#     image: "images/imageName" # or URL
#     alt: "<alt text>"
#     caption: "<text>"
#     relative: false # when using page bundles set this to true
#     hidden: true # only hide on current single page
editPost:
    URL: "https://github.com/Glup3/blog/content/how-to-get-started-with-hugo"
    Text: "Suggest Changes"
    appendFilePath: true
---

## Step 0: Introduction

> **Hugo is a fast and modern static site generator written in Go, and designed to make website creation fun again.**
>
> Hugo is a general-purpose website framework. Technically speaking, Hugo is a static site generator. Unlike systems that dynamically build a page with each visitor request, Hugo builds pages when you create or update your content. Since websites are viewed far more often than they are edited, Hugo is designed to provide an optimal viewing experience for your website’s end users and an ideal writing experience for website authors.

**Features**

- Extremely fast build times (< 1 ms per page)
- Completely cross platform
- LiveReload
- Powerful theming
- Straightforward organization for your projects
- ...

You can read more about the feature [here](https://gohugo.io/about/features/).
This tutorial is based on the official [Hugo Quick Start](https://gohugo.io/getting-started/quick-start/) guide.

## Step 1: Install Hugo

Installation on Mac is as easy as this. Refer [here](https://gohugo.io/getting-started/installing) for other systems.

```shell

$ brew install hugo

```

Verify if you installed Hugo correctly:

```shell

$ hugo version

# output: hugo v0.82.1+extended darwin/amd64 BuildDate=unknown

```

## Step 2: Create a new Hugo project (aka Site)

```shell

$ hugo new site fresh_blog

$ cd fresh_blog

```

This will create a new Hugo site in a folder named `fresh_blog`.

## Step 3: Add a Hugo Theme

There are a lot of themes under [themes.gohugo.io](https://themes.gohugo.io/). I'm going to use
[PaperMod](https://themes.gohugo.io/hugo-papermod/) for this tutorial.

```shell

$ git init

$ git submodule add https://github.com/adityatelange/hugo-PaperMod themes/papermod

```

This will add the theme as git submodule under `themes/papermod`. You can also download the theme and
put the content here or `git clone` it.

Now you need to use the theme by adding `theme = "PaperMod"` to the bottom of the file `config.toml`.
It should look like this now:

```toml
baseURL = "http://example.org/"
languageCode = "en-us"
title = "My New Hugo Site"
theme = "PaperMod"
```

## Step 4: Add Some Content

Before we create content, we will use the `PaperMod` content template. Create a new file in `archetypes/post.md` and
paste this into it:

```
---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
# weight: 1
# aliases: ["/first"]
tags: ["tag1", "tag2"]
categories: ["category1", "category2"]
author: "Me" # multiple authors: ["Me", "You"]
showToc: false
TocOpen: false
draft: true
hidemeta: false
comments: false
# description: "Description Text."
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: true
ShowPostNavLinks: true
cover:
    image: "images/imageName" # or URL
    alt: "<alt text>"
    caption: "<text>"
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page
editPost:
    URL: "https://github.com/<USERNAME>/<PROJECT_NAME>/content/{{ .Name }}"
    Text: "Suggest Changes"
    appendFilePath: true
---
```

Create content by using the `new` command or create the file manually.

```shell

$ hugo new --kind post posts/first-post/index.md

```

This will generate a content file `index.md` based on the `post` template under `content/posts/first-post/`.
Write your content at the bottom of the file and modify the theme configs above if neeeded.

## Step 5: Start the Hugo server

```shell

$ hugo server -D

# output:
                   | EN
-------------------+-----
  Pages            | 18
  Paginator pages  |  0
  Non-page files   |  0
  Static files     |  0
  Processed images |  0
  Aliases          |  6
  Sitemaps         |  1
  Cleaned          |  0

Built in 45 ms
Watching for changes in /user_dir/fresh_blog/{archetypes,content,data,layouts,static,themes}
Watching for config changes in /user_dir/fresh_blog/config.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```

The `-D` flag tells the server to also use `draft` content. File changes will automatically refresh the server,
no need to refresh the browser.

**You can find your running webserver at** [http://localhost:1313/](http://localhost:133/).

## Step 6: Build static pages

Super simple. Just call:

```shell

$ hugo -D

```

This will create the folder `public` with all static files in it. Have fun now :)
