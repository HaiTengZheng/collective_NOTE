# Typesetting an algorithm
```tex
\usepackage{dsfont}
\usepackage{mathtools}
\usepackage{algorithm}
\usepackage{algorithmicx}
\usepackage{algpseudocode}
```

---
# Printing a code listing
```tex
\usepackage{listings}
\usepackage{xcolor}
% `inconsolata` for an excellent typewritter font
\usepackage{inconsolata}

% commands and environments of the listings package start with the `\lst` prefix
\lstset{
    language            = C++,
    basicstyle          = \ttfamily,
    keywordstyle        = \color{blue}\textbf,
    commentstyle        = \color{gray},
    stringstyle         = \color{green!70!black},
    stringstyle         = \color{red},
    columns             = fullflexible,
    numbers             = left,
    numberstyle         = \scriptsize\sffamily\color{gray},
    xleftmargin         = 0.16\textwidth,
    xrightmargin        = 0.16\textwidth,
    showstringspaces    = flase,
    float,
}

\begin{document}
%\begin{lstlisting}[language = C++]
\begin{lstlisting}
// include standard input/output stream objects:
#include <iostream>
int main() {
    std::cout << "Hello World!" << std::endl;
}
\end{lstlisting}

% like `ver`
Use \lstinline!#inclue <iostream>! for including i/o streams.
\end{document}
```
