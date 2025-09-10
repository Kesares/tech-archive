# 06 Java – Verzweigungen

<p>Verzweigungen (eng. branches) können den Programmverlauf ändern. Welche Code-Teile ausgeführt werden, hängt von den
Bedingungen (eng. conditions) ab. Java bietet drei Sprachkonstrukte, um Verzweigungen realisieren zu können.</p>

<list>
  <li><p><format color="%c1%"><a href="#if-else">if-else</a></format></p></li>
  <li><p><format color="%c2%"><a href="#switch-case">switch-case</a></format></p></li>
  <li><p><format color="%c3%"><a href="#ternary-operator">Ternäre Operator</a></format></p></li>
</list>

## <format color="%c1%">if-else</format> {id="if-else"}

<p>Das am häufigsten verwendete Sprachkonstrukt ist <code>if</code>-<code>else</code>. Hier kommen die Keywords
<code>if</code> und <code>else</code> zum Einsatz. Eine <code>if</code>-Abfrage beginnt mit dem Keyword <code>if</code>
 gefolgt von der Bedingung und der Blockanweisung die ausgeführt wird, wenn die Condition <code>true</code> ergibt.</p>

<code-block lang="java">
    if (condition) {
        // Code...
    }
</code-block>

<code-block lang="java">
    int n = 7;
    if (n &lt;= 10) {
        System.out.println("n is less than or equal to 10!");
    }
</code-block>

<p>Mehrstufige Verzweigungen sind mit <code>else if</code> möglich. Dadurch wird der zutreffende Block ausgeführt und
alle weiteren übersprungen.</p>

<code-block lang="java">
    int n = 7;
    if (n &lt;= 10) {
        System.out.println("n is less than or equal to 10!");
    } else if (n &lt;= 20) {
        System.out.println("n is less than or equal to 20!");
    }
</code-block>

<p>Der <code>else</code>-Block bietet einen alternativen Code-Block, der ausgeführt wird, wenn alle vorherigen
Bedingungen nicht zutreffen.</p>

<code-block lang="java">
    int n = 7;
    if (n &lt;= 10) {
        System.out.println("n is less than or equal to 10!");
    } else if (n &lt;= 20) {
        System.out.println("n is less than or equal to 20!");
    } else {
        System.out.println("n is greater than 20!!");
    }
</code-block>

<p>Die Reihenfolge ist zu beachten. Würde die <code>n &lt;= 20</code>-Abfrage wie im Folgenden an erster Stelle stehen,
würde die Blockanweisung mit der Bedingung <code>n &lt;= 10</code> niemals ausgeführt werden.</p>

<code-block lang="java">
    int n = 7;
    if (n &lt;= 20) {
        System.out.println("n is less than or equal to 20!");
    } else if (n &lt;= 10) {
        System.out.println("n is less than or equal to 10!");
    } else {
        System.out.println("n is greater than 20!");
    }
</code-block>

<p>Die geschweiften Klammern können weggelassen werden, wenn nur eine Anweisung auf die Bedingung folgt.</p>

<code-block lang="java">
    int n = 7;
    if (n &lt;= 10) 
        System.out.println("n is less than or equal to 10!");
</code-block>

<p>Zu beachten ist, dass im folgenden Beispiel die zweite Ausgabe immer ausgeführt wird. Nur die erste Anweisung ohne
die geschweiften Klammern besteht in Abhängigkeit zur Bedingung.</p>

<code-block lang="java">
    int n = 7;
    if (n &lt;= 10) 
        System.out.println("n is less than or equal to 10!");
    System.out.println("n = " + n);
</code-block>

<p>Bedingungen können auch verknüpft werden.</p>

<code-block lang="java">
    int n = 13;
    if (n &gt;= 10 && &lt; 20) {
        System.out.println("n is between 10 and 20!");
    }
</code-block>

<p>Auch die Negierung von Bedingungen ist möglich.</p>

<code-block lang="java">
    int n = 7;
    if (!(n &gt;= 10 && &lt; 20)) {
        System.out.println("n isn't between 10 and 20!");
    }
</code-block>

## <format color="%c2%">switch-case</format> {id="switch-case"}

<p>Eine Alternative zu <format color="%c1%">if-else</format> ist das <code>switch</code>-<code>case</code>-Konstrukt.
Diese bietet sich als Kurzform gerade für speziell angehäufte <code>if</code>-Abfragen an. Verwendete Keywords sind
<code>switch</code>, <code>case</code>, <code>default</code> und <code>break</code>.</p>

<p>Das <code>switch</code>-<code>case</code>-Konstrukt erlaubt die Überprüfung von:</p>

<list>
  <li><p><format color="%LinkColor%"><a href="02-java-data-types.md#integers">Ganzzahlen</a></format></p></li>
  <li><p><format color="%LinkColor%"><a href="05-java-strings.md">Strings</a></format></p></li>
  <li><p><tooltip term="Wrapper-Class"><format color="%GlossaryLinkColor%">Wrapper-Typen</format></tooltip> (nur,
    <code>Byte</code>, <code>Short</code>. <code>Integer</code>, <code>Long</code>)</p></li>
  <li><p><format color="%LinkColor%"><a href="13-java-enumerations.md">Enumerationen</a></format></p></li>
  <li><p><format color="%LinkColor%"><a href="14-java-oop.md#sealed-classes-and-interfaces">Versiegelte Klassen</a>
    </format> (Ab Java 17)</p></li>
</list>

### <format color="%c2%">switch-case vs. if-else</format> {id="if-else-vs-switch-case"}

<p>Die einzelnen Cases müssen mit einer <code>break</code>-Anweisung beendet werden. Ansonsten wird auch der
nachfolgende Case ausgeführt.</p>

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

<p>Seit Java 12 gab es einige Änderungen und syntaktische Anpassungen, welche in Java 13 nochmal verändert und in
Java 14 fest integriert wurden. Es ist nun möglich mehrere Ausdrücke für einen Case durch Kommas getrennt
zusammenzufassen.</p>

<code-block lang="java">
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
</code-block>

<p>Seit Java 14 ist nun auch die folgende Syntax möglich. Implizit beendet ein <code>break</code> den Anweisungsblock.
Daher muss dieser nicht selbst hinzugefügt werden.</p>

<code-block lang="java">
    int option = 2;
    switch (option) {
        case 1 -&gt; {
            System.out.println("Option 1 was chosen.");
        }
        case 2 -&gt; {
            System.out.println("Option 2 was chosen.");
        }
        case 3 -&gt; {
            System.out.println("Option 3 was chosen.");
        }
        default -&gt; {
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
            case 1 -&gt; System.out.println("Option 1 was chosen.");
            case 2 -&gt; System.out.println("Option 2 was chosen.");
            case 3 -&gt; System.out.println("Option 3 was chosen.");
            default -&gt; System.out.println("This option doesn't exist.");
        }
    </code-block>
</compare>

<tip>
    <p>Der Pfeil ähnelt einem <format color="%Highlight%">Lambda-Ausdruck</format>, hat aber in diesem Fall nichts damit
    zu tun.</p>
</tip>

#### <format color="%c2%">switch case –</format> `yield` {id="switch-case-yield"}

<p>Anweisungen liefern normalerweise keinen Rückgabewert. Seit Java 14 ist auch dies möglich.</p>

<code-block lang="java">
    int monthNumber = 3;
    String month = switch (monthNumber) {
        case 1 -&gt; "January";
        case 2 -&gt; "February";
        case 3 -&gt; "March";
        case 4 -&gt; "April";
        case 5 -&gt; "May";
        case 6 -&gt; "June";
        case 7 -&gt; "July";
        case 8 -&gt; "August";
        case 9 -&gt; "September";
        case 10 -&gt; "October";
        case 11 -&gt; "November";
        case 12 -&gt; "December";
        default -&gt; "Unknown month";
    };
    System.out.println(month); // March
</code-block>

<p>Wird in solchen Fällen mit Blockanweisungen gearbeitet, muss auch dieser Block ein Ergebnis zurückliefern. Hier kommt
das Contextual Keyword <code>yield</code> ins Spiel. Dieses findet nur in
<code>switch</code>-<code>case</code>-Konstrukten Anwendung.</p>

<code-block lang="java">
    int monthNumber = 3;  
    String month = switch (monthNumber) {  
        case 1 -&gt; "January";  
        case 2 -&gt; "February";  
        case 3 -&gt; {  
           System.out.println("March was chosen.");  
           yield "March";  
        }  
        case 4 &gt; "April";  
        case 5 -&gt; "May";  
        case 6 -&gt; "June";  
        case 7 -&gt; "July";  
        case 8 -&gt; "August";  
        case 9 -&gt; "September";  
        case 10 -&gt; "October";  
        case 11 -&gt; "November";  
        case 12 -&gt; "December";  
        default -&gt; "Unknown month";  
    };
    System.out.println(month); // March
</code-block>

### <format color="%c2%">switch-case mit versiegelten Klassen</format> {id="switch-case-sealed-classes"}

<p>Mit dem Konzept der
<format color="%LinkColor%"><a href="14-java-oop.md#sealed-classes-and-interfaces">versiegelten Klassen</a></format>
 (sealed classes), das ab Java 15 eingeführt und mit Java 17 finalisiert wurde, gibt es eine enge Integration mit
<code>switch</code>. Wenn eine <format color="%LinkColor%"><a href="10-java-classes.md">Klasse</a></format> als
<code>sealed</code> deklariert ist und nur eine festgelegte Gruppe von Unterklassen besitzt, kann ein
<code>switch</code> auf <format color="%LinkColor%"><a href="11-java-objects.md">Objekte</a></format> dieser Klasse
garantieren, dass alle möglichen Unterklassen abgedeckt sind.</p>

<code-block lang="java">
public sealed interface Shape permits Circle, Rectangle, Triangle {}

public final class Circle implements Shape {}
public final class Rectangle implements Shape {}
public final class Triangle implements Shape {}

public String describeShape(Shape shape) {
    return switch (shape) {
        case Circle c -&gt; "Circle";
        case Rectangle r -&gt; "Rectangle";
        case Triangle t -&gt; "Triangle";
        // No 'default' necessary, since all allowed types are covered.
    };
}
</code-block>

## <format color="%c3%">Ternäre Operator</format> {id="ternary-operator"}

<p>Der ternäre Operator ist der einzige Operator, der 3 Operanden verwendet. Er wird häufig angewendet um schnell den
einen oder anderen Ausdruck zu berechnen, da er in einer Zeile geschrieben werden kann. Der
<format color="%LinkColor%">[Operator](01-java-token.md#operators)</format> besteht aus <code>?</code> und
<code>:</code>.</p>

<code-block>
    condition ? expression, if true : expression, if false
</code-block>

<tip>
    <p>Je nachdem, welche Operationen ausgewertet werden sollen, kann der ternäre Operator sehr lang werden.</p>
</tip>

<p>Im folgenden Beispiel wird einmal <format color="%c1%">if-else</format> und einmal der
<format color="%c3%">ternäre Operator</format> verwendet, um den Maximalwert zu bestimmen.</p>

<compare first-title="if-else" second-title="Ternäre Operator">
    <code-block lang="java">
        int x = 7;
        int y = 13;
        int max = 0;
        if (x &gt; y) {
            max = x;
        } else {
            max = y;
        }
    </code-block>
    <code-block lang="java">
        int x = 7;
        int y = 13;
        int max = x &gt; y ? x : y;
    </code-block>
</compare>

## Kurzschlussauswertung {id="short-circuit-evaluation"}

<p>Die Kurzschlussauswertung (eng. short-circuit evaluation) beschreibt den Abbruch der Auswertung auf der rechten
Seite, wenn das Endergebnis bereits feststeht. Mit anderen Worten: Eine Auswertung, die nicht (mehr) benötigt wird, wird
nicht evaluiert.</p>

<p>Es gibt nur zwei <format color="%LinkColor%"><a href="01-java-token.md#operators">Operatoren</a></format> die diese
Auswertung unterstützen.</p>

<table>
    <tr>
        <td>Operator</td>
        <td>Bezeichnung</td>
        <td>Beschreibung</td>
    </tr>
    <tr>
        <td><code>&&</code></td>
        <td>Logisches Und</td>
        <td>Die Auswertung endet, sobald das erste Teilergebnis <code>false</code> ergibt. Das Gesamtergebnis ist dann
        zwingend <code>false</code>.</td>
    </tr>
    <tr>
        <td><code>||</code></td>
        <td>Logisches Oder</td>
        <td>Die Auswertung endet, sobald das erste Teilergebnis <code>true</code> ergibt. Das Gesamtergebnis ist dann
        zwingend <code>true</code>.</td>
    </tr>
</table>

<code-block lang="java">
    int x = 1;
    int y = 10;
    
    if (x == 0 && y == 12) {
        // Code...
    }
</code-block>

<p>Da hier eine UND-Verknüpfung besteht, muss sowohl die linke als auch die rechte Auswertung <code>true</code> ergeben,
damit die Blockanweisung ausgeführt wird. <code>x == 0</code> ergibt hier jedoch <code>false</code>. Damit wird der
rechte Teil nicht mehr evaluiert, da das Gesamtergebnis bereits feststeht.</p>

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

<note>
    <p>Etwas tiefgehendere Informationen über die <format color="%NoteHighlight%">Short-Circuit Evaluation</format>, die
    logischen Operatoren <code>&&</code> und <code>||</code> und den bitweisen Operatoren <code>&</code> und
    <code>|</code> könnt ihr in diesem interessanten Artikel
    <format color="%NoteHighlight%"><a href="https://pvs-studio.com/en/blog/posts/java/1135/?ref=dailydev">
    "Bitwise operators in Java: unpacking ambiguities"</a></format> finden.</p>
</note>

## Assertions {id="assertions"}

<p>Assertions sind eine Methode zur Laufzeitüberprüfung von Annahmen, die ein Entwickler während der Implementierung
seines Codes macht und dazu dienen, potenzielle Fehler während der Entwicklungsphase zu erkennen.</p>

<code-block lang="java">
    int n = 13;
    assert n &lt; 10;
</code-block>

<p>Assertions können sowohl mit als auch ohne zusätzliche Meldung geschrieben werden.</p>

<code-block lang="java">
    int n = 13;
    assert n &lt; 10 : "n is not less than 10";
</code-block>

<p>Ist eine Bedingung nicht erfüllt, wird ein Error ausgegeben – speziell ein <code>AssertionError</code>.</p>

<warning>
    <code-block>
        Exception in thread "main" java.lang.AssertionError: n is not less than 10
        at kesares.techarchive.Main.main(Main.java:11)
    </code-block>
</warning>

<p>Assertions müssen explizit aktiviert werden, um sie nutzen zu können. Dabei muss beim Programmstart der
<tooltip term="JVM"><format color="%GlossaryLinkColor%">JVM</format></tooltip> als Argument <code>-ea</code> übergeben
werden, was für <code>enable assertions</code> steht. Standardmäßig sind diese deaktiviert, da sie den eigentlichen
Programmfluss verlangsamen können.</p>

### Aktivierung von Assertions {id="activating-assertions"}

<tabs group="enable-assertions">
    <tab id="enable-assertion-intellij" title="IntelliJ IDEA">
        <list>
            <li><ui-path>Current File</ui-path> am oberen Fensterrand. Alternativ <ui-path>Main Menu | Run</ui-path> am
            linken oberen Fensterrand.</li>
            <li><ui-path>Edit Configurations</ui-path></li>
            <li><ui-path>+</ui-path> bzw. <ui-path>Add New Configuration</ui-path> links oben.</li>
            <li><ui-path>Application</ui-path></li>
            <li>Wählt einen Namen für diese Applikation.</li>
            <li>Wählt die Main-Klasse mit der <code>main</code>-Methode der Applikation unter dem Writer
                <ui-path>Build and run</ui-path>.</li>
            <li><ui-path>Okay | Modify options | Add VM options</ui-path></li>
            <li>Fügt <code>-ea</code> in das Feld <ui-path>VM options</ui-path> hinzu.</li>
            <li><ui-path>Okay | Run Main</ui-path></li>
        </list>
        <note>
            <p>Vorgehensweise durchgeführt mit <format color="%NoteHighlight%">IntelliJ IDEA Ultimate 2024.2</format>.
            </p>
            <p>In anderen Versionen möglicherweise (leicht) veränderte Vorgehensweise.</p>
        </note>
    </tab>
</tabs>

## Übung {id="exercise"}

<p>Erweitern wir unseren Taschenrechner mit einigen Abfragen und dem Wissen aus
<format color="%Highlight%"><a href="05-java-strings.md">Kapitel 5 – Zeichenketten</a></format>, um nur das Ergebnis
einer bestimmten Berechnung auszugeben.</p>

<tabs group="task">
    <tab id="task-task" title="Aufgabe">
        <note title="Taschenrechner">
            <p>Erweitert den Taschenrechner aus
            <format color="%NoteLinkColor%"><a href="04-java-io.md#exercise">Kapitel 4 – Ein- und Ausgaben</a></format>
            so, dass nur das Ergebnis einer Operation auf der Konsole ausgegeben wird. Tipp: Ein Menü könnte hilfreich
            sein.</p>
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
                    case 1 -&gt; System.out.println(x + " + " + y + " = " + (x + y));
                    case 2 -&gt; System.out.println(x + " - " + y + " = " + (x - y));
                    case 3 -&gt; System.out.println(x + " * " + y + " = " + (x * y));
                    case 4 -&gt; System.out.println(x + " / " + y + " = " + (x / y));
                    default &gt; System.out.println("This option doesn't exist.");
                }  
                sc.close();
            }
        </code-block>
    </tab>
</tabs>