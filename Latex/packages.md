# packages
- geometry
- graphicx
- amsmath
- amssymb
- tikz
- xcolor
- hyperref
- siunitx
- fancyhdr
- biblatex
- setspace
- wrpfig

# geometry
adjust the page margins and line spacing
> \usepackage[margin=1.5cm]{geometry}
> \usepackage[left=2cm, right=2cm, top=1.54cm, bottom=1cm]{geometry}

# setspace
a simple way of changing the line spacing
> \usepackage[onehalfspacing]{setspace}     % for 1.5x line spacing

# wrpfig
habe text wrapping around a figure
```latex
\begin{wrapfigure}{|}{0.3\textwidth}
    \centering
    \includegraphics[width=0.3\textwidth]{figure}
\end{wrapfigure}
```
