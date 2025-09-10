# 04 Java – Ein- und Ausgaben

<p>Beim Programmieren sind Ausgaben sehr essenziell. Zum einen können bestimmte Werte auf der Konsole zur Überprüfung
ausgegeben werden. Zum anderen können über die Ausgabe auf der Konsole <format color="%Highlight%">Errors</format>
 identifiziert werden, was wesentlich für die <format color="%Highlight%">Fehlersuche und –behebung</format> ist.</p>

<p>Eingaben wiederum ermöglichen uns die Interaktion mit Programmen und damit den Zugriff auf den weiteren
Programmablauf – auch über die Konsole. Nahezu alles, was über elektronische Geräte getan wird, wird mit Eingaben
realisiert – das Tippen auf der Tastatur, das Klicken mit der Maus oder sogar das Drücken von Tasten auf einem
Controller so wie viele weitere Dinge.</p>

<p>Demnach sind natürlich nicht nur Ein- und Ausgaben über die Konsole möglich. Dafür werden jedoch
<format color="%LinkColor%"><a href="29-java-gui.md">Benutzeroberflächen</a></format> benötigt. In
<format color="%LinkColor%"><a href="02-java-data-types.md">Kapitel 2 – Datentypen</a></format> gab es bereits einen
kleinen Einblick zu den Konsolenausgaben.</p>

## Ausgaben {id="outputs"}

<p>Um Ausgaben über die Konsole zu realisieren, gibt es mehrere Möglichkeiten.</p>

<code-block lang="java">
    System.out.print();   // Output without line break
    System.out.println(); // Output with line break
    System.out.printf();  // Formatted output without line break
    
    System.err.print();   // Output of an error without line break
    System.err.println(); // Output of an error with line break
    System.err.printf();  // Formatted output of an error without line breaks
</code-block>

<p>Die <code>print</code>-Ausdrücke werden
<format color="%LinkColor%"><a href="09-java-methods.md">Methoden</a></format> genannt. An diese können Werte übergeben
werden. Diese Methoden sorgen dann dafür, dass die Werte auf der Konsole ausgegeben werden. Die
<code>printf()</code>-Methode wird im nachfolgenden
<format color="%LinkColor%"><a href="05-java-strings.md">Kapitel 5 – Zeichenketten</a></format>
 genauer betrachtet.</p>

<tip>
    <p>Die Ausgabe von Fehlern mittels der <code>err.printf()</code>-Methoden sollte ausschließlich für diesen Zweck
    verwendet werden und nicht zur visuellen Hervorhebung von Text dienen.</p>
</tip>

<code-block lang="java">
    int i = 10;
    int j = 10;
    int k = i + k;
    System.out.println(k); // 20
</code-block>

<code-block lang="java">
    System.out.println(5 + 11); // 16 (Line break)
    System.out.println(3 + 8);  // 11
</code-block>

<code-block lang="java">
    System.out.print(1);
    System.out.print(1);
    System.out.print(1); // 111 (No line breaks)
</code-block>

<code-block lang="java">
    System.out.println("Hello World!"); // Hello World!
</code-block>

<note>
    <p>In IntelliJ kann die Abkürzung <code>sout</code> eingegeben werden. Wird mit der Enter-Taste bestätigt, wird der
    Code automatisch zu <code>System.out.println()</code> vervollständigt.</p>
</note>

## Eingaben {id="inputs"}

<p>Es gibt mehrere Varianten, um Eingaben zu realisieren. Zwei davon werden hier vorgestellt. Dafür muss jedoch auf
bestimmte Klassen und Objekte zurückgegriffen werden, die erst importiert werden müssen.</p>

<p>Klassen und Objekte werden in
<format color="%LinkColor%"><a href="10-java-classes.md">Kapitel 10 – Klassen</a></format> und
<format color="%LinkColor%"><a href="11-java-objects.md">Kapitel 11 – Objekte</a></format> genauer behandelt. Mehr zu
Imports folgt in
<format color="%LinkColor%"><a href="16-java-packages-and-imports.md">Kapitel 16 – Pakete & Imports</a></format>.</p>

### Die `BufferedReader`-Klasse {id="the-buffered-reader-class"}

<p>Eine mögliche Variante funktioniert über den <code>BufferedReader</code> in Verbindung mit dem
<code>InputStreamReader</code> und einem <code>InputStream</code>-Objekt <code>System.in</code>.</p>

<p>Um nun über diesen Reader eine Eingabe von der Konsole einlesen zu können, muss Folgendes geschrieben werden.</p>

<code-block lang="java">
    BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
</code-block>

<p>Um nun über diesen Reader eine Eingabe von der Konsole einlesen zu können, wird die
<code>readLine()</code>-<format color="%LinkColor%"><a href="09-java-methods.md">Methode</a></format> verwendet.</p>

<code-block lang="java">
reader.readLine();
</code-block>

<p>Die <code>readLine()</code>-Methode liest einen
<format color="%LinkColor%"><a href="05-java-strings.md">String</a></format> von der Konsole ein. Dieser kann nun in
einer Variablen gespeichert und ausgegeben werden.</p>

<code-block lang="java">
    String input = reader.readLine();
    System.out.println(input);
</code-block>

<p>Der <code>BufferedReader</code> stellt selbst keine Methoden zur Verfügung, um Werte als
<format color="%LinkColor%"><a href="02-java-data-types.md#primitive-data-types">primitive Datentypen</a></format>
 einzulesen. Daher muss auf die Methoden der jeweiligen
<tooltip term="Wrapper-Class"><format color="%GlossaryLinkColor%">Wrapper-Klassen</format></tooltip> zurückgegriffen
werden.</p>

<code-block lang="java">
    byte b = Byte.parseByte(input);
    short s = Short.parseShort(input);
    int i = Integer.parseInt(input);
    long l = Long.parseLong(input);
    float f = Float.parseFloat(input);
    double d = Double.parseDouble(input);
    boolean bool = Boolean.parseBoolean(input);
</code-block>

> Eine `Character.parseChar()`-Methode gibt es nicht.

<p>Jedoch besitzt der Reader eine Methode <code>read()</code>. Die Eingabe liegt jedoch als <code>int</code> vor, daher
muss diese noch in ein <code>char</code>
<format color="%LinkColor%"><a href="03-java-variables.md#type-casting">gecastet</a></format> werden.</p>

<code-block lang="java">
    char c = (char) reader.read();
</code-block>

### Die `Scanner`-Klasse {id="the-scanner-class"}

<p>Eine weitere Variante wird über die <code>Scanner</code>-Klasse umgesetzt.</p>

<code-block lang="java">
    Scanner scanner = new Scanner(System.in);
</code-block>

<p>Der <code>Scanner</code> stellt zwar selbst
<format color="%LinkColor%"><a href="09-java-methods.md">Methoden</a></format> für die Eingabe von
<format color="%LinkColor%"><a href="02-java-data-types.md#primitive-data-types">primitiven Datentypen</a></format> zur
Verfügung, jedoch besitzt er keine Methode für die Eingabe oder die Umwandlung in ein <code>char</code>.</p>

<code-block lang="java">
    byte b = scanner.nextByte(input);
    short s = scanner.nextShort(input);
    int i = scanner.nextInt(input);
    long l = scanner.nextLong(input);
    float f = scanner.nextFloat(input);
    double d = scanner.nextDouble(input);
    boolean bool = scanner.nextBoolean(input);
</code-block>

<p>Wenn ein <code>char</code> gefordert wird, muss die Eingabe erst mit der <code>next()</code>- oder der
<code>nextLine()</code>-Methode erfolgen, welche als Input einen
<format color="%LinkColor%"><a href="05-java-strings.md">String</a></format> erhält.</p>

<code-block lang="java">
    String input = scanner.next();
</code-block>

<code-block lang="java">
    String input = scanner.nextLine();
</code-block>

<p>Im Anschluss wird dann über die <code>charAt()</code>-Methode das erste Zeichen des Strings in ein <code>char</code>
 umgewandelt. <code>charAt(0)</code> bezieht sich auf den ersten Index eines
<format color="%LinkColor%"><a href="05-java-strings.md">Strings</a></format>. Damit wird das erste Zeichen des
<code>String</code>s abgegriffen. Alle folgenden Zeichen werden ignoriert. Mehr zu Indizes folgt in
<format color="%LinkColor%"><a href="08-java-arrays.md">Kapitel 8 – Arrays</a></format>.</p>

<list>
  <li>
    <p>Mit <code>next()</code> wird alles bis zum ersten Leerzeichen eingelesen.</p>
  </li>
  <li>
    <p>Mit <code>nextLine()</code> wird der komplette <code>String</code> eingelesen inklusive Leerzeichen.</p>
  </li>
</list>

<tip>
    <p>Werden mehrere Eingaben mit der Methode <code>next()</code> hintereinander geschrieben und auf der Konsole
    mehrere durch Leerzeichen getrennte Zeichenfolgen eingegeben, wird jede getrennte Zeichenfolge automatisch für jedes
    weitere Einlesen verwendet.</p>
</tip>

<code-block lang="java">
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
</code-block>

<code-block lang="console">
    Input 1: a b c d
    Input 2: Input 3: Input 4:
    a
    b
    c
    d
</code-block>

<warning title="InputMismatchException">
    <p>Sowohl beim <code>BufferedReader</code> als auch beim <code>Scanner</code> werden
    <format color="%WarningLinkColor%"><a href="05-java-strings.md">Strings</a></format> eingelesen. Diese werden über die
    <format color="%WarningLinkColor%"><a href="09-java-methods.md">Methoden</a></format> in die jeweiligen
    <format color="%WarningLinkColor%"><a href="02-java-data-types.md">Datentypen</a></format> umgewandelt. Beinhaltet
    beispielsweise ein <code>String</code> andere Zeichen als Zahlen, wenn er z. B. in ein <code>int</code>
    konvertiert wird, schmeißt der
    <tooltip term="Compiler"><format color="%GlossaryLinkColor%">Compiler</format></tooltip> einem eine
    <format color="%WarningLinkColor%"><a href="15-java-exceptions.md">Exception</a></format> um die Ohren.</p>
    <code-block lang="java">
        System.out.print("Please enter an integer: ");
        int i = scanner.nextInt();
    </code-block>
    <code-block lang="console">
        Please enter an integer: Hello!
        Exception in thread "main" java.util.InputMismatchException
        at java.base/java.util.Scanner.throwFor(Scanner.java:947)
        at java.base/java.util.Scanner.next(Scanner.java:1602)
        at java.base/java.util.Scanner.nextInt(Scanner.java:2267)
        at java.base/java.util.Scanner.nextInt(Scanner.java:2221)
        at kesares.techarchive.kesares.techarchive.Main.main(kesares.techarchive.Main.java:10)
    </code-block>
</warning>

<note>
    <p>Die Methoden des <code>Scanner</code>s können eine <code>InputMismatchException</code> auslösen.</p>
    <p>Die <code>parseXXX()</code>-Methoden können eine <code>NumberFormatException</code> auslösen.</p>
    <p><format color="%NoteLinkColor%"><a href="15-java-exceptions.md">Exceptions</a></format> allgemein müssen mit
    einem <code>try</code>-<code>catch</code>-Block abgefangen werden.</p>
</note>

<p>Um Ressourcen zu schonen, sollten der <code>Scanner</code> und/oder <code>BufferedReader</code> nach ihrer Verwendung
wieder geschlossen werden.</p>

<code-block lang="java">
    scanner.close();
</code-block>

<code-block lang="java">
    reader.close();
</code-block>

### `BufferedReader` vs `Scanner` {id="buffered-reader-vs-scanner"}

<p>Da sowohl der <code>BufferedReader</code> als auch der <code>Scanner</code> für Eingaben über die Konsole genutzt
werden, könnte man sich jetzt fragen, warum nicht eine Variante ausreicht.</p> 

<p>Wie bei vielen Dingen in der Programmierung können mit unterschiedlichen Lösungen in verschiedenen Umgebungen
unterschiedliche Ergebnisse erzielt werden. Nicht jeder Lösungsansatz ist an jeder Stelle oder für jede Anforderung
geeignet. Daher seht ihr im Folgenden die primären Unterschiede zwischen dem <code>Scanner</code> und dem
<code>BufferedReader</code> aufgelistet.</p>

<table>
    <tr>
        <td></td>
        <td><code>BufferedReader</code></td>
        <td><code>Scanner</code></td>
    </tr>
    <tr>
        <td>Version</td>
        <td>Seit Java 1.1 dabei.</td>
        <td>Seit Java 1.5 dabei.</td>
    </tr>
    <tr>
        <td><format color="%LinkColor%"><a href="16-java-packages-and-imports.md">Package</a></format></td>
        <td><code>java.io</code></td>
        <td><code>java.util</code></td>
    </tr>
    <tr>
        <td><format color="%LinkColor%"><a href="27-java-multithreading.md">Thread-sicher</a></format></td>
        <td>Ja</td>
        <td>Nein</td>
    </tr>
    <tr>
        <td>Lesen/Analysieren (Reading/Parsing)</td>
        <td>Liest Daten, stellt selbst jedoch keine Methoden zum Analysieren von primitiven Datentypen bereit.
        Stattdessen muss auf die <code>parseXXX()</code>-Methoden der
        <tooltip term="Wrapper-Class"><format color="%GlossaryLinkColor%">Wrapper-Klassen</format></tooltip>
        zurückgegriffen werden.</td>
        <td>Stellt <code>nextXXX()</code>-Methoden bereit, um primitive Datentypen einzulesen und zu analysieren.</td>
    </tr>
    <tr>
        <td>Puffergröße</td>
        <td>8 KB (8192 Byte)</td>
        <td>1 KB (1024 Byte)</td>
    </tr>
    <tr>
        <td>Fehlerbehandlung</td>
        <td>Manuelles Abfangen von <format color="%LinkColor%"><a href="15-java-exceptions.md">Exceptions</a></format>
        mittels <code>try</code>-<code>catch</code>-Blocks.</td>
        <td>Verfügt selbst über Prüfmethoden wie <code>hasNextInt()</code> oder <code>hasNextDouble()</code>.</td>
    </tr>
</table>

#### Zusammenfassung

<table>
    <tr>
        <td>Kriterium</td>
        <td><code>BufferedReader</code> + <code>parseXXX()</code>-Methoden</td>
        <td><code>Scanner</code></td>
    </tr>
    <tr>
        <td>Geschwindigkeit</td>
        <td>Schneller bei großen Datenmengen</td>
        <td>Langsamer (Parsing ist integriert)</td>
    </tr>
    <tr>
        <td>Flexibilität</td>
        <td>Mehr Kontrolle, eigene Validierungslogik</td>
        <td>Einfachere und schnellere Nutzung, weniger Code</td>
    </tr>
    <tr>
        <td>Fehlerbehandlung</td>
        <td>Manuell mittels <code>try</code>-<code>catch</code>-Blocks</td>
        <td>Integrierte Prüfmethoden</td>
    </tr>
    <tr>
        <td>Komplexität</td>
        <td>Höher, da Parsing und Validierung manuell</td>
        <td>Niedriger, da Parsing integriert</td>
    </tr>
</table>

## Farbliche Gestaltung (Ausblick) {id="color-design-outlook"}

<p>Wir Menschen lieben es, uns durch schicke, benutzerfreundliche Oberflächen zu klicken. Kein Wunder, sie machen das
Leben einfacher und sorgen dafür, dass wir uns nicht im digitalen Dschungel verirren. Doch wenn ihr euch in die
Programmierung stürzt, werdet ihr irgendwann auf einen unverzichtbaren Begleiter treffen: die Konsole.</p>

<p>Viele sehen die Konsole als das graue, langweilige Arbeitszimmer der Programmierung – keine Fenster, keine Bilder,
nur Text. Klar, sie ist nicht so bunt und aufregend wie die Benutzeroberflächen, die ihr sonst vielleicht gewohnt seid,
aber genau das ist ihre Stärke!</p>

<p>Ihr müsst jedoch nicht komplett auf Farben verzichten! Mit ein paar
<format color="%LinkColor%"><a href="https://gist.github.com/fnky/458719343aabd01cfb17a3a4f7296797">ANSI-Zeichencodes
</a></format> kann man der Konsole durchaus etwas Farbe und Leben einhauchen. So wird aus einem grauen, langweiligen
Arbeitszimmer plötzlich eine farbenfrohe Wohlfühloase (mehr oder weniger). Wer also genug vom Standard-Look hat und sich
nach etwas Abwechslung sehnt, könnte in dieser kleinen Designfreiheit den nötigen Ansporn finden, sich näher mit der
Konsole zu beschäftigen.</p>

<p>Im nächsten Kapitel – <format color="%LinkColor%"><a href="05-java-strings.md">Kapitel 5 – Zeichenketten</a></format>
 – werde ich euch zeigen, wie ihr die Konsole mit
<format color="%LinkColor%"><a href="05-java-strings.md#ansi-escape-sequences">ANSI Escape Codes</a></format> aufpeppen
könnt. Denn Programmieren muss ja nicht immer nur schwarz-weiß sein, oder?</p>

<note>
    <p>Hinweis: Die meisten <tooltip term="IDE"><format color="%GlossaryLinkColor%">IDEs</format></tooltip> unterstützen
    die Darstellung von ANSI-Farbcodes in der Konsole. Es wird jedoch möglicherweise nicht immer die vollständige
    Palette von 256 Farben in jeder Umgebung unterstützt werden.</p>
</note>

## Übung {id="exercise"}

<p>Da wir jetzt alle nötigen Bausteine zusammen haben, um ein einfaches Programm mit Ein- und Ausgaben schreiben zu
können, folgt nun eine kleine Übung.</p>

<tabs group="task">
    <tab id="task-task" title="Aufgabe">
        <note title="Taschenrechner">
            <p>Programmierung eines simplen Taschenrechners mit Addition, Subtraktion, Multiplikation und Division von
            zwei Zahlen mit Ein- und Ausgaben über die Konsole.</p>
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
                System.out.println(x + y);
                System.out.println(x - y);
                System.out.println(x * y);
                System.out.println(x / y);
                sc.close();
            }
        </code-block>
    </tab>
</tabs>