# Overview

This is a collection of LaTeX style files designed for poster creation by SIUE undergraduate mathematics majors as part of their senior capstone projects.
It uses the FlowFram package to achieve the appropriate layouts.
The included layouts were designed with FlowframTk.

# Getting started

The style files end in `.sty` should be placed in one of two places:

* __simple:__ whichever folder you keep your `.tex` file for the poster.
* __better:__ your local `texmf` directory tree (e.g., `~/texmf/tex/latex/siue-poster/` or similar).

The file `example-poster.tex` provides an example of the usage of these packages.
There are a few important pieces of information to note.

* __fonts:__ you will have to change the fonts chosen in the example document (i.e., `Linux Libertine` and `DejaVu Sans`) to some installed on your system (e.g., `Times New Roman` and `Arial`).
* __TeX engine:__ currently, the system requires that you compile your document with `LuaTeX` as opposed to the more common `pdfTeX` or similar. However, `LuaTeX` comes bundled with all major TeX distributions including MikTeX (Windows), MacTeX (Apple) and TeX Live (Linux); it should not be particularly hard to use.
* __SIUE logo:__ for copyright reasons, a copy of the SIUE logo cannot be included with the distribution of this software. However, you can obtain a copy of it in `.eps` format from the [University Marketing and Communications][https://www.siue.edu/marketing-and-communications/services/graphic-design/wordmarks-for-download.shtml] website. You can also contact Dr. Loreaux for a copy of the logo in `.pdf` format.

After attending to these three items, you should be able to compile `example-poster.tex` successfully.

# Basic usage

There are four necessary steps to achieve a working poster document.

1. Choosing fonts (serif and sans serif) that are installed on your system.
2. Include the SIUE poster settings, which defines a number of color palettes and theorem-like environments.
3. Include a poster layout format.
4. Choose a provided color palette.

You can choose the fonts with the `\setmainfont{<serif-font-name>}` and `\setsansfont{<sans-serif-font-name>}` commands.
The poster settings are included in the `siue-poster-settings` package, and the poster layout formats are included in the other `.sty` package files.
You should always have the following somewhere in your preamble (i.e., before `\begin{document}`):

```latex
\usepackage{siue-poster-settings.sty}
\usepackage{harper-subdued.sty}
```

In the above, `harper-subdued.sty` may be replaced by one of the other poster layouts.
The department cannot afford to print layouts with background colors.
Therefore, if you choose to use the `harper-lobster.sty` layout, then you will need to have the document printed on your own dime elsewhere.

You can choose (or switch) color palettes using `\colorpalette{<palette-name>}`.
The recommended color palette for a white background is `siuesubdued`.
Other color palettes can easily be defined using hexadecimal RGB values.
See the `siue-poster-settings.sty` file for examples.

# Defined macros

## Predefined environments

There are a number of predefined environments included in this package.
There are *theorem-like* environments,

* theorem,
* lemma,
* proposition,
* formula;

and *definition-like* environments,

* definition,
* remark,
* example,
* question,
* problem.

The reason for the categories is to distinguish between *results* and *information*.
Using a predefined environment is standard.
In particular, the code

```latex
\begin{theorem}
  Here is the text of my theorem.
\end{theorem}
```

will produce a theorem-like box in the output.

## Creating new environments

Adding a new theorem-like (or definition-like) environment is as simple as:

```latex
\thmstylebox{<environment-name>}{<environment-title>}
\defstylebox{<environment-name>}{<environment-title>}
```
The `<environment-name>` is the name used to create the environment in the TeX source, and the `<environment-title>` is the text which will appear in the final pdf as the heading of the encased environment.

## One-off environments

If you wish to give an environment a special single-use title without defining a whole new environment, you can achieve that in the following way.
There are two special environments, `thmcustom` and `defcustom`, which take an additional mandatory argument that serves as the environment title.
So, for example,

```latex
\begin{thmcustom}{Loreaux's Theorem}
  This is the content of Loreaux's Theorem.
  It is not particularly interesting.
\end{thmcustom}
```

produces a definition-like environment with the title *Loreaux's Theorem*.

# Formatting tips

Text in the document will "flow" from one "box" in the layout into the other.
If you have several environments in your document, this can lead to unsightly ragged bottoms to your columns.
After you have finished editing your content, it might be useful to help the formatting via the use of the `\vfill` and `\newpage` commands.
The `\vfill` command is a flexbile vertical space gets distributed evenly among all `\vfill`s in the same column.
You can then use `\newpage` to indicate forced column breaks in the source.

# Custom layouts

If for some reason none of the provided layouts suit the needs for your poster, please contact Dr. Loreaux so that we can accommodate you.
It is recommended that you try to use one of the default layouts provided, and we do not recommend that you design a custom layout yourself; the work involved is arduous for new users.
