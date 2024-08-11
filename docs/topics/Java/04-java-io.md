# 04 Java Ein- und Ausgaben

Beim Programmieren sind Ausgaben sehr essenziell. Zum einen können bestimmte Werte auf der Konsole zur Überprüfung ausgegeben werden. Zum anderen können über die Ausgabe auf der Konsole <format color="%Highlight%">Errors</format> identifiziert werden, was wesentlich für die <format color="%Highlight%">Fehlersuche und –behebung</format> ist.

Eingaben wiederum ermöglichen uns die Interaktion mit Programmen und damit den Zugriff auf den weiteren Programmablauf – auch über die Konsole. Nahezu alles, was über elektronische Geräte getan wird, wird mit Eingaben realisiert – das Tippen auf der Tastatur, das Klicken mit der Maus oder sogar das Drücken von Tasten auf einem Controller so wie viele weitere Dinge.

Demnach sind natürlich nicht nur Ein- und Ausgaben über die Konsole möglich. Dafür werden jedoch <format color="%LinkColor%">[Benutzeroberflächen](java-gui.md)</format> benötigt. In <format color="%LinkColor%">[Kapitel 2 – Datentypen](02-java-data-types.md)</format> gab es bereits einen kleinen Einblick zu den Konsolenausgaben.

## Ausgaben {id="outputs"}

Um Ausgaben über die Konsole zu realisieren, gibt es mehrere Möglichkeiten.

```Java
System.out.print();   // Ausgabe ohne Zeilenumbruch am Ende
System.out.println(); // Ausgabe mit Zeilenumbruch am Ende
System.out.printf();  // Formatierte Ausgabe ohne Zeilenumbruch am Ende

System.err.print();   // Ausgabe eines Errors ohne Zeilenumbruch am Ende
System.err.println(); // Ausgabe eines Errors mit Zeilenumbruch am Ende
System.err.printf();  // Formatierte Ausgabe eines Errors ohne Zeilenumbruch am Ende
```
Die `print`-Ausdrücke werden <format color="%LinkColor%">[Methoden](09-java-methods.md)</format> genannt. An diese können Werte übergeben werden. Diese Methoden sorgen dann dafür, dass die Werte auf der Konsole ausgegeben werden. Die `printf()`-Methode wird im nachfolgenden <format color="%LinkColor%">[Kapitel 5 – Zeichenketten](05-java-strings.md)</format> genauer betrachtet.

> Die Ausgabe von Fehlern mittels der `err.prinf()`-Methoden sollte ausschließlich für diesen Zweck verwendet werden und nicht zur visuellen Hervorhebung von Text dienen.

```Java
int i = 10;
int j = 10;
int k = i + k;
System.out.println(k); // 20
```

```Java
System.out.println(5 + 11); // 16 (Zeilenumbruch)
System.out.println(3 + 8);  // 11
```

```Java
System.out.print(1);
System.out.print(1);
System.out.print(1); // 111 (Keine Zeilenumbrüche)
```

```Java
System.out.println("Hello World!"); // Hello World!
```

> In IntelliJ kann die Abkürzung `sout` eingegeben werden. Wird mit der Enter-Taste bestätigt, wird der Code automatisch zu `System.out.println()` vervollständigt.
{style="note"}

## Eingaben {id="inputs"}

Es gibt mehrere Varianten Eingaben zu realisieren. Zwei davon werden hier vorgestellt. Dafür muss jedoch auf bestimmte Klassen und Objekte zurückgegriffen werden, die erst importiert werden müssen.

Klassen und Objekte werden in <format color="%LinkColor%">[Kapitel 10 – Klassen](10-java-classes.md)</format> und <format color="%LinkColor%">[Kapitel 11 – Objekte](11-java-objects.md)</format> genauer behandelt. Mehr zu Imports folgt in <format color="%LinkColor%">[Kapitel 16 – Pakete & Imports](16-java-packages-and-imports.md)</format>.

### BufferedReader {id="buffered-reader"}

Eine mögliche Variante funktioniert über den `BufferedReader` in Verbindung mit dem `InputStreamReader` und einem `InputStream`-Objekt `System.in`.

Um nun über diesen Reader eine Eingabe von der Konsole einlesen zu können, muss folgendes geschrieben werden.

```Java
BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
```

Um nun über diesen Reader eine Eingabe von der Konsole einlesen zu können, wird die `readLine()`-<format color="%LinkColor%">[Methode](09-java-methods.md)</format> verwendet.

```Java
reader.readLine();
```

Die `readLine()`-Methode liest einen <format color="%LinkColor%">[String](05-java-strings.md)</format> von der Konsole ein. Dieser kann nun in einer Variablen gespeichert und ausgegeben werden.

```Java
String input = reader.readLine();
System.out-println(input);
```

Der `BufferedReader` stellt selbst keine Methoden zur Verfügung, um Werte als <format color="%LinkColor%">[primitive Datentypen](02-java-data-types.md#primitive-data-types)</format> einzulesen. Daher muss auf die Methoden der jeweiligen <tooltip term="Wrapper-Class"><format color="%GlossaryLinkColor%">Wrapper-Klassen</format></tooltip> zurückgegriffen werden.

```Java
byte b = Byte.parseByte(input);
short s = Short.parseShort(input);
int i = Integer.parseInt(input);
long l = Long.parseLong(input);
float f = Float.parseFloat(input);
double d = Double.parseDouble(input);
boolean bool = Boolean.parseBoolean(input);
```

> Eine `Character.parseChar()`-Methode gibt es nicht.

Jedoch besitzt der Reader eine Methode `read()`. Die Eingabe liegt jedoch als `int` vor, daher muss diese noch in ein `char` <format color="%LinkColor%">[gecastet](03-java-variables.md#type-casting)</format> werden.

```Java
char c = (char) reader.read();
```

### Scanner {id="scanner"}

Eine weitere Variante wird über die `Scanner`-Klasse umgesetzt.

```Java
Scanner scanner = new Scanner(System.in);
```


Der `Scanner` stellt zwar selbst <format color="%LinkColor%">[Methoden](09-java-methods.md)</format> für die Eingabe von <format color="%LinkColor%">[primitiven Datentypen](02-java-data-types.md#primitive-data-types)</format> zur Verfügung, jedoch besitzt er keine Methode für die Eingabe oder die Umwandlung in ein `char`.

```Java
byte b = scanner.nextByte(input);
short s = scanner.nextShort(input);
int i = scanner.nextInt(input);
long l = scanner.nextLong(input);
float f = scanner.nextFloat(input);
double d = scanner.nextDouble(input);
boolean bool = scanner.nextBoolean(input);
```

Wenn ein `char` gefordert wird, muss die Eingabe erst mit der `next()`- oder der `nextLine()`-Methode erfolgen, welche als Input einen <format color="%LinkColor%">[String](05-java-strings.md)</format> erhält.

```Java
String input = scanner.next();
```

```Java
String input = scanner.nextLine();
```

Im Anschluss wird dann über die `charAt()`-Methode das erste Zeichen des Strings in ein `char` umgewandelt. `charAt(0)` bezieht sich auf den ersten Index eines <format color="%LinkColor%">[Strings](05-java-strings.md)</format>. Damit wird das erste Zeichen des `Strings` abgegriffen. Alle folgenden Zeichen werden ignoriert. Mehr zu Indizes folgt in <format color="%LinkColor%">[Kapitel 8 – Arrays](08-java-arrays.md)</format>.

- Mit `next()` wird alles bis zum ersten Leerzeichen eingelesen.
- Mit `nextLine()` wird der komplette `String` eingelesen inklusive Leerzeichen.

> Werden mehrere Eingaben mit der Methode `next()` hintereinander geschrieben und auf der Konsole mehrere durch Leerzeichen getrennte Zeichenfolgen eingegeben, wird jede getrennte Zeichenfolge automatisch für jedes weitere Einlesen verwendet.

```Java
System.out.print("Input 1: ");
String s1 = scanner.next();
System.out.print("Input 2: ");
String s2 = scanner.next();
System.out.print("Input 3: ");
String s3 = scanner.next();
System.out.print("Input 4: ");
String s4 = scanner.next();

System.out.println();
System.out.println(s1);
System.out.println(s2);
System.out.println(s3);
System.out.println(s4);
```

```Console
Input 1: a b c d
Input 2: Input 3: Input 4:
a
b
c
d
```

> Sowohl beim `BufferedReader` als auch beim `Scanner` werden <format color="%WarningLinkColor%">[Strings](05-java-strings.md)</format> eingelesen. Diese werden über die <format color="%WarningLinkColor%">[Methoden](09-java-methods.md)</format> in die jeweiligen <format color="%WarningLinkColor%">[Datentypen](02-java-data-types.md)</format> umgewandelt. Beinhaltet beispielsweise ein `String` andere Zeichen als Zahlen, wenn er z.B. in ein `int` konvertiert wird, schmeißt der <tooltip term="Compiler"><format color="%GlossaryLinkColor%">Compiler</format></tooltip> einem eine <format color="%WarningLinkColor%">[Exception](15-java-exceptions.md)</format> um die Ohren.
>```Java
>System.out.print("Bitte eine Zahl eingeben: ");
>int i = scanner.nextInt();
>```
>```Console
>Bitte eine Zahl eingeben: Hello!
>Exception in thread "main" java.util.InputMismatchException
>at java.base/java.util.Scanner.throwFor(Scanner.java:947)
>at java.base/java.util.Scanner.next(Scanner.java:1602)
>at java.base/java.util.Scanner.nextInt(Scanner.java:2267)
>at java.base/java.util.Scanner.nextInt(Scanner.java:2221)
>at kesares.techarchive.Main.main(Main.java:10)
>```
{style="warning" title="InputMismatchException"}

> Die Methoden des `Scanners` können eine `InputMismatchException` auslösen.
> 
> Die `parse`-Methoden können eine `NumberFormatException` auslösen.
> 
> <format color="%NoteLinkColor%">[Exceptions](15-java-exceptions.md)</format> allgemein müssen mit einem `try`-`catch`-Block abgefangen werden.
{style="note"}

Um Ressourcen zu schonen, sollten der `Scanner` und/oder `BufferedReader` nach ihrer Verwendung wieder geschlossen werden.

```Java
scanner.close();
```

```Java
reader.close();
```

## Farbliche Gestaltung (Ausblick) {id="color-design-outlook"}

Wir Menschen bevorzugen oft ansprechend gestaltete Benutzeroberflächen, weil sie eine einfachere und schnellere Navigation ermöglichen. Wer jedoch in die Programmierung einsteigt, wird früher oder später mit der Arbeit auf der Konsole konfrontiert.

Viele empfinden die Konsole als mühsam oder langweilig. Gleichzeitig bin ich der Meinung, dass das direkte Arbeiten mit der Konsole und simplen Ein- und Ausgaben einen einfachen Einstieg in die Programmierung ermöglicht. Ich schätze jedoch auch Möglichkeiten zur kreativen Gestaltung von Elementen und nutze daher <format color="%LinkColor%">[ANSI-Zeichencodes](https://gist.github.com/fnky/458719343aabd01cfb17a3a4f7296797)</format>, um die Konsolenausgaben etwas farbenfroher zu gestalten.

Wer also den Standard-Look als etwas eintönig empfindet, könnte darin die Motivation finden, sich intensiver mit der Konsole zu beschäftigen. Im folgenden <format color="%LinkColor%">[Kapitel 5 – Zeichenketten](05-java-strings.md)</format> wird ein Abschnitt den <format color="%LinkColor%">[ANSI Escape Codes](05-java-strings.md#ansi-escape-sequences)</format> gewidmet sein.

>Hinweis: Die meisten <tooltip term="IDE"><format color="%GlossaryLinkColor%">IDEs</format></tooltip> unterstützen die Darstellung von ANSI-Farbcodes in der Konsole. Es wird jedoch möglicherweise nicht immer die vollständige Palette von 256 Farben in jeder Umgebung unterstützt werden.

## Übung {id="exercise"}

Da wir jetzt alle nötigen Bausteine zusammen haben, um ein einfaches Programm mit Ein- und Ausgaben schreiben zu können, folgt nun eine kleine Übung.

<tabs group="task">
    <tab id="task-task" title="Aufgabe">
        <note title="Taschenrechner">
            Programmierung eines simplen Taschenrechners mit Addition, Subtraktion, Multiplikation und Division von zwei Zahlen mit Ein- und Ausgaben über die Konsole.
        </note>
    </tab>
    <tab id="task-solution" title="Mögliche Lösung">
        <code-block lang="java">
            public static void main(String[] args) {
                Scanner sc = new Scanner(System.in);
                System.out.print("1. Zahl: ");
                int x = sc.nextInt();
                System.out.print("2. Zahl: ");
                int y = sc.nextInt();
                System.out.println(x + y);
                System.out.println(x - y);
                System.out.println(x * y);
                System.out.println(x / y);
                sc.close();
            }
        </code-block>
    </tab>
</tabs>