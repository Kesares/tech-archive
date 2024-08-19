# Vektoren

## Was ist ein Vektor? {id="what-is-a-vector"}

Ein Vektor ist ein mathematisches Objekt, welcher eine Länge (auch <format color="%LinkColor%">[Betrag](#magnitude)</format> genannt) und eine Richtung besitzt. Er beschreibt eine Bewegung bzw. eine Verschiebung im Raum und wird nicht durch seinen Ort definiert. Haben zwei Vektoren dieselbe Länge, dieselbe Orientierung und sind parallel zueinander, handelt es sich um denselben Vektor.

Vektoren werden häufig verwendet um Geschwindigkeiten, Kraft oder Verschiebungen im Raum zu beschreiben und werden oft durch einen Pfeil über einem Buchstaben <format color="%Highlight%">$\vec{v}$</format> dargestellt. Die einzelnen Zahlen eines Vektors werden <format color="%Highlight%">Komponenten</format> genannt.

Ein Vektor besteht aus den folgenden Eigenschaften.

- <format color="%LinkColor%">[Betrag](#magnitude)</format> (Länge)
- <format color="%LinkColor%">[Richtung](#direction)</format>
- <format color="%LinkColor%">[Dimension](#dimension)</format>

## Betrag {id="magnitude"}

Der Betrag <format color="%Highlight%">$|\vec{v}|$</format> eines Vektors gibt die Länge des Vektors an und ist immer eine nicht-negative Zahl.

```tex
\begin{align}
Betrag\geq0
\end{align}
```

Der Betrag eines Vektors wird aus der Wurzel des <format color="%LinkColor%">[Skalarprodukts](#scalar-product)</format> berechnet.

```tex
\begin{align}
    |\vec{v}|=\sqrt{Skalarprodukt}
\end{align}
```

## Richtung {id="direction"}

Die Richtung eines Vektors gibt an, wohin der Vektor „zeigt“, z.B. in welche Richtung eine Kraft wirkt oder sich ein Objekt bewegt.

## Dimension {id="dimension"}

Vektoren können in verschiedenen Dimensionen existieren. Ein Vektor in einer zweidimensionalen Ebene (2D) hat <format color="%Highlight%">zwei Komponenten</format> (z.B. $x$ und $y$), während ein Vektor in einem dreidimensionalen Raum (3D) <format color="%Highlight%">drei Komponenten</format> hat (z.B. $x$, $y$ und $z$).

### 2D Vektor {id="2d-vector"}

```tex
\begin{align}
    \vec{v}=\begin{pmatrix}3\\5\end{pmatrix}
\end{align}
```

### 3D Vektor {id="3d-vector"}

```tex
\begin{align}
    \vec{v}=\begin{pmatrix}3\\5\\2\end{pmatrix}
\end{align}
```

## Addition und Subtraktion von Vektoren {id="addition-and-subtraction-of-vectors"}

> Vektoren können nur addiert bzw. subtrahiert werden, wenn sie die <format color="%NoteHighlight%">gleiche Zeilenanzahl</format> besitzen.
> {style="note"}

Die <format color="%Highlight%">Komponenten</format> werden Zeile für Zeile addiert bzw. subtrahiert.

```tex
\begin{align}
    \vec{v}=
    \vec{a}+\vec{b}=
    \begin{pmatrix}
        \textcolor{cyan}{a_{1}}\\
        \textcolor{orange}{a_{2}}\\
        \textcolor{lightgreen}{a_{3}}
    \end{pmatrix}
    +
    \begin{pmatrix}
        \textcolor{cyan}{b_{1}}\\
        \textcolor{orange}{b_{2}}\\
        \textcolor{lightgreen}{b_{3}}
    \end{pmatrix}=
    \begin{pmatrix}
        \textcolor{cyan}{a_{1}+b_{1}}\\
        \textcolor{orange}{a_{2}+b_{2}}\\
        \textcolor{lightgreen}{a_{3}+b_{3}}
    \end{pmatrix}
\end{align}
```

```tex
\begin{align}
    \vec{v}=
    \vec{a}-\vec{b}=
    \begin{pmatrix}
        \textcolor{cyan}{a_{1}}\\
        \textcolor{orange}{a_{2}}\\
        \textcolor{lightgreen}{a_{3}}
    \end{pmatrix}
    -
    \begin{pmatrix}
        \textcolor{cyan}{b_{1}}\\
        \textcolor{orange}{b_{2}}\\
        \textcolor{lightgreen}{b_{3}}
    \end{pmatrix}=
    \begin{pmatrix}
        \textcolor{cyan}{a_{1}-b_{1}}\\
        \textcolor{orange}{a_{2}-b_{2}}\\
        \textcolor{lightgreen}{a_{3}-b_{3}}
    \end{pmatrix}
\end{align}
```

### Beispiel {id="addition-and-subtraction-of-vectors-example"}

```tex
\begin{align}
    \vec{v}=
    \begin{pmatrix}
        \textcolor{cyan}{3}\\
        \textcolor{orange}{5}\\
        \textcolor{lightgreen}{2}
    \end{pmatrix}
    +
    \begin{pmatrix}
        \textcolor{cyan}{-2}\\
        \textcolor{orange}{4}\\
        \textcolor{lightgreen}{1}
    \end{pmatrix}
    =
    \begin{pmatrix}
        \textcolor{cyan}{3+(-2)}\\
        \textcolor{orange}{5+4}\\
        \textcolor{lightgreen}{2+1}
    \end{pmatrix}
    =
    \begin{pmatrix}
        \textcolor{cyan}{1}\\
        \textcolor{orange}{9}\\
        \textcolor{lightgreen}{3}
    \end{pmatrix}
\end{align}
```

```tex
\begin{align}
    \vec{v}=
    \begin{pmatrix}
        \textcolor{cyan}{3}\\
        \textcolor{orange}{5}\\
        \textcolor{lightgreen}{2}
    \end{pmatrix}
    -
    \begin{pmatrix}
        \textcolor{cyan}{-2}\\
        \textcolor{orange}{4}\\
        \textcolor{lightgreen}{1}
    \end{pmatrix}
        =
    \begin{pmatrix}
        \textcolor{cyan}{3-(-2)}\\
        \textcolor{orange}{5-4}\\
        \textcolor{lightgreen}{2-1}
    \end{pmatrix}
    =
    \begin{pmatrix}
        \textcolor{cyan}{5}\\
        \textcolor{orange}{1}\\
        \textcolor{lightgreen}{1}
    \end{pmatrix}
\end{align}
```

## Skalare Multiplikation {id="scalar-multiplication"}

Ein Vektor kann mit einem <format color="%Highlight%">Skalar</format> (einem einzigen Wert) multipliziert werden, wodurch sich die Länge des Vektors ändert, seine Richtung jedoch gleich bleibt. Ist der Skalar negativ, kehrt sich die Richtung um.

```tex
\begin{align}
    \vec{v}=
    s\cdot
    \begin{pmatrix}
        \textcolor{cyan}{v_{1}}\\
        \textcolor{orange}{v_{2}}\\
        \textcolor{lightgreen}{v_{3}}\\
    \end{pmatrix}
    =
    \begin{pmatrix}
        s\cdot\textcolor{cyan}{v_{1}}\\
        s\cdot\textcolor{orange}{v_{2}}\\
        s\cdot\textcolor{lightgreen}{v_{3}}\\
    \end{pmatrix}
\end{align}
```

### Beispiel {id="scalar-multiplication-example"}

```tex
\begin{align}
    \vec{v}&=
    2\cdot
    \begin{pmatrix}
        \textcolor{cyan}{-2}\\
        \textcolor{orange}{4}\\
        \textcolor{lightgreen}{1}
    \end{pmatrix}&&|\space umformen\\
    \vec{v}&=
    \begin{pmatrix}
        2\cdot\textcolor{cyan}{(-2)}\\
        2\cdot\textcolor{orange}{4}\\
        2\cdot\textcolor{lightgreen}{1}
    \end{pmatrix}&&|\space ausmultiplizieren\\
    \vec{v}&=
    \begin{pmatrix}
        \textcolor{cyan}{-4}\\
        \textcolor{orange}{8}\\
        \textcolor{lightgreen}{2}
    \end{pmatrix}
\end{align}
```

## Skalarprodukt {id="scalar-product"}

Das Skalarprodukt <format color="%Highlight%">$\vec{a}\cdot\vec{b}$</format> ist eine einzige Zahl und ergibt sich aus der Multiplikation der Zeilen zweier Vektoren und dem anschließenden Addieren der Produkte.

```tex
\begin{align}
    S&=\vec{a}\cdot\vec{b}
    =
    \begin{pmatrix}
        \textcolor{cyan}{a_{1}}\\
        \textcolor{orange}{a_{2}}\\
        \textcolor{lightgreen}{a_{3}}
    \end{pmatrix}
    \cdot
    \begin{pmatrix}
        \textcolor{cyan}{b_{1}}\\
        \textcolor{orange}{b_{2}}\\
        \textcolor{lightgreen}{b_{3}}
    \end{pmatrix}
    =\textcolor{cyan}{a_{1}}\cdot \textcolor{cyan}{b_{1}}+
    \textcolor{orange}{a_{2}}\cdot \textcolor{orange}{b_{2}}+
    \textcolor{lightgreen}{a_{3}}\cdot \textcolor{lightgreen}{b_{3}}
\end{align}
```

### Beispiel {id="scalar-product-example"}

```tex
\begin{align}
    S&=
    \begin{pmatrix}
        \textcolor{cyan}{3}\\
        \textcolor{orange}{5}\\
        \textcolor{lightgreen}{2}
    \end{pmatrix}
    \cdot
    \begin{pmatrix}
        \textcolor{cyan}{-2}\\
        \textcolor{orange}{4}\\
        \textcolor{lightgreen}{1}
    \end{pmatrix}&&|\space umformen\\
    S&=
    \begin{pmatrix}
        \textcolor{cyan}{3\cdot(-2)}\\
        \textcolor{orange}{5\cdot4}\\
        \textcolor{lightgreen}{2\cdot1}
    \end{pmatrix}&&|\space ausmultiplizieren\\
    S&=
    \begin{pmatrix}
        \textcolor{cyan}{-6}\\
        \textcolor{orange}{20}\\
        \textcolor{lightgreen}{2}
    \end{pmatrix}&&|\space umformen\\
    S&=
        \textcolor{cyan}{-6}+
        \textcolor{orange}{20}+
        \textcolor{lightgreen}{2} &&|\space Produkte\space addieren\\
    S&=16
\end{align}
```

> Ergibt das Skalarprodukt zweier Vektoren `0`, so sind sie <tooltip term="Orthogonality"><format color="%GlossaryLinkColor%">orthogonal</format></tooltip> (senkrecht) zueinander.
{style="note" title="Orthogonalität zweier Vektoren"}

##  Kreuzprodukt {id="cross-product"}

Das Kreuzprodukt <format color="%Highlight%">$\vec{a}\times\vec{b}$</format> oder auch Vektorprodukt ergibt sich aus der Multiplikation von zwei Vektoren und ist selbst wieder ein Vektor mit derselben Anzahl an Komponenten. Die Berechnung des Kreuzprodukts ist jedoch etwas komplizierter als das <format color="%LinkColor%">[Skalarprodukt](#scalar-product)</format> und wird durch die folgende Formel berechnet.

```tex
\begin{align}
    \vec{k}&=\vec{a}\times\vec{b}
    =
    \begin{pmatrix}
        \textcolor{cyan}{a_{1}}\\
        \textcolor{orange}{a_{2}}\\
        \textcolor{lightgreen}{a_{3}}
    \end{pmatrix}
    \times
    \begin{pmatrix}
        \textcolor{cyan}{b_{1}}\\
        \textcolor{orange}{b_{2}}\\
        \textcolor{lightgreen}{b_{3}}
    \end{pmatrix}
    =
    \begin{pmatrix}
        \textcolor{orange}{a_{2}}\cdot \textcolor{lightgreen}{b_{3}}-
        \textcolor{lightgreen}{a_{3}}\cdot\textcolor{orange}{b_{2}}\\
        \textcolor{lightgreen}{a_{3}}\cdot \textcolor{cyan}{b_{1}}-
        \textcolor{cyan}{a_{1}}\cdot\textcolor{lightgreen}{b_{3}}\\
        \textcolor{cyan}{a_{1}}\cdot \textcolor{orange}{b_{2}}-
        \textcolor{orange}{a_{2}}\cdot\textcolor{cyan}{b_{1}}
    \end{pmatrix}
\end{align}
```

### Beispiel {id="cross-product-example"}

```tex
\begin{align}
    \vec{k}&=
    \begin{pmatrix}
        \textcolor{cyan}{3}\\
        \textcolor{orange}{5}\\
        \textcolor{lightgreen}{2}
    \end{pmatrix}
    \times
    \begin{pmatrix}
        \textcolor{cyan}{-2}\\
        \textcolor{orange}{4}\\
        \textcolor{lightgreen}{1}
    \end{pmatrix}&&|\space umformen\\
    \vec{k}&=
    \begin{pmatrix}
        \textcolor{orange}{5}\cdot \textcolor{lightgreen}{1}-
        \textcolor{lightgreen}{2}\cdot\textcolor{orange}{4}\\
        \textcolor{lightgreen}{2}\cdot \textcolor{cyan}{(-2)}-
        \textcolor{cyan}{3}\cdot\textcolor{lightgreen}{1}\\
        \textcolor{cyan}{3}\cdot \textcolor{orange}{4}-
        \textcolor{orange}{5}\cdot\textcolor{cyan}{(-2)}
    \end{pmatrix}&&|\space ausmultiplizieren\\
    \vec{k}&=
    \begin{pmatrix}
        5-8\\
        -4-3\\
        12-(-10)
    \end{pmatrix}&&|\space umformen\\
    \vec{k}&=
    \begin{pmatrix}
        5-8\\
        -4-3\\
        12+10
    \end{pmatrix}&&|\space zusammenfassen\\
    \vec{k}&=
    \begin{pmatrix}
        -3\\-7\\22
    \end{pmatrix}
\end{align}
```

> Der neue Vektor ist <tooltip term="Orthogonality"><format color="%GlossaryLinkColor%">orthogonal</format></tooltip> zu den beiden ursprünglichen Vektoren.
{style="note"}