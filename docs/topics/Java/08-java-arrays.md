# 08 Java – Arrays

<p>Ein Array ist eine Art Container eines
<format color="%LinkColor%"><a href="02-java-data-types.md">Datentyps</a></format>, in dessen Inhalt eine feste Anzahl
von Elementen passt. Die Größe des Arrays muss am Anfang festgelegt werden – entweder durch den Entwickler selbst oder
durch den Compiler. Da Arrays statisch sind, kann die Größe danach auch nicht mehr geändert werden. Zudem können sie
aus jeder Art von Objekten gebildet werden.</p>

## Struktur {id="structure"}

<code-block lang="java">
    Type[] identifier = new Type[];
</code-block>

<p>Folgendes Beispiel deklariert ein <code>int[]</code> und wird mit einer Größe von <code>5</code> initialisiert.</p>

<code-block lang="java">
    int[] array1 = new int[5];
    
    int[] array2;
    array2 = new int[5];
</code-block>

<p>Wird das Array direkt mit Werten initialisiert, übernimmt der Compiler die Aufgabe die richtige Größe des Arrays
anzulegen.</p>

<code-block lang="java">
    int[] nums = new int[]{4, 6, 2, 5, 7};
</code-block>

<p>Auch eine verkürzte Schreibweise ist möglich.</p>

<code-block lang="java">
    int[] nums = {4, 6, 2, 5, 7};
</code-block>

## Indizes {id="indices"}

<p>In vielen Programmiersprachen beginnen Indizes aus historischen und praktischen Gründen bei <code>0</code> statt bei
<code>1</code>. Diese Konvention hat sich im Laufe der Zeit etabliert und bietet einige Vorteile. Die Werte innerhalb
eines Arrays werden über die Positionen (Indizes) referenziert.</p>

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

<p>Die Zahl, die in den eckigen Klammern angegeben wird, bezieht sich auf den Index – also die Position auf dem sich der
Wert befindet.</p>

## Elemente einfügen und auslesen {id="inserting-and-reading-elements"}

<code-block lang="java">
    int[] nums = new int[10];
    
    // Insert elements
    nums[0] = 3;
    nums[1] = 6;
    nums[2] = 4;
    nums[3] = 5;
    
    // Read elements
    int i = nums[0];
    int j = nums[1];
    int k = nums[2];
    int l = nums[3];
</code-block>

<tip>Eine Möglichkeit, Elemente aus Arrays zu löschen, gibt es nicht. Die Werte können nur überschrieben werden.</tip>

## Iteration {id="iteration"}

<p>Jeden Wert einzeln aus einem Array zu lesen strengt an und lässt den Code im Museum der Spaghetti-Codes erstrahlen.
Wir wissen bereits, wie Schleifen funktionieren. Nutzen wir eine, die das gesamte Array auf der Konsole ausgibt. Mit
<code>nums.length</code> können wir die Größe des Arrays abfragen.</p>

<code-block lang="java">
    for (int i = 0; i &lt; nums.length; i++) {
        System.out.print(nums[i] + " ");
    }
</code-block>

<code-block lang="console">
    3 6 4 5 0 0 0 0 0 0
</code-block>

<p>Unser Array wurde mit einer Größe von <code>10</code> initialisiert. Da wir nur <code>4</code> Werte hinzugefügt
haben, bleiben <code>6</code> "freie" Plätze. Java initialisiert standardmäßig leere numerische Arrays mit
<code>0</code>, booleans mit <code>false</code> und
<format color="%LinkColor%"><a href="11-java-objects.md">Objekte</a></format> mit <code>null</code>.</p>

<tabs group="task">
    <tab title="Frage">
        <p>Und ein <code>char[]</code>-Array?</p>
    </tab>
    <tab title="Lösung">
        <p>Das <code>\u0000</code>-Zeichen ist das Nullzeichen und entspricht in der ASCII- und Unicode-Tabelle dem
        Zeichen mit dem Wert <code>0</code>. Es wird oft als <code>NUL</code> oder null character bezeichnet</p>
        <note>
            In Java werden Elemente eines <code>char[]</code>-Arrays standardmäßig mit diesem Unicode-Zeichen
            (<code>\u0000</code>) initialisiert.
        </note>
        <p>Viele Entwicklungsumgebungen und Texteditoren haben spezielle Darstellungen für Zeichen, die normalerweise
        unsichtbar sind, wie das Nullzeichen (<code>\u0000</code>). Diese Darstellung kann je nach Umgebung variieren.
        </p>
        <p>In <format color="%Highlight%">IntelliJ IDEA</format> wird das Nullzeichen oft als ein kleines Rechteck mit
        einer diagonalen Linie dargestellt, um den Entwickler darauf hinzuweisen, dass es sich um ein unsichtbares oder
        nicht druckbares Zeichen handelt.</p>
    </tab>
</tabs>

## Mehrdimensionale Arrays {id="multidimensional-arrays"}

<p>Arrays lassen sich mehrdimensional darstellen. Tatsächlich verwaltet Java jedoch keine echten mehrdimensionalen
Arrays, sondern Arrays von Arrays (von Arrays …). Um ein mehrdimensionales Array anzulegen, muss ein weiteres Paar
Klammern hinzugefügt werden – ein paar Klammern pro Dimension. Das folgende Beispiel beinhaltet 2 Zeilen und 3 Spalten.
</p>

<code-block lang="java">
    int[][] array = new int[2][3];
</code-block>

<code-block lang="java">
    int[][] array = {
        {3, 6, 4},
        {3, 2, 1}
    };
</code-block>

### Beispiele für die Ausgabe des zweidimensionalen Arrays {id="outputs-for-multidimensional-arrays"}

<code-block lang="java">
    for (int i = 0; i &lt; array.length; i++) {
        for (int j = 0; j &lt; array[i].length; j++) {
            System.out.print(array[i][j]);
        }
        System.out.println();
    }
</code-block>

<code-block lang="java">
    for (int[] i : array) {
        for (int j : i) {
            System.out.print(j);
        }
        System.out.println();
    }
</code-block>

<p>Zu beachten ist, dass bei der zweiten Variante die Schleifenvariable <code>i</code> den Typ <code>int[]</code>
 aufweist. Jedes Element, dass diese Schleifenvariable durchläuft, ist also selbst ein Array.</p>

<p>Konsolenausgabe in beiden Fällen:</p>

<code-block lang="console">
    364
    321
</code-block>