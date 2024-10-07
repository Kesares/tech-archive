# 06 Java – Verzweigungen

Verzweigungen (engl. Branches) können den Programmverlauf ändern. Welche Code-Teile ausgeführt werden, hängt von den Bedingungen (engl. Conditions) ab. Java bietet drei Sprachkonstrukte um Verzweigungen realisieren zu können.

- <format color="%c1%">[if-else](#if-else)</format>
- <format color="%c2%">[switch-case](#switch-case)</format>
- <format color="%c3%">[Ternäre Operator](#ternary-operator)</format>

## <format color="%c1%">if-else</format> {id="if-else"}

Das am häufigsten verwendete Sprachkonstrukt ist `if`-`else`. Hier kommen die Keywords `if` und `else` zum Einsatz. Eine `if`-Abfrage beginnt mit dem Keyword `if` gefolgt von der Bedingung und der Blockanweisung die ausgeführt wird, wenn die Condition `true` ergibt.

```Java
if (condition) {
    // Code...
}
```

```Java
int n = 7;
if (n <= 10) {
    System.out.println("n is less than or equal to 10!");
}
```

Mehrstufige Verzweigungen sind mit `else if` möglich. Dadurch wird der zutreffende Block ausgeführt und alle weiteren übersprungen.

```Java
int n = 7;
if (n <= 10) {
    System.out.println("n is less than or equal to 10!");
} else if (n <= 20) {
    System.out.println("n is less than or equal to 20!");
}
```

Der `else`-Block bietet einen alternativen Code-Block, der ausgeführt wird, wenn alle vorherigen Bedingungen nicht zutreffen.

```Java
int n = 7;
if (n <= 10) {
    System.out.println("n is less than or equal to 10!");
} else if (n <= 20) {
    System.out.println("n is less than or equal to 20!");
} else {
    System.out.println("n is greater than 20!!");
}
```

Die Reihenfolge ist zu beachten. Würde die `n <= 20`-Abfrage wie im Folgenden an erster Stelle stehen, würde die Blockanweisung mit der Bedingung `n <= 10` niemals ausgeführt werden.

```Java
int n = 7;
if (n <= 20) {
    System.out.println("n is less than or equal to 20!");
} else if (n <= 10) {
    System.out.println("n is less than or equal to 10!");
} else {
    System.out.println("n is greater than 20!");
}
```

Die geschweiften Klammern können weggelassen werden, wenn nur eine Anweisung auf die Bedingung folgt.

```Java
int n = 7;
if (n <= 10) 
    System.out.println("n is less than or equal to 10!");
```

Zu beachten ist, dass im folgenden Beispiel die zweite Ausgabe immer ausgeführt wird. Nur die erste Anweisung ohne die geschweiften Klammern besteht in Abhängigkeit zur Bedingung.

```Java
int n = 7;
if (n <= 10) 
    System.out.println("n is less than or equal to 10!");
System.out.println("n = " + n);
```

Bedingungen können auch verknüpft werden.

```Java
int n = 13;
if (n >= 10 && < 20) {
    System.out.println("n is between 10 and 20!");
}
```

Auch die Negierung von Bedingungen ist möglich.

```Java
int n = 7;
if (!(n >= 10 && < 20)) {
    System.out.println("n isn't between 10 and 20!");
}
```

## <format color="%c2%">switch-case</format> {id="switch-case"}

Eine Alternative zu <format color="%c1%">if-else</format> ist das `switch`-`case`-Konstrukt. Diese bietet sich als Kurzform gerade für speziell angehäufte `if`-Abfragen an. Verwendete Keywords sind `switch`, `case`, `default` und `break`.

Das `switch`-`case`-Konstrukt erlaubt die Überprüfung von:
- <format color="%LinkColor%">[Ganzzahlen](02-java-data-types.md#integers)</format>
- <format color="%LinkColor%">[Strings](05-java-strings.md)</format>
- <tooltip term="Wrapper-Class"><format color="%GlossaryLinkColor%">Wrapper-Typen</format></tooltip> (nur, `Byte`, `Short`. `Integer`, `Long`)
- <format color="%LinkColor%">[Enumerationen](13-java-enumerations.md)</format>
- <format color="%LinkColor%">[Versiegelte Klassen](14-java-oop.md)</format> (Ab Java 17)

### <format color="%c2%">switch-case vs. if-else</format> {id="if-else-vs-switch-case"}

Die einzelnen Cases müssen mit einer `break`-Anweisung beendet werden. Ansonsten wird auch der nachfolgende Case ausgeführt.

<compare first-title="if-else" second-title="switch-case">
    <code-block lang="java">
        int option = 2;
        if (option == 1) {
            System.out.println("Option 1 was chosen.");
        } else if (option == 2) {
            System.out.println("Option 2 was chosen.");
        } else if (option == 3) {
            System.out.println("Option 3 was chosen.);
        } else {
            System.out.println("This option doesn't exist.");
        }
    </code-block>
    <code-block lang="java">
        int option = 2;
        switch (option) {
            case 1:
                System.out.println("Option 1 was chosen.");
                break;
            case 2:
                System.out.println("Option 2 was chosen.");
                break;
            case 3:
                System.out.println("Option 3 was chosen.");
                break;
            default:
                System.out.println("This option doesn't exist.");
        }
    </code-block>
</compare>

### <format color="%c2%">Syntaktische Änderungen in Java 12, 13 und 14</format> {id="syntactic-changes"}

Seit Java 12 gab es einige Änderungen und syntaktische Anpassungen, welche in Java 13 nochmal verändert und in Java 14 fest integriert wurden. Es ist nun möglich mehrere Ausdrücke für einen Case durch Kommas getrennt zusammenzufassen.

```Java
int option = 2;
switch (option) {
    case 1:
        System.out.println("Option 1 was chosen.");
        break;
    case 2, 3:
        System.out.println("Option 2 or 3 was chosen.");
        break;
    default:
        System.out.println("This option doesn't exist.");
}
```

Seit Java 14 ist nun auch die folgende Syntax möglich. Implizit beendet ein `break` den Anweisungsblock. Daher muss dieser nicht selbst hinzugefügt werden.

<code-block lang="java">
int option = 2;
switch (option) {
    case 1 -> {
        System.out.println("Option 1 was chosen.");
    }
    case 2 -> {
        System.out.println("Option 2 was chosen.");
    }
    case 3 -> {
        System.out.println("Option 3 was chosen.");
    }
    default -> {
        System.out.println("This option doesn't exist.");
    }
}
</code-block>

Auch hier können die Klammern bei einzelnen Anweisungen weggelassen werden.

<compare>
    <code-block lang="java">
        int option = 2;
        switch (option) {
            case 1:
                System.out.println("Option 1 was chosen.");
                break;
            case 2:
                System.out.println("Option 2 was chosen.");
                break;
            case 3:
                System.out.println("Option 3 was chosen.");
                break;
            default:
                System.out.println("This option doesn't exist.");
        }
    </code-block>
    <code-block lang="java">
        int option = 2;
        switch (option) {
            case 1 -> System.out.println("Option 1 was chosen.");
            case 2 -> System.out.println("Option 2 was chosen.");
            case 3 -> System.out.println("Option 3 was chosen.");
            default -> System.out.println("This option doesn't exist.");
        }
    </code-block>
</compare>

> Der Pfeil ähnelt einem <format color="%Highlight%">Lambda-Ausdruck</format>, hat aber in diesem Fall nichts damit zu tun.

#### <format color="%c2%">switch case –</format> `yield` {id="switch-case-yield"}

Anweisungen liefern normalerweise keinen Rückgabewert. Seit Java 14 ist auch dies möglich.

```Java
int monthNumber = 3;
String month = switch (monthNumber) {
    case 1 -> "January";
    case 2 -> "February";
    case 3 -> "March";
    case 4 -> "April";
    case 5 -> "May";
    case 6 -> "June";
    case 7 -> "July";
    case 8 -> "August";
    case 9 -> "September";
    case 10 -> "October";
    case 11 -> "November";
    case 12 -> "December";
    default -> "Unknown month";
};
System.out.println(month); // March
```

Wird in solchen Fällen mit Blockanweisungen gearbeitet, muss auch dieser Block ein Ergebnis zurückliefern. Hier kommt das Contextual Keyword `yield` ins Spiel. Dieses findet nur in `switch`-`case`-Konstrukten Anwendung.

```Java
int monthNumber = 3;  
String month = switch (monthNumber) {  
    case 1 -> "January";  
    case 2 -> "February";  
    case 3 -> {  
       System.out.println("March was chosen.");  
       yield "March";  
    }  
    case 4 -> "April";  
    case 5 -> "May";  
    case 6 -> "June";  
    case 7 -> "July";  
    case 8 -> "August";  
    case 9 -> "September";  
    case 10 -> "October";  
    case 11 -> "November";  
    case 12 -> "December";  
    default -> "Unknown month";  
};
System.out.println(month); // March
```

### <format color="%c2%">switch-case mit versiegelten Klassen</format> {id="switch-case-sealed-classes"}

Mit dem Konzept der <format color="%LinkColor%">[versiegelten Klassen](14-java-oop.md#sealed-classes-and-interfaces)</format> (sealed classes), das ab Java 15 eingeführt und mit Java 17 finalisiert wurde, gibt es eine enge Integration mit `switch`. Wenn eine <format color="%LinkColor%">[Klasse](10-java-classes.md)</format> als `sealed` deklariert ist und nur eine festgelegte Gruppe von Unterklassen besitzt, kann ein `switch` auf <format color="%LinkColor%">[Objekte](11-java-objects.md)</format> dieser Klasse garantieren, dass alle möglichen Unterklassen abgedeckt sind.

```Java
public sealed interface Shape permits Circle, Rectangle, Triangle {}

public final class Circle implements Shape {}
public final class Rectangle implements Shape {}
public final class Triangle implements Shape {}

public String describeShape(Shape shape) {
    return switch (shape) {
        case Circle c -> "Circle";
        case Rectangle r -> "Rectangle";
        case Triangle t -> "Triangle";
        // No 'default' necessary, since all allowed types are covered.
    };
}

```

## <format color="%c3%">Ternäre Operator</format> {id="ternary-operator"}

Der ternäre Operator ist der einzige Operator der 3 Operanden verwendet. Er wird häufig angewendet um schnell den einen oder anderen Ausdruck zu berechnen, da er in einer Zeile geschrieben werden kann. Der <format color="%LinkColor%">[Operator](01-java-token.md#operators)</format> besteht aus `?` und `:`.

```
condition ? expression, if true : expression, if false
```

> Je nachdem, welche Operationen ausgewertet werden sollen, kann der ternäre Operator sehr lang werden.

Im folgenden Beispiel wird einmal <format color="%c1%">if-else</format> und einmal der <format color="%c3%">ternäre Operator</format> verwendet, um den Maximalwert zu bestimmen.

<compare first-title="if-else" second-title="Ternäre Operator">
    <code-block lang="java">
        int x = 7;
        int y = 13;
        int max = 0;
        if (x > y) {
            max = x;
        } else {
            max = y;
        }
    </code-block>
    <code-block lang="java">
        int x = 7;
        int y = 13;
        int max = x > y ? x : y;
    </code-block>
</compare>

## Kurzschlussauswertung {id="short-circuit-evaluation"}

Die Kurzschlussauswertung (engl. short-circuit evaluation) beschreibt den Abbruch der Auswertung auf der rechten Seite, wenn das Endergebnis bereits feststeht. Mit anderen Worten: Eine Auswertung die nicht (mehr) benötigt wird, wird nicht evaluiert.

Es gibt nur zwei <format color="%LinkColor%">[Operatoren](01-java-token.md#operators)</format> die diese Auswertung unterstützen.

<table>
    <tr>
        <td>Operator</td>
        <td>Bezeichnung</td>
        <td>Beschreibung</td>
    </tr>
    <tr>
        <td><code>&&</code></td>
        <td>Logisches Und</td>
        <td>Die Auswertung endet, sobald das erste Teilergebnis <code>false</code> ergibt. Das Gesamtergebnis ist dann zwingend <code>false</code>.</td>
    </tr>
    <tr>
        <td><code>||</code></td>
        <td>Logisches Oder</td>
        <td>Die Auswertung endet, sobald das erste Teilergebnis <code>true</code> ergibt. Das Gesamtergebnis ist dann zwingend <code>true</code>.</td>
    </tr>
</table>

```Java
int x = 1;
int y = 10;

if (x == 0 && y == 12) {
    // Code...
}
```

Da hier eine UND-Verknüpfung besteht, muss sowohl die linke als auch die rechte Auswertung `true` ergeben, damit die Blockanweisung ausgeführt wird. `x == 0` ergibt hier jedoch `false`. Damit wird der rechte Teil nicht mehr evaluiert, da das Gesamtergebnis bereits feststeht.

<table>
    <tr>
        <td width="200">Operation mit <code>&&</code></td>
        <td>Auswertung</td>
    </tr>
    <tr>
        <td><code>false && false</code></td>
        <td><code>false</code></td>
    </tr>
    <tr>
        <td><code>false && true</code></td>
         <td><code>false</code></td>
    </tr>
    <tr>
        <td><code>true && false</code></td>
         <td><code>false</code></td>
    </tr>
    <tr>
        <td><code>true && true</code></td>
         <td><code>true</code></td>
    </tr>
</table>

<table>
    <tr>
        <td width="200">Operation mit <code>||</code></td>
        <td>Auswertung</td>
    </tr>
    <tr>
        <td><code>false || false</code></td>
        <td><code>false</code></td>
    </tr>
    <tr>
        <td><code>false || true</code></td>
         <td><code>true</code></td>
    </tr>
    <tr>
        <td><code>true || false</code></td>
         <td><code>true</code></td>
    </tr>
    <tr>
        <td><code>true || true</code></td>
         <td><code>true</code></td>
    </tr>
</table>

> Etwas tiefgehendere Informationen über die <format color="%NoteHighlight%">Short-Circuit Evaluation</format>, die logischen Operatoren `&&` und `||` und den bitweisen Operatoren `&` und `|` könnt ihr in diesem interessanten Artikel "<format color="%NoteHighlight%">[Bitwise operators in Java: unpacking ambiguities](https://pvs-studio.com/en/blog/posts/java/1135/?ref=dailydev)</format>" finden.
{style="note"}

## Assertions {id="assertions"}

Assertions sind eine Methode zur Laufzeitüberprüfung von Annahmen, die ein Entwickler während der Implementierung seines Codes macht und dienen dazu, potenzielle Fehler während der Entwicklungsphase zu erkennen.

```Java
int n = 13;
assert n < 10;
```

Assertions können sowohl mit als auch ohne zusätzliche Meldung geschrieben werden.

```Java
int n = 13;
assert n < 10 : "n is not less than 10";
```

Ist eine Bedingung nicht erfüllt, wird ein Error ausgegeben – speziell ein `AssertionError`.

>```Java
>Exception in thread "main" java.lang.AssertionError: n is not less than 10
>at kesares.techarchive.Main.main(Main.java:11)
>```
{style="warning"}

Assertions müssen explizit aktiviert werden um sie nutzen zu können. Dabei muss beim Programmstart der <tooltip term="JVM"><format color="%GlossaryLinkColor%">JVM</format></tooltip> als Argument `-ea` übergeben werden, was für `enable assertions` steht. Standardmäßig sind diese deaktiviert, da sie den eigentlichen Programmfluss verlangsamen können.

### Aktivierung von Assertions {id="activating-assertions"}

<tabs group="enable-assertions">
    <tab id="enable-assertion-intellij" title="IntelliJ IDEA">
        <list>
            <li><ui-path>Current File</ui-path> am oberen Fensterrand. Alternativ <ui-path>Main Menu | Run</ui-path> am linken oberen Fensterrand.</li>
            <li><ui-path>Edit Configurations</ui-path></li>
            <li><ui-path>+</ui-path> bzw. <ui-path>Add New Configuration</ui-path> links oben.</li>
            <li><ui-path>Application</ui-path></li>
            <li>Wählt einen Namen für diese Applikation.</li>
            <li>Wählt die Main-Klasse mit der <code>main</code>-Methode der Applikation unter dem Writer <ui-path>Build and run</ui-path>.</li>
            <li><ui-path>Okay | Modify options | Add VM options</ui-path></li>
            <li>Fügt <code>-ea</code> in das Feld <ui-path>VM options</ui-path> hinzu.</li>
            <li><ui-path>Okay | Run Main</ui-path></li>
        </list>
        <note>
            <p>Vorgehensweise durchgeführt mit <format color="%NoteHighlight%">IntelliJ IDEA Ultimate 2024.2</format>.</p>
            <p>In anderen Versionen möglicherweise (leicht) veränderte Vorgehensweise.</p>
        </note>
    </tab>
</tabs>

## Übung {id="exercise"}

Erweitern wir unseren Taschenrechner mit einigen Abfragen und dem Wissen aus <format color="%Highlight%">[Kapitel 5 – Zeichenketten](05-java-strings.md)</format>, um nur das Ergebnis einer bestimmten Berechnung auszugeben.

<tabs group="task">
    <tab id="task-task" title="Aufgabe">
        <note title="Taschenrechner">
            Erweitert den Taschenrechner aus <format color="%NoteLinkColor%"><a href="04-java-io.md#exercise">Kapitel 4 – Ein- und Ausgaben</a></format> so, dass nur das Ergebnis einer Operation auf der Konsole ausgegeben wird. Tipp: Ein Menü könnte hilfreich sein.
        </note>
    </tab>
    <tab id="task-solution" title="Mögliche Lösung">
        <code-block lang="java">
            public static void main(String[] args) {
                Scanner sc = new Scanner(System.in);  
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
                switch (option) {
                    case 1 -> System.out.println(x + " + " + y + " = " + (x + y));
                    case 2 -> System.out.println(x + " - " + y + " = " + (x - y));
                    case 3 -> System.out.println(x + " * " + y + " = " + (x * y));
                    case 4 -> System.out.println(x + " / " + y + " = " + (x / y));
                    default -> System.out.println("This option doesn't exist.");
                }  
                sc.close();
            }
        </code-block>
    </tab>
</tabs>