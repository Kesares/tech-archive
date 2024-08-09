# Matrizen

## Addition und Subtraktion von Matrizen

Matrizen können nur addiert bzw. subtrahiert werden, wenn sie in <format color="LightSkyBlue">Zeilen und Spalten übereinstimmen</format>. Legt man zwei Matrizen übereinander, werden die übereinanderliegenden Zahlen addiert bzw. subtrahiert.

```tex
\begin{align}
    \begin{pmatrix}
        \textcolor{red}{2}&\textcolor{orange}{3}&\textcolor{lightgreen}{2}\\
        1&4&1\\
        4&2&2
    \end{pmatrix}
    +
    \begin{pmatrix}
        \textcolor{red}{3}&\textcolor{orange}{0}&\textcolor{lightgreen}{3}\\
        2&4&1\\
        1&2&1
    \end{pmatrix}
    =
    \begin{pmatrix}
        \textcolor{red}{5}&\textcolor{orange}{3}&\textcolor{lightgreen}{5}\\
        3&8&2\\
        5&4&3
    \end{pmatrix}
\end{align}
```

```tex
\begin{align}
    \begin{pmatrix}
        \textcolor{red}{2}&\textcolor{orange}{3}&\textcolor{lightgreen}{2}\\
        1&4&1\\
        4&2&2
    \end{pmatrix}
    -
    \begin{pmatrix}
        \textcolor{red}{3}&\textcolor{orange}{0}&\textcolor{lightgreen}{3}\\
        2&4&1\\
        1&2&1
    \end{pmatrix}
    =
    \begin{pmatrix}
        \textcolor{red}{-1}&\textcolor{orange}{3}&\textcolor{lightgreen}{-1}\\
        -1&0&0\\
        3&0&1
    \end{pmatrix}
\end{align}
```

>Das Ergebnis einer Addition ist eine <format color="LightSkyBlue">Summenmatrix</format>.
> 
>Das Ergebnis einer Subtraktion ist eine <format color="LightSkyBlue">Differenzmatrix</format>.
{style="note"}

## Multiplikation von Matrizen

Matrizen können nur multipliziert werden, wenn die <format color="LightSkyBlue">Spaltenanzahl der ersten Matrix</format> mit der <format color="LightSkyBlue">Zeilenanzahl der zweiten Matrix</format> übereinstimmt. Eine Matrix der Dimension <format color="LightSkyBlue">(3 $\times$ 2)</format> kann <format color="LightSkyBlue">nicht</format> mit einer Matrix der Dimension <format color="LightSkyBlue">(3 $\times$ 3)</format> multipliziert werden.

Die Dimension der Ergebnismatrix ergibt sich aus der <format color="LightSkyBlue">Zeilenanzahl der ersten Matrix</format> und der <format color="LightSkyBlue">Spaltenanzahl der zweiten Matrix</format>. Eine Matrix der Dimension <format color="LightSkyBlue">(2 $\times$ 3)</format> multipliziert mit einer Matrix der Dimension <format color="LightSkyBlue">(3 $\times$ 5)</format> ergibt eine neue Matrix der Dimension <format color="LightSkyBlue">(2 $\times$ 5)</format>.

```tex
\begin{align}
	M&=
    \begin{pmatrix}
        \textcolor{red}{1}&\textcolor{orange}{2}&\textcolor{lightgreen}{3}\\
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
        \textcolor{red}{1}*\textcolor{purple}{1}+\textcolor{orange}{2}*\textcolor{#0070C0}{2}+\textcolor{lightgreen}{3}*\textcolor{#E5572B}{3}&1*4+2*5+3*6\\
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

## Multiplikation mit Vektoren

Matrizen können nur mit einem Vektor multipliziert werden, wenn die <format color="LightSkyBlue">Spaltenanzahl der Matrix</format> mit der <format color="LightSkyBlue">Zeilenanzahl des Vektors übereinstimmt. Die Spaltenanzahl eines Vektors</format> ist immer `1` und das Ergebnis einer Multiplikation ist immer ein neuer Vektor.

```tex
\begin{align}
	M&=
    \begin{pmatrix}
        \textcolor{red}{2}&\textcolor{orange}{2}&\textcolor{lightgreen}{0}\\
        2&-1&-3\\
        1&0&1
    \end{pmatrix}
    \cdot
    \begin{pmatrix}
        \textcolor{purple}{3}\\
        \textcolor{#0070C0}{1}\\
        \textcolor{#E5572B}{2}
    \end{pmatrix}\\
    M&=
    \begin{pmatrix}
        \textcolor{red}{2}*\textcolor{purple}{3}+\textcolor{orange}{2}*\textcolor{#0070C0}{1}+\textcolor{lightgreen}{0}*\textcolor{#E5572B}{2}\\
        2*3-1*1-3*2\\
        1*3+0*1+1*2
    \end{pmatrix}\\
    M&=
    \begin{pmatrix}
        6+2+0\\
        6-1-6\\
        3+0+2
    \end{pmatrix}\\
    M&=
    \begin{pmatrix}
        8\\
        -1\\
        5
    \end{pmatrix}
\end{align}
```

## Einheitsmatrix

Die Elemente auf der Hauptdiagonalen einer <format color="LightSkyBlue">Einheitsmatrix</format> (auch als <format color="LightSkyBlue">Identitätsmatrix</format> bezeichnet) bestehen nur aus `1` und sonst überall aus `0`.

```tex
\begin{align}
   \begin{pmatrix}
        1&0&0\\
        0&1&0\\
        0&0&1
    \end{pmatrix}\\
\end{align}
```