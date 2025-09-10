# 07 Java – Schleifen

<p>Schleifen führen einen bestimmten Code-Abschnitt so lange aus, bis ein bestimmter Zustand erreicht ist. Dieser
Zustand wird hier über eine Bedingung ermittelt. Solange die Bedingung zutrifft, wird der Schleifenrumpf ausgeführt.
Alle Schleifen können die <format color="%LinkColor%"><a href="01-java-token.md#keywords">Keywords</a></format>
<code>break</code> und <code>continue</code> verwenden. Weitere Keywords werden in den jeweiligen Abschnitten
beschrieben. Schleifen können in die folgenden 4 Arten unterteilt werden.</p>

<list>
  <li><p><format color="%c1%"><a href="#for-loop">for-Schleife</a></format></p></li>
  <li><p><format color="%c2%"><a href="#while-loop">while-Schleife</a></format></p></li>
  <li><p><format color="%c3%"><a href="#do-while-loop">do-while-Schleife</a></format></p></li>
  <li><p><format color="%c4%"><a href="#for-each-loop">for-each-Schleife</a></format></p></li>
</list>

## <format color="%c1%">for-Schleife</format> {id="for-loop"}

<p>Die <code>for</code>-Schleife wird auch als Zählschleife bezeichnet. Sie verwendet das
<format color="%LinkColor%"><a href="01-java-token.md#keywords">Keyword</a></format> <code>for</code>. Der Kopf der
Schleife besteht aus 3 Teilen, die durch Semikolons getrennt sind.</p>

<code-block lang="java">
    for (initialization; condition; in- or decrement) {
        // Code...
    }
</code-block>

<table>
    <tr>
        <td>Schleifenteil</td>
        <td>Beschreibung</td>
    </tr>
    <tr>
        <td>Initialisierung</td>
        <td>Hier werden alle Variablen initialisiert, die im Schleifenrumpf benötigt werden.</td>
    </tr>
    <tr>
        <td>Bedingung</td>
        <td>Die Bedingung prüft, ob ein gewisser Zustand erreicht ist. Solange die Bedingung erfüllt ist, wird der
        Schleifenrumpf ausgeführt.</td>
    </tr>
    <tr>
        <td>In- bzw. Dekrement</td>
        <td>Nachdem der Rumpf ausgeführt wurde, wird die Schleifenvariable erhöht oder verringert.</td>
    </tr>
</table>

<p>Folgendes Beispiel zeigt die einfachste Form der <code>for</code>-Schleife, welche die Zahlen von <code>1</code> bis
<code>10</code> auf der Konsole ausgibt.</p>

<code-block lang="java">
    for (int i = 0; i &lt; 10; i++) {
        System.out.println(i);
    }
</code-block>

<list>
  <li><p>Die Variable <code>i</code> wird auf 0 gesetzt.</p></li>
  <li><p>Der Rumpf wird ausgeführt, so lange <code>i</code> kleiner <code>10</code> ist.</p></li>
  <li><p>Nach der Ausführung des Rumpfes wird <code>i</code> jedes Mal um eins erhöht.</p></li>
</list>

<note title="Endlosschleife">
    <p>Folgendes Beispiel ist eine <format color="%NoteHighlight%">gültige</format> Schleife. Diese hat keine Bedingung
    und wird niemals zu einem Abbruch führen. Das Programm muss in solchen Fällen dann zwingend beendet werden.</p>
    <p>Anfängern wird es immer wieder passieren, dass sie unabsichtlich eine
    <format color="%NoteHighlight%">Endlosschleife</format> programmieren. Auch erfahrenen Entwicklern passiert das –
    nur seltener.</p>
    <code-block lang="java">
        for (int i = 0; ; i++) {
             System.out.println(i);
        }
    </code-block>
</note>

## <format color="%c2%">while-Schleife</format> {id="while-loop"}

<p>Die while-Schleife verwendet das <format color="%LinkColor%"><a href="01-java-token.md#keywords">Keyword</a></format>
<code>while</code>.</p>

<code-block lang="java">
    while (condition) {
        // Code...
    }
</code-block>

<p>Solange die Bedingung zutrifft, wird der Rumpf ausgeführt.</p>

<code-block lang="java">
    boolean isRunning = true;
    while (isRunning) {
        // Code...
    }
</code-block>

<p>Jede <code>while</code>-Schleife kann auch als <format color="%c1%">for-Schleife</format> geschrieben werden und
umgekehrt.</p>

<compare first-title="wile-Schleife" second-title="for-Schleife">
    <code-block lang="java">
        int i = 0;
        while (10 > i) {
            System.out.println(i);
            i++;
        }
    </code-block>
    <code-block lang="java">
        for (int i = 0; 10 > i; i++) {
            System.out.println(i);
        }
    </code-block>
</compare>

## <format color="%c3%">do-while-Schleife</format> {id="do-while-loop"}

<p>Die <code>do</code>-<code>while</code>-Schleife funktioniert im Grund genauso wie die
<format color="%c2%">while-Schleife</format>. Der einzige Unterschied besteht darin, dass die Bedingung nach dem
Schleifenrumpf überprüft wird. D. h. der Schleifenrumpf wird immer
<format color="%Highlight%">mindestens einmal</format> ausgeführt. Die Schleife verwendet die
<format color="%LinkColor%"><a href="01-java-token.md#keywords">Keywords</a></format> <code>do</code> und <code></code>.
</p>

<code-block lang="java">
    do {
        // Code...
    } while (condition);
</code-block>

<code-block lang="java">
    boolean isRunning = true;
    do {
        // Code...
    } while (isRunning);
</code-block>

## <format color="%c4%">for-each-Schleife</format> {id="for-each-loop"}

<p>Die <code>for</code>-each oder auch enhanced-<code>for</code>-Schleife ist eine verkürzte Schreibweise der
<format color="%c1%">for-Schleife</format>. Diese kann nur verwendet werden, wenn über
<format color="%LinkColor%"><a href="19-java-collections.md">Collections</a></format> oder
<format color="%LinkColor%"><a href="08-java-arrays.md">Arrays</a></format> iteriert werden soll.</p>

<code-block lang="java">
    for (type identifier : array) {
        // Code...
    }
</code-block>

<code-block lang="java">
    int[] array = {4, 6, 2, 7, 1};
    
    for (int i : array) {
        System.out.println(i);
    }
</code-block>

<p>Die Schleifenvariable <code>i</code> nimmt nacheinander alle Werte des
<format color="%LinkColor%"><a href="08-java-arrays.md">Arrays</a></format> an.</p>

<note title="forEach()-Methode">
    <p>Werden <format color="%NoteLinkColor%"><a href="19-java-collections.md">Collections</a></format> verwendet, kann
    auch auf die passende <code>forEach()</code>-Methode zurückgegriffen werden. Diese verwendet intern die
    <code>for</code>-each-Schleife.</p>
</note>

## `break` & `continue`

<p>Das <format color="%LinkColor%"><a href="01-java-token.md#keywords">Keyword</a></format> <code>break</code> steht für
die Zuständigkeit, eine Schleife an einem bestimmten Punkt vorzeitig zu beenden. Das Keyword <code>continue</code> steht
für die Zuständigkeit, den weiteren Schleifenablauf zu überspringen und mit dem nächsten Schleifendurchlauf
fortzufahren.</p>

<p>Die folgende Schleife gibt alle Zahlen von <code>0</code> bis <code>4</code> auf der Konsole aus, bis <code>i</code>
 die Zahl <code>5</code> enthält. Dann wird die komplette Schleife durch die <code>break</code>-Anweisung abgebrochen.
</p>

<code-block lang="java">
    for (int i = 0; i &lt; 10; i++) {
        if (i == 5) break;
        System.out.println(i);
    }
</code-block>

<p>Die folgende Schleife gibt alle Zahlen von <code>0</code> bis <code>4</code> auf der Konsole aus, bis <code>i</code>
 die Zahl <code>5</code> enthält. Dann wird die Ausgabe übersprungen und mit dem nächsten Schleifendurchlauf
fortgesetzt.</p>

<code-block lang="java">
    for (int i = 0; i &lt; 10; i++) {
        if (i == 5) continue;
        System.out.println(i);
    }
</code-block>

## Geschachtelte Schleifen {id="nested-loops"}

<p>Wie <format color="%LinkColor%"><a href="06-java-branches.md">Verzweigungen</a></format> können auch Schleifen
verschachtelt werden. Folgendes Beispiel gibt das kleine 1x1 in tabellarischer Form auf der Konsole aus.</p>

<code-block lang="java">
    for (int i = 1; i &lt;= 10; i++) {
        for (int j = 1; j &lt;= 10; j++) {
            System.out.print(i * j + "\t");
        }
        System.out.println();
    }
</code-block>

<code-block>
    1	2	3	4	5	6	7	8	9	10	
    2	4	6	8	10	12	14	16	18	20	
    3	6	9	12	15	18	21	24	27	30	
    4	8	12	16	20	24	28	32	36	40	
    5	10	15	20	25	30	35	40	45	50	
    6	12	18	24	30	36	42	48	54	60	
    7	14	21	28	35	42	49	56	63	70	
    8	16	24	32	40	48	56	64	72	80	
    9	18	27	36	45	54	63	72	81	90	
    10	20	30	40	50	60	70	80	90	100	
</code-block>

## break label {id="break-label"}

<p>Es kann vorkommen, dass mit mehreren geschachtelten Schleifen gearbeitet wird. Das
<format color="%LinkColor%"><a href="01-java-token.md#keywords">Keyword</a></format> <code>break</code> beendet immer
nur die innerste Schleife. Soll der Ablauf der äußeren Schleife abgebrochen werden, kann dafür ein gelabeltes
<code>break</code> verwendet werden.</p>

<code-block lang="java">
    label:
    for (int i = 1; i &lt;= 10; i++) {
        for (int j = 1; j &lt;= 10; j++) {
            System.out.print(i * j + "\t");
            if (i * j &gt;= 50) {
                break label;
            }
        }
        System.out.println();
    }
</code-block>

<p>Ergibt das erste Ergebnis beim kleinen 1x1 eine Zahl, die größer oder gleich <code>50</code> ist, wird das
<code>label</code> gebrochen und die äußerste Schleife bricht ab. Dadurch wird in diesem Fall nur die erste Hälfte des
kleinen 1x1 ausgegeben. <code>label</code> ist hier ein
<format color="%LinkColor%"><a href="01-java-token.md#identifier">Identifier</a></format> und kann auch anders benannt
werden.</p>

## Übung {id="exercise"}

<p>Erweitert den Taschenrechner um eine Schleife. Das Programm soll nach jedem Ergebnis nach einer weiteren Berechnung
fragen.</p>

<tabs group="task">
    <tab id="task-task" title="Aufgabe">
        <note title="Taschenrechner">
            Erweitert den Taschenrechner so, dass das Programm beendet wird, wenn der User etwas anderes als <code>j</code> eingibt.
        </note>
    </tab>
    <tab id="task-solution" title="Mögliche Lösung">
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
                    switch (option) {
                        case 1 -> System.out.println(x + " + " + y + " = " + (x + y));
                        case 2 -> System.out.println(x + " - " + y + " = " + (x - y));
                        case 3 -> System.out.println(x + " * " + y + " = " + (x * y));
                        case 4 -> System.out.println(x + " / " + y + " = " + (x / y));
                        default -> System.out.println("This option doesn't exist.");
                    } 
                    System.out.println("Should another calculation be performed?");
                    String keepGoing = sc.next();
                    if (!keepGoing.equalsIgnoreCase("y")) {  
                        isRunning = false;  
                    }
                } 
                System.out.println("Bye.");
                sc.close();
            }
        </code-block>
    </tab>
</tabs>