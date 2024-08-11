# 05 Java Zeichenketten

Zeichenketten (auch Strings genannt) sind eine der häufigsten angewendeten Datentypen. Sie repräsentieren eine Folge von Zeichen, gehören zu den <format color="%LinkColor%">[Referenzdatentypen](02-java-data-types.md#reference-data-types)</format> (Objekte) und sind daher keine <format color="%LinkColor%">[primitiven Datentypen](02-java-data-types.md#primitive-data-types)</format>. Wird eine Variable vom Typ `String` angelegt, enthält diese nicht die Zeichenkette selbst, sondern eine Referenz (Verweis) auf das eigentliche Objekt der Klasse `String`. Ein `char` ist ein primitiver Datentyp und kann nur ein einziges Zeichen darstellen. Sollen mehr dargestellt werden muss auf einen `String` zurückgegriffen werden.

## Konkatenation {id="concatenation"}

Im vorherigen <format color="%LinkColor%">[Kapitel 4 – Ein- und Ausgaben](04-java-io.md)</format> gab es bereits einen kleinen Einblick zu Strings. Wenn zwei Strings mit einem `+` verbunden werden, wird das eine Konkatenation (Verkettung, engl. concatenation) genannt. Dies ist auch zwischen Strings und <format color="%LinkColor%">[primitiven Datentypen](02-java-data-types.md#primitive-data-types)</format> möglich.

```Java
String name = "Kesares";
System.out.println(name); // Kesares
```

```Java
System.out.println("42" + 5); // 425
```

```Java
int x = 2;
int y = 40;
String s = x + " + " + y + " = " + (x + y);
System.out.println(s); // 2 + 40 = 42
```

## String-Pool und Java-Heap {id="string-pool-and-java-heap"}

Ein `String` ist ein spezielles <format color="%LinkColor%">[Objekt](11-java-objects.md)</format>, das für die Arbeit mit Texten verwendet wird. Obwohl Strings in Java Objekte sind, unterscheiden sich ihre Erzeugung und Verwaltung von der vieler anderer Objekte.

Normalerweise werden <format color="%LinkColor%">[Objekte](11-java-objects.md)</format> mit dem `new`-Keyword erstellt, was zu einem neuen Objekt auf dem <tooltip term="Java-Heap"><format color="%GlossaryLinkColor%">Java-Heap</format></tooltip> führt. 

```Java
String name = new String("Kesares");
```

In diesem Fall werden zwei `String`-Objekte erstellt: eines auf dem <tooltip term="Java-Heap"><format color="%GlossaryLinkColor%">Java-Heap</format></tooltip>, das durch den `new`-Operator erzeugt wird und ein weiteres im sogenannten <tooltip term="String-Pool"><format color="%GlossaryLinkColor%">String-Pool</format></tooltip>. Der String-Pool ist ein spezieller Speicherbereich, der von der <tooltip term="JVM"><format color="%GlossaryLinkColor%">JVM</format></tooltip> verwaltet wird und zur Optimierung von Speicherverbrauch und Leistung dient.

Der <tooltip term="String-Pool"><format color="%GlossaryLinkColor%">String-Pool</format></tooltip> speichert einmal erstellte `String`-Literale und stellt sicher, dass alle identischen Literale auf denselben Speicherort im Pool verweisen. Dies bedeutet, dass bei der Nutzung von <format color="%LinkColor%">[Literalen](01-java-token.md#literals)</format> wie `"Kesares"` die JVM nicht jedes Mal ein neues `String`-Objekt erstellen muss, sondern auf das bereits im Pool vorhandene <format color="%LinkColor%">[Objekt](11-java-objects.md)</format> verweist.

Die bevorzugte und performantere Schreibweise zur Erstellung eines `String`-Objekts ist daher:

```Java
String s = "Kesares";
```

In diesem Fall wird, sofern bereits eine Zeichenkette mit dieser Zeichenfolge existiert, kein weiteres `String`-Objekt angelegt und alle Verweise auf das Literal `"Kesares"` zeigen auf das gleiche <format color="%LinkColor%">[Objekt](11-java-objects.md)</format> im Pool. Diese Methode reduziert den Speicherverbrauch und verbessert die Leistung, da die <tooltip term="JVM"><format color="%GlossaryLinkColor%">JVM</format></tooltip> unnötige Duplikate von `String`-Objekten vermeidet und die Verwaltung von Speicher effizienter gestaltet wird.

## String-Methoden {id="string-methods"}

In der Java-Programmierung gibt es zahlreiche Operationen, die auf einem `String`-Objekt durchgeführt werden können. Diese <format color="%LinkColor%">[Methoden](09-java-methods.md)</format> werden direkt über die jeweiligen `String`-Objekte aufgerufen, um verschiedene Bearbeitungen oder Abfragen durchzuführen. Im Folgenden sind einige der wichtigsten Methoden beschrieben, die für die Arbeit mit Strings von Bedeutung sind.

<table>
    <tr>
        <td>Methode</td>
        <td>Beschreibung</td>
    </tr>
    <tr>
        <td><code>length()</code></td>
        <td>Gibt die Anzahl der Zeichen (inklusive Leerzeichen) im <code>String</code> zurück.</td>
    </tr>
    <tr>
        <td><code>equals(otherString)</code></td>
        <td>Vergleicht den aktuellen <code>String</code> mit einem übergebenen <code>String</code>, um festzustellen, ob sie inhaltlich identisch sind. Gibt <code>true</code> zurück, wenn die beiden Strings gleich sind, andernfalls <code>false</code>.</td>
    </tr>
    <tr>
        <td><code>equalsIgnoreCase(otherString)</code></td>
        <td>Vergleicht den aktuellen <code>String</code> mit einem übergebenen <code>String</code>, um festzustellen, ob sie inhaltlich identisch sind, wobei die Groß- und Kleinschreibung ignoriert wird. Gibt <code>true</code> zurück, wenn die beiden Strings inhaltlich gleich sind, andernfalls <code>false</code>.</td>
    </tr>
    <tr>
        <td><code>charAt(index)</code></td>
        <td>Liefert das Zeichen an der übergebenen Position (Index) im <code>String</code>.</td>
    </tr>
    <tr>
        <td><code>substring(start, end)</code></td>
        <td>Extrahiert einen Teilstring aus dem Originalstring. Die Methode nimmt einen Start- und einen Endindex entgegen und gibt den entsprechenden Teilstring zurück.</td>
    </tr>
    <tr>
        <td><code>toLowerCase()</code></td>
        <td>Konvertiert alle Zeichen im <code>String</code> in Kleinbuchstaben.</td>
    </tr>
    <tr>
        <td><code>toUpperCase()</code></td>
        <td>Konvertiert alle Zeichen im <code>String</code> in Großbuchstaben.</td>
    </tr>
    <tr>
        <td><code>startsWith(prefix)</code></td>
        <td>Prüft, ob der <code>String</code> mit einer bestimmten Zeichenfolge (Präfix) beginnt. Gibt <code>true</code> zurück, wenn dies der Fall ist, andernfalls <code>false</code>.</td>
    </tr>
    <tr>
        <td><code>endsWith(suffix)</code></td>
        <td>Prüft, ob der <code>String</code> mit einer bestimmten Zeichenfolge (Suffix) endet. Gibt <code>true</code> zurück, wenn dies der Fall ist, andernfalls <code>false</code>.</td>
    </tr>
    <tr>
        <td><code>indexOf(substring)</code></td>
        <td>Sucht nach der ersten Position einer übergebenen Zeichenfolge im <code>String</code> und gibt den Index dieser Position zurück. Falls die Zeichenfolge nicht gefunden wird, wird <code>-1</code> zurückgegeben.</td>
    </tr>
    <tr>
        <td><code>lastIndexOf(substring)</code></td>
        <td>Im Gegensatz zu <code>indexOf(substring)</code> sucht diese Methode nach der letzten Position einer übergebenen Zeichenfolge im <code>String</code> und gibt deren Index zurück. Auch hier wird <code>-1</code> zurückgegeben, wenn die Zeichenfolge nicht gefunden wird.</td>
    </tr>
    <tr>
        <td><code>trim()</code></td>
        <td>Entfernt führende und nachfolgende Leerzeichen aus dem <code>String</code>.</td>
    </tr>
    <tr>
        <td><code>replace(oldChar, newChar)</code></td>
        <td>Ersetzt bestimmte Zeichen im <code>String</code> durch andere Zeichen.</td>
    </tr>
    <tr>
        <td><code>split(delimiter)</code></td>
        <td>Zerlegt den <code>String</code> anhand eines angegebenen Trennzeichens und gibt ein <format color="%LinkColor%"><a href="08-java-arrays.md">Array</a></format> von Strings zurück.</td>
    </tr>
    <tr>
        <td><code>contains(substring)</code></td>
        <td>Überprüft, ob der <code>String</code> eine bestimmte Zeichenfolge enthält. Gibt <code>true</code> zurück, wenn die Zeichenfolge vorhanden ist, andernfalls <code>false</code>.</td>
    </tr>
    <tr>
        <td><code>valueOf(value)</code></td>
        <td>Wandelt einen anderen Datentyp in einen <code>String</code> um. Das Ergebnis ist eine <code>String</code>-Darstellung des übergebenen Wertes.</td>
    </tr>
    <tr>
        <td><code>isEmpty()</code></td>
        <td>Überprüft, ob der <code>String</code> leer ist (d.h., keine (Leer-)Zeichen enthält). Sie gibt <code>true</code> zurück, wenn der <code>String</code> leer ist, andernfalls <code>false</code>.</td>
    </tr>
    <tr>
        <td><code>isBlank()</code></td>
        <td>Überprüft, ob der <code>String</code> leer oder nur aus Leerzeichen besteht. Im Gegensatz zur Methode <code>isEmpty()</code>, berücksichtigt <code>isBlank()</code> auch Strings, die nur Leerzeichen, Tabs oder andere Whitespace-Zeichen enthalten. Gibt <code>true</code> zurück, wenn der <code>String</code> leer ist oder nur aus Whitespace-Zeichen besteht, andernfalls <code>false</code>.</td>
    </tr>
</table>

> Strings sind <format color="%NoteHighlight%">immutable</format> (unveränderlich). Sie können also nicht verändert werden. Wird ein `String` verändert, wird intern ein neuer `String` mit dem geänderten Inhalt angelegt.
{style="note"}

```Java
String name = "Kesares";

name.length();           // 7
name.equals("Kesares");  // true
name.charAt(3);          // 'a'
name.startsWith("s");    // false
name.endsWith("res");    // true
name.substring(3);       // "ares"
name.substring(3, 6);    // "are"
name.indexOf("e");       // 1
name.lastIndexOf("e");   // 5
name.toLowerCase();      // "kesares"
name.toUpperCase();      // "KESARES"
name.replace('e', 'i');  // "Kisaris"
"   Kesares   ".trim();  // "Kesares"
name.split("a");         // ["Kes", "res"]
name.contains("sar");    // true
name.valueOf(42);        // "42"
name.isEmpty();          // false
name.isBlank();          // false
```

## Escape Sequenzen {id="escape-sequences"}

Folgende Liste wurde bereits in <format color="%LinkColor%">[Kapitel 2 – Datentypen](02-java-data-types.md)</format> präsentiert. Auch in Strings können diese verwendet werden.

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

## Konvertierung {id="conversion"}

An einigen Stellen muss im Programm möglicherweise ein `String` in einen anderen Datentyp konvertiert werden. Java stellt für diese Anwendungsfälle die `parse`-Methoden zur Verfügung. Einen kleinen Einblick in diese <format color="%LinkColor%">[Methoden](09-java-methods.md)</format> gab es bereits in <format color="%LinkColor%">[Kapitel 4 – Ein- und Ausgaben](04-java-io.md)</format>.

Die `parse`-Methoden sind statisch und werden daher über die <tooltip term="Wrapper-Class"><format color="%GlossaryLinkColor%">Wrapper-Klassen</format></tooltip> der jeweiligen <format color="%LinkColor%">[primitiven Datentypen](02-java-data-types.md#primitive-data-types)</format> angesprochen. Der <format color="%LinkColor%">[Rückgabewert](09-java-methods.md#return-type)</format> der Methoden entspricht dem jeweiligen Datentyp.

```Java
byte b = Byte.parseByte("127");
short s = Short.parseShort("32767");
int i = Integer.parseInt("2147483647");
long l = Long.parseLong("9223372036854775807");
float f = Float.parseFloat("3.4028235e38");
double d = Double.parseDouble("1.7976931348623157e308");
boolean bool = Boolean.parseBoolean("true");
```

>Sämtliche `parse`-Methoden der <tooltip term="Wrapper-Class"><format color="%GlossaryLinkColor%">Wrapper-Klassen</format></tooltip> erwarten einen `String` als Parameter, den sie umwandeln können. Beinhaltet ein `String` beispielsweise keine echte Zahl, wenn dieser in ein `int` umgewandelt wird, wirft der <tooltip term="Compiler"><format color="%GlossaryLinkColor%">Compiler</format></tooltip> eine <format color="%WarningLinkColor%">[Exception](15-java-exceptions.md)</format>.
> ```Java
>Integer.parseInt("42b");
> ```
> ```Console
>Exception in thread "main" java.lang.NumberFormatException: For input string: "42b"
>at java.base/java.lang.NumberFormatException.forInputString(NumberFormatException.java:67)
>at java.base/java.lang.Integer.parseInt(Integer.java:662)
>at java.base/java.lang.Integer.parseInt(Integer.java:778)
>at kesares.techarchive.Main.main(Main.java:6)
>```
{style="warning" title="NumberFormatException"}

>Es existiert keine vergleichbare `parse`-Methode für die Konvertierung von `char`.
Soll ein `String` in ein `char` umgewandelt werden, wird die `charAt()-`Methode verwendet.
{style="note"}

```Java
String name = "Kesares";
char c = name.charAt(2);
System.out.println(c); // s
```

## Formatierung {id="formatting"}

Um Strings zu formatieren, gibt es mehrere Möglichkeiten und Varianten. Hier wird sich auf die folgenden beiden Vorgehensweisen konzentriert. Beide Varianten sind vom Prinzip identisch.

```Java
String s = String.format(format, args...)
System.out.println(s);

System.out.printf(format, args...)
```

Die `format()`-Methode ist eine <format color="%LinkColor%">[statische Methode](10-java-classes.md#class-methods)</format> der Klasse `String`. Sie formatiert Strings nach einer bestimmten Vorgabe und gibt einen `String` mit den eingebetteten Argumenten zurück.

Der erste Parameter der Methode ist der eigentliche `String`, der am Ende beispielsweise auf der Konsole ausgegeben wird. Dieser kann zudem bestimmte <format color="%LinkColor%">[Spezifizierer und Flags](#specifier-and-flags)</format> enthalten, die der Methode mitteilen, wie sie die Argumente formatieren soll. Der zweite Parameter ist ein `Vararg` (siehe <format color="%LinkColor%">[Variable Parameteranzahl](09-java-methods.md#varargs)</format>), mit den Werten, die für die jeweiligen Spezifizierer eingesetzt werden sollen.

Die Formatierungen des `format`-Strings werden nach folgendem Schema geschrieben.

```Console
%[flags][width][.precision]conversion
```

Die Anzahl an Spezifizierer muss der Anzahl an Argumenten gleichen.

### Spezifizierer und Flags {id="specifier-and-flags"}

<table>
    <tr>
        <td width="130">Spezifizierer</td>
        <td>Beschreibung</td>
    </tr>
    <tr>
        <td><code>%n</code></td>
        <td>Zeilenumbruch</td>
    </tr>
    <tr>
        <td><code>%%</code></td>
        <td>Prozentzeichen</td>
    </tr>
    <tr>
        <td><code>%x</code></td>
        <td>Hexadezimalsystem</td>
    </tr>
    <tr>
        <td><code>%o</code></td>
        <td>Oktalsystem</td>
    </tr>
    <tr>
        <td><code>%f</code></td>
        <td>Fließkommazahl</td>
    </tr>
    <tr>
        <td><code>%b</code></td>
        <td>Boolean</td>
    </tr>
    <tr>
        <td><code>%s</code></td>
        <td>String</td>
    </tr>
    <tr>
        <td><code>%c</code></td>
        <td>Character</td>
    </tr>
    <tr>
        <td><code>%d</code></td>
        <td>Dezimalzahl</td>
    </tr>
    <tr>
        <td><code>%t</code></td>
        <td>Datum und Zeit</td>
    </tr>
    <tr>
        <td><code>%e</code></td>
        <td>Wissenschaftliche Notation</td>
    </tr>
</table>

<table>
    <tr>
        <td width="130">Flag (optional)</td>
        <td>Beschreibung</td>
    </tr>
    <tr>
        <td><code>-</code></td>
        <td>Linksbündige Ausgabe innerhalb der angegebenen Breite.</td>
    </tr>
    <tr>
        <td><code>+</code></td>
        <td>Zeigt immer das Vorzeichen (<code>+</code> oder <code>-</code>) für numerische Werte an.</td>
    </tr>
    <tr>
        <td><code>0</code></td>
        <td>Auffüllen mit Nullen (anstelle von Leerzeichen) für Zahlen.</td>
    </tr>
    <tr>
        <td><code>,</code></td>
        <td>Tausendertrennzeichen verwenden (z.B. <code>1.000</code>). Zeichen ist abhängig von der Spracheinstellung des Systems.</td>
    </tr>
    <tr>
        <td><code>(</code></td>
        <td>Negative Zahlen in Klammern anzeigen.</td>
    </tr>
</table>

Die `conversion` ist der eigentliche Spezifizierer. Optional kann noch eine Breite und die Präzision angegeben werden.
- `conversion` – der eigentliche Spezifizierer wie `%d`, `%s`, `%f` usw.
- `width` – bestimmt die minimale Anzahl an Zeichen, die ausgegeben werden sollen. Wenn der Wert kürzer ist, wird er mit Leerzeichen aufgefüllt.
- `.precision` – gibt die Anzahl der Nachkommastellen für Fließkommazahlen oder die maximale Anzahl an Zeichen für Strings an.
- `%n$` – gibt das n-te Argument an, dass an die `format()`-Methode übergeben wird. Dadurch ist es möglich die Reihenfolge der Argumente zu vertauschen oder die Argumente mehrmals verwenden zu können.

```Java
System.out.println(String.format("Hallo %s!", "Welt"));
System.out.println(String.format("Die Zahl ist %d.", 42));
System.out.println(String.format("Der Preis ist %.2f Euro.", 12.3456));
System.out.println(String.format("Die Zahl in Hexadezimal: %x", 255));
System.out.println(String.format("Die Zahl in Oktal: %o", 8));
System.out.println(String.format("Das Zeichen ist %c.", 'A'));
System.out.println(String.format("Der Wert ist %b.", true));
System.out.println(String.format("Erste Zeile%nZweite Zeile"));
System.out.println(String.format("Wert: %8.2f", 123.4567));
System.out.println(String.format("Name: %-10s", "Java"));
System.out.println(String.format("Der Betrag ist %,d.", 1000000));
System.out.println(String.format("%2$d + %1$d = %3$d", 5, 3, 8));
```

## Textblock {id="text-block"}

Zeilenumbrüche kommen immer wieder vor. Gerade wenn es um Bildschirmausgaben oder eingebetteten Code wie HTML, JSON, SQL, etc. geht. In Java 15 wurden Textblöcke eingeführt, mit denen sich mehrzeilige Strings leichter bilden lassen, als über Konkatenationen. Eingeleitet wird ein Textblock mit drei doppelten Anführungsstrichen `"""`.

```Java
String text = """
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Title</title>
    </head>
    <body>
    
    </body>
    </html>
""";
```

## Die Klassen `StringBuilder` und `StringBuffer` (Advanced) {id="string-builder-and-string-buffer-classes"}

Strings sind <format color="%Highlight%">immutable</format> und Konkatenationen sind teuer. Die Klassen `StringBuilder` und `StringBuffer` existieren zum Zweck der Veränderung von Strings. Werden mehrere Verkettungen durchgeführt (z.B. in Schleifen ab einer bestimmten Anzahl an Iterationen), ist ein `StringBuilder`-Objekt sinnvoller.

Soll eine <format color="%LinkColor%">[Methode](09-java-methods.md)</format> am Ende die Verkettung des `StringBuilder`-Objekts als `String` liefern, muss noch die `toString()`-Methode über den `StringBuilder` aufgerufen werden.

```Java
public static String getConcatString() {
    StringBuilder builder = new StringBuilder();

    for (int i = 0; i < 10; i++) {
        builder.append(i);
        builder.append("-");
    }
    return builder.toString();
}
```

> `String` – <format color="%NoteHighlight%">unveränderlich (immutable)</format>. Einmal erstellt, kann der Wert eines `String`-Objekts nicht mehr geändert werden. Ein Änderungsversuch erzeugt ein neues `String`-Objekt, was <format color="%NoteHighlight%">ineffizient</format> sein kann, <format color="%NoteHighlight%">wenn viele Änderungen</format> vorgenommen werden.
> 
> `StringBuilder` – <format color="%NoteHighlight%">veränderlich (mutable)</format>. Der Inhalt kann nach der Erstellung geändert werden, ohne neue Objekte zu erzeugen. <format color="%NoteHighlight%">[Nicht thread-sicher](java-threads.md)</format>, da keine Synchronisation verwendet wird, was es schneller macht als `StringBuffer`.
> 
> `StringBuffer` – ähnlich wie `StringBuilder`, auch <format color="%NoteHighlight%">veränderlich (mutable)</format> und effizient bei häufigen Änderungen. <format color="%NoteLinkColor%">[Thread-sicher](java-threads.md)</format>, da alle Methoden synchronisiert sind. Aufgrund der Synchronisation etwas langsamer als `StringBuilder`.
{style="note" title="String, StringBuilder und StringBuffer"}

Folgendes Beispiel misst die Zeit um die jeweiligen Strings mittels `StringBuilder` und Konkatenation zu bilden.

```Java
long now = 0;  
long timeTaken = 0;  
  
now = System.nanoTime();  
  
StringBuilder builder = new StringBuilder();  
for (int i = 0; i < 1000; i++) {  
    builder.append("-");  
}
  
timeTaken = System.nanoTime() - now;  
System.out.printf("1. Zeit: %d ns%n", timeTaken);



now = System.nanoTime();  
  
String text = "";  
for (int i = 0; i < 1000; i++) {  
    text += "-";  
}
  
timeTaken = System.nanoTime() - now;  
System.out.printf("2. Zeit: %d ns%n", timeTaken);
```

> Die Zeiten können sich je nach System unterscheiden. Je nachdem wie stark der Prozessor ist.

## ANSI Escape-Sequenzen {id="ansi-escape-sequences"}

ANSI Escape-Sequenzen sind eine Reihe von Zeichenfolgen, die verwendet werden können, um Text in der Konsole zu formatieren, um z.B. die Farbe oder den Stil des Textes zu ändern. Diese Sequenzen werden typischerweise in terminalbasierten Anwendungen verwendet, die ANSI-Farbcodes unterstützen, können aber auch innerhalb von <tooltip term="IDE"><format color="%GlossaryLinkColor%">IDEs</format></tooltip> verwendet werden.

> Mehr und genauere Informationen können <format color="%NoteLinkColor%">[hier](https://gist.github.com/fnky/458719343aabd01cfb17a3a4f7296797)</format> gefunden werden.
{style="note"}

Eine ANSI Escape-Sequenz beginnt immer mit einem Escape-Zeichen wie `\033` oder `\u001B` (beides wird in Java unterstützt, letzteres ist typischer in der Java-Umgebung) gefolgt von einem `[` und einer Reihe von Codes, die durch Semikolons getrennt sind und endet mit einem `m`.

Um die Formatierung nach einer ANSI-Sequenz zurückzusetzen und zur Standardkonfiguration zurückzukehren, wird `\u001B[0m` verwendet.

```Java
System.out.println("\u001B[31mDieser Text ist rot!\u001B[0m");
```

### Farbcodes {id="color-codes"}

<table>
    <tr>
        <td>Code</td>
        <td>Farbe</td>
    </tr>
    <tr>
        <td><code>30</code></td>
        <td>Schwarz</td>
    </tr>
    <tr>
        <td><code>31</code></td>
        <td>Rot</td>
    </tr>
    <tr>
        <td><code>32</code></td>
        <td>Grün</td>
    </tr>
    <tr>
        <td><code>33</code></td>
        <td>Gelb</td>
    </tr>
    <tr>
        <td><code>34</code></td>
        <td>Blau</td>
    </tr>
    <tr>
        <td><code>35</code></td>
        <td>Magenta</td>
    </tr>
    <tr>
        <td><code>36</code></td>
        <td>Cyan</td>
    </tr>
    <tr>
        <td><code>37</code></td>
        <td>Weiß</td>
    </tr>
    <tr>
        <td><code>40</code></td>
        <td>Schwarzer Hintergrund</td>
    </tr>
    <tr>
        <td><code>41</code></td>
        <td>Roter Hintergrund</td>
    </tr>
    <tr>
        <td><code>42</code></td>
        <td>Grüner Hintergrund</td>
    </tr>
    <tr>
        <td><code>43</code></td>
        <td>Gelber Hintergrund</td>
    </tr>
    <tr>
        <td><code>44</code></td>
        <td>Blauer Hintergrund</td>
    </tr>
    <tr>
        <td><code>45</code></td>
        <td>Magenta Hintergrund</td>
    </tr>
    <tr>
        <td><code>46</code></td>
        <td>Cyan Hintergrund</td>
    </tr>
    <tr>
        <td><code>47</code></td>
        <td>Weißer Hintergrund</td>
    </tr>
</table>

### Stile {id="styles"}

<table>
    <tr>
        <td>Code</td>
        <td>Stil</td>
    </tr>
    <tr>
        <td><code>0</code></td>
        <td>Alle Attribute zurücksetzen (Normaler Text)</td>
    </tr>
    <tr>
        <td><code>1</code></td>
        <td>Fettschrift</td>
    </tr>
    <tr>
        <td><code>3</code></td>
        <td>Kursivschrift</td>
    </tr>
    <tr>
        <td><code>4</code></td>
        <td>Unterstrichen</td>
    </tr>
    <tr>
        <td><code>7</code></td>
        <td>Invertiert Vordergrund- und Hintergrundfarbe</td>
    </tr>
    <tr>
        <td><code>9</code></td>
        <td>Durchgestrichen</td>
    </tr>
</table>

Mehrere Codes können kombiniert werden, indem sie durch Semikolons getrennt werden.

```Java
System.out.println("\u001B[31mDieser Text ist rot!\u001B[0m");
System.out.println("\u001B[32mDieser Text ist grün!\u001B[0m");
System.out.println("\u001B[1;34mDieser Text ist blau und fett!\u001B[0m");
```

>Nicht alle Terminals unterstützen <format color="%NoteHighlight%">ANSI Escape-Sequenzen</format> und ihre Unterstützung kann auf verschiedenen Betriebssystemen variieren. In Windows-Terminals kann es z.B. erforderlich sein, die Unterstützung für ANSI-Sequenzen explizit zu aktivieren, da ältere Versionen dies standardmäßig nicht unterstützen.
{style="note" title="Fehlende oder nicht vollständige Unterstützung"}