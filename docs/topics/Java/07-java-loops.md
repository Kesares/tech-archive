# 07 Java Schleifen

Schleifen führen einen bestimmten Code-Abschnitt so lange aus, bis ein bestimmter Zustand erreicht ist. Dieser Zustand wird hier über eine Bedingung ermittelt. Solange die Bedingung zutrifft, wird der Schleifenrumpf ausgeführt. Alle Schleifen können die <format color="%LinkColor%">[Keywords](01-java-token.md#keywords)</format> `break` und `continue` verwenden. Weitere Keywords werden in den jeweiligen Abschnitten beschrieben. Schleifen können in die folgenden 4 Arten unterteilt werden.

- <format color="%c1%">[for-Schleife](#for-loop)</format>
- <format color="%c2%">[while-Schleife](#while-loop)</format>
- <format color="%c3%">[do-while-Schleife](#do-while-loop)</format>
- <format color="%c4%">[for-each-Schleife](#for-each-loop)</format>

## <format color="%c1%">for-Schleife</format> {id="for-loop"}

Die `for`-Schleife wird auch als Zählschleife bezeichnet. Sie verwendet das <format color="%LinkColor%">[Keyword](01-java-token.md#keywords)</format> `for`. Der Kopf der Schleife besteht aus 3 Teilen, die durch Semikolons getrennt sind.

```Java
for (inizialisation; condition; in- or decrement) {
    // Code...
}
```

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
        <td>Die Bedingung prüft, ob ein gewisser Zustand erreicht ist. Solange die Bedingung erfüllt ist, wird der Schleifenrumpf ausgeführt.</td>
    </tr>
    <tr>
        <td>In- bzw. Dekrement</td>
        <td>Nachdem der Rumpf ausgeführt wurde, wird die Schleifenvariable erhöht oder verringert.</td>
    </tr>
</table>

Folgendes Beispiel zeigt die einfachste Form der `for`-Schleife, welche die Zahlen von `1` bis `10` auf der Konsole ausgibt.

```Java
for (int i = 0; i < 10; i++) {
    System.out.println(i);
}
```

- Die Variable `i` wird auf 0 gesetzt.
- Der Rumpf wird ausgeführt, so lange `i` kleiner `10` ist.
- Nach der Ausführung des Rumpfes wird `i` jedes Mal um eins erhöht.

> Folgendes Beispiel ist eine <format color="%NoteHighlight%">gültige</format> Schleife. Diese hat keine Bedingung und wird niemals zu einem Abbruch führen. Das Programm muss in solchen Fällen dann zwingend beendet werden.
>
> Anfängern wird es immer wieder passieren, dass sie unabsichtlich eine <format color="%NoteHighlight%">Endlosschleife</format> programmieren. Auch erfahrenen Entwicklern passiert das – nur seltener.
>```Java
>for (int i = 0; ; i++) {
>     System.out.println(i);
>}
>```
{style="note" title="Endlosschleife"}

## <format color="%c2%">while-Schleife</format> {id="while-loop"}

Die while-Schleife verwendet das <format color="%LinkColor%">[Keyword](01-java-token.md#keywords)</format> `while`.

```Java
while (condition) {
    // Code...
}
```

Solange die Bedingung zutrifft, wird der Rumpf ausgeführt.

```Java
boolean isRunning = true;
while (isRunning) {
    // Code...
}
```

Jede `while`-Schleife kann auch als <format color="%c1%">for-Schleife</format> geschrieben werden und umgekehrt.

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

Die `do`-`while`-Schleife funktioniert im Grund genauso wie die <format color="%c2%">while-Schleife</format>. Der einzige Unterschied besteht darin, dass die Bedingung nach dem Schleifenrumpf überprüft wird. D.h. der Schleifenrumpf wird immer <format color="%Highlight%">mindestens einmal</format> ausgeführt. Die Schleife verwendet die <format color="%LinkColor%">[Keywords](01-java-token.md#keywords)</format> `do` und `while`.

```Java
do {
    // Code...
} while (condition);
```

```Java
boolean isRunning = true;
do {
    // Code...
} while (isRunning);
```

## <format color="%c4%">for-each-Schleife</format> {id="for-each-loop"}

Die `for`-each oder auch enhanced-`for`-Schleife ist eine verkürzte Schreibweise der <format color="%c1%">for-Schleife</format>. Diese kann nur verwendet werden, wenn über <format color="%LinkColor%">[Collections](collections.md)</format> oder <format color="%LinkColor%">[Arrays](08-java-arrays.md)</format> iteriert werden soll.

```Java
for (type identifier : array) {
    // Code...
}
```

```Java
int[] array = {4, 6, 2, 7, 1};

for (int i : array) {
    System.out.println(i);
}
```

Die Schleifenvariable `i` nimmt nacheinander alle Werte des <format color="%LinkColor%">[Arrays](08-java-arrays.md)</format> an.

> Werden <format color="%NoteLinkColor%">[Collections](collections.md)</format> verwendet, kann auch auf die passende `forEach()`-Methode zurückgegriffen werden. Diese verwendet intern die `for`-each-Schleife.
{style="note" title="forEach()-Methode"}

## `break` & `continue`

Das <format color="%LinkColor%">[Keyword](01-java-token.md#keywords)</format> `break` steht für die Zuständigkeit, eine Schleife an einem bestimmten Punkt vorzeitig zu beenden. Das Keyword `continue` steht für die Zuständigkeit, den weiteren Schleifenablauf zu überspringen und mit dem nächsten Schleifendurchlauf fortzufahren.

Die folgende Schleife gibt alle Zahlen von `0` bis `4` auf der Konsole aus, bis `i` die Zahl `5` enthält. Dann wird die komplette Schleife durch die `break`-Anweisung abgebrochen.

```Java
for (int i = 0; i < 10; i++) {
    if (i == 5) break;
    System.out.println(i);
}
```

Die folgende Schleife gibt alle Zahlen von `0` bis `4` auf der Konsole aus, bis `i` die Zahl `5` enthält. Dann wird die Ausgabe übersprungen und mit dem nächsten Schleifendurchlauf fortgesetzt.

```Java
for (int i = 0; i < 10; i++) {
    if (i == 5) continue;
    System.out.println(i);
}
```

## Geschachtelte Schleifen {id="nested-loops"}

Wie <format color="%LinkColor%">[Verzweigungen](06-java-branches.md)</format> können auch Schleifen verschachtelt werden. Folgendes Beispiel gibt das kleine 1x1 in tabellarischer Form auf der Konsole aus.

```Java
for (int i = 1; i <= 10; i++) {
    for (int j = 1; j <= 10; j++) {
        System.out.print(i * j + "\t");
    }
    System.out.println();
}
```

```Console
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
```

## break label {id="break-label"}

Es kann vorkommen, dass mit mehreren geschachtelten Schleifen gearbeitet wird. Das <format color="%LinkColor%">[Keyword](01-java-token.md#keywords)</format> `break` beendet immer nur die innerste Schleife. Soll der Ablauf der äußeren Schleife abgebrochen werden, kann dafür ein gelabeltes `break` verwendet werden.

```Java
label:
for (int i = 1; i <= 10; i++) {
    for (int j = 1; j <= 10; j++) {
        System.out.print(i * j + "\t");
        if (i * j >= 50) {
            break label;
        }
    }
    System.out.println();
}
```

Ergibt das erste Ergebnis beim kleinen 1x1 eine Zahl die größer oder gleich `50` ist, wird das `label` gebrochen und die äußerste Schleife bricht ab. Dadurch wird in diesem Fall nur die erste Hälfte des kleinen 1x1 ausgegeben. `label` ist hier ein <format color="%LinkColor%">[Identifier](01-java-token.md#identifier)</format> und kann auch anders benannt werden.

## Übung {id="exercise"}

Erweitert den Taschenrechner um eine Schleife. Das Programm soll nach jedem Ergebnis nach einer weiteren Berechnung fragen.

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
                    System.out.print("1. Zahl: ");  
                    int x = sc.nextInt();  
                    System.out.print("2. Zahl: ");  
                    int y = sc.nextInt();  
                    System.out.print("""
                        =================
                        1: Addition
                        2: Subtraktion
                        3: Multiplikation
                        4: Division
                        =================
                        Option:\s""");
                    int option = sc.nextInt();
                    switch (option) {
                        case 1 -> System.out.println(x + " + " + y + " = " + (x + y));
                        case 2 -> System.out.println(x + " - " + y + " = " + (x - y));
                        case 3 -> System.out.println(x + " * " + y + " = " + (x * y));
                        case 4 -> System.out.println(x + " / " + y + " = " + (x / y));
                        default -> System.out.println("Diese Option gibt es nicht.");
                    } 
                    System.out.println("Soll eine weitere Berechnung durchgeführt werden?");
                    String keepGoing = sc.next();
                    if (!keepGoing.equalsIgnoreCase("j")) {  
                        isRunning = false;  
                    }
                } 
                System.out.println("Bye.");
                sc.close();
            }
        </code-block>
    </tab>
</tabs>