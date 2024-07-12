---
title: "Migration"
date: 2020-07-09
# weight: 1
# aliases: ["/first"]
tags: ["Hugo", "Static-Site", "Markdown"]
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

### Today I am just about finished with migrating my personal site from wordpress.

I wanted to revamp the way I interact with my site, to make it easy to integrate
into my workflow, and hopefully produce more documentation of what I'm up to.

### I was looking for the following features in my migration:

1. **Write pages in markdown format**.
>I like to do everything in a modal editor these days. I am currently using [Helix text editor](https://helix-editor.com/)
>after migrating from vim. Writing pages in markdown on my prefered editor fits nicely into my setup.
2. **Version control and automation**.
>I wanted an easy way to update my site using version control and pushing to a service like github.
>I am already pushing code to github on the regular so why not my website too?
3. **A place to host my academic notes**.
>I am currently in a computer science major. I wanted to start using my modal editor to take notes in lecture
>and to summerize texts etc. Many of my courses invlove math equations and charts, so I needed the ability to
>use markdown with these integrations.
4. **There were a lot of things I didn't want or need**.
>Complexity was first and foremost. I wanted to keep things as simple and straightforward as possible. I have built
>complicated react sites and javascript web-scrapers before, but that is not my focus here. Here everything should
>be to serve the goal of documenting what I'm doing as easily as possible.
>Lastly I hardly ever used my previous site (lol) so I didnt need to find a streamlined way to convert old posts
and content.

### My solution
After a lot of experiments I finally settled on [Hugo](https://gohugo.io/) which is classified as a 'static site generator'.
Essentially it is a command line tool that I installed on linux. Using the hugo command in a terminal allows you to generate a
static site, and easily add content in markdown format. 
```
hugo new site <site-name>
```
creates a new directory which contains the skeleton of the site and
```
hugo server
```
serves a preview of the site on the local-host, Which is extremly convenient to say the least.

Another big advantage of hugo is it's theme system. I can easily install a theme by git clone-ing the theme 
into the right place and then pointing to it in the yml file hugo uses for its config. I was able to choose a super
minimal theme that looks totally fine [(Papermod)](https://themes.gohugo.io/themes/hugo-papermod/) and hugo
does all the styling for me.

Git-hub automation was very easy, which was another reason I was drawn to hugo. They have a step by step guide
detailed [here](https://gohugo.io/hosting-and-deployment/hosting-on-github/) that details hosting your site on git-hub
pages and setting up automatic deployment when pushing to the repository. I found it painless to set up, and it is sooo
convenient (and free!).

Lastly, hugo supports display of inline [math equations](https://gohugo.io/content-management/mathematics/),
using LaTeX syntax, in markdown pages. This was a must-have for storing my academic notes.

code like:
```
\[
\begin{aligned}
KL(\hat{y} || y) &= \sum_{c=1}^{M}\hat{y}_c \log{\frac{\hat{y}_c}{y_c}} \\
JS(\hat{y} || y) &= \frac{1}{2}(KL(y||\frac{y+\hat{y}}{2}) + KL(\hat{y}||\frac{y+\hat{y}}{2}))
\end{aligned}
\]
```
will turn into:
$$
\begin{aligned}
KL(\hat{y} || y) &= \sum_{c=1}^{M}\hat{y}_c \log{\frac{\hat{y}_c}{y_c}} \\
JS(\hat{y} || y) &= \frac{1}{2}(KL(y||\frac{y+\hat{y}}{2}) + KL(\hat{y}||\frac{y+\hat{y}}{2}))
\end{aligned}
$$
To me thats magic.

Additionally, hugo supports [diagrams and charts](https://gohugo.io/content-management/diagrams/) in markdown format, which is great for computer science.

code like this:
```

```goat


   .---.       .-.        .-.       .-.                                       .-.
   | A +----->| 1 +<---->| 2 |<----+ 4 +------------------.                  | 8 |
   '---'       '-'        '+'       '-'                    |                  '-'
                           |         ^                     |                   ^
                           v         |                     v                   |
                          .-.      .-+-.        .-.      .-+-.      .-.       .+.       .---.
                         | 3 +---->| B |<----->| 5 +---->| C +---->| 6 +---->| 7 |<---->| D |
                          '-'      '---'        '-'      '---'      '-'       '-'       '---'
```

will turn into this:
```goat


   .---.       .-.        .-.       .-.                                       .-.
   | A +----->| 1 +<---->| 2 |<----+ 4 +------------------.                  | 8 |
   '---'       '-'        '+'       '-'                    |                  '-'
                           |         ^                     |                   ^
                           v         |                     v                   |
                          .-.      .-+-.        .-.      .-+-.      .-.       .+.       .---.
                         | 3 +---->| B |<----->| 5 +---->| C +---->| 6 +---->| 7 |<---->| D |
                          '-'      '---'        '-'      '---'      '-'       '-'       '---'
```
### Conclusion
So far I am loving the new workflow with hugo. I can stay comfy on the command-line all day and I don't have to
spend extra time and energy on a lot of extra styling/features and what-not. Pushing the changes to github is great.

The only downside that I have found to using hugo is the initial configuration. For me it just took a bit of time,
but really it was easy and enjoyable for someone like me who likes to tinker here and there. Relative to the experience
of setting up a website using wordpress or some other CMS it was downright awesome. I would recommend anyone try out
hugo for their personal site or blog.
