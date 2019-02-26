# Syntax Highlighting of Argdown Codeblocks in Markdown Documents Using Pandoc

The files *"argdown.xml"* and *"ardgown.theme"* can be used to highlight [argdown](http://argdown.org) code blocks within markdown documents via [pandoc](http://pandoc.org/). The simplest way is to use commandline options of pandoc [as described in the documentation](http://pandoc.org/MANUAL.html#syntax-highlighting), e.g.:

```bash
pandoc inputfile --syntax-definition=argdown.xml --highlight-style=argdown.theme -o outputfile
```

*Ǹotes:*

+ These features require a pandoc of at least version 2.0.
+ Additionally to the two files specified by the options, the file 'language.dtd' has to be in the same directory.

## Customised Argdown Codeblocks for Pdf- and Beamer-Output

In case you want to adjust the formatting of code blocks for pdf- and/or latex-beamer output, you can redefine the latex-environments of the given pandoc template by providing an additional *tex-file* to be included in the header by the `H`-option (`pandoc ... -H extra-header-file.tex ...`). E.g. something like:

```latex
\usepackage[framemethod=TikZ]{mdframed}
\usepackage{xcolor}
\mdfsetup{skipabove=\topskip,skipbelow=\topskip}
\mdfdefinestyle{codedefault}{%
backgroundcolor=black!4,
roundcorner=2pt,
linecolor=black!30,
linewidth=0.5pt,
leftmargin=10, rightmargin=10,
rightline=true,
innerleftmargin=10,innerrightmargin=10}
% redefining the Shaded-Environment of the pandoc-template to allow customised
% style-settings
\renewenvironment{Shaded} {\centering \begin{mdframed}[style=codedefault]} {\end{mdframed}}

% Adjust fontsize for code-blocks if necessary (by redefining the
% Highlighting-Environment of the pandoc-template)
%\DefineVerbatimEnvironment{Highlighting}{Verbatim}{commandchars=\\\{\},fontsize=\small}
```


## Credits and license

The development of Argdown and Argdown-related tools is funded by the [DebateLab](http://debatelab.philosophie.kit.edu/) at KIT, Karlsruhe.

All code is published under the MIT license.
