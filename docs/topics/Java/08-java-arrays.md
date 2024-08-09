# 08 Java Arrays

Ein Array ist eine Art Container eines <format color="%LinkColor%">[Datentyps](02-java-data-types.md)</format>, in dessen Inhalt eine feste Anzahl von Elementen passt. Die Größe des Arrays muss am Anfang festgelegt werden – entweder durch den Entwickler selbst oder durch den Compiler. Da Arrays statisch sind, kann die Größe danach auch nicht mehr geändert werden. Zudem können sie aus jeder Art von Objekten gebildet werden.

## Struktur {id="structure"}

```Java
Type[] identifier = new Type[];
```

Folgendes Beispiel deklariert ein `int[]` und wird mit einer Größe von `5` initialisiert.

```Java
int[] array1 = new int[5];

int[] array2;
array2 = new int[5];
```

Wird das Array direkt mit Werten initialisiert, übernimmt der Compiler die Aufgabe die richtige Größe des Arrays anzulegen.

```Java
int[] nums = new int[]{4, 6, 2, 5, 7};
```

Auch eine verkürzte Schreibweise ist möglich.

```Java
int[] nums = {4, 6, 2, 5, 7};
```

## Indizes {id="indices"}

Die Werte innerhalb eines Arrays werden über die Positionen (Indizes) referenziert. Arrays fangen standardmäßig bei `0` an zu zählen.

<tabs group="task">
    <tab title="Frage">
        <p>Welcher Wert wird beim folgenden Beispiel auf der Konsole ausgegeben?</p>
        <code-block lang="java">
            int[] array = new int[]{4, 6, 2, 5, 7};
            System.out.println(array[3]);
        </code-block>
    </tab>
    <tab title="Lösung">
        <code-block lang="java">
            //                      0  1  2  3  4
            int[] array = new int[]{4, 6, 2, 5, 7};
            System.out.println(array[3]); // 5
        </code-block>
    </tab>
</tabs>

Die Zahl die in den eckigen Klammern angegeben wird, bezieht sich auf den Index – also die Position auf dem sich der Wert befindet.

## Elemente einfügen und auslesen {id="inserting-and-reading-elements"}

```Java
int[] nums = new int[10];

// Elemente einfügen
nums[0] = 3;
nums[1] = 6;
nums[2] = 4;
nums[3] = 5;

// Elemente auslesen
int i = nums[0];
int j = nums[1];
int k = nums[2];
int l = nums[3];
```

> Eine Möglichkeit Elemente aus Arrays zu löschen gibt es nicht. Die Werte können nur überschrieben werden.

## Iteration {id="iteration"}

Jeden Wert einzeln aus einem Array zu lesen strengt an und lässt den Code im Museum der Spaghetti-Codes erstrahlen. Wir wissen bereits, wie Schleifen funktionieren. Nutzen wir eine, die das gesamte Array auf der Konsole ausgibt. Mit `nums.length` können wir die Größe des Arrays abfragen.

```Java
for (int i = 0; i < nums.length; i++) {
    System.out.print(nums[i] + " ");
}
```

```Console
3 6 4 5 0 0 0 0 0 0
```

Unser Array wurde mit einer Größe von `10` initialisiert. Da wir nur `4` Werte hinzugefügt haben, bleiben `6` frei Plätze. Java initialisiert standardmäßig leere numerische Arrays mit `0`, booleans mit `false` und Objects mit `null`.

<tabs group="task">
    <tab title="Frage">
        <p>Und ein <code>char[]</code>-Array?</p>
    </tab>
    <tab title="Lösung">
        <p>Das <code>\u0000</code>-Zeichen ist das Nullzeichen und entspricht in der ASCII- und Unicode-Tabelle dem Zeichen mit dem Wert <code>0</code>. Es wird oft als <code>NUL</code> oder null character bezeichnet</p>
        <note>
            In Java werden Elemente eines <code>char[]</code>-Arrays standardmäßig mit diesem Unicode-Zeichen (<code>\u0000</code>) initialisiert.
        </note>
        <p>Viele Entwicklungsumgebungen und Texteditoren haben spezielle Darstellungen für Zeichen, die normalerweise unsichtbar sind, wie das Nullzeichen (<code>\u0000</code>). Diese Darstellung kann je nach Umgebung variieren.</p>
        <p>In <format color="%Highlight%">IntelliJ IDEA</format> wird das Nullzeichen oft als ein kleines Rechteck mit einer diagonalen Linie dargestellt, um den Entwickler darauf hinzuweisen, dass es sich um ein unsichtbares oder nicht druckbares Zeichen handelt.</p>
    </tab>
</tabs>

## Mehrdimensionale Arrays {id="multidimensional-arrays"}

Arrays lassen sich mehrdimensional darstellen. Tatsächlich verwaltet Java jedoch keine echten mehrdimensionalen Arrays, sondern Arrays von Arrays (von Arrays …). Um ein mehrdimensionales Array anzulegen, muss ein weiteres Paar Klammern hinzugefügt werden – ein paar Klammern pro Dimension. Die folgenden Beispiele beinhaltet 2 Zeilen und 3 Spalten.

```Java
int[][] array = new int[2][3];
```

```Java
int[][] array = {
    {3, 6, 4},
    {3, 2, 1}
};
```

### Beispiele für die Ausgabe des zweidimensionalen Arrays {id="outputs-for-multidimensional-arrays"}

```Java
for (int i = 0; i < array.length; i++) {
    for (int j = 0; j < array[i].length; j++) {
        System.out.print(array[i][j]);
    }
    System.out.println();
}
```

```Java
for (int[] i : array) {
    for (int j : i) {
        System.out.print(j);
    }
    System.out.println();
}
```

Zu beachten ist, dass bei der zweiten Variante die Schleifenvariable `i` den Typ `int[]` aufweist. Jedes Element, dass diese Schleifenvariable durchläuft, ist also selbst ein Array.

Konsolenausgabe in beiden Fällen:

```Console
000
000
```