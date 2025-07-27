# Want to Write Your Novel in LaTeX?

An utterly deranged\* decision.

So did I.

This repository contains a **template for writing fiction in LaTeX** – not just
novels, but anthologies; short stories; anything you might want –
**compiling to both PDF and e-reader-ready EPUB 3 formats,** something for which
weeks of research and a whole heap of boilerplate would normally be required.
It sets a reasonable default style, and aims to be customizable.

As an added bonus, it lets you track your writing via Git, the benefits of
which I hardly need to extol if you’ve found your way here!

\*&thinsp;&NoBreak;Though in reality, it turns out to be surprisingly
practical!


## How to Use

In preparation, you will need:

* **[Visual Studio Code](https://code.visualstudio.com/)** as your editor.

* The **[LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop)**
  extension for VS Code.

* Though optional, the **[LTeX+](https://marketplace.visualstudio.com/items?itemName=ltex-plus.vscode-ltex-plus)**
  extension for VS Code is useful for checking spelling and grammar.

* An installation of LaTeX, specifically **LuaTeX.** There are several LaTeX
  distributions, but the main players are **[MiKTeX](https://miktex.org/)**
  and **[TeX Live](https://www.tug.org/texlive/).** The former is smaller but
  more fussy, while the latter is enormous but has… *everything* included.

* An installation of **Perl.** You may already have it installed – run `perl
  -v` on the command line to check. If you’re on Windows, I recommend
  **[Strawberry Perl](https://strawberryperl.com/).**

* A rogues’ gallery of LaTeX packages, but you should either already have those
  included with your distribution, or you should be prompted to install them
  in medias res. The one package you may need to install manually is
  **[TeX4ebook](https://ctan.org/pkg/tex4ebook)** – see your distribution’s
  instructions for installing packages.

To begin writing, simply make a copy of `Book/template.tex`, add your new file
to the list of source files in `book.tex`, and start typing away.
…Oh, and you should probably remove the example chapters.
By default, this repository is set up for long-form fiction split into multiple
files, but if you want to write something shorter, there’s nothing stopping you
from typing directly into (and renaming!) `book.tex`.

The build flow works as such: Whenever you save a chapter, that chapter will
be automatically built as a PDF, so that you may preview it (semi-)live. To
build the whole book, open `book.tex` (it matters which file is open!), press
<kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd> to open the command palette,
and run <kbd>Latex Workshop: Build with recipe</kbd>. In the next menu, select
whether you want to build a PDF or an EPUB. The resulting file will be output
as `book.pdf` or `book.epub`, respectively.

If I may make a suggestion, keeping your writing ⁠/ plotting notes in an
[Obsidian](https://obsidian.md/) vault in the same folder works wonders –
it makes your notes trackable via Git alongside your writing as well.


### Customization

You’ll likely want to configure various metadata and typographical options.
They can be added and edited primarily in these places:

* The `.tex` files in `configuration/` **(`preamble.tex`, `packages.tex`,
  `fonts.tex`, `style.tex`, and `text-commands.tex`)** contain all the LaTeX
  code that will appear before the document in every LaTeX file. Here’s where
  you add packages, change options, style the PDF, and generally write LaTeX
  code.

* Replace **`Images/cover.jpeg`** to set the cover image for the book.

* Out of the box, this template is set to use American English. To change this,
  change the line `\usepackage[USenglish]{babel}` in
  **`configuration/packages.tex`**, the line `"ltex.language": "en-US",`
  in **`.vscode/settings.json`**, and the line
  `\Configure{DocumentLanguage}{en-US}` in
  **`configuration/xhtml-config.cfg`**. For example, to switch to British
  English, change them to `\usepackage[UKenglish]{babel}`,
  `"ltex.language": "en-GB",`, and `\Configure{DocumentLanguage}{en-GB}`
  respectively.

* **`configuration/xhtml-style.css`** lets you style the EPUB using CSS.

* **`configuration/xhtml-config.cfg`** contains the [TeX4Ht configuration](https://www.kodymirus.cz/tex4ht-doc/Configurations.html#configurations2) –
  i.e. the configuration for EPUB output. Among other things, it lets you
  set metadata (title, contributors, ISBN…) and add fonts.

* **`configuration/xhtml-code.cfg`** contains more TeX4Ht configuration, but is
  intended to contain the more technical side of things – custom HTML code
  certain LaTeX elements are translated into, for example. Hopefully, you won’t
  have to mess with this at all.

Note that the styles of the PDF version and the EPUB version are almost
entirely separate – think of it as “LaTeX style goes for the PDF; CSS style
goes for the EPUB.”

The `code/` directory belongs to code inherent to the template – you likely
won’t have to look in there unless you want to contribute to this repository.


### Special Commands

As this is LaTeX, you can make your own macros as willy-nilly as you want, but
the template ships with some commands that are particularly handy for writing
fiction. You can dig into the custom ones in `configuration/text-commands.tex`,
but for your convenience, allow me to introduce a few:

* **`\chapter{Chapter Title}`** will start a new numbered chapter complete with
  heading, while `\chapter*{Chapter Title}` will do the same but unnumbered
  (for example useful for `\chapter*{Prologue}`).

* **`\scene`** will create a scene break – i.e., leave a line blank before
  the next paragraph.

* **`\sectionbreak`** will create a section break with an asterism. It’s like a
  scene break, but even more prominent.

* We have *three different kinds of italics!* I recommend using these over
  LaTeX’s default `\textit`.

    * **`\em{emphasized text}`** creates italics in the PDF version, and `<em>`
      tags (which are also italic) in the EPUB ⁠/ HTML versions.
    * **`\italic{italicized text}`** creates italics in the PDF version, and
      `<i>` tags (which are italic) in the EPUB ⁠/ HTML versions.
    * **`\titalic{two-letter ISO language code}{some title}`** creates italics
      in the PDF version, and `<cite>` tags (which are italic) in the
      EPUB ⁠/ HTML versions.
      For example, `\titalic{ja}{Sōten no Shiroki Kami no Za}` renders as
      `<cite lang="ja-Latn">Sōten no Shiroki Kami no Za</cite>`.
  
  The Mozilla Developer Network summarizes the differences between these as
  following:

  > [T]he visual result is the same. However, the semantic meaning is different. The `<em>` element represents stress emphasis of its contents, while the `<i>` element represents text that is set off from the normal prose, such as a foreign word, fictional character thoughts, or when the text refers to the definition of a word instead of representing its semantic meaning. (The title of a work, such as the name of a book or movie, should use `<cite>`.)

* **`\footnote{Blah blah blah…}`** will create a footnote.

* **`\href{https://example.com}{link text}`** will create a web link.


## Minutiæ

This template makes some minor typographical decisions – it assumes that you
won’t want linebreaks before en and em dashes, for one, and it sets em dashes
surrounded by two hair spaces (“a&hairsp;&NoBreak;—&hairsp;b” instead of
“a—b”).

What it does *not* do is automate “smart” typography. For [deeply nerdy
reasons,](https://tex.stackexchange.com/a/126315/392788) this template
delegates that to you, the typist: You’ll have to decide if you want to use
spaced en dashes, em dashes, smart quotes, dumb quotes, or what have you.
My suggestion for typing these is a *compose key* (on Windows, that’s
[WinCompose](https://github.com/samhocevar/wincompose)), but of course, you
can also use LaTeX or Babel graphemes such as ` `` `, `''`, `--`, and `---`.


## Contributions

This template can certainly be made better, more user-friendly, and more
versatile. Do you have LaTeX experience and wish to help out your fellow
apex-nerd writers? Feel free to submit issues and pull requests to this repo!
Typographical improvements, accessibility improvements, features, and
ease-of-use improvements are all welcome.

At the moment, it’s made for a build flow centered around VS Code, but that’s
only because it happens to be what I use – if you want to add support for
alternative tooling, be my guest!


## Acknowledgements

I could not possibly have put this together without the help of Michal Hoftich
(@michal-h21), the maintainer of TeX4ebook and Make4ht (and honorary maintainer
of TeX4ht, if I’m to be honest), who tirelessly answers *everybody’s* questions
about the software on the TeX Stack Exchange, and adds fixes and compatibility
workarounds upstream in real time as needed. It’s not the most user-friendly
software in the world (heck, it’s LaTeX – what do you expect), but
user-friendliness matters less when you have a wonderful man to help you out
personally.


## Contact

Having written a good bit of fiction in LaTeX, I now possess arcane answers to the most abstruse of questions. If you want help with this template, feel free to [hit me up on BlueSky.](https://bsky.app/profile/obskyr.bsky.social) My direct messages are open!


---

Go forth&hairsp;&NoBreak;—&hairsp;write righteously and egregiously.  
—&hairsp;&NoBreak;Molly
