# 15 Java – Exceptions

Exceptions sind Ereignisse, die während der Programmausführung auftreten und den normalen Ablauf des Programms unterbrechen. Sie werden in der Regel durch Fehler oder unerwartete Bedingungen verursacht, die vom Programm erkannt und behandelt werden können/müssen.

In den bisherigen Kapiteln ist es immer mal wieder vorgekommen, dass uns der <tooltip term="Compiler"><format color="%GlossaryLinkColor%">Compiler</format></tooltip> bestimmte Exceptions um die Ohren gehauen hat. Nun werden wir uns unter anderem damit beschäftigen, wie Exceptions abgefangen werden können, was der Unterschied zwischen <format color="%LinkColor%">[Checked und Unchecked Exceptions](#checked-vs-unchecked-exceptions)</format> ist und wie wir eigene Exceptions auslösen oder erstellen können.

Java unterscheidet zwischen zwei Hauptarten von Exceptions: <format color="%Highlight%">Checked Exceptions</format>, die während der Kompilierung überprüft und vom Entwickler behandelt werden müssen und <format color="%LinkColor%">Unchecked Exceptions</format>, die zur Laufzeit auftreten und in der Regel auf Programmierfehler hinweisen.

## Checked vs. Unchecked Exceptions {id="checked-vs-unchecked-exceptions"}
### Checked Exceptions {id="checked-exceptions"}

Checked Exceptions sind Ausnahmen, die zur Kompilierungszeit (Compile-Time) überprüft werden. Der <tooltip term="Compiler"><format color="%GlossaryLinkColor%">Compiler</format></tooltip> muss sicherstellen, dass diese Exceptions entweder mit einem <format color="%LinkColor%">[try-catch](#catch-exceptions)</format>-Block abgefangen oder explizit mit dem <format color="%LinkColor%">[Keyword](01-java-token.md#keywords)</format> `throws` weitergereicht werden.

Folgendes Beispiel zeigt eine Methodensignatur, welche mit dem Keyword `throws` versehen ist.

```Java
public void readFile(String path) throws FileNotFoundException {
    // ...
}
```

Die Methode versucht eine Datei einzulesen. Existiert diese jedoch nicht, wird eine `FileNotFoundException` ausgelöst, die jedoch an den Aufrufer dieser <format color="%LinkColor%">[Methode](09-java-methods.md)</format> weitergereicht wird. Dort muss diese dann abgefangen werden – oder ebenfalls weitergereicht werden.

> Das permanente Weiterreichen von Exceptions ist meistens nicht zielführend. Es kommt der Punkt, an dem die Exceptions abgefangen werden <format color="%NoteHighlight%">müssen</format>.
> {style="note"}

Typische Beispiele für Checked Exceptions sind `IOException`, die beim Arbeiten mit Dateien oder eine `SQLException`, die in Verbindung mit Datenbanken auftreten können. Diese Exceptions zwingen den Entwickler, sich mit potenziellen Fehlerquellen auseinanderzusetzen und eine entsprechende <format color="%LinkColor%">[Fehlerbehandlung](#catch-exceptions)</format> zu implementieren.

### Unchecked Exceptions {id="unchecked-exceptions"}

Unchecked Exceptions werden zur Laufzeit des Programms geworfen, daher werden sie auch als Laufzeitausnahmen (Runtime Exceptions) bezeichnet. Sie leiten sich von der <format color="%LinkColor%">[Klasse](10-java-classes.md)</format> `RuntimeException` ab und umfassen häufige Fehler wie `NullPointerException`, `ArrayIndexOutOfBoundsException` oder `ArithmeticException`, welchen ihr mit Sicherheit schon mal begegnet seid.

Eine `RuntimeException` muss nicht zwingend behandelt werden. Da solche Fehler jedoch oft auf Programmierfehler zurückzuführen sind, sollten Entwickler den Code so schreiben, dass sie vermieden werden. Unchecked Exceptions dienen somit eher als Hinweis auf Logikfehler im Programmcode, die durch Korrekturen behoben werden können.

## `Throwable`-Klassenhierarchie {id="class-hierarchic"}

Im Folgenden ist ein "kleiner" Teil aus der `Throwable`-Klassenhierarchie abgebildet. Sämtliche Exceptions und Errors stammen von `Throwable` ab und `Throwable` natürlich von `Object`.

![15_java_exception_1.png](15_java_exception_1.png)

## Exceptions vs. Errors {id="exceptions-vs-errors"}

Ein `Error` repräsentiert ein schwerwiegendes Problem, welches außerhalb der Kontrolle des Programms liegt und in der Regel nicht durch den Code behoben werden kann. Er resultiert oft aus Ressourcenmangel (wie einem Speicherüberlauf → `OutOfMemoryError`) oder anderen kritischen Fehlern im Laufzeitsystem (z. B. einem Stapelüberlauf → `StackOverflowError`).

Sowohl `Exception` als auch `Error` erben beide von `Throwable`. `Error` wird jedoch meistens von der <tooltip term="JVM"><format color="%GlossaryLinkColor%">JVM</format></tooltip> in einem schwerwiegenden Zustand ausgelöst und für die Anwendung keine Möglichkeit besteht, den Fehler zu beheben.

Obwohl auch Anwendungen einen `Error` auslösen können, ist es keine passende Vorgehensweise, solche Fehler abzufangen, da es häufig nicht möglich ist, den Programmablauf sinnvoll fortzusetzen. Stattdessen sollten Checked Exceptions für wiederherstellbare Bedingungen und `RuntimeException` für Programmierfehler verwendet werden, während `Error` als Hinweis darauf betrachtet werden sollte, dass das Programm beendet werden oder es drastisch umstrukturiert werden muss.

## Exceptions abfangen {id="catch-exceptions"}

Um Exceptions abzufangen und angemessen auf diese reagieren zu können, verwenden wir den `try`-`catch`-Block bei bestimmten Programmcodes, welche potenziell Exceptions werfen können.

```Java
try {
    // Code that can throw an exception.
} catch (Exception e) {
    // Code that is executed to respond appropriately to an exception.
}
```

Dazu folgendes Beispiel.

```Java
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
```

Der Code kann eine `ArithmeticException` auslösen, sollte der Benutzer eine `0` als Nenner eingeben. Ist dies der Fall und es wird `numerator / denominator` ausgeführt, wird der `catch`-Block ausgeführt, der diese Exception abfängt und eine einfache Fehlermeldung auf der Konsole ausgibt.

Wer bereits einen `Scanner` für Konsoleneingaben verwendet hat oder sich <format color="%LinkColor%">[Kapitel 04 – Ein- und Ausgaben](04-java-io.md)</format> angeschaut hat, wird vielleicht merken, dass die <format color="%LinkColor%">[Methoden](09-java-methods.md)</format> des Scanners ebenfalls eine Exception auslösen können.

Eine `InputMismatchEception` wird geworfen, sobald der Benutzer etwas anderes als eine Zahl eingibt oder wenn sich die Zahl außerhalb des darstellbaren Zahlenbereichs von `int` befindet. Auch diese Exception können wir abfangen, indem wir einen weiteren `catch`-Block hinzufügen.

```Java
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
```

Eine Alternative zum Abfangen der `ArithmeticException` kann auch eine einfache `if`-Abfrage sein, die überprüft, ob die Eingabe ungleich `0` ist.

```Java
if (denominator != 0) {
    int result = numerator / denominator;
    System.out.println("The result is: " + result);
}
```

Wird genauer in die Java-Dokumentation geschaut, fällt auf, dass die Methode `nextInt()` nicht nur eine `ArithmeticException`, sondern noch zwei weitere Exceptions `NoSuchElementException` und `IllegalStateException` werfen kann.

Statt jedoch weitere `catch`-Blöcke hinzuzufügen, können wir einen für alle drei Exceptions schreiben.

```Java
try {
    // ...
} catch (InputMismatchException | NoSuchElementException | IllegalStateException e) {
    System.err.println(e + ": Invalid input. Please enter an integer.");
}
```

Eine `InputMismatchException` erbt von `NoSuchElementException`. Daher können wir `InputMismatchException` auch weglassen. `NoSuchElementException` und `IllegalStateException` erben wiederum von `RuntimeException`. Daher können wir diese beiden durch `RuntimeException` ersetzen.

```Java
try {
    // ...
} catch (RuntimeException e) {
    System.err.println(e + ": Invalid input. Please enter an integer.");
}
```

Wie wir bereits wissen, wird im Allgemeinen empfohlen RuntimeExceptions nicht abzufangen, da sie häufig auf Programmierfehler hinweisen.

Auf `NoSuchElementException` und `IllegalStateException` trifft das zu. Eine `InputMismatchException` kann jedoch durch einen Benutzer ausgelöst werden, wenn dieser eine ungültige Eingabe tätigt. Dieser Fall liegt außerhalb unseres Einflussbereichs, weshalb er programmatisch behandelt werden muss.

```Java
public class Main {

    private static final Scanner SCANNER = new Scanner(System.in);

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
    
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
```

Die Methode `getValidInteger()` besitzt eine rekursive Implementierung. Der Benutzer wird so lange nach einer Ganzzahl gefragt, bis er einen gültigen Wert eingibt.

> Der Lösungsweg innerhalb der Methode `getValidInteger()` ist zwar korrekt, aber ein iterativer Lösungsansatz ist in Bezug auf Speicherverbrauch und Performance stabiler und wird in vielen Fällen oft bevorzugt.

Tatsächlich ist dies ein "Es-kommt-drauf-an"-Fall. In einfachen Konsolenanwendungen spielen übermäßige Eingaben bei Rekursionen kaum eine Rolle. Insbesondere dann, wenn es nur darum geht, dass der Nutzer daran gehindert werden soll, ungültige Eingaben zu tätigen.

Die Implementierung der `getValidInteger()`-Methode ist eine Variante, welche ich selbst in vielen meiner Konsolenanwendungen verwende. Anstelle eines Scanners nutze ich jedoch einen `BufferedReader`.

## Der `finally`-Block {id="the-finally-block"}

Zuvor hatten wir uns angeschaut, wie wir Exceptions abfangen können. Es kann jedoch der Fall sein, dass unabhängig davon, ob eine Exception geworfen wurde oder nicht, "Aufräumarbeiten" stattfinden sollen. Z. B. wenn eine bestehende Ressource, wie ein `Scanner`, geschlossen werden soll.

Um dies zu erreichen, wird der `finally`-Block nach einem `catch`-Block verwendet. Dieser Block wird immer ausgeführt. Egal, ob eine Exception ausgelöst wurde oder nicht.

```Java
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
```

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
        <p>Der <code>finally</code>-Block wird immer ausgeführt. Das bedeutet, dass eine <code>return</code>-Anweisung im <code>finally</code>-Block, die <code>return</code>-Anweisungen im <code>try</code>- und <code>catch</code>-Block überschreibt.</p>
    </tab>
</tabs>

> Solche Beispiele stiften nur Verwirrung. Generell sollten `return`-Anweisungen in `finally`-Blöcken vermieden werden, da dies zu unerwarteten Ergebnissen führen kann.
{style="note"}

In den meisten Fällen werden `finally`-Blöcke nicht benötigt und wenn doch, dann sollte auf <format color="%LinkColor%">[try-with-resources](#try-with-resources)</format>-Blöcke zurückgegriffen werden.

## `try`-with-resources {id="try-with-resources"}

try-with-resources ist eine spezielle Form des `try`-Blocks, die eingeführt wurde, um Ressourcen wie Dateien, Datenbankverbindungen, Netzwerkverbindungen oder andere Objekte automatisch zu schließen. Es bietet eine Alternative zum `finally`-Block und schließt am Ende des `catch`-Blocks automatisch die Ressource, unabhängig davon, ob eine Exception geworfen wurde oder nicht. 

```Java
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
```

> Ressourcen, die in einem try-with-resources-Block verwendet werden, müssen das `AutoCloseable`-<format color="%LinkColor%">[Interface](14-java-oop.md#interfaces)</format> implementieren, welches die Methode `close()` enthält.
{style="note"}

## Exceptions werfen {id="throw-exceptions"}

Exceptions werden geworfen, wenn ein unerwarteter Zustand oder ein Fehler auftritt, der vom aktuellen Codeabschnitt nicht direkt behoben werden kann. Das Werfen einer Exception mittels `throw` ermöglicht es, das Problem an den Aufrufer weiterzuleiten, der entweder die Exception mittels `try`-`catch`behandelt oder sie weiter nach oben im Aufrufstapel propagieren lässt.

Nehmen wir unsere `Dog`-Klasse aus den letzten Kapiteln als Beispiel. Der <format color="%LinkColor%">[Konstruktor](10-java-classes.md#constructors)</format> erwartet ein Alter als Parameter. Ein negatives Alter wäre ungültig, also könnte eine `IllegalArgumentException` geworfen werden.

```Java
public Dog(String name, int age) {
    if (age < 0) {
        throw new IllegalArgumentException("Age cannot be negative");
    }
    this.name = name;
    this.age = age;
}
```

## Eigene Exceptions erstellen {id="create-your-own-exceptions"}

In manchen Situationen ist es nötig, eine spezifische Exception zu haben, die einen Fehler genauer beschreibt. In solchen Fällen kann eine eigene Exception-Klasse erstellt werden und diese werfen.

```Java
public class InvalidAgeException extends Exception {

    public InvalidAgeException(String message) {
        super(message);
    }
}

public class Dog {

    // ...
    
    public Dog(String name, int age) {
        if (age < 0) {
            throw new InvalidAgeException("Age cannot be negative");
        }
        this.name = name;
        this.age = age;
    }
    
    // ...
}
```