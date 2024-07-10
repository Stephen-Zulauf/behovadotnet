---
title: "Marker Reference Tests"
date: 2024-07-06
# weight: 1
# aliases: ["/first"]
tags: ["test", "markdown", "mathjax", "goat"]
categories: ["notes"]
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
hideSummary: true
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

In this example we will shows most of the basic syntax and test its functionality. 

# MARKER Test

## Maths

This is a block equation:
$$
\begin{cases}
x = 42\\
y = \log_{10}(x)
\end{cases}
$$

An this is an inline equation: $$x\in A$$.

## Listings

The first listing is a simple ```cpp``` code and it should be visualized as code (and with syntax highlight if enabled).

```cpp
int 
main(int argc, 
     char *argv[])
{
  std::cout<<"hello world\n";
  return 0;
}
```

The following code block instead can be visualized as _Mermaid_ chart if the extension is enabled in the preferences.

```mermaid
graph LR
A --> B
B -.->C
```

The last code block instead is a _Charter_ plot and the results is plotted as SVG if the extension is enabled:

@figure
```charter
title: a simple plot
x-axis:
  label: x
y-axis:
  label: y
plot:
  x range: -3 3 60
  y math: exp(-(x^2))
  label: gausian
```
@caption(A simple plot)
@/

## Pictures

This is an embedded picture test:

![alt text](kitten.jpg?width=50px)

## Marksmen

This is a test of a goto definition
link through the marksmen lsp.

```
gd
```
to follow link.

[[link-test]]

## Results

For the **Preview**:

| Test               | Status |
| :----------------- | :----- |
| Basic MD           | Ok     |
| Block equation     | Ok     |
| KaTeX settings     | Ok     |
| Inline equation    | Ok     |
| Code listing       | Ok     |
| highlight settings | Ok     |
| Mermaid graph      | Ok     |
| Mermaid settings   | Ok     |
| Figure caption     | Ok     |
| Numbering          | Ok     |
| Charter            | Ok     |
| Charter preferences| OK     | 


For the **Editor**:


| Test               | Status |
| :----------------- | :----- |
| Lines number       | Ok     |
| Wrap Test          | Ok     |
| Right Margin       | Ok     |
| Spell check        | Ok     |
| Current line HL    | Ok     |
| Syntax highlight   | Ok     |
| Editor theme       | Ok     |
| Tabulation settings| Ok     |
| Sketcher           | Ok     |
| Scroll position    | Ok     |
