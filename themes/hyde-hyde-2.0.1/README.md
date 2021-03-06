# Hyde-hyde

__`Hyde-hyde`__ is a [Hugo](https://gohugo.io)'s theme inspired and derived from @spf13's [Hyde](https://github.com/spf13/hyde.git) and [Nate Finch's blog](https://npf.io). 

## Breaking Changes

Since version 2.0, __`hyde-hyde`__ has been overhauled and, therefore, might cause some disruptions.

* The main styles are refactored and redeveloped using SCSS (see [_static-src/scss_](https://github.com/htr3n/hyde-hyde/blob/master/static-src/scss)),  `poole.css` and `hyde.css` are no longer needed because `hyde-hyde.scss` already incorporates relevant elements (I still keep them there for reference purpose)
* The layouts have been heavily restructured and modularised further (see [_layouts_](https://github.com/htr3n/hyde-hyde/blob/master/layouts))
* Adding '[_Portfolio_](https://github.com/htr3n/hyde-hyde/blob/master/layouts/portfolio)' page inspired by Xiaoying Riley (@3rdwave_themes) [Developer-Theme](https://github.com/xriley/developer-theme)
* Switching to use system fonts instead of Web fonts (e.g. privacy issues)

For more details, please refer to [CHANGELOG](https://github.com/htr3n/hyde-hyde/blob/master/CHANGELOG.md).  A real site in action can be found [here](https://htr3n.github.io) and its [WIP source](https://github.com/htr3n/htr3n-blog) for reference.

## Usage

### Installation

__`Hyde-hyde`__ can be easily installed as many other Hugo themes:

```sh
$ cd HUGO_PROJECT

# then either clone hyde-hyde
$ git clone https://github.com/htr3n/hyde-hyde.git themes/hyde-hyde

# or just add hyde-hyde as a submodule
$ git submodule add https://github.com/htr3n/hyde-hyde.git themes/hyde-hyde
```

After that, choose `hyde-hyde` as the main theme.

* `config.toml` 

```toml
theme = "hyde-hyde"
```

* `config.yaml`

```yaml
theme : "hyde-hyde"
```

That's all. You can render your site using `hugo` and see `hyde-hyde` in action.

### Options

__`Hyde-hyde`__ essentially inherits most of Hyde's [options](https://github.com/spf13/hyde#options). There are some extra options though

* `highlightjs = true`: use [highlight.js](https://highlightjs.org) instead of Hugo built-in support for code highlighting

	* `highlightjsstyle="highlight-style"`: only when `highlightjs = true`, please choose one of many _highlight.js_'s [styles](https://highlightjs.org/static/demo).

* `postNavigation = true|false` (default `true`): Setting to `false` will disable the navigation _Previous Post_/ _Next Post_

* `relatedPosts = false|true` (default `false`): Setting to `true` allows related posts. Please refer [here](https://gohugo.io/content-management/related) for more details on related contents with Hugo.

* `GraphCommentId = "your-graphcomment-id"`: to use [GraphComment](https://graphcomment.com) instead of the built-in [Disqus](https://disqus.com). This option should be used exclusively with `disqusShortname = "disqus-shortname"`.

* `[params.social]`: in this section, you can set many social identities such as Twitter, Facebook, Github, Bitbucket, Gitlab, Instagram, LinkedIn, StackOverflow, Medium, Xing, Keybase.

	```toml
	[params.social]
		twitter = "htr3n"
		keybase = "htr3n"
		github = "htr3n"
		...
	```

	

### Customisations

* Most of the customisable SCSS styles in [_static-src/scss/hyde-hyde_](https://github.com/htr3n/hyde-hyde/blob/master/static-src/scss/hyde-hyde) and Hugo templates in [_hyde-hyde/layouts_](https://github.com/htr3n/hyde-hyde/blob/master/layouts) are modularised and can be altered/adapted easily.

## Portfolio

Since version 2.0+, I added a portfolio page just in case. If you need it, simply add a menu section '_Portfolio_' in `config.toml` as following.

```toml
[[menu.main]]
    name = "Portfolio"
    identifier = "portfolio"
    weight = xxx
    url = "/portfolio/"
```

In the folder `content` , create a subfolder `portfolio` and use the following folder/content structure as reference.

```
$ tree portfolio
portfolio
????????? _index.md
????????? p1.md
????????? p1.png
????????? p2.md
????????? p2.png
    ...
????????? pn.md
????????? pn.png
```

As I design the section _portfolio_ to be rendered as _list_,  `_index.md` can be used to set the title for your portfolio (you can read more about `_index.md` [here](https://gohugo.io/content-management/organization/#index-pages-index-md)). For instance, when I want to set the title of my portfolio "_Projects_", the front matter of `_index.md` will be:

```markdown
---
title: 'Projects'
---
```
The remaining of `_index.md` will be ignored.

For each project, just create a Markdown file with the following parameters in the front matter:

```markdown
---
title: "Project P1's Title"
description: "A short description"
date: '2018-01-02'
link: 'https://project-p1.com'
screenshot: 'p1.png'
layout: 'portfolio'
featured: true
---
Here is a longer summary of the project. You can write as long as you wish.
```

> __Note__:
>
> * `date` is important to sort the project chronologically
> * `layout 'portfolio'` is important as you don't want your project's page appear in the list of posts in the main page of your Web site but only in the _Portfolio_ ;)
> * `featured: true` : when you want to show a project as featured project. It is default to `false`. Note that only one project should be marked `featured: true` , otherwise, the result could be random as [the Hugo template](https://github.com/htr3n/hyde-hyde/blob/master/layouts/partials/portfolio/content.html) will take the first one.
> * The body of the Markdown file will be the summary of the project.

If you want to adjust the portfolio page to your needs, please have a look at the [main template](https://github.com/htr3n/hyde-hyde/blob/master/layouts/portfolio/list.html), that uses this [partial template](https://github.com/htr3n/hyde-hyde/blob/master/layouts/partials/portfolio/content.html) and [this SCSS style](https://github.com/htr3n/hyde-hyde/blob/master/static-src/scss/hyde-hyde/_project.scss).

## Some Screenshots

### Main page

![hyde-hyde main screen](https://github.com/htr3n/hyde-hyde/raw/master/images/main.png)

### A post

![A post in hyde-hyde](https://github.com/htr3n/hyde-hyde/raw/master/images/post.png)

### Portfolio

![Portfolio hyde-hyde](https://github.com/htr3n/hyde-hyde/raw/master/images/portfolio.png)



## Author(s)

### Original Developed by Mark Otto

- <https://github.com/mdo>
- <https://twitter.com/mdo>

### Hugo's Hyde Ported by Steve Francia
- <https://github.com/spf13>
- <https://twitter.com/spf13>

## License

Open sourced under the [MIT license](LICENSE.md).
