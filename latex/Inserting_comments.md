# Insert comments
> texdoc pdfcomment
```tex
\usepackage[author={Your name},icon=Note,color=Yellow,open=true]{pdfcomment}
```

## insert a simple comment
```tex
\pdfcomment{Simple documents don't have chapters.}
```

## let the comment marker appear in the margin instead
```tex
\begin{equation}
    \pdfmargincomment{...}
\end{equation}
```

## mark visible content while displaying a comment
```tex
\pdfmargincomment{sections}{You should use subsections.}
```

## Markup comments can be tooltips 
> become visible when we move the mouse pointer over them
```tex
\pdftooltop{formulas}{Formulas can be inline or displayed in their own paragraph}
```

## embrace whole environments with a side line comments
```tex
\begin{pdfsidecomment}[color=Red]{A bulleted list}
    \begin{itemize}
        \item ...
    \end{itemize}
\end{pdfmargincomment}
```

## Place free text somewhere in the document with custom dimensions...
```tex
\pdffreetextcomment[subject={Summar},width=7.5cm,height=2.2cm,opacity=0.5,voffset=-3cm]
{The whole ...}
```

## To make all comments invisible in the final published version, add the final option
```tex
\usepackage[...,final]{pdfcomment}
```
