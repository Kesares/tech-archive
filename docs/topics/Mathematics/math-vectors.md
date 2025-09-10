# Mathematik – Vektoren

## Was ist ein Vektor? {id="what-is-a-vector"}

<p>Ein Vektor ist ein mathematisches Objekt, welcher eine Länge (auch
<format color="%LinkColor%">[Betrag](#magnitude)</format> genannt) und eine Richtung besitzt. Er beschreibt eine
Bewegung bzw. eine Verschiebung im Raum und wird nicht durch seinen Ort definiert. Haben zwei Vektoren dieselbe Länge,
dieselbe Orientierung und sind parallel zueinander, handelt es sich um denselben Vektor.</p>

Vektoren werden häufig verwendet, um Geschwindigkeiten, Kraft oder Verschiebungen im Raum zu beschreiben. Sie werden
oft durch einen Pfeil über einem Buchstaben <format color="%Highlight%">$\vec{v}$</format> dargestellt. Die einzelnen
Zahlen eines Vektors werden <format color="%Highlight%">Komponenten</format> genannt.

<p>Ein Vektor besteht aus den folgenden Eigenschaften.</p>

<list>
  <li>
    <p><format color="%LinkColor%"><a href="#magnitude">Betrag</a></format> (Länge)</p>
  </li>
  <li>
    <p><format color="%LinkColor%"><a href="#direction">Richtung</a></format></p>
  </li>
  <li>
    <p><format color="%LinkColor%"><a href="#dimension">Dimension</a></format></p>
  </li>
</list>

## Betrag {id="magnitude"}

Der Betrag <format color="%Highlight%">$|\vec{v}|$</format> eines Vektors gibt die Länge des Vektors an und ist immer
eine nicht-negative Zahl.

<code-block lang="tex">
    \begin{align}
        Betrag\geq0
    \end{align}
</code-block>

<p>Der Betrag eines Vektors wird aus der Wurzel des
<format color="%LinkColor%"><a href="#scalar-product">Skalarprodukts</a></format> berechnet.</p>

<code-block lang="tex">
    \begin{align}
        |\vec{v}|=\sqrt{Skalarprodukt}
    \end{align}
</code-block>

## Richtung {id="direction"}

<p>Die Richtung eines Vektors gibt an, wohin der Vektor „zeigt“, z. B. in welche Richtung eine Kraft wirkt oder sich
ein Objekt bewegt.</p>

## Dimension {id="dimension"}

Vektoren können in verschiedenen Dimensionen existieren. Ein Vektor in einer zweidimensionalen Ebene (2D) hat
<format color="%Highlight%">zwei Komponenten</format> (z. B. $x$ und $y$), während ein Vektor in einem
dreidimensionalen Raum (3D) <format color="%Highlight%">drei Komponenten</format> hat (z.B. $x$, $y$ und $z$).

### 2D Vektor {id="2d-vector"}

<code-block lang="tex">
    \begin{align}
        \vec{v}=\begin{pmatrix}3\\5\end{pmatrix}
    \end{align}
</code-block>

### 3D Vektor {id="3d-vector"}

<code-block lang="tex">
    \begin{align}
        \vec{v}=\begin{pmatrix}3\\5\\2\end{pmatrix}
    \end{align}
</code-block>

## Nullvektor {id="zero-vector"}

<code-block lang="tex">
    \begin{align}
        \vec{v}=\begin{pmatrix}0\\0\\0\end{pmatrix}
    \end{align}
</code-block>

## Addition und Subtraktion von Vektoren {id="addition-and-subtraction-of-vectors"}

<note>
    <p>Vektoren können nur addiert bzw. subtrahiert werden, wenn sie die
    <format color="%NoteHighlight%">gleiche Zeilenanzahl</format> besitzen.</p>
</note>

<p>Die <format color="%Highlight%">Komponenten</format> werden Zeile für Zeile addiert bzw. subtrahiert.</p>

<code-block lang="tex">
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
</code-block>

<code-block lang="tex">
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
</code-block>

### Beispiel {id="addition-and-subtraction-of-vectors-example"}

<code-block lang="tex">
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
</code-block>

<code-block lang="tex">
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
</code-block>

## Skalare Multiplikation {id="scalar-multiplication"}

<p>Ein Vektor kann mit einem <format color="%Highlight%">Skalar</format> (einem einzigen Wert) multipliziert werden,
wodurch sich die Länge des Vektors ändert, seine Richtung jedoch gleich bleibt. Ist der Skalar negativ, kehrt sich die
Richtung um.</p>

<code-block lang="tex">
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
</code-block>

### Beispiel {id="scalar-multiplication-example"}

<code-block lang="tex">
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
</code-block>

## Skalarprodukt {id="scalar-product"}

Das Skalarprodukt <format color="%Highlight%">$\vec{a}\cdot\vec{b}$</format> ist eine einzige Zahl und ergibt sich aus
der Multiplikation der Zeilen zweier Vektoren und dem anschließenden Addieren der Produkte.

<code-block lang="tex">
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
</code-block>

### Beispiel {id="scalar-product-example"}

<code-block lang="tex">
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
</code-block>

<note title="Orthogonalität zweier Vektoren">
    <p>Ergibt das Skalarprodukt zweier Vektoren <code>0</code>, so sind sie
    <tooltip term="Orthogonality"><format color="%GlossaryLinkColor%">orthogonal</format></tooltip> (senkrecht)
    zueinander.</p>
</note>

##  Kreuzprodukt {id="cross-product"}

Das Kreuzprodukt <format color="%Highlight%">$\vec{a}\times\vec{b}$</format> oder auch Vektorprodukt ergibt sich aus der
Multiplikation von zwei Vektoren und ist selbst wieder ein Vektor mit derselben Anzahl an Komponenten. Die Berechnung
des Kreuzprodukts ist jedoch etwas komplizierter als das <format color="%LinkColor%">[Skalarprodukt](#scalar-product)</format> und
wird durch die folgende Formel berechnet.

<code-block lang="tex">
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
</code-block>

### Beispiel {id="cross-product-example"}

<code-block lang="tex">
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
</code-block>

<note>
    <p>Der neue Vektor ist <tooltip term="Orthogonality"><format color="%GlossaryLinkColor%">orthogonal</format>
    </tooltip> zu den beiden ursprünglichen Vektoren.</p>
</note>
