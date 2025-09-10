# 15 Java – Exceptions

<p>Exceptions sind Ereignisse, die während der Programmausführung auftreten und den normalen Ablauf des Programms
unterbrechen. Sie werden in der Regel durch Fehler oder unerwartete Bedingungen verursacht, die vom Programm erkannt und
behandelt werden können/müssen.</p>

<p>In den bisherigen Kapiteln ist es immer mal wieder vorgekommen, dass uns der
<tooltip term="Compiler"><format color="%GlossaryLinkColor%">Compiler</format></tooltip> bestimmte Exceptions um die
Ohren gehauen hat. Nun werden wir uns unter anderem damit beschäftigen, wie Exceptions abgefangen werden können, was der
Unterschied zwischen
<format color="%LinkColor%"><a href="#checked-vs-unchecked-exceptions">Checked und Unchecked Exceptions</a></format> ist
und wie wir eigene Exceptions auslösen oder erstellen können.</p>

<p>Java unterscheidet zwischen zwei Hauptarten von Exceptions: <format color="%Highlight%">Checked Exceptions</format>,
die während der Kompilierung überprüft und vom Entwickler behandelt werden müssen und
<format color="%LinkColor%">Unchecked Exceptions</format>, die zur Laufzeit auftreten und in der Regel auf
Programmierfehler hinweisen.</p>

## Checked vs. Unchecked Exceptions {id="checked-vs-unchecked-exceptions"}
### Checked Exceptions {id="checked-exceptions"}

<p>Checked Exceptions sind Ausnahmen, die zur Kompilierungszeit (Compile-Time) überprüft werden. Der
<tooltip term="Compiler"><format color="%GlossaryLinkColor%">Compiler</format></tooltip> muss sicherstellen, dass diese
Exceptions entweder mit einem <format color="%LinkColor%"><a href="#catch-exceptions">try-catch</a></format>-Block
abgefangen oder explizit mit dem <format color="%LinkColor%"><a href="01-java-token.md#keywords">Keyword</a></format>
<code>throws</code> weitergereicht werden.</p>

<p>Folgendes Beispiel zeigt eine Methodensignatur, welche mit dem Keyword <code>throws</code> versehen ist.</p>

<code-block lang="java">
    public void readFile(String path) throws FileNotFoundException {
        // ...
    }
</code-block>

<p>Die Methode versucht eine Datei einzulesen. Existiert diese jedoch nicht, wird eine
<code>FileNotFoundException</code> ausgelöst, die jedoch an den Aufrufer dieser
<format color="%LinkColor%"><a href="09-java-methods.md">Methode</a></format> weitergereicht wird. Dort muss diese dann
abgefangen werden – oder ebenfalls weitergereicht werden.</p>

<note>Das permanente Weiterreichen von <format color="%NoteHighlight%">Exceptions</format> ist meistens nicht
zielführend. Es kommt der Punkt, an dem die Exceptions abgefangen werden
<format color="%NoteHighlight%">müssen</format>.</note>

<p>Typische Beispiele für Checked Exceptions sind <code>IOException</code>, die beim Arbeiten mit Dateien oder eine
<code>SQLException</code>, die in Verbindung mit Datenbanken auftreten können. Diese Exceptions zwingen den Entwickler,
sich mit potenziellen Fehlerquellen auseinanderzusetzen und eine entsprechende
<format color="%LinkColor%"><a href="#catch-exceptions">Fehlerbehandlung</a></format> zu implementieren.</p>

### Unchecked Exceptions {id="unchecked-exceptions"}

<p>Unchecked Exceptions werden zur Laufzeit des Programms geworfen, daher werden sie auch als Laufzeitausnahmen (Runtime
Exceptions) bezeichnet. Sie leiten sich von der
<format color="%LinkColor%"><a href="10-java-classes.md">Klasse</a></format> <code>RuntimeException</code> ab und
umfassen häufige Fehler wie <code>NullPointerException</code>, <code>ArrayIndexOutOfBoundsException</code> oder
<code>ArithmeticException</code>, welchen ihr mit Sicherheit schon mal begegnet seid.</p>

<p>Eine <code>RuntimeException</code> muss nicht zwingend behandelt werden. Da solche Fehler jedoch oft auf
Programmierfehler zurückzuführen sind, sollten Entwickler den Code so schreiben, dass sie vermieden werden. Unchecked
Exceptions dienen somit eher als Hinweis auf Logikfehler im Programmcode, die durch Korrekturen behoben werden können.
</p>

## `Throwable`-Klassenhierarchie {id="class-hierarchic"}

<p>Im Folgenden ist ein "kleiner" Teil aus der <code>Throwable</code>-Klassenhierarchie abgebildet. Sämtliche Exceptions
und Errors stammen von <code>Throwable</code> ab und <code>Throwable</code> natürlich von <code>Object</code>.</p>

<img src="15_java_exception_1.png" alt="15_java_exception_1.png" />

## Exceptions vs. Errors {id="exceptions-vs-errors"}

<p>Ein <code>Error</code> repräsentiert ein schwerwiegendes Problem, welches außerhalb der Kontrolle des Programms liegt
und in der Regel nicht durch den Code behoben werden kann. Er resultiert oft aus Ressourcenmangel (wie einem
Speicherüberlauf → <code>OutOfMemoryError</code>) oder anderen kritischen Fehlern im Laufzeitsystem (z. B. einem
Stapelüberlauf → <code>StackOverflowError</code>).</p>

<p>Sowohl <code>Exception</code> als auch <code>Error</code> erben beide von <code>Throwable</code>. <code>Error</code>
 wird jedoch meistens von der <tooltip term="JVM"><format color="%GlossaryLinkColor%">JVM</format></tooltip> in einem
schwerwiegenden Zustand ausgelöst und für die Anwendung keine Möglichkeit besteht, den Fehler zu beheben.</p>

<p>Obwohl auch Anwendungen einen <code>Error</code> auslösen können, ist es keine passende Vorgehensweise, solche Fehler
abzufangen, da es häufig nicht möglich ist, den Programmablauf sinnvoll fortzusetzen. Stattdessen sollten Checked
Exceptions für wiederherstellbare Bedingungen und <code>RuntimeException</code> für Programmierfehler verwendet werden,
während <code>Error</code> als Hinweis darauf betrachtet werden sollte, dass das Programm beendet oder es
drastisch umstrukturiert werden muss.</p>

## Exceptions abfangen {id="catch-exceptions"}

<p>Um Exceptions abzufangen und angemessen auf diese reagieren zu können, verwenden wir den <code>try</code>-
<code>catch</code>-Block bei bestimmten Programmcodes, welche potenziell Exceptions werfen können.</p>

<code-block lang="java">
    try {
        // Code that can throw an exception.
    } catch (Exception e) {
        // Code that is executed to respond appropriately to an exception.
    }
</code-block>

<p>Dazu folgendes Beispiel.</p>

<code-block lang="java">
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
    
        try {
            System.out.print("Enter the numerator: ");
            int numerator = scanner.nextInt();
    
            System.out.print("Enter the denominator: ");
            int denominator = scanner.nextInt();
    
            int result = numerator / denominator; // Possible division by zero
            System.out.println("The result is: " + result);
        } catch (ArithmeticException e) {
            System.err.println(e + ": Division by zero is not allowed.");
        }
    }
</code-block>

<p>Der Code kann eine <code>ArithmeticException</code> auslösen, sollte der Benutzer eine <code>0</code> als Nenner
eingeben. Ist dies der Fall und es wird <code>numerator / denominator</code> ausgeführt, wird der
<code>catch</code>-Block ausgeführt, der diese Exception abfängt und eine einfache Fehlermeldung auf der Konsole
ausgibt.</p>

<p>Wer bereits einen <code>Scanner</code> für Konsoleneingaben verwendet hat oder sich
<format color="%LinkColor%"><a href="04-java-io.md">Kapitel 04 – Ein- und Ausgaben</a></format> angeschaut hat, wird
vielleicht merken, dass die <format color="%LinkColor%"><a href="09-java-methods.md">Methoden</a></format> des Scanners
benfalls eine Exception auslösen können.</p>

<p>Eine <code>InputMismatchException</code> wird geworfen, sobald der Benutzer etwas anderes als eine Zahl eingibt oder
wenn sich die Zahl außerhalb des darstellbaren Zahlenbereichs von <code>int</code> befindet. Auch diese Exception können
wir abfangen, indem wir einen weiteren <code>catch</code>-Block hinzufügen.</p>

<code-block lang="java">
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
    
        try {
            System.out.print("Enter the numerator: ");
            int numerator = scanner.nextInt();
    
            System.out.print("Enter the denominator: ");
            int denominator = scanner.nextInt();
    
            int result = numerator / denominator; // Possible division by zero
            System.out.println("The result is: " + result);
        } catch (ArithmeticException e) {
            System.err.println(e + ": Division by zero is not allowed.");
        } catch (InputMismatchException e) {
            System.err.println(e + ": Invalid input. Please enter an integer.");
        }
    }
</code-block>

<p>Eine Alternative zum Abfangen der <code>ArithmeticException</code> kann auch eine einfache <code>if</code>-Abfrage
sein, die überprüft, ob die Eingabe ungleich <code>0</code> ist.</p>

<code-block lang="java">
    if (denominator != 0) {
        int result = numerator / denominator;
        System.out.println("The result is: " + result);
    }
</code-block>

<p>Wird genauer in die Java-Dokumentation geschaut, fällt auf, dass die Methode <code>nextInt()</code> nicht nur eine
<code>InputMismatchException</code>, sondern noch zwei weitere Exceptions <code>NoSuchElementException</code> und
<code>IllegalStateException</code> werfen kann.</p>

<p>Statt jedoch weitere <code>catch</code>-Blöcke hinzuzufügen, können wir einen für alle drei Exceptions schreiben.</p>

<code-block lang="java">
    try {
        // ...
    } catch (InputMismatchException | NoSuchElementException | IllegalStateException e) {
        System.err.println(e + ": Invalid input. Please enter an integer.");
    }
</code-block>

<p>Eine <code>InputMismatchException</code> erbt von <code>NoSuchElementException</code>. Daher können wir
<code>InputMismatchException</code> auch weglassen. <code>NoSuchElementException</code> und
<code>IllegalStateException</code> erben wiederum von <code>RuntimeException</code>. Daher können wir diese beiden durch
<code>RuntimeException</code> ersetzen.</p>

<code-block lang="java">
    try {
        // ...
    } catch (RuntimeException e) {
        System.err.println(e + ": Invalid input. Please enter an integer.");
    }
</code-block>

<p>Wie wir bereits wissen, wird im Allgemeinen empfohlen RuntimeExceptions nicht abzufangen, da sie häufig auf
Programmierfehler hinweisen.</p>

<p>Auf <code>NoSuchElementException</code> und <code>IllegalStateException</code> trifft das zu. Eine
<code>InputMismatchException</code> kann jedoch durch einen Benutzer ausgelöst werden, wenn dieser eine ungültige
Eingabe tätigt. Dieser Fall liegt außerhalb unseres Einflussbereichs, weshalb er programmatisch behandelt werden muss.
</p>

<code-block lang="java">
    public class Main {
    
        private static final Scanner SCANNER = new Scanner(System.in);
    
        public static void main(String[] args) {
            int numerator = getValidInteger("Enter the numerator: ");
            int denominator = getValidInteger("Enter the denominator: ");
            
            if (denominator != 0) {
                int result = numerator / denominator;
                System.out.println("The result is: " + result);
            } else  {
                System.out.println("Division by zero is not allowed.");
            }
            SCANNER.close();
        }
        
        private static int getValidInteger(String text) {
            try {
                System.out.print(text);
                return SCANNER.nextInt();
            } catch (InputMismatchException e) {
                System.err.println(e + ": Invalid input. Please enter an integer.");
                SCANNER.nextLine();
                return getValidInteger(text);
            }
        }
    }
</code-block>

<p>Die Methode <code>getValidInteger()</code> besitzt eine rekursive Implementierung. Der Benutzer wird so lange nach
einer Ganzzahl gefragt, bis er einen gültigen Wert eingibt.</p>

<tip>Der Lösungsweg innerhalb der Methode <code>getValidInteger()</code> ist zwar korrekt, aber ein iterativer
Lösungsansatz ist in Bezug auf Speicherverbrauch und Performance stabiler und wird in vielen Fällen oft bevorzugt.</tip>

<p>Tatsächlich ist dies ein "Es-kommt-drauf-an"-Fall. In einfachen Konsolenanwendungen spielen übermäßige Eingaben bei
Rekursionen kaum eine Rolle. Insbesondere dann, wenn es nur darum geht, dass der Nutzer daran gehindert werden soll,
ungültige Eingaben zu tätigen.</p>

<p>Die Implementierung der <code>getValidInteger()</code>-Methode ist eine Variante, welche ich selbst in vielen meiner
Konsolenanwendungen verwende. Anstelle eines Scanners nutze ich jedoch einen <code>BufferedReader</code>.
</p>

## Der `finally`-Block {id="the-finally-block"}

<p>Zuvor hatten wir uns angeschaut, wie wir Exceptions abfangen können. Es kann jedoch der Fall sein, dass unabhängig
davon, ob eine Exception geworfen wurde oder nicht, "Aufräumarbeiten" stattfinden sollen. Z. B. wenn eine bestehende
Ressource, wie ein <code>Scanner</code>, geschlossen werden soll.</p>

<p>Um dies zu erreichen, wird der <code>finally</code>-Block nach einem <code>catch</code>-Block verwendet. Dieser Block
wird immer ausgeführt. Egal, ob eine Exception ausgelöst wurde oder nicht.</p>

<code-block lang="java">
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
    
        try {
            System.out.print("Enter the numerator: ");
            int numerator = scanner.nextInt();
    
            System.out.print("Enter the denominator: ");
            int denominator = scanner.nextInt();
    
            int result = numerator / denominator; // Possible division by zero
            System.out.println("The result is: " + result);
        } catch (ArithmeticException e) {
            System.err.println("Error: Division by zero is not allowed.");
        } catch (IOException e) {
            System.err.println("Error: Invalid input. Please enter an integer.");
        } finally {
            scanner.close();
        }
    }
</code-block>

<tabs>
    <tab title="Frage">
        <p>Welche Zahl wird auf der Konsole ausgegeben?</p>
        <code-block lang="java">
            public static void main(String[] main) {
                System.out.println(getNumber());
            }
            public static int getNumber() {
                try {
                    return 1;
                } catch (Exception e) {
                    return 2;
                } finally {
                    return 3;
                }
            }
        </code-block>
    </tab>
    <tab title="Lösung">
        <code-block lang="console">
            3
        </code-block>
        <p>Der <code>finally</code>-Block wird immer ausgeführt. Das bedeutet, dass eine <code>return</code>-Anweisung
        im <code>finally</code>-Block, die <code>return</code>-Anweisungen im <code>try</code>- und
        <code>catch</code>-Block überschreibt.</p>
    </tab>
</tabs>

<note>Solche Beispiele stiften nur Verwirrung. Generell sollten <code>return</code>-Anweisungen in
<code>finally</code>-Blöcken vermieden werden, da dies zu unerwarteten Ergebnissen führen kann.</note>


<p>In den meisten Fällen werden <code>finally</code>-Blöcke nicht benötigt und wenn doch, dann sollte auf
<format color="%LinkColor%"><a href="#try-with-resources">try-with-resources</a></format>-Blöcke zurückgegriffen werden.
</p>

## `try`-with-resources {id="try-with-resources"}

<p>try-with-resources ist eine spezielle Form des <code>try</code>-Blocks, die eingeführt wurde, um Ressourcen wie
Dateien, Datenbankverbindungen, Netzwerkverbindungen oder andere Objekte automatisch zu schließen. Es bietet eine
Alternative zum <code>finally</code>-Block und schließt am Ende des `catch`-Blocks automatisch die Ressource, unabhängig
davon, ob eine Exception geworfen wurde oder nicht.</p> 

<code-block lang="java">
    public void readFile(String path) {
        try (BufferedReader reader = new BufferedReader(new FileReader(path))) {
            String line;
            while ((line = reader.readLine()) != null) {
                System.out.println(line);
            }
        } catch (IOException e) {
            System.err.println("Error reading file: " + e.getMessage());
        }
    }
</code-block>

<note>Ressourcen, die in einem try-with-resources-Block verwendet werden, müssen das <code>AutoCloseable</code>-
<format color="%LinkColor%"><a href="14-java-oop.md#interfaces">Interface</a></format> implementieren, welches die
Methode <code>close()</code> enthält.</note>

## Exceptions werfen {id="throw-exceptions"}

<p>Exceptions werden geworfen, wenn ein unerwarteter Zustand oder ein Fehler auftritt, der vom aktuellen Codeabschnitt
nicht direkt behoben werden kann. Das Werfen einer Exception mittels <code>throw</code> ermöglicht es, das Problem an
den Aufrufer weiterzuleiten, der entweder die Exception mittels <code>try</code>- <code>catch</code> behandelt oder sie
weiter nach oben im Aufrufstapel propagieren lässt.</p>

<p>Nehmen wir unsere <code>Dog</code>-Klasse aus den letzten Kapiteln als Beispiel. Der
<format color="%LinkColor%"><a href="10-java-classes.md#constructors">Konstruktor</a></format> erwartet ein Alter als
Parameter. Ein negatives Alter wäre ungültig, also könnte eine <code>IllegalArgumentException</code> geworfen werden.
</p>

<code-block lang="java">
    public Dog(String name, int age) {
        if (age &lt; 0) {
            throw new IllegalArgumentException("Age cannot be negative");
        }
        this.name = name;
        this.age = age;
    }
</code-block>

## Eigene Exceptions erstellen {id="create-your-own-exceptions"}

<p>In manchen Situationen ist es nötig, eine spezifische Exception zu haben, die einen Fehler genauer beschreibt. In
solchen Fällen kann eine eigene Exception-Klasse erstellt werden und diese werfen.</p>

<code-block lang="java">
    public class InvalidAgeException extends Exception {
    
        public InvalidAgeException(String message) {
            super(message);
        }
    }
    
    public class Dog {
    
        // ...
        
        public Dog(String name, int age) {
            if (age &lt; 0) {
                throw new InvalidAgeException("Age cannot be negative");
            }
            this.name = name;
            this.age = age;
        }
        
        // ...
    }
</code-block>