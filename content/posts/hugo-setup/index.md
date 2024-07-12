---
title: "LaTeX with Hugo and PaperMod"
date: 2024-07-11
# weight: 1
# aliases: ["/first"]
tags: ["LaTex", "MathJax", "Hugo", "PaperMod", "Markdown"]
categories: ["blog"]
author: "behoovah"
# author: ["Me", "You"] # multiple authors
showToc: true
TocOpen: false
draft: false
hidemeta: true
comments: false
# description: "Desc Text."
# canonicalURL: "https://canonical.url/to/page"
disableHLJS: true # to disable highlightjs
disableShare: true
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: false
ShowPostNavLinks: false
ShowWordCount: true
ShowRssButtonInSectionTermList: false
UseHugoToc: true
# cover:
  #  image: "<image path/url>" # image path/url
  #  alt: "<alt text>" # alt text
  #  caption: "<text>" # display caption under cover
  #  relative: false # when using page bundles set this to true
  #  hidden: true # only hide on current single page
# editPost:
  #  URL: "https://github.com/<path_to_repo>/content"
  #  Text: "Suggest Changes" # edit text
  #  appendFilePath: true # to append file path to Edit link
---
## Intro
I recently set up my personal site using [Hugo](https://gohugo.io/) the static site generator, with deployment
to github pages. Most of the proccess was straight-forward and enjoyable. I did run into a few problems when 
trying to enable support for LaTeX type syntax embedded in my markdown files. I thought I would do a short
step-by-step write-up for future reference.

Most of this setup is available in the [Official Hugo Documentation](https://gohugo.io/content-management/mathematics/)
but there are a few pitfalls and theme specific steps that are not included there.

## Configure Goldmark
[Goldmark](https://gohugo.io/getting-started/configuration-markup/) is the default way that Hugo turns your
markdown files into HTML.  

You will need to add this to your main config, hugo.yml or toml file at the top of the directory your site is in:
(<your-site-name>/hugo.yml)
```
markup:
  goldmark:
    extensions:
      passthrough:
        delimiters:
          block:
          - - \[
            - \]
          - - $$
            - $$
          inline:
          - - \(
            - \)
        enable: true
params:
  math: true
```
This will prevent GoldMark from wrongly interpreting LaTeX syntax within the delimiters as markdown.
If you are using a parser other than goldmark you will need to refer to the docs to see if it will 
inerfere with the LaTeX syntax.

##  Create a Partial Template
Next you will want to navigate from the top directory into layouts/partials/ and create a new file called
math.html, with the following content:

/site-name/layouts/partials/math.html
```
<script id="MathJax-script" async src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-chtml.js"></script>
<script>
  MathJax = {
    tex: {
      displayMath: [['\\[', '\\]'], ['$$', '$$']],  // block
      inlineMath: [['\\(', '\\)']]                  // inline
    }
  };
</script>
```
We will have our theme load this script into the header of each page. It will connect to the CDN at the given
url and using the js file to convert the LaTeX syntax to be displayed on the fly when the page is loaded.
(note that you will want all your delimiters to match in each of these steps/files, if you want to change them to something
different just make sure it is consistent).

## Use Theme to Call the Partial Script
I am using the [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme, which has a file called 
'extend_head.html' in the layouts/partials within the theme folder. (for me: <site-name>/themes/PaperMod/layouts/partials/extend_head.html).
We want to copy this file into our global Hugo layouts/partials directory. So something like:
```
cp <site-name>/themes/PaperMod/layouts/partials/extend_head.html ~/<site-name>/layouts/partials/extend_head.html
```
Then add a call to load the partial created in the previous step to the file in the global directory:
~/site-name/layouts/partials/extend_head.html
```
{{ if .Param "math" }}
    {{ partialCached "math.html" . }}
  {{ end }}
```
When hugo loads the PaperMod theme it will use our custom extend_head.html to override the content of the one in the
theme folder. PaperMod will then add it to the header of every page, extending the normal header.

## Add Math Parameter to Config
Hugo will be checking if we have the 'math' parameter enabled before it utilizes the partial so we need to enable
it in the main config hugo.yml or we can enable it per page:

### Per Page:
/site-name/hugo.yml
```
params:
  math: false
```
Then to enable per page:
/site-name/content/blog-post.md
```
---
title: "Migration"
date: 2020-07-09
# weight: 1
# aliases: ["/first"]
tags: ["Hugo", "Static-Site", "Markdown"]
categories: ["blog"]
author: "behoovah"

math: true
---
```
### Globally:
/site-name/hugo.yml
```
params:
  math: true
```

## Testing
You can test that your changes have worked by running the hugo server command.
if you do some syntax such as:
```
This is an inline \(a^*=x-b^*\) equation.

These are block equations:

\[a^*=x-b^*\]

\[ a^*=x-b^* \]

\[
a^*=x-b^*
\]

These are block equations using alternate delimiters:

$$a^*=x-b^*$$

$$ a^*=x-b^* $$

$$
a^*=x-b^*
$$
```
You should get an output like this:

This is an inline \(a^*=x-b^*\) equation.

These are block equations:

\[a^*=x-b^*\]

\[ a^*=x-b^* \]

\[
a^*=x-b^*
\]

These are block equations using alternate delimiters:

$$a^*=x-b^*$$

$$ a^*=x-b^* $$

$$
a^*=x-b^*
$$

Another thing to check is to open the browser inspector and go to the network tab or
wherever it shows what urls are activated from the page load. You should be able to see that when you refresh,
the URL for the mathjax CDN is being called.
