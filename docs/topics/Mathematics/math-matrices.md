# Matrizen

## Was ist eine Matrix? {id="what-is-a-matrix"}

Eine Matrix ist eine rechteckige Anordnung von Zahlen, die in Zeilen und Spalten organisiert sind. Diese Anordnung ermöglicht es, komplexe Berechnungen und Transformationen in kompakten Formen darzustellen. Matrizen werden häufig verwendet, um lineare Gleichungssysteme zu lösen oder geometrische Transformationen durchzuführen.

Eine Matrix besteht aus den folgenden Eigenschaften.

- <format color="%LinkColor%">[Ordnung](#order)</format>
- Rang

## Ordnung {id="order"}

Die Größe oder Ordnung einer Matrix wird durch die Anzahl der Zeilen <format color="%Highlight%">$m$</format> und Spalten <format color="%Highlight%">$n$</format> beschrieben. Eine Matrix mit <format color="%Highlight%">$m$</format> Zeilen und <format color="%Highlight%">$n$</format> Spalten wird als <format color="%Highlight%">$m \times n$</format> Matrix bezeichnet.

## Addition und Subtraktion von Matrizen {id="addition-and-subtraction-of-matrices"}

> Matrizen können nur addiert bzw. subtrahiert werden, wenn sie in <format color="%NoteHighlight%">Zeilen und Spalten</format> übereinstimmen.
{style="note"}

Legt man zwei Matrizen übereinander, werden die übereinanderliegenden Zahlen addiert bzw. subtrahiert.

```tex
\begin{align}
    \begin{pmatrix}
        \textcolor{cyan}{2}&\textcolor{orange}{3}&\textcolor{lightgreen}{2}\\
        1&4&1\\
        4&2&2
    \end{pmatrix}
    +
    \begin{pmatrix}
        \textcolor{cyan}{3}&\textcolor{orange}{0}&\textcolor{lightgreen}{3}\\
        2&4&1\\
        1&2&1
    \end{pmatrix}
    =
    \begin{pmatrix}
        \textcolor{cyan}{5}&\textcolor{orange}{3}&\textcolor{lightgreen}{5}\\
        3&8&2\\
        5&4&3
    \end{pmatrix}
\end{align}
```

```tex
\begin{align}
    \begin{pmatrix}
        \textcolor{cyan}{2}&\textcolor{orange}{3}&\textcolor{lightgreen}{2}\\
        1&4&1\\
        4&2&2
    \end{pmatrix}
    -
    \begin{pmatrix}
        \textcolor{cyan}{3}&\textcolor{orange}{0}&\textcolor{lightgreen}{3}\\
        2&4&1\\
        1&2&1
    \end{pmatrix}
    =
    \begin{pmatrix}
        \textcolor{cyan}{-1}&\textcolor{orange}{3}&\textcolor{lightgreen}{-1}\\
        -1&0&0\\
        3&0&1
    \end{pmatrix}
\end{align}
```

>Das Ergebnis einer Addition ist eine <format color="%Highlight%">Summenmatrix</format>.
> 
>Das Ergebnis einer Subtraktion ist eine <format color="%Highlight%">Differenzmatrix</format>.

## Multiplikation von Matrizen {id="multiplication-with-matrices"}

> Zwei Matrizen können nur miteinander multipliziert werden, wenn die <format color="%NoteHighlight%">Spaltenanzahl der ersten Matrix</format> mit der <format color="%NoteHighlight%">Zeilenanzahl der zweiten Matrix</format> übereinstimmt.
{style="note"}

Eine Matrix der Dimension (3 $\times$ 2) kann <format color="%Highlight%">nicht</format> mit einer Matrix der Dimension (3 $\times$ 3) multipliziert werden.

Die Dimension der Ergebnismatrix ergibt sich aus der <format color="%Highlight%">Zeilenanzahl der ersten Matrix</format> und der <format color="%Highlight%">Spaltenanzahl der zweiten Matrix</format>. Eine Matrix der Dimension (2 $\times$ 3) multipliziert mit einer Matrix der Dimension (3 $\times$ 5) ergibt eine neue Matrix der Dimension (2 $\times$ 5).

```tex
\begin{align}
	M&=
    \begin{pmatrix}
        \textcolor{cyan}{1}&\textcolor{orange}{2}&\textcolor{lightgreen}{3}\\
        4&5&6\\
        7&8&9
    \end{pmatrix}
    \cdot
    \begin{pmatrix}
        \textcolor{purple}{1}&4\\
        \textcolor{#0070C0}{2}&5\\
        \textcolor{#E5572B}{3}&6
    \end{pmatrix}\\
    M&=
    \begin{pmatrix}
        \textcolor{cyan}{1}*\textcolor{purple}{1}+\textcolor{orange}{2}*\textcolor{#0070C0}{2}+\textcolor{lightgreen}{3}*\textcolor{#E5572B}{3}&1*4+2*5+3*6\\
        4*1+5*2+6*3&4*4+5*5+6*6\\
        7*1+8*2+9*3&7*4+8*5+9*6
    \end{pmatrix}\\
    M&=
    \begin{pmatrix}
        1+4+9&44+10+18\\
        4+10+18&16+25+36\\
        7+16+27&28+40+54
    \end{pmatrix}\\
    M&=
    \begin{pmatrix}
        14&72\\
        32&77\\
        50&122
    \end{pmatrix}
\end{align}
```

Wird eine Matrix $A$ mit einer Matrix $B$ multipliziert, heißt dies nicht, dass die Matrix $B$ auch mit $A$ multipliziert werden kann.

Zwei quadratische Matrizen derselben Ordnung können jedoch immer multipliziert werden.

## Multiplikation mit Vektoren {id="multiplication-with-vectors"}

> Matrizen können nur mit einem Vektor multipliziert werden, wenn die <format color="%NoteHighlight%">Spaltenanzahl der Matrix</format> mit der <format color="%NoteHighlight%">Zeilenanzahl des Vektors</format> übereinstimmen.
{style="note"}

Die Spaltenanzahl eines Vektors ist immer `1` und das Ergebnis einer Multiplikation ist immer ein neuer <format color="%LinkColor%">[Vektor](math-vectors.md)</format>.

```tex
\begin{align}
	V&=
    \begin{pmatrix}
        \textcolor{cyan}{2}&\textcolor{orange}{2}&\textcolor{lightgreen}{0}\\
        2&-1&-3\\
        1&0&1
    \end{pmatrix}
    \cdot
    \begin{pmatrix}
        \textcolor{purple}{3}\\
        \textcolor{#0070C0}{1}\\
        \textcolor{#E5572B}{2}
    \end{pmatrix}\\
    V&=
    \begin{pmatrix}
        \textcolor{cyan}{2}*\textcolor{purple}{3}+\textcolor{orange}{2}*\textcolor{#0070C0}{1}+\textcolor{lightgreen}{0}*\textcolor{#E5572B}{2}\\
        2*3-1*1-3*2\\
        1*3+0*1+1*2
    \end{pmatrix}\\
    V&=
    \begin{pmatrix}
        6+2+0\\
        6-1-6\\
        3+0+2
    \end{pmatrix}\\
    V&=
    \begin{pmatrix}
        8\\
        -1\\
        5
    \end{pmatrix}
\end{align}
```

## Nullmatrix und Einheitsmatrix {id="zero-matrix-and-identity-matrix"}

Die Elemente einer <format color="%Highlight%">Nullmatrix</format> bestehen überall aus `0`.

```tex
\begin{align}
    N&=
    \begin{pmatrix}
        0&0&0\\
        0&0&0\\
        0&0&0
    \end{pmatrix}\\
\end{align}
```

Die Elemente auf der Hauptdiagonalen einer <format color="%Highlight%">Einheitsmatrix</format> (auch als <format color="%Highlight%">Identitätsmatrix</format> bezeichnet) bestehen nur aus `1` und sonst überall aus `0`.

```tex
\begin{align}
    E&=
    \begin{pmatrix}
        1&0&0\\
        0&1&0\\
        0&0&1
    \end{pmatrix}\\
\end{align}
```

## Transponierte Matrix {id="transposed-matrix"}

Die Transponierte einer Matrix $M$ ist $M^{T}$.

### Transponierte 4 $\times$ 5 Matrix {id="transposed-4x5-matrix"}

```tex
\begin{align}
    M&=
   \begin{pmatrix}
        \textcolor{cyan}{1}&\textcolor{purple}{2}&\textcolor{orange}{3}&\textcolor{#0070C0}{4}&\textcolor{lightgreen}{5}\\
        6&7&8&9&10\\
        11&12&13&14&15\\
        16&17&18&19&20\\
    \end{pmatrix}\\
    M^{T}&=
   \begin{pmatrix}
        \textcolor{cyan}{1}&6&11&16\\
        \textcolor{purple}{2}&7&12&17\\
        \textcolor{orange}{3}&8&13&18\\
        \textcolor{#0070C0}{4}&9&14&19\\
        \textcolor{lightgreen}{5}&10&15&20\\
    \end{pmatrix}
\end{align}
```

### Transponierte 5 $\times$ 1 Matrix {id="transposed-5x1-matrix"}

```tex
\begin{align}
    M&=
   \begin{pmatrix}
        1\\2\\3\\4\\5\\
    \end{pmatrix}\\
    M^{T}&=
   \begin{pmatrix}
        1&2&3&4&5\\
    \end{pmatrix}
\end{align}
```

### Transponierte 1 $\times$ 3 Matrix {id="transposed-1x3-matrix"}

```tex
\begin{align}
    M&=
   \begin{pmatrix}
        1&2&3\\
    \end{pmatrix}\\
    M^{T}&=
   \begin{pmatrix}
        1\\2\\3\\
    \end{pmatrix}
\end{align}
```

## Symmetrische Matrix {id="symmetric-matrix"}
## Inverse Matrix {id="inverse-matrix"}
## Determinante {id="determinant"}
## Dreiecksmatrizen {id="triangular-matrices"}