# LaTeX Article Template

Latex article template, meant for use in [Visual Studio Code](https://code.visualstudio.com/)

## Requirements

- Windows 10 PC

## Setup

This section will guide the user through installing the appropriate software, downloading
this repository, opening the document with Visual Studio Code, and doing the initial build.

### Install Software

Using a Windows 10 PC, install the following software:

- [Chocolatey](https://chocolatey.org/install)
- Visual Studio Code
    - > choco install vscode
    - install [Latex Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop) extension
- MikTex
    - > choco install miktek
- Perl
    - > choco install strawberryperl

### Download Repository

Download this repository by selecting Code -> Download ZIP

Unzip to where you want to keep your document folder, rename the folder to the new 
document's name.

### Open the folder within Visual Studio Code

Open Visual Studio Code. 
- This can done quickly by pressing the windows key, then typing "vscode" + Enter

Open the folder within Visual Studio Code. Select File -> Open Folder.
- This can be done quickly by holding the CTRL key and pressing "k" then "o".

Navigate to where the folder is kept, open the folder.
Select "Select Folder"

Using Visual Studio's built in file explorer, open the "subfiles-collections" folder, then select 
"main-document.tex"

### Initial Build

Select the green triangle in the top right to build the document.
- This can be done quickly by similtaneosly pressing CTRL + ALT + B

Select the split window icon with the magnifying glass directly left of the build arrow to open the
compiled pdf in a split window.
- This can be done quickly by similtaneosly pressing CTRL + ALT + V

## Editing

This section will guide the user through the basics of editing.

### Finding resources

Find package documentation from [ctan.org](https://www.ctan.org/pkg/)

Packages used in this template:

- [hyperref](https://www.ctan.org/pkg/hyperref) | [pdf manual](https://mirrors.rit.edu/CTAN/macros/latex/contrib/hyperref/doc/hyperref-doc.pdf)
- [geometry](https://www.ctan.org/pkg/geometry) | [pdf manual](https://mirrors.rit.edu/CTAN/macros/latex/contrib/geometry/geometry.pdf)
- [subfiles](https://www.ctan.org/pkg/subfiles) | [pdf manual](https://ctan.math.washington.edu/tex-archive/macros/latex/contrib/subfiles/subfiles.pdf)
- [graphicx](https://www.ctan.org/pkg/graphicx) | [pdf manual](https://mirrors.rit.edu/CTAN/macros/latex/required/graphics/grfguide.pdf)
- [datetime2](https://www.ctan.org/pkg/datetime2) | [pdf manual](https://mirrors.concertpass.com/tex-archive/macros/latex/contrib/datetime2/datetime2.pdf)
- [biblatex](https://www.ctan.org/pkg/biblatex) | [pdf manual](https://ctan.mirrors.hoobly.com/macros/latex/contrib/biblatex/doc/biblatex.pdf)

### Main Document

This section begins the document with the document's title page and creating the table of contents:

```
\begin{document}
\subfile{../subfiles-tex/title-page.tex}
\pagenumbering{roman}
\tableofcontents
\addtocontents{toc}{~\hfill\textbf{Page}\par}
\clearpage
```

The `\subfile{../subfiles-tex/title-page.tex}` line tells the main document to include the title page,
which is defined in the sub-file `/subfiles-tex/title-page.tex`



This section begins the body of the document:

```
\pagenumbering{arabic}

\section{SECTION 1}
\subfile{../subfiles-tex/subfile.tex} \newpage{}
```

The `\subfile{../subfiles-tex/subfile.tex} \newpage{}` line tells the main document to include a 
subfile listed int the `/subfiles-tex/` directory. The `\newpage{}` tells the main document
to end the page, starting a new one after the called subfile. This can be omitted to include
multiply sub-files on the same page.

### Sub Files

All sub-files must include the lines:

```
\documentclass[../subfiles-collections/main-document.tex]{subfiles}

\begin{document}
    <YOUR CONTENTS HERE>
\end{document}
```