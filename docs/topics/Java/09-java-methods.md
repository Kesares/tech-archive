# 09 Java – Methoden

Methoden bestimmen das Verhalten von <format color="%LinkColor%">[Objekten](11-java-objects.md)</format> und des Programms. Sie werden innerhalb einer <format color="%LinkColor%">[Klasse](10-java-classes.md)</format> angelegt. Wird derselbe Programmcode an mehreren Stellen verwendet, kann dieser in eine Methode ausgelagert werden und stattdessen die Methode aufgerufen werden.

## Klassen- & Objektmethoden {id="class-and-object-methods"}

Grundsätzlich kann zwischen zwei Methodenarten unterschieden werden.
- <format color="%c1%">Objektmethoden</format> (auch Instanzmethoden)
- <format color="%c2%">Klassenmethoden</format> (auch statische Methoden)

<format color="%LinkColor%">[Objektmethoden](10-java-classes.md#object-methods)</format> können nur über konkret instanziierte <format color="%LinkColor%">[Objekte](11-java-objects.md)</format> aufgerufen werden. <format color="%LinkColor%">[Klassenmethoden](10-java-classes.md#class-methods)</format> brauchen kein instanziiertes Objekt. Sie können über die Klasse direkt aufgerufen werden. In diesem Kapitel fokussieren wir uns auf die Klassenmethoden, da wir diese aus der <format color="%LinkColor%">[main-Methode](#main-method)</format> aufrufen können, ohne dass ein Objekt instanziiert werden muss.

## Methodenstruktur {id="method-structure"}

Allgemein wird eine Methode in zwei Bereiche unterteilt. Zum einen den <format color="%Highlight%">Kopf</format> - dieser beinhaltet alles vom <format color="%TipLinkColor%">[Access Modifier](12-java-modifier-access-rights.md#access-modifier)</format> bis zur geschlossenen runden Klammer. Zum anderen den <format color="%TipLinkColor%">Rumpf</format> - dieser ist der eigentliche Code-Block mit den geschweiften Klammern `{}`.


```
// Class methodf
access-modifier static return-type methodName(parameter) {
    // Code...
}
```

```
// Object method
access-modifier return-type methodName(parameter) {
    // Code...
}
```

<table>
    <tr>
        <td>Teil des Methodenkopfes</td>
        <td>Beschreibung</td>
    </tr>
    <tr>
        <td>access-modifier</td>
        <td><code>public</code>, <code>private</code>, <code>protected</code> oder implizit <code>package-private</code>.</td>
    </tr>
    <tr>
        <td><code>static</code></td>
        <td><a href="01-java-token.md">Keyword</a> für den statischen Aufruf der Methode über den Klassennamen.</td>
    </tr>
    <tr>
        <td>type</td>
        <td>Der Rückgabetyp der angibt, von welchem <format color="%LinkColor%"><a href="02-java-data-types.md">Datentyp</a></format> das Ergebnis der Methode ist, sofern etwas zurückgegeben wird.</td>
    </tr>
    <tr>
        <td>methodName</td>
        <td>Ein <format color="%LinkColor%"><a href="01-java-token.md#identifier">Identifier</a></format> für den Namen der Methode.</td>
    </tr>
    <tr>
        <td>parameter</td>
        <td>Ein oder mehrere Werte die optional an diese Methode übergeben werden können.</td>
    </tr>
</table>

> Der <format color="%NoteLinkColor%">[Access Modifier](12-java-modifier-access-rights.md#access-modifier)</format> kann weggelassen werden. Die Methode besitzt dann implizit den Modifier `package-private`. Dieser Modifier kann vom Entwickler nicht selbst gesetzt werden.
> {style="note" title="package-private"}

### Methodensignatur {id="method-signature"}

Die Signatur einer Methode besteht aus ihrem Namen und ihrer Parameterliste. Der Rückgabetyp und die <format color="%LinkColor%">[Zugriffsmodifizierer](12-java-modifier-access-rights.md#access-modifier)</format> sind nicht Teil der Signatur. Die Signatur ist wichtig, um Methoden innerhalb einer <format color="%LinkColor%">[Klasse](10-java-classes.md)</format> zu unterscheiden, insbesondere bei der <format color="%LinkColor%">[Methodenüberladung](#method-overloading)</format> (engl. method overloading), wo mehrere Methoden denselben Namen, aber unterschiedliche Parameterlisten haben können.

## `main`-Methode {id="main-method"}

Eine Methode sollte bereits bekannt sein – die `main()`-Methode.

```Java
public static void main(String[] args) {
    // Code...
}
```

Diese ist die Wichtigste, da sie als zentraler Einstiegspunkt in unsere eigenen Programme fungiert und vorhanden sein muss. Die Methode erwartet ein `String[]` als Parameter, welches optionale Argumente beinhaltet, die beim Programmstart mit übergeben werden können und innerhalb des Programms verarbeitet werden.

`public` und `static` sind Keywords und werden im <format color="%LinkColor%">[Kapitel 12 – Modifizierer & Zugriffsrechte](12-java-modifier-access-rights.md)</format> genauer erklärt.

An der `main()`-Methode darf nichts verändert werden, außer den <format color="%LinkColor%">[Identifier](01-java-token.md#identifier)</format> des Parameters anders zu nennen oder das <format color="%LinkColor%">[Array](08-java-arrays.md)</format> in ein <format color="%LinkColor%">[Vararg](#varargs)</format> zu ändern.

```Java
public static void start(String[] args) {
    // Code...
}
```

> ```Java
>Fehler: Hauptmethode in Klasse kesares.techarchive.Main nicht gefunden. Definieren Sie die Hauptmethode als:
>public static void main(String[] args):
>oder eine JavaFX-Anwendung muss javafx.application.Application erweitern
> ```
{style="warning" title="Fehlende main-Methode"}

> Je nachdem welche <tooltip term="IDE"><format color="%GlossaryLinkColor%">IDE</format></tooltip> verwendet wird und welche Systemsprache eingestellt ist, kann die Fehlermeldung etwas anders aussehen.

## Rückgabetyp {id="return-type"}

Eine Methode hat die Möglichkeit ein Ergebnis an den Methodenaufrufer (engl. method caller) zurückzugeben – hier findet auch das Keyword `return` Anwendung. Der Rückgabewert der zurückgegeben wird, hängt vom Rückgabetyp ab.

> In Java wird eine Methode von einer anderen Methode aufgerufen. Die aufrufende Methode wird als Method Caller (Methodenaufrufer) bezeichnet. Dieser Aufrufer kann das Ergebnis, das von der aufgerufenen Methode zurückgegeben wird, empfangen und weiterverwenden.
> {style="note" title="Method Caller"}

Methoden können sowohl <format color="%LinkColor%">[primitive Datentypen](02-java-data-types.md#primitive-data-types)</format> als auch <format color="%LinkColor%">[Objekte](11-java-objects.md)</format> zurückgeben. Für die primitiven Datentypen werden deren Keywords angegeben, für Referenztypen deren Klassennamen. Falls die Methode nichts zurückgibt, steht im Methodenkopf das Keyword `void`.

Zur direkten Weitergabe kann der Rückgabewert z.B. an eine andere Methode oder eine andere Berechnung übermittelt werden. Alternativ kann dieser auch zwischengespeichert werden, anstatt den Wert erneut zu berechnen.

```Java
public static void main(String[] args) {
    System.out.println(isEven(3));

    boolean b = isEven(6);
    System.out.println(b);
}

public static boolean isEven(int n) {
    if (n % 2 == 0) {
        return true;
    } else {
        return false;
    }
}
```

Durch die `return`-Anweisung ist es möglich eine Methode auch früher zu verlassen. Im folgenden Beispiel erhält die Methode eine Trennzeichenfolge und einen Text. Der Text soll überall dort gesplittet werden, an dessen Stelle dieses Zeichen bzw. diese Zeichenfolge – also der `delimeter` – vorkommt und gibt die getrennten Wörter in einem `String[]` zurück.

Die Methode kann jedoch früher verlassen werden und gibt ein leeres <format color="%LinkColor%">[Array](08-java-arrays.md)</format> zurück, wenn der Text `null`, also nicht vorhanden, oder die Textlänge kleiner oder gleich `0` ist.

```Java
public static String[] splitTextBy(String delimeter, String text) {
    if (text == null || text.length == 0) return new String[0];
    String[] words = text.split(delimeter);
    return words;
}
```

Folgende Methode bekommt einen `String` mit einem Namen übergeben. Die Methode gibt jedoch nichts zurück, sondern gibt stattdessen den Namen mit einem Begrüßungstext auf der Konsole aus.

```Java
public static void printWelcomeMessage(String name) {
    System.out.println("Hello " + name + "!");
}
```

Folgende Methode bekommt eine Zahl übergeben und überprüft, ob diese Zahl gerade ist. Wenn ja, wird `true` zurückgegeben, ansonsten `false`.

```Java
public static boolean isEven(int n) {
    if (n % 2 == 0) {
        return true;
    } else {
        return false;
    }
}
```

Die Methode `isEven()` kann sogar noch vereinfacht werden.

<compare>
    <code-block lang="java">
        public static boolean isEven(int n) {
            if (n % 2 == 0) {
                return true;
            } else {
                return false;
            }
        }
    </code-block>
    <code-block lang="java">
        public static boolean isEven(int n) {
            if (n % 2 == 0) {
                return true;
            }
            return false;
        }
    </code-block>
</compare>

<tabs>
    <tab title="Frage">
        <p>Kann die Methode <code>isEven()</code> noch weiter vereinfacht werden?</p>
    </tab>
    <tab title="Lösung">
        <code-block lang="java">
            public static boolean isEven(int n) {
                return n % 2 == 0;
            }
        </code-block>
    </tab>
</tabs>

## Statischer Methodenaufruf {id="static-method-call"}

```Java
ClassName.methodName(parameter);
```

Um die beiden Methoden aus dem vorherigen Abschnitt aufzurufen, muss folgendes geschrieben werden:

```Java
Main.isEven(4);

printWelcomeMessage("Kesares");
```

Beide Methoden befinden sich in derselben Klasse wie die `main()`-Methode, aus der wir die beiden Methoden aufrufen. Daher kann auf den vorangestellten Klassennamen `Main` verzichtet werden.

> Ein Methodenaufruf über ein <format color="%LinkColor%">[Objekt](11-java-objects.md)</format> muss über den Variablennamen oder das Objekt selbst geschehen.
> ```Java
>String name = "Kesares";
>int length = name.length();
>length = "Kesares".length();
>```

## Methodenüberladung {id="method-overloading"}

Es ist möglich, mehr als eine Methode mit demselben Methodennamen zu schreiben. Jedoch müssen sich die Methoden entweder in der Anzahl der übergebenen Parameter oder – bei gleicher Anzahl – im Parametertyp unterscheiden.

```Java
public void print(int n) {
    System.out.println(n);
}

public void print(double n) {
    System.out.println(n);
}

public void print(int n1, int n2) {
    System.out.println(n1 + n2);
}
```

## Variable Parameteranzahl {id="varargs"}

Seit Java 5 ist es möglich eine beliebige Anzahl von Parametern vom gleichen Typ an eine Methode zu übergeben – auch Vararg genannt. Intern erzeugt Java daraus ein <format color="%LinkColor%">[Array](08-java-arrays.md)</format>, dass für die Weiterverarbeitung verwendet werden kann.

```Java
public static void method1(int... numbers) {
    // Code...
}

public static void method2(String text, boolean b, int... numbers) {
    // Code...
}
```

```Java
public static void main(String[] args) {
    method1(1, 2, 3, 4, 5);
    method2("Hallo Kesares!", true, 1, 2, 3, 4, 5);
}
```

> Nur der <format color="%NoteHighlight%">letzte</format> Methodenparameter darf ein Vararg sein. Der <tooltip term="Compiler"><format color="%GlossaryLinkColor%">Compiler</format></tooltip> kann die Parameter ansonsten nicht eindeutig übergeben.
> {style="note" title="Letzter Parameter als Vararg"}

## Finale Methoden {id="final-methods"}

Finale Methoden werden mit dem Keyword `final` deklariert. Sie können nicht von Kindklassen überschrieben werden. Das Überschreiben von Methoden wird auch als Polymorphie oder <format color="%LinkColor%">[Polymorphismus](14-java-oop.md#polymorphism)</format> bezeichnet und findet nur bei der Vererbung Anwendung. Mehr zum Keyword `final` in <format color="%LinkColor%">[Kapitel 12 – Modifizierer und Zugriffsrechte](12-java-modifier-access-rights.md)</format>.

```Java
public final void print() {
    // Code...
}
```

## Rekursion {id="recursion"}

Eine rekursive Methode ruft sich selbst immer wieder auf, bis ein bestimmter Zustand erreicht ist – vergleichbar mit einer <format color="%LinkColor%">[Schleife](07-java-loops.md)</format>.

```Java
public static void foo() {
    foo();
}
```

> Bei diesem Beispiel gibt es <format color="%WarningHighlight%">keine</format> Abbruchbedingung. D.h. diese Methode wird nie aufhören sich selbst aufzurufen, was in einem `StackOverflowError` resultiert!
> {style="warning" title="StackOverflowError"}

Folgende rekursive Methode berechnet die Quersumme einer übergebenen Zahl `n` und gibt diesen Wert zurück.

```Java
public static int calculateChecksum(int n) {
    if (n <= 0) return 0;
    return n % 10 + calculateChecksum(n / 10);
}
```

> Rekursion ist zwar eine feine Sache, in der Praxis wird diese jedoch oft vermieden und auf iterative Lösungen gesetzt, wenn es darum geht robuste Software zu schreiben.
{style="note"}

![Recursion Meme](09_java_methods_1.jpg){width="400"}

## Die `Math`-Klasse {id="the-math-class"}

Java bringt von Haus aus eine <format color="%LinkColor%">[Klasse](10-java-classes.md)</format> mit, die ausschließlich <format color="%LinkColor%">[statische Methoden](10-java-classes.md#class-methods)</format> für verschiedene Berechnungen besitzt. Die `Math`-Klasse enthält Methoden für beispielsweise das Runden von Kommazahlen, das Finden des Max- oder Min-Wertes, Wurzelberechnung, Zufallszahlen, Berechnung von Cosinus, Sinus und sehr viel mehr.

```Java
@IntrinsicCandidate
public static int abs(int a) {
    return (a < 0) ? -a : a;
}
```

```Java
@IntrinsicCandidate
public static long round(double a) {
    long longBits = Double.doubleToRawLongBits(a);
    long biasedExp = (longBits & DoubleConsts.EXP_BIT_MASK)
            >> (DoubleConsts.SIGNIFICAND_WIDTH - 1);
    long shift = (DoubleConsts.SIGNIFICAND_WIDTH - 2
            + DoubleConsts.EXP_BIAS) - biasedExp;
    if ((shift & -64) == 0) {
        long r = ((longBits & DoubleConsts.SIGNIF_BIT_MASK)
                | (DoubleConsts.SIGNIF_BIT_MASK + 1));
        if (longBits < 0) {
            r = -r;
        }
        return ((r >> shift) + 1) >> 1;
    } else {
        return (long) a;
    }
}
```

```Java
@IntrinsicCandidate
public static double pow(double a, double b) {
    return StrictMath.pow(a, b);
}
```

> Die <format color="%LinkColor%">[Klasse](10-java-classes.md)</format> ist Teil des `java.lang`-Package und muss daher nicht selbst <format color="%LinkColor%">[importiert](16-java-packages-and-imports.md)</format> werden.

## Call by Value vs. Call by Reference {id="call-by-value-or-reference"}

Wenn eine Methode mit <format color="%Highlight%">Call-by-Value</format> aufgerufen wird, wird der Wert an diese Methode übergeben. Innerhalb der Methode wird eine Kopie des Werts erstellt und verwendet. Änderungen, die innerhalb der Methode am Parameter vorgenommen werden, wirken sich nicht auf die ursprüngliche <format color="%LinkColor%">[Variable](03-java-variables.md)</format> außerhalb der Methode aus. Dies ist der Standard für <format color="%LinkColor%">[primitive Datentypen](02-java-data-types.md#primitive-data-types)</format> in vielen Programmiersprachen, einschließlich Java.

Beim <format color="%Highlight%">Call-by-Reference</format> wird eine Referenz (ein Zeiger) auf die ursprüngliche <format color="%LinkColor%">[Variable](03-java-variables.md)</format> an die Funktion übergeben. Das bedeutet, dass die Funktion direkt auf die ursprüngliche Variable zugreift. Änderungen, die innerhalb der Funktion am Parameter vorgenommen werden, wirken sich direkt auf die ursprüngliche Variable aus.

In Programmiersprachen wie C++ kann explizit <format color="%Highlight%">Call-by-Reference</format> verwendet werden. In Java gibt es kein echtes <format color="%Highlight%">Call-by-Reference</format>. Es gibt jedoch ein ähnliches Verhalten bei der Übergabe von <format color="%LinkColor%">[Objektreferenzen](11-java-objects.md)</format>.

Java verwendet ausschließlich <format color="%Highlight%">Call-by-Value</format> für die Übergabe von <format color="%LinkColor%">[Variablen](03-java-variables.md)</format>. Aber bei <format color="%LinkColor%">[Objekten](11-java-objects.md)</format> wird eine Kopie der Referenz (also der Speicheradresse des Objekts) übergeben, nicht das Objekt selbst. Dies führt zu einem Verhalten, das ähnlich wie <format color="%Highlight%">Call-by-Reference</format> erscheint, wenn mit Objekten gearbeitet wird.

## Coding Conventions {id="coding-conventions"}

- Methoden sollten mit einem Verb beginnen (`calculate`, `print`, `remove` etc.).
- Methoden, die einen Rückgabewert vom Typ `boolean` aufweisen, sollten nach Möglichkeit mit `is` beginnen. Alternativ kann auch auf `has` zurückgegriffen werden.
- Methoden sollten nach der <tooltip term="CamelCase-Notation"><format color="%GlossaryLinkColor%">CamelCase-Notation</format></tooltip> geschrieben werden.

```Java
double getAverageOf(int[] nums) {}
void printText(String text) {}
void removeBuffsFromPlayer(Player player) {}
boolean hasEffects() {}
```

## Übung {id="exercise"}

Erweitert den Taschenrechner mit dem Wissen aus diesem Kapitel um eine Methode, die die Berechnung durchführt und auf der Konsole ausgibt.

<tabs>
    <tab title="Aufgabe">
        <note title="Taschenrechner">
            Fügt eine Methode <code>printCalculations()</code> zum Taschenrechner hinzu, welche drei <code>int</code>-Werte als Parameter erwartet.
            <code>x</code> und <code>y</code> stehen für die Werte, die miteinander verrechnet werden sollen. Welche Berechnung ausgeführt wird, ist von der Variablen <code>option</code> abhängig.
        </note>
    </tab>
    <tab title="Mögliche Lösung">
        <code-block lang="java">
            public static void main(String[] args) {
                Scanner sc = new Scanner(System.in);  
                boolean isRunning = true;
                while (isRunning) {}
                    System.out.print("1st number: ");  
                    int x = sc.nextInt();  
                    System.out.print("2nd number: ");  
                    int y = sc.nextInt();  
                    System.out.print("""
                        =================
                        1: Addition
                        2: Subtraction
                        3: Multiplication
                        4: Division
                        =================
                        Option:\s""");
                    int option = sc.nextInt();
                    printCalculations(x, y, option);
                    System.out.println("Should another calculation be performed?");
                    String keepGoing = sc.next();
                    if (!keepGoing.equalsIgnoreCase("y")) {  
                        isRunning = false;  
                    }
                } 
                System.out.println("Bye.");
                sc.close();
            }
            private static void printCalculations(int x, int y, int option) {  
                switch (option) {  
                    case 1 -> System.out.println(x + " + " + y + " = " + (x + y));
                    case 2 -> System.out.println(x + " - " + y + " = " + (x - y));
                    case 3 -> System.out.println(x + " * " + y + " = " + (x * y));
                    case 4 -> System.out.println(x + " / " + y + " = " + (x / y));
                    default -> System.out.println("This option does not exist.");  
               }  
            }
        </code-block>
    </tab>
</tabs>