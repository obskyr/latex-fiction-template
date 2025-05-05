# Want to Write Your Novel in LaTeX?

An utterly deranged\* decision. So did I. This repository contains a **template
for writing fiction in LaTeX** (and Markdown!)**, compiling to both PDF and
e-reader-ready EPUB formats,** something for which a whole heap of boilerplate
is required. It sets a reasonable default style, and aims to be customizable.

As an added bonus, it lets you track your writing via Git, the benefits of
which I hardly need to extol if you’ve found your way here!

\* Though in reality, it turns out to be surprisingly practical!


## How to Use

In preparation, you will need:

* **[Visual Studio Code](https://code.visualstudio.com/)** as your editor.
* The **[LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)**
  extension for VS Code.
* Though optional, the **[LTeX+](https://marketplace.visualstudio.com/items?itemName=ltex-plus.vscode-ltex-plus)**
  extension for VS Code is useful for checking spelling and grammar.
* An installation of LaTeX, specifically **LuaTeX.** There are several LaTeX
  distributions, but the main players are **[MiKTeX](https://miktex.org/)**
  and [TeX Live](https://www.tug.org/texlive/). The former is smaller but
  more fussy, while the latter is enormous but has… *everything* included.
* An installation of **Perl.** You may already have it installed – run `perl
  -v` to check. If you’re on Windows, I recommend
  **[Strawberry Perl](https://strawberryperl.com/).**
* A rogues’ gallery of LaTeX packages, but you should either already have those
  included with your distribution, or you should be prompted to install them
  in medias res. The one package you may need to install manually is
  **[tex4ebook](https://ctan.org/pkg/tex4ebook)** – see your distribution’s
  instructions for installing packages.

To begin writing, simply copy `Sections/template.tex`, add your new file to the
list of source files in `book.tex`, and start typing away. …Oh, and you should probably remove the example chapters.

The build flow works as such: Whenever you save a chapter, that chapter will
be automatically built as a PDF, so that you may preview it (semi-)live. To
build the whole book, open `book.tex` (it matters which file is open!), press
<kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd> to open the command palette,
and run <kbd>Latex Workshop: Build with recipe</kbd>. In the next menu, select
whether you want to build a PDF or an EPUB. The resulting file will be output
as `book.pdf` or `book.epub`, respectively.


## Contributions

This template can certainly be made better, more user-friendly, and more
versatile. Do you have LaTeX experience and wish to help out your fellow
apex-nerd writers? Feel free to submit issues and pull requests to this repo!
Typographical improvements, accessibility improvements, features, and
ease-of-use improvements are all welcome.

At the moment, it’s made for a build
flow centered around VS Code, but that’s just because it happens to be what I
use – if you want to add support for alternative tooling, be my guest.
