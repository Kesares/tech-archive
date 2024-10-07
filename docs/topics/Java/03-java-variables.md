# 03 Java – Variablen

Variablen sind benannte Speicherstellen und dienen dazu, Daten im Hauptspeicher zu allokieren. Durch die Benennung kann auf die Variablen zugegriffen werden und Datenwerte hineingeschrieben und später wieder ausgelesen oder verändert werden. Es wird zwischen 5 Variablenarten unterschieden.

- <format color="%c1%">Lokale Variablen</format> existieren nur innerhalb von <format color="%LinkColor%">[Methoden](09-java-methods.md)</format> oder Anweisungsblöcken.
- <format color="%c2%">Parametervariablen</format> existieren ebenfalls nur innerhalb von Methoden. Auch sie sind automatisch immer <format color="%c1%">lokale Variablen</format>, die in der Parameterliste deklariert werden und Werte beinhalten, die über einen <format color="%LinkColor%">[Methodenaufruf](09-java-methods.md#)</format> an die Methoden übergeben wurden.
- <format color="%c3%">Objektvariablen</format> (auch Instanzvariablen genannt) werden im Rahmen einer <format color="%LinkColor%">[Klasse](10-java-classes.md)</format> definiert und zusammen mit <format color="%LinkColor%">[Objekten](11-java-objects.md)</format> angelegt.
- <format color="%c4%">Klassenvariablen</format> (auch statische Variablen genannt) werden ebenfalls innerhalb einer <format color="%LinkColor%">[Klasse](10-java-classes.md)</format> definiert, existieren jedoch unabhängig von <format color="%LinkColor%">[Objekten](11-java-objects.md)</format>.
- <format color="%c5%">Konstanten</format> sind immer <format color="%c4%">Klassenvariablen</format>. Der Wert kann jedoch nicht überschrieben werden.

> In den folgenden Kapiteln wird sich zunächst nur auf die Verwendung von <format color="%c1%">lokalen Variablen</format> beschränkt.
> 
> Mit <format color="%c2%">Parametervariablen</format> wird sich in <format color="%LinkColor%">[Kapitel 9 – Methoden](09-java-methods.md)</format> beschäftigt.
> 
> <format color="%c3%">Objektvariablen</format>, <format color="%c4%">Klassenvariablen</format> und <format color="%c5%">Konstanten</format> werden in <format color="%LinkColor%">[Kapitel 10 – Klassen](10-java-classes.md)</format> vorgestellt.

## Variablendeklaration {id="variable-declaration"}
Eine Variable besteht, abhängig vom <format color="%LinkColor%">[primitiven](02-java-data-types.md#primitive-data-types)</format> oder <format color="%LinkColor%">[Referenzdatentyp](02-java-data-types.md#reference-data-types)</format>, aus verschiedenen Bestandteilen.

<tabs group="variable-declaration">
  <tab id="variable-declaration-primitive" title="Primitiven Datentypen" group-key="primitive">
    <p>1. Datentyp</p>
    <p>2. Bezeichner der Variablen</p>
    <p>3. Zuweisungsoperator <code>=</code></p>
    <p>4. Literal</p>
    <p>5. Semikolon <code>;</code></p><br/>
    <code-block>
      type identifier = literal;
    </code-block><br />
    <code-block lang="java">
      int meaningOfLife = 42;
      boolean isRunning = false;
      char at = '@';
    </code-block>
    <table>
      <tr>
        <td>Bestandteil</td>
        <td>Beispiel</td>
      </tr>
      <tr>
        <td>type</td>
        <td><code>int</code>, <code>char</code>, <code>boolean</code></td>
      </tr>
      <tr>
        <td>identifier</td>
        <td><code>meaningOfLife</code>, <code>isRunning</code>, <code>at</code></td>
      </tr>
      <tr>
        <td>literal</td>
        <td><code>42</code>, <code>false</code>, <code>@</code></td>
      </tr>
    </table>
  </tab>
  <tab id="variable-declaration-reference" title="Referenzdatentypen (Objekte)" group-key="reference">
    <p>1. Datentyp</p>
    <p>2. Bezeichner der Variablen</p>
    <p>3. Zuweisungsoperator <code>=</code></p>
    <p>4. Schlüsselwort <code>new</code></p>
    <p>5. Datentyp</p>
    <p>6. Runde Klammern <code>()</code></p>
    <p>7. Semikolon <code>;</code></p><br/>
    <code-block>
      Type identifier = new Type();
    </code-block><br/>
    <code-block lang="java">
      String name = "Kesares";
      Movie movie = new Movie();
      Dog dog = new Dog();
    </code-block>
    <table>
      <tr>
        <td>Bestandteil</td>
        <td>Beispiel</td>
      </tr>
      <tr>
        <td>type</td>
        <td><code>String</code>, <code>Movie</code>, <code>Dog</code></td>
      </tr>
      <tr>
        <td>identifier</td>
        <td><code>name</code>, <code>movie</code>, <code>dog</code></td>
      </tr>
      <tr>
        <td>object</td>
        <td><code>"Kesares"</code>, <code>Movie()</code>, <code>Dog()</code></td>
      </tr>
    </table>
  </tab>
</tabs>

> <format color="%NoteLinkColor%">[Primitive Datentypen](02-java-data-types.md#primitive-data-types)</format> werden immer klein und <format color="%NoteLinkColor%">[Referenzdatentypen](02-java-data-types.md#reference-data-types)</format> immer großgeschrieben.
{style="note"}

## Deklaration vs. Initialisierung {id="declaration-vs-initialisation"}
Durch eine Deklaration wird eine Variable erstellt und Speicherplatz für sie reserviert. Dabei wird der Variablen noch kein Wert zugewiesen. Dies erfolgt erst durch eine Initialisierung.

Die Deklaration und Initialisierung einer Variablen kann entweder in einer oder in zwei separaten Zeilen erfolgen.

```java
int x;       // declaration
x = 15;      // initialization

int y = 10;  // declaration & initialization
y = 42;      // assignment, value is overwritten
```

Auch mehrere Variablen in einer Zeile sind möglich.

```java
int v1, v2, v3;                // declaration
int v4 = 10, v5 = 11, v6 = 12; // declaration & initialization
```

>Ein guter Programmierstil sieht vor, dass jede Variable in einer eigenen Zeile deklariert wird, um die Übersichtlichkeit des Codes zu gewährleisten.
{style="note"}

## Typumwandlung {id="type-casting"}
Als Typumwandlung (engl. type casting) wird die Umwandlung eines <format color="%LinkColor%">[Datentyps](02-java-data-types.md)</format> in einen anderen bezeichnet. In Java wird zwischen 2 Arten unterschieden.

- <format color="%c1%">Implizite Typumwandlung</format>
- <format color="%c2%">Explizite Typumwandlung</format>

### <format color="%c1%">Implizite Typumwandlung</format> {id="implicit-type-casting"}
Die implizite Typumwandlung erfolgt automatisch bei der Zuweisung von Werten. Dabei wird ein Datentyp mit niedrigerer Präzision in einen Datentyp mit höherer Präzision umgewandelt, zum Beispiel vom Typ `int` zum Typ `long`.

```java
int i = 42;
long l = i;
```

### <format color="%c2%">Explizite Typumwandlung</format> {id="explicit-type-casting"}
Die explizite Typumwandlung erfolgt mithilfe des `cast`-Operators, der eine gezielte Konvertierung im Quellcode ermöglicht. Dabei wird ein Datentyp mit höherer Präzision in einen Datentyp mit niedrigerer Präzision umgewandelt, zum Beispiel von `short` in `byte` oder von `float` in `int`. Der `cast`-Operator erfordert die explizite Angabe des Zieltyps, in den umgewandelt werden soll.

```java
short s = 128;
byte b = (byte) s;

float f = 3.14;
int i = (int) f;
```

Wenn in einer Zeile, in der ein Cast durchgeführt wird, auch eine Berechnung stattfinden soll, muss die Berechnung in runden Klammern gesetzt werden. Dadurch wird sichergestellt, dass die Berechnung vor der Typumwandlung ausgeführt wird.

```java
double a = 10.5;
short b = 20;

short ab = (short) (a + b);
```

>Da zum Beispiel ein `byte` weniger Speicherplatz bietet als ein `short` und ein `short` im Vergleich zu `double` nur ganze Zahlen verarbeitet, kann es zu fehlerhaften Berechnungen kommen - mit anderen Worten: <format color="%WarningLinkColor%">Datenverlust</format>!
> {style="warning" title="Achtung: Datenverlust!"}

> Auch die Konvertierung zwischen Referenztypen ist möglich. Dazu mehr in <format color="%LinkColor%">[Kapitel 14 – OOP](14-java-oop.md)</format>.

## Reservierter Typname – `var` {id="reserved-type-name-var"}

Seit Java 10 ist es möglich die explizite Typangabe durch ein `var` zu ersetzen. `var` dient im Rahmen der <format color="%NoteHighlight%">Type Inference</format> als Platzhalter für einen Datentyp.

<compare>
    <code-block lang="java">
        int meaningOfLife = 42;
        boolean isRunning = false;
        char at = '@';
    </code-block>
    <code-block lang="java">
        var meaningOfLife = 42;
        var isRunning = false;
        var at = '@';
    </code-block>
</compare>

> Wird eine Variable mit `var` deklariert aber in derselben Zeile <format color="%WarningHighlight%">nicht</format> initialisiert, führt dies zu einem <format color="%WarningHighlight%">Compilerfehler</format>!
{style="warning"}

Sowohl die Deklaration als auch die Initialisierung müssen in derselben Zeile stehen. Der <tooltip term="Compiler"><format color="%GlossaryLinkColor%">Compiler</format></tooltip> ermittelt den Typ der Variablen selbst. Zudem kann `var` nur für <format color="%c1%">lokale Variablen</format> eingesetzt werden.

> `var` wird häufig als Keyword verwechselt, ist aber ein <format color="%Highlight%">Reserved Type Name</format> und kann daher auch als <format color="%LinkColor%">[Bezeichner](01-java-token.md#identifier)</format> verwendet werden.

## Lebensdauer und Sichtbarkeit {id="lifespan-and-visibility"}

Die Lebensdauer beschreibt die Zeitspanne von der „Geburt“ bis zum „Tod“ einer Variablen. Die Lebensdauer einer <format color="Coral">lokalen Variablen</format> beginnt mit der Variablendeklaration. Wurde die Variable innerhalb einer Block-Anweisung deklariert, endet ihre Lebenszeit mit Verlassen des Blocks. Wurde die Variable in einer <format color="%LinkColor%">[Methode](09-java-methods.md)</format> deklariert, dann wird ihre Existenz mit Ende des <format color="%LinkColor%">[Methodenaufrufs](09-java-methods.md)</format> ausgelöscht. Solange eine Variable existiert ist sie auch für andere Programmteile sichtbar.

Folgendes Beispiel zur Veranschaulichung. Zu beachten sind die geschweiften Klammern `{}`:

```Java
{ // Start of 1st block
	int i = 10;
	i++;
	{ // Start of 2nd block
		int j = 10;
		i++;
		j++;
		{ // Start of 3rd block
			int k = 10;
			i++;
			j++;
			k++;
		} // End of 3rd block
		i++;
		j++;
		k++; // Out of scope
	} // End of 2nd block
	i++;
	j++; // Out of scope
	k++; // Out of scope
} // End of 1st block
```

Die Variable `i` ist in allen Anweisungsblöcken sichtbar.
Die Variable `j` ist nur im 2. und 3. Block sichtbar.
Die Variable `k` ist nur im 3. Block sichtbar.

Bei den letzten beiden Zuweisungen, kann nicht auf die Variable `j` und `k` zugegriffen werden, da sie nur innerhalb des 2. bzw. 3. Blocks existieren. Dasselbe gilt für den Variablenzugriff `k` im 2. Anweisungsblock.

![03_java_variables_1.jpg](03_java_variables_1.jpg){width="400"}

## Typisierung {id="typing"}
### Starke vs. schwache Typisierung {id="strong-vs-weak-typing"}

> Java ist eine stark typisierte Sprache.
{style="note"}

<format color="%Highlight%">Stark typisiert</format> bedeutet, dass eine Sprache <format color="%Highlight%">sehr strikt bei der Durchsetzung von Datentypen</format> vorgeht. Wird eine Variable angelegt, sorgt Java auch dafür, dass der Programmierer genau angeben muss, welchen Datentyp diese Variable haben soll. Zudem behält Java bzw. der <tooltip term="Compiler"><format color="%GlossaryLinkColor%">Compiler</format></tooltip> ein Auge darauf, dass sich der Typ dieser Variablen nicht verändert. Einmal eine Variable erstellt, behält sie den Typ bis zum Ende der Lebensdauer.

Eine Ausnahme bildet hier die in Java 10 hinzugefügte Möglichkeit Variablen mit `var` anzugeben. Doch auch hier bleibt während der gesamten Lebensdauer der Typ gleich.

<format color="%Highlight%">Schwach typisiert</format> bedeutet, dass eine Sprache "nachsichtiger" ist, wenn es um Typisierung geht. Hier wird eine automatische Typenumwandlung durchgeführt, um möglichst einfach Resultate generieren zu können.

> Stark typisierte Sprachen sind z.B. Java, C++, Python, Smalltalk, Haskell und Pascal.
> 
> Schwach typisierte Sprachen sind z.B. C, JavaScript, PHP und Perl.

### Statische vs. dynamische Typisierung {id="static-vs-dynamic-typing"}

> Java ist eine statisch typisierte Sprache.
{style="note"}

<format color="%Highlight%">Statisch typisiert</format> bedeutet, dass eine Sprache <format color="%Highlight%">zur Kompilierungszeit</format> sicherstellt, dass alle Typregeln stets befolgt werden.

Bei der <format color="%Highlight%">dynamischen Typisierung</format> findet diese Überprüfung nicht zur Kompilierungszeit, sondern später <format color="%Highlight%">zur Laufzeit</format> statt, wenn das Programm bereits läuft. Dies macht das Schreiben von Code einfacher, da der Entwickler sich nicht darum kümmern muss, welche Datentypen die Variablen haben. Allerdings erschwert dies auch das spätere Debugging, sollte es zu einem `Runtime Error` kommen, wenn zwei Datentypen inkompatibel sind.

> Statisch typisierte Sprachen sind z.B. Java, C, C++, Haskell und Pascal.
> 
> Dynamisch typisierte Sprachen sind z.B. Python, Smalltalk, PHP, JavaScript und Perl.

## Coding Conventions {id="coding-conventions"}

- Variablen sollten nach der <tooltip term="CamelCase-Notation"><format color="%GlossaryLinkColor%">CamelCase-Notation</format></tooltip> geschrieben werden.
- Bei einer <format color="%LinkColor%">[Schleifenvariable](07-java-loops.md)</format> ist auch ein Buchstabe ausreichend.
- Variablen vom Typ `boolean`, sollten nach Möglichkeit mit `is` beginnen. Alternativ kann auch auf `has` zurückgegriffen werden.
- <format color="%c5%"><a href="10-java-classes.md#constants">Konstanten</a></format> sollten nach der <tooltip term="Constants-Notation"><format color="%GlossaryLinkColor%">SCREAMING_SNAKE_CASE-Notation</format></tooltip> geschrieben werden.