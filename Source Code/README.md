# Source TeX Files

If you're here you can take a look at how we have done our TeX files up and if you want to contribute, here's a general style guide for what you can do.

## Style Guide
Our questions follow a common format that we (mostly) stick to and if you would like to contribute it is important that you follow the same style.  

### General Set-Up
Here is the general set-up of our TeX document, very minor but there are some things to take note if you would like to create your own Question Papers from scratch.

```latex
\documentclass[12pt, a4 paper]{article} % Our text is 12pt and we target A4 Paper
\usepackage[inner=2.0cm,outer=2.0cm,top=2.5cm,bottom=2.5cm]{geometry} % These are our margins
\usepackage{environ} % To help define our switchable answer environment
\usepackage{outlines, enumitem} % For custom enumerate labelling
\usepackage{amsgen,amsmath,amstext,amsbsy,amsopn,tikz,amssymb,tkz-linknodes} % These are our Math Libraries: tkz-linknodes is not found by default on TeXLive
\usepackage{pgfplots} % To Draw our graphs we use pgfplots
\usepackage{graphicx} % Package to display inline images

\linespread{1.6} % Double Line Spacing

% Our custom enumerate labelling, just making the outlines bold basically
\setlist[enumerate,1]{label=\textbf{\arabic*}}
\setlist[enumerate,2]{label=\textbf{({\alph*})}}
\setlist[enumerate,3]{label=\textbf{({\roman*})}}

% Comment the first one out when rendering the Question Paper, comment the second one out when rendering the answer key.
\newcommand{\comm}[1]{}
\NewEnviron{answer}{\vspace{3mm} \\ \color{blue} {\BODY} \color{black}}
%\NewEnviron{answer}{\color{blue} \comm{\BODY} \color{black}}% Use this method to hide all answers

```

### Question Set-Up
Each question is found in a template like this

```latex
\begin{outline}[enumerate]
  \1 Lorem ipsum dolor sit amet, consectetur adipiscing elit. % Question 1
    \2 Solve for $x$
      \begin{answer}
        % Answers go within here
        \begin{align*}
          x=\frac{-b\pm\sqrt{b^2-4ac}}{2a}
        \end{align*}
      \end{answer}
    \2 Herein lies more questions that you need to find the answer to:
    ...
\end{outline}
```

### Caveats
Please make your answers as detailed as possible, with a good explanation preceding why you're performing the arithmetic in the *align* blocks. Great rigour is not really expected but it is helpful for others who are reading if solutions are thorough!  

Here are more technical caveats:
```latex
\begin{DOSnDONTS}
  \int x^2 dx %vs% \int x^2 \mathrm{d}x % To make sure that 'dx, dy, dz' etc. are rendered properly, please use \mathrm{d}x
  f(x) %vs% \mathrm{f}(x) % To make sure that 'f(x), g(x)' etc. are rendered properly, please use \mathrm{f}(x)
  e %vs% \mathrm{e} % Throughout this project euler's number has been represented as \mathrm{e} instead of e so we'd like to keep it consistent!
\end{DOSnDONTS}
```
