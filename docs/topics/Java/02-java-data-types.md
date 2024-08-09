# 02 Java Datentypen

Datentypen sind Schemen für die Verwendung von <tooltip term="Bit"><format color="%GlossaryLinkColor%">Bits</format></tooltip>. Mit ihnen lassen sich Werte, abhängig von der Größe der jeweiligen Datentypen, darstellen. Z.B. ist eine Ganzzahl ein anderer Datentyp als eine Fließkommazahl.

Grundsätzlich wird zwischen 2 Arten von Datentypen unterschieden.

- <format color="%c1%">[Primitive Datentypen](#primitive-data-types)</format>
- <format color="%c2%">[Referenzdatentyp](#reference-data-types)</format>

## <format color="%c1%">Primitive Datentypen</format> {id="primitive-data-types"}
Primitive Datentypen werden auch einfache oder elementare Datentypen genannt. In Java existieren nur 8 solcher Datentypen. Die folgende Tabelle zeigt eine Übersicht aller primitiven Datentypen.

| Datentyp  | Kategorie           | Wrapper-Klasse        | Größe in Bit                                                                                    | Wertebereich                                                                                             | Beschreibung                                             |
|-----------|---------------------|-----------------------|-------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------|----------------------------------------------------------|
| `byte`    | Ganzzahlig          | `java.lang.Byte`      | 8                                                                                               | -128 bis +127                                                                                            | Zweierkomplement-Werte                                   |
| `short`   | Ganzzahlig          | `java.lang.Short`     | 16                                                                                              | -32.768 bis +32.767                                                                                      | Zweierkomplement-Werte                                   |
| `int`     | Ganzzahlig          | `java.lang.Integer`   | 32                                                                                              | -2.147.483.648 bis +2.147.483.647                                                                        | Zweierkomplement-Werte                                   |
| `long`    | Ganzzahlig          | `java.lang.Long`      | 64                                                                                              | -9.223.372.036.854.775.808 bis +9.223.372.036.854.775.807                                                | Zweierkomplement-Werte                                   |
| `float`   | Gleitkommazahl      | `java.lang.Float`     | 32                                                                                              | -3,40282347 * 10<sup>38</sup> bis +3,40282347 * 10<sup>38</sup> (8 Nachkommastellen)                     | 32-Bit IEEE 754-Gleitkommazahl                           |
| `double`  | Gleitkommazahl      | `java.lang.Double`    | 64                                                                                              | -1,79769313486231570 * 10<up>308</sup> bis +1,79769313486231570 * 10<sup>308</sup> (17 Nachkommastellen) | 64-Bit IEEE 754-Gleitkommazahl mit doppelter Genauigkeit |
| `char`    | Character-Datentyp  | `java.lang.Character` | 16                                                                                              | 0 bis +65.535                                                                                            | Unicode-Zeichen (UTF-16)                                 |
| `boolean` | Boolescher Datentyp | `java.lang.Boolean`   | Abhängig von der <tooltip term="JVM"><format color="%GlossaryLinkColor%">JVM</format></tooltip> | `true` oder `false`                                                                                      | Boolescher Wahrheitswert                                 |

### Ganzzahlen {id="integers"}

<warning>
    Vorsicht bei der Verwendung von Ganzzahlen, welche außerhalb des Wertebereichs von <code>int</code> liegen.
    <code-block lang="java">
        System.out.println(8273469237); // Compiler-Fehler!
    </code-block>
</warning>

Der <tooltip term="Compiler"><format color="%GlossaryLinkColor%">Compiler</format></tooltip> interpretiert solche <format color="%LinkColor%">[Literale](01-java-token.md#literals)</format> standardmäßig als Integer-Ganzzahlen. Damit der Compiler erkennt, dass es sich um einen Datenwert vom Typ `long` handelt, muss dies mit einem `L` am Ende gekennzeichnet werden.

<compare>
    <code-block lang="java">
        System.out.println(8273469237);
    </code-block>
    <code-block lang="java">
        System.out.println(8273469237L);
    </code-block>
</compare>

> `System.out.println()` wird für die Ausgabe auf der Konsole verwendet – siehe <format color="%NoteLinkColor%">[Kapitel 4 – Ein- und Ausgaben](04-java-io.md)</format>.
{style="note"}

Neben der standardmäßigen Dezimalschreibweise, kann auch die binäre, oktale oder hexadezimale Schreibweise angewendet werden.

| Zahlensystem | Präfix |
|--------------|--------|
| Binär        | `0b`   |
| Oktal        | `0`    |
| Hexadezimal  | `0x`   |

Folgendes Beispiel zur Veranschaulichung. Die Syntax wird im nachfolgenden <format color="%LinkColor%">[Kapitel 3 – Variablen](03-java-variables.md)</format> genauer erklärt.

```java
int decimal = 42;  
int binary = 0b1101;  
int octal = 023;  
int hexadecimal = 0x2B;
```

### Gleitkommazahlen {id="floating-point-numbers"}

Um Gleitkommazahlen darstellen zu können, wurden die Datentypen `float` und `double` eingeführt. Soll der Restwert berechnet werden, wird dafür der Operator `%` verwendet. Das folgende Beispiel zeigt 4 Varianten für die Kennzeichnung einer Kommazahl.

<code-block lang="java">
    System.out.println(1 / 10.0);
    System.out.println(1 / 10.);
    System.out.println(1 / 10f);
    System.out.println(1 / 10d);
</code-block>

<tabs group="floating-point-1">
    <tab id="floating-point-division-task-1" title="Aufgabe" group-key="task">
        <p>Was wird bei folgendem Beispiel auf der Konsole ausgegeben?</p><br/>
        <code-block lang="java">
            System.out.println(1 / 10);
        </code-block>
    </tab>
    <tab id="floating-point-division-solution-1" title="Lösung" group-key="solution">
        <p>Regulär würde man im Kopf auf das Ergebnis <code>0.1</code> kommen. Da in Java jedoch standardmäßig mit Ganzzahlen gearbeitet wird, wird alles, was nach dem Komma steht abgeschnitten. Das Ergebnis ist also <code>0</code>.</p>
    <note>
        Wenn das Ergebnis als Kommazahl vorliegen soll, muss bei mindestens einer der beiden Operanden angegeben werden, dass es sich bei dessen Datentyp um eine Kommazahl handelt.
    </note>
    </tab>
</tabs>

<tabs group="floating-point-2">
    <tab id="floating-point-division-task-2" title="Aufgabe" group-key="task">
        <p>Was ergibt <code>0.1 + 0.2</code>?</p><br/>
    </tab>
    <tab id="floating-point-division-solution-2" title="Lösung" group-key="solution">
        <code-block lang="java">
            ~0.30000000000000004
        </code-block>
        <warning>
            Da der Computer nur <code>0</code> und <code>1</code> versteht, kann es beim Rechnen mit Fließkommazahlen zu geringfügigen Ungenauigkeiten kommen. Dies ist jedoch kein Problem von Java, sondern betrifft Programmiersprachen und CPUs allgemein. Dies liegt an einer ungünstigen Binärdarstellung, da Dezimalzahlen nicht exakt als endliche binäre Zahl dargestellt werden können.
        </warning>
    </tab>
</tabs>

<note title="Die Fließkommazahlenproblematik">
    <p>Ein sehr zu empfehlendes Video über die Fließkommazahlenproblematik ist hier zu finden:</p>
    <video src="https://www.youtube.com/watch?v=PZRI1IfStY0"/>
</note>

Gleitkommazahlen können auch die wissenschaftliche Notation repräsentieren. Diese kann direkt angewendet werden.

```Java
double d = 1e-10;
```

### Datentyp `char` {id="data-type-character"}

Der Datentyp `char` ist für die Darstellung eines einzelnen Zeichens verantwortlich. `char` steht als Abkürzung für `character`. Intern werden die Zeichen als Unicode (16-Bit-Dualzahl) dargestellt. Mit anderen Worten: Jedes Zeichen repräsentiert intern eine Ganzzahl. Daher kann ein `char` auch als `int` gespeichert werden.

```Java
int at1 = '@';
char at2 = '@';
System.out.println(at1);  // 64
System.out.println(at2);  // @
```

#### Escape Sequenzen {id="escape-sequences"}

Der <tooltip term="Compiler"><format color="%GlossaryLinkColor%">Compiler</format></tooltip> interpretiert einige Zeichen als Escape-Sequenzen. Eine Escape-Sequenz ist eine spezielle Zeichenfolge, die durch ein Escape-Zeichen eingeleitet wird und dazu dient, spezielle oder nicht druckbare Zeichen darzustellen.

Folgende Tabelle zeigt einige Escape-Sequenzen.

| Escape Sequenz | Beschreibung                    |
|----------------|---------------------------------|
| `\t`           | Horizontaler Tabulator          |
| `\r`           | Carriage Return (Wagenrücklauf) |
| `\n`           | Zeilenumbruch                   |
| `\uXXXX`       | Unicode XXXX (hexadezimal)      |
| `\b`           | Backspace (Rückschritt)         |
| `\f`           | Form Feed (Seitenumbruch)       |
| `\'`           | Hochkommata                     |
| `\"`           | Anführungszeichen               |
| `\\`           | Backslash                       |

### Datentyp `boolean` {id="data-type-boolean"}

Vergleiche werden mit dem Typ `boolean` realisiert. Beispielsweise um zu prüfen, ob eine Zahl größer ist, als eine andere. Die einzigen <format color="%LinkColor%">[Literale](01-java-token.md#literals)</format> die ein `boolean` annehmen kann, sind `true` (wahr) oder `false` (falsch).

<code-block lang="java">
    boolean isRunning = false;
    boolean isJumping = true;
</code-block>

## <format color="%c2%">Referenzdatentypen</format> {id="reference-data-types"}

Referenzdatentypen werden im Verlauf der späteren Kapitel genauer beschrieben. Referenztypen werden häufig auch als Instanzen oder Objekte, seltener auch als komplexe Datentypen bezeichnet. Objekte repräsentieren konkrete Exemplare von Bauplänen (<format color="%LinkColor%">[Klassen](10-java-classes.md)</format>). Zur Vereinfachung wird in den folgenden Kapiteln der Begriff „Objekt“ bzw. „Objekte“ verwendet.

Ein Objekt kann im Grunde alles sein, was einem in den Sinn kommt. Beispielsweise ein Ball, ein Mensch, eine Aktivität oder sogar eine Dimension. Solche Objekte werden durch Eigenschaften (Objektvariablen) und Funktionalitäten (Objektmethoden) beschrieben.

- Objektmethoden stellen dabei die Funktionen eines Objekts dar. Ein Mensch kann z.B. gehen (vgl. <format color="%LinkColor%">[Kapitel 9 – Methoden](09-java-methods.md)</format> & <format color="%LinkColor%">[Kapitel 10 – Klassen: Objektmethoden](10-java-classes.md#object-methods)</format>).
- Objektvariablen speichern zu jedem Objekt spezifische Eigenschaften. Ein Mensch hat z.B. ein Alter und einen Namen (vgl. <format color="%LinkColor%">[Kapitel 3 – Variablen](03-java-variables.md)</format> & <format color="%LinkColor%">[Kapitel 10 – Klassen: Objektvariablen](10-java-classes.md#object-variables)</format>).
- Auf Objekte wird in <format color="%LinkColor%">[Kapitel 11 – Objekte](11-java-objects.md)</format> & <format color="%LinkColor%">[Kapitel 14 – OOP](14-java-oop.md)</format> genauer eingegangen.
- Auf zwei bestimmte Objekte wird bereits früher in <format color="%LinkColor%">[Kapitel 5 – Zeichenketten](05-java-strings.md)</format> und <format color="%LinkColor%">[Kapitel 8 – Arrays](08-java-arrays.md)</format> eingegangen.