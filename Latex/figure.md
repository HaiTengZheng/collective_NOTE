# graphicx
> \usepackage{graphicx}
## config search path
> \graphicspath{{./figures}{./additionalFigures}}

# scale the image to 80% of the text width
> \includegraphics[width=0.8\textwidth]{figure.eps}

# fix the height of a figure, or both width and height
> [width=2cm, height=5cm]

# rotate a figure
> [angle=90]

# env
```latex
\begin{figure}[h]
    ...
    \caption{}
    \label{}
\end{figure}
```
- [h]       here
- [t]       top
- [b]       bottom
- [p]       have it on its own page
- [!]       override Latex default positioning parameter
the \caption

