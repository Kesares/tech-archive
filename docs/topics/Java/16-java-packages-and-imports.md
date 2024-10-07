# 16 Java – Pakete und Imports

Mit Sicherheit sind euch am Anfang in euren Dateien oder auch hier im <format color="%Highlight%">Tech-Archive</format> bestimmte Zeilen wie `package kesares.techarchive` oder `import java.util.List` aufgefallen.

In Java werden Klassen in sogenannten Paketen (Packages) organisiert. Ein Package ist eine Sammlung von zusammengehörigen <format color="%LinkColor%">[Klassen](10-java-classes.md)</format>, <format color="%LinkColor%">[Interfaces](14-java-oop.md#interfaces)</format>, <format color="%LinkColor%">[Enums](13-java-enumerations.md)</format>, etc. die logisch gruppiert sind. Sie helfen dabei, den Code zu strukturieren und Namenskonflikte zu vermeiden. Zudem fördern Pakete auch die Zugriffskontrolle.

![16_java_packages_imports_1.png](16_java_packages_imports_1.png)

## Package-Zugriff aus anderem Package {id="access-package-from-another-package"}

Es gibt drei Möglichkeiten, um von außerhalb auf ein Package zuzugreifen.

1. `import package.*`
2. `import package.className`
3. Angabe des vollständig qualifizierten Namens

### Verwendung von `import package.*` {id="import-package"}

Wird `import package.*` verwendet, erhält die Klasse Zugriff auf sämtliche <format color="%LinkColor%">[Klassen](10-java-classes.md)</format> und <format color="%LinkColor%">[Schnittstellen](14-java-oop.md#interfaces)</format> innerhalb dieses Packages, jedoch nicht auf Subpackages.

```Java
package kesares.print;

public class Printer {

    public void printHello() {
        System.out.println("Hello!");
    }
}
```

```Java
package kesares.techarchive;

import kesares.print.*;

public class Main {

    public static void main(String[] args) {
        Printer printer = new Printer();
        printer.printHello();
    }
}
```

### Verwendung von `import package.className` {id="import-package-class-name"}

Wenn jedoch `package.className` importiert wird, hat die <format color="%LinkColor%">[Klasse](10-java-classes.md)</format> nur auf die deklarierte Klasse des Packages Zugriff.

```Java
package kesares.print;

public class Printer {

    public void printHello() {
        System.out.println("Hello!");
    }
}
```

```Java
package kesares.print;

public class Manager {

    public void printHello() {
        System.out.println("Hello!");
    }
}
```

```Java
package kesares.techarchive;

import kesares.print.Printer;

public class Main {

    public static void main(String[] args) {
        Test test = new Test();
        test.printHello();
        
        Manager manager = new Manager(); // Compile error!
        manager.printHello();
    }
}
```

### Verwendung des vollständig qualifizierten Namens {id="full-qualified-name"}

Auch wenn der vollständige qualifizierte Name einer <format color="%LinkColor%">[Klasse](10-java-classes.md)</format> angegeben wird, ist nur diese deklarierte Klasse zugänglich.

Hierbei ist `import` nicht notwendig. Allerdings muss jedes Mal der vollständig qualifizierte Name angegeben werden, wenn auf diese Klasse zugegriffen wird.

```Java
package kesares.print;

public class Printer {

    public void printHello() {
        System.out.println("Hello!");
    }
}
```

```Java
package kesares.techarchive;

public class Main {

    public static void main(String[] args) {
        kesares.print.Printer printer = new kesares.print.Printer();
        printer.printHello();
    }
}
```

Es wird meistens verwendet, wenn zwei Packages denselben Klassennamen haben. Die Packages `java.util` und `java.sql` enthalten z. B. jeweils eine `Date`-Klasse.

## Subpackages {id="subpackages"}

Subpackages sind Unterpakete eines Hauptpakets und dienen dazu, den Code besser zu strukturieren und organisieren. Ein Paket kann beliebig viele Subpackages enthalten und diese wiederum ebenfalls weitere Subpackages.

Im vorherigen Abschnitt <format color="%LinkColor%">[Package-Zugriff aus anderem Package](#access-package-from-another-package)</format> haben wir die Subpackages `kesares.techarchive` und `kesares.print` verwendet. Die Struktur der Subpackages folgt dabei einer hierarchischen Ordnung, die durch Punkte getrennt wird. In einem Dateisystem fungieren alle Packages wie normale Verzeichnisse oder Ordner. Das vorherige Beispiel würde auf der Festplatte dann folgendermaßen aussehen.

```
kesares
├───techarchive
│   └───Main.java
└───print
    └───Printer.java
```

Anderes Beispiel: Sun Microsystems hat ein Hauptpaket `java` definiert, welches zahlreiche <format color="%LinkColor%">[Klassen](10-java-classes.md)</format> wie `System`, `String`, `Reader`, `Writer`, `Proxy`, `Socket` und noch viele mehr enthält. Diese Klassen sind thematisch in verschiedene Gruppen kategorisiert. `Reader` und `Writer` dienen dabei als Ein- und Ausgabe von Zeichenströmen (character streams), während `Socket` und `Proxy` Klassen für die Netzwerkkommunikation bereitstellen.

Um die Verwaltung zu erleichtern, wurde das `java`-Package in mehrere Subpackages unterteilt, darunter `java.lang`, `java.io` und `java.net`. Die <format color="%LinkColor%">[Klassen](10-java-classes.md)</format> `Reader` und `Writer` sind dabei dem `java.io`-Package und die Klassen `Socket` und `Proxy` dem `java.net`-Package zugeordnet.

<note>
    <p>Standardmäßig wird <code>domain.company.package.subpackage</code> als Definition für Pakete verwendet.</p> 
    <p>Beispiele: <code>com.fasterxml.jackson.core</code> oder <code>com.google.common</code></p>
</note>

## Das `java.lang`-Package {id="the-java-lang-package"}

Das `java.lang`-Package ist eines der zentralen und wichtigsten Pakete in der Java-Standardbibliothek. Es wird automatisch in jedem Java-Programm importiert, sodass die darin enthaltenen <format color="%LinkColor%">[Klassen](10-java-classes.md)</format> ohne expliziten Import verwendet werden können.

`java.lang` stellt unter anderem die folgenden grundlegenden Klassen zur Verfügung, die essenziell für die Programmierung mit Java sind.

- `Object`: Kennen wir bereits aus <format color="%LinkColor%">[Kapitel 14 – OOP: Die Mutter aller Klassen – Object](14-java-oop.md)</format>. Von dieser <format color="%LinkColor%">[Klasse](10-java-classes.md)</format> erben alle anderen Klassen direkt oder indirekt.
- `String`: Auch diese Klasse kennen wir bereits aus <format color="%LinkColor%">[Kapitel 5 – Zeichenketten](05-java-strings.md)</format>, welche zur Arbeit mit Zeichenketten dient.
- `Math`: Die `Math`-Klasse wurde bereits in <format color="%LinkColor%">[Kapitel 09 – Methoden: Die `Math`-Klasse](09-java-methods.md#the-math-class)</format> vorgestellt und bietet unter anderem mathematische Funktionen für Logarithmen und Exponentialrechnung.
- `System`: Ermöglicht den Zugriff auf Systemressourcen, wie die Standard-Ein- und Ausgabe oder den Zugriff auf Umgebungsvariablen.
- `Thread`: Dient zur Erstellung und Verwaltung von <format color="%LinkColor%">[Threads](java-multithreading.md)</format> für die Parallelverarbeitung.

> Da `java.lang` so grundlegend ist, wird es oft auch als "Kernpaket" (core package) der Java-Plattform bezeichnet.

## Statischer Import –`import static` {id="import-static"}

Die statische Importfunktion wurde in Java 5 hinzugefügt und erleichtert das häufige Arbeiten mit statischen Klassenmitgliedern (<format color="%LinkColor%">[](10-java-classes.md#class-methods)</format>, <format color="%LinkColor%">[](10-java-classes.md#class-variables)</format>und <format color="%LinkColor%">[](10-java-classes.md#constants)</format>).

Die Syntax ähnelt der regulären Importanweisung hinsichtlich der durch Punkte getrennten Liste von Paket- und Unterpaketnamen und es können ebenso einzelne bzw. alle statischen Mitglieder einer <format color="%LinkColor%">[Klasse](10-java-classes.md)</format> importiert werden.

```Java
import static java.lang.Math.PI;  // imports only the static constant PI
import static java.lang.Math.cos; // imports only the static method cos()
import static java.lang.Math.*;   // imports all static members of Math
```

```Java
import static java.lang.Math.PI;
import static java.lang.Math.cos;

public class Main {

    public static void main(String[] args) {
        double d = cos(PI); // no errors
    }
}
```

<note>
    <p>Werden mehrere statische Mitglieder importiert, die die gleiche Methodensignatur aufweisen, zeigt der <tooltip term="Compiler"><format color="%GlossaryLinkColor%">Compiler</format></tooltip> einen Fehler wie im folgenden Beispiel an.</p>
    <warning>
        <p>java: reference to cos is ambiguous</p>
        <p>both method cos(double) in test.Math and method cos(double) in java.lang.Math match</p>
    </warning>
</note>

