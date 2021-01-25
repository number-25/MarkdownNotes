# Creating Beautiful Documents

This is a short guide to demonstrate how to build beautiful documents
using markdown, html, css, javascript, latex, pandoc and git. This document
itself is NOT beautiful but the example.html file shows what is possible.

## Using Vim

Vim is the best command line text editor. It is a bit of a learning curve
but it is well worth it. You can get a nice introduction to vim by typing
`vimtutor` into the terminal once vim is installed.


## Create a Markdown Doc

Typing `vim example.md` will create a markdown file. To learn more about Markdown check
out [markdowntutorial](https://www.markdowntutorial.com/).

 
## Latex

You can use latex by enclosing the symbols inside single \$ signs for inline e.g. $x^2$, and double \$\$  which will render as:

$$
y = mx+c
$$

## Citations
You can add citations using bibtex or others. The database is just stored in a separate file as

```bash
BIB_FILE="./references.bib"
```

They can be added in-text by using [@uniqueIdentifier1; @uniqueIdentifier2] etc.

To include hyper-links to the bibliography, use the following metadata argument with pandoc

```bash
pandoc ... -M link-citations=true
``` 

## CSL - Style

[Zotero](https://www.zotero.org/styles?format=numeric) has all the citation styles you need. Just download to your folder and 
create a link to your citation style with:

```bash
CITE_FILE="./nature.csl"
```

## CSS
You can style the whole document using css, and give it to pandoc using the `-c` or `--css=$STYLE_FILE` argument in pandoc.
It can point to multiple css files.

```bash
STYLE_FILE="./style.css"
```

## Convert to HTML

The following command can be run, either in vim (include !) or in bash.

```bash
OUT_FILE="./example.html"
```

```bash
!pandoc $IN_FILE -t html -s --standalone --mathjax --bibliography=$BIBFILE --csl=$CITE_FILE -M link-citations=true --css=$STYLE_FILE -o $OUT_FILE
```

Pandoc is extremely powerful and has heaps of options which you can read about [here](https://pandoc.org/MANUAL.html).

## Git

This can all be integrated with git using the standard `git init` + `git add` + `git commit` commands etc. A good workflow is shown
in this [article](https://medium.com/@rvprasad/a-git-workflow-for-writing-papers-in-latex-4cfb31be4b06). 

## Other Remarks

That is pretty much it. The hardest part is coming up with nice css so it will render as you desire. It is probably worth having a base
 style e.g. `base_style.css` file to take care of the page width, background color etc for the body, as well as any other common commands.

Plenty to explore!


## Extras! 

The following should serve as a rough template for creating .pdf files from markdown documents with citations embedded and a bibliography generated at the end of the document. 

```pandoc ./M1_Introduction.md --citeproc --csl=$CSL --bibliography=$BIB --variable papersize=a4paper -V geometry:margin=1in -o testing.pdf```






