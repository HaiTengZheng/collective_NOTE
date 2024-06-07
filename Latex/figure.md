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

# for bitmaps, enable interpolation (插值)
> [interpolation]

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
- [!]       override Latex default positioning parameter    (!:exclamation)
the \caption
## lable
good practice
`fig:name` for figures
`tab:name` for tables
`eq:name` for equations

# limit the floating figures and tables
> \usepackage[section]{placeins}
> \FloatBarrier

# fix the position of a figure
```latex
\usepackage{float}
\begin{figure}[H]
```

# trim and clip
```latex
\includegraphics[trim = 1cm 2cm 3cm 4cm, clip]{filename}
```
left bottom right top

# add a frame to an image
> \frame{...}
> \framebox{...}
> \fbox{...}
