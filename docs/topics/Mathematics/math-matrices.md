# Mathematik – Matrizen

## Was ist eine Matrix? {id="what-is-a-matrix"}

<p>Eine Matrix ist eine rechteckige Anordnung von Zahlen, die in Zeilen und Spalten organisiert sind. Diese Anordnung
ermöglicht es, komplexe Berechnungen und Transformationen in kompakten Formen darzustellen. Matrizen werden häufig
verwendet, um lineare Gleichungssysteme zu lösen oder geometrische Transformationen durchzuführen.</p>

<p>Eine Matrix besteht aus den folgenden Eigenschaften.</p>

<list>
  <li>
    <p><format color="%LinkColor%"><a href="#order">Ordnung</a></format></p>
  </li>
  <li>
    <p>Rang</p>
  </li>
</list>

## Ordnung {id="order"}

Die Größe oder Ordnung einer Matrix wird durch die Anzahl der Zeilen <format color="%Highlight%">$m$</format> und
Spalten <format color="%Highlight%">$n$</format> beschrieben. Eine Matrix mit <format color="%Highlight%">$m$</format>
 Zeilen und <format color="%Highlight%">$n$</format> Spalten wird als <format color="%Highlight%">$m \times n$</format>
 Matrix bezeichnet.

## Addition und Subtraktion von Matrizen {id="addition-and-subtraction-of-matrices"}

<note>
    <p>Matrizen können nur addiert bzw. subtrahiert werden, wenn sie in <format color="%NoteHighlight%">Zeilen und
    Spalten</format> übereinstimmen.</p>
</note>

<p>Legt man zwei Matrizen übereinander, werden die übereinanderliegenden Zahlen addiert bzw. subtrahiert.</p>

<code-block lang="tex">
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
</code-block>

<code-block lang="tex">
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
</code-block>

<tip>
    <p>Das Ergebnis einer Addition ist eine <format color="%Highlight%">Summenmatrix</format>.</p>
    <p>Das Ergebnis einer Subtraktion ist eine <format color="%Highlight%">Differenzmatrix</format>.</p>
</tip>

## Multiplikation von Matrizen {id="multiplication-with-matrices"}

<note>
    <p>Zwei Matrizen können nur miteinander multipliziert werden, wenn die
    <format color="%NoteHighlight%">Spaltenanzahl der ersten Matrix</format> mit der
    <format color="%NoteHighlight%">Zeilenanzahl der zweiten Matrix</format> übereinstimmt.</p>
</note>

Eine Matrix der Dimension (3 $\times$ 2) kann <format color="%Highlight%">nicht</format> mit einer Matrix der
Dimension (3 $\times$ 3) multipliziert werden.

Die Dimension der Ergebnismatrix ergibt sich aus der <format color="%Highlight%">Zeilenanzahl der ersten Matrix</format>
und der <format color="%Highlight%">Spaltenanzahl der zweiten Matrix</format>. Eine Matrix der Dimension
(2 $\times$ 3) multipliziert mit einer Matrix der Dimension (3 $\times$ 5) ergibt eine neue Matrix der
Dimension (2 $\times$ 5).

<code-block lang="tex">
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
            \textcolor{cyan}{1}*\textcolor{purple}{1}+\textcolor{orange}{2}*\textcolor{#0070C0}{2}+
            \textcolor{lightgreen}{3}*\textcolor{#E5572B}{3}&1*4+2*5+3*6\\
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
</code-block>

Wird eine Matrix $A$ mit einer Matrix $B$ multipliziert, heißt dies nicht, dass die Matrix $B$ auch mit $A$
multipliziert werden kann.

<p>Zwei quadratische Matrizen derselben Ordnung können jedoch immer multipliziert werden.</p>

## Multiplikation mit Vektoren {id="multiplication-with-vectors"}

<note>
    <p>Matrizen können nur mit einem Vektor multipliziert werden, wenn die
    <format color="%NoteHighlight%">Spaltenanzahlen der Matrix</format> mit der
    <format color="%NoteHighlight%">Zeilenanzahl des Vektors</format> übereinstimmen.</p>
</note>

<p>Die Spaltenanzahl eines Vektors ist immer <code>1</code> und das Ergebnis einer Multiplikation ist immer ein neuer
<format color="%LinkColor%"><a href="math-vectors.md">Vektor</a></format>.</p>

<code-block lang="tex">
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
</code-block>

## Nullmatrix und Einheitsmatrix {id="zero-matrix-and-identity-matrix"}

<p>Die Elemente einer <format color="%Highlight%">Nullmatrix</format> bestehen überall aus <code>0</code>.</p>

<code-block lang="tex">
    \begin{align}
        N&=
        \begin{pmatrix}
            0&0&0\\
            0&0&0\\
            0&0&0
        \end{pmatrix}\\
    \end{align}
</code-block>

<p>Die Elemente auf der Hauptdiagonalen einer <format color="%Highlight%">Einheitsmatrix</format> (auch als
<format color="%Highlight%">Identitätsmatrix</format> bezeichnet) bestehen nur aus <code>1</code> und sonst überall aus
<code>0</code>.</p>

<code-block lang="tex">
    \begin{align}
        E&=
        \begin{pmatrix}
            1&0&0\\
            0&1&0\\
            0&0&1
        \end{pmatrix}\\
    \end{align}
</code-block>

## Transponierte Matrix {id="transposed-matrix"}

Die Transponierte einer Matrix $M$ ist $M^{T}$.

### Transponierte 4 $\times$ 5 Matrix {id="transposed-4x5-matrix"}

<code-block lang="tex">
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
</code-block>

### Transponierte 5 $\times$ 1 Matrix {id="transposed-5x1-matrix"}

<code-block lang="tex">
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
</code-block>

### Transponierte 1 $\times$ 3 Matrix {id="transposed-1x3-matrix"}

<code-block lang="tex">
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
</code-block>

## Symmetrische Matrix {id="symmetric-matrix"}
## Inverse Matrix {id="inverse-matrix"}
## Determinante {id="determinant"}
## Dreiecksmatrizen {id="triangular-matrices"}