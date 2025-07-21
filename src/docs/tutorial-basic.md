---
eleventyNavigation:
  parent: Eleventy Projects
  key: First Step Tutorial
  pinned: true
  order: -2
---


TODO : explain goal of the tutorial

- assume only basic technical knowledge
- GOAL : create a very basic website with pages, CSS and images
- (no blog posts, no navigation --> can be a 2nd step tutorial)
- maybe a little bit of data file (for site/author metadata?)


TODO : explains (minimal) opinionated choices (for this 1fst step tutorial)

- JS module
- Nunjucks
- same folder structure as [Base Blog](https://github.com/11ty/eleventy-base-blog)
- no bundler, no CSS tool, no JS, no image processing



# Vocabulary

TODO explain briefly (and send to other doc / website for in-depth study)

- markdown
- HTML
- CSS
- Template Languages
- [Nunjucks](https://mozilla.github.io/nunjucks/)
- [*template*](https://www.11ty.dev/docs/glossary/#template)
- [*layout*](https://www.11ty.dev/docs/glossary/#layout) 
- [*Front Matter Data*](https://www.11ty.dev/docs/data-frontmatter/) 
- [*data cascade*](https://www.11ty.dev/docs/glossary/#data-cascade)




# Prerequisite

TODO should have working nodeJS/NPM, send people to [Get Started](/docs) otherwise

TODO have a text editor (such as VSCode)

- [vscode](https://code.visualstudio.com/download)
- [VSCodium](https://vscodium.com/)

TODO optional but recommended : have git


# Create the project directory and 11ty install

TODO initialize npm and project

```
mkdir 11ty_tutorial && cd "$_"
npm init -y
npm pkg set type="module"
npm install @11ty/eleventy
```

TODO explain [ESM](https://www.11ty.dev/docs/cjs-esm/) (note to the reader: still a lot of documentation on internet with the old syntax)

TODO explain git

TODO create `.gitignore` 

```
node_modules
_site
.cache
```

# Folder and 11ty configuration

TODO explain and create `eleventy.config.js` 

```
export const config = {
    // Directory configuration
    dir: {
        input: "content",          // default: "."
        includes: "../_includes",  // default: "_includes" (`input` relative)
        data: "../_data",          // default: "_data" (`input` relative)
        output: "_site"
    },

    // Pre-process *.md files with nunjucks (default: `liquid`)
    markdownTemplateEngine: "njk",

    // Pre-process *.html files with nunjucks (default: `liquid`)
    htmlTemplateEngine: "njk",

};

export default async function (eleventyConfig) {

    // Copy the contents of the `public` folder to the output folder
    // For example, `./public/css/` ends up in `_site/css/`
    eleventyConfig
        .addPassthroughCopy({
            "./public/": "/"
        })

};
```

TODO Create Folders

```
mkdir _data _includes content public public/{css,img}
```



TODO results and explain

```
├── content     # TODO explain what's go here
├── _data       # TODO explain what's go here
├── _includes   # TODO explain what's go here
└── public
    ├── css     # TODO explain what's go here
    └── img     # TODO explain what's go here
```


# First Page in markdown

TODO create `content/index.md` 

```
Hello world
```


TODO start dev server in IDE

```
npx @11ty/eleventy --serve
```


TODO check result [http://localhost:8080/](http://localhost:8080/)

TODO explain dev server, errors in terminal


# First layout file and correct HTML

TODO explain partial HTML `<p>Hello world</p>` from `index.md`.

Create `_includes/base.njk` 

{% raw %}
```
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="generator" content="{{ eleventy.generator }}">
    <title>{{title }}</title>
</head>
<body>
{{content | safe }}
</body>
</html> 
```
{% endraw %}

{% raw %}
TODO

- explain basic HTML (referer to other website)
- explain Nunjucks file
- explain Nunjucks expression ``{{comme ça}}``
- explain `{{title}}` 
- explain `{{content | safe }}` 
- explain meta generator
{% endraw %}


# Layout Usage

TODO explain *Front Matter Data*.

TODO modify `index.md` such as

```
---
title: Hello
layout: base.njk
---

Hello world
```

TODO
- explain [YAML](https://yaml.org/) become javascript value data
- explain md text becomes HTML in the `content` data
- `layout` line trigger layout file application


# Another page, add link

TODO add another page with a link from the index.md

TODO explain `http://localhost:8080/xxx` instead of `http://localhost:8080/xxx.html`


TODO refer to https://www.11ty.dev/docs/permalinks/#cool-uris-dont-change


# Add CSS

TODO Create `public/css/style.css` 

```
body {
    font-family: Helvetica, Arial, sans-serif;
    background-color: cadetblue;
    max-width: 80ch;
    text-wrap: pretty;
    margin-inline: auto;
}

h1, h2, h3 {
  text-wrap: balance;
}

h1 {
  text-align: center;
}
```

TODO update `head` of `base.njk` with

```
<link rel="stylesheet" href="/css/style.css">
```

# Add a image

TODO

# Add a data file

TODO


# Deployment

TODO explain web server

TODO explain old-school with FTP, rsync or zip file
```
npx @11ty/eleventy
```


TODO explain JAMSTACK way with serverless cloud

- [Jamstack](https://jamstack.org/)


TODO give context with some provider ?

- [netlify](https://www.netlify.com/)
- [Vercel](https://vercel.com/)
- [cloudfare page](https://pages.cloudflare.com/)

TODO explain git usage, push

TODO explain deployment https://www.11ty.dev/docs/deployment/


# What to do next

TODO give pointer to bigger good quality and uptodate tutorial?

- https://11tybundle.dev/categories/getting-started/
- https://learn-eleventy.pages.dev/


