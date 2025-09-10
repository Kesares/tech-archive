# 16 Java – Pakete und Imports

<p>Mit Sicherheit sind euch am Anfang in euren Dateien oder auch hier im
<format color="%Highlight%">Tech-Archive</format> bestimmte Zeilen wie <code>package kesares.techarchive</code> oder
<code>import java.util.List</code> aufgefallen.</p>

<p>In Java werden Klassen in sogenannten Paketen (Packages) organisiert. Ein Package ist eine Sammlung von
zusammengehörigen <format color="%LinkColor%"><a href="10-java-classes.md">Klassen</a></format>,
<format color="%LinkColor%"><a href="14-java-oop.md#interfaces">Interfaces</a></format>,
<format color="%LinkColor%"><a href="13-java-enumerations.md">Enums</a></format>, etc. die logisch gruppiert sind. Sie
helfen dabei, den Code zu strukturieren und Namenskonflikte zu vermeiden. Zudem fördern Pakete auch die
Zugriffskontrolle.</p>

<img src="16_java_packages_imports_1.png" alt="16_java_packages_imports_1.png" />

## Package-Zugriff aus anderem Package {id="access-package-from-another-package"}

<p>Es gibt drei Möglichkeiten, um von außerhalb auf ein Package zuzugreifen.</p>

<list type="decimal">
  <li><code>import package.*</code></li>
  <li><code>import package.className</code></li>
  <li>Angabe des vollständig qualifizierten Namens</li>
</list>

### Verwendung von `import package.*` {id="import-package"}

<p>Wird `import package.*` verwendet, erhält die Klasse Zugriff auf sämtliche
<format color="%LinkColor%"><a href="10-java-classes.md">Klassen</a></format> und
<format color="%LinkColor%">[Schnittstellen](14-java-oop.md#interfaces)</format> innerhalb dieses Packages, jedoch nicht
auf Subpackages.</p>

<code-block lang="java">
    package kesares.print;
    
    public class Printer {
    
        public void printHello() {
            System.out.println("Hello!");
        }
    }
</code-block>

<code-block lang="java">
    package kesares.techarchive;
    
    import kesares.print.*;
    
    public class kesares.techarchive.Main {
    
        public static void main(String[] args) {
            Printer printer = new Printer();
            printer.printHello();
        }
    }
</code-block>

### Verwendung von `import package.className` {id="import-package-class-name"}

<p>Wenn jedoch <code>package.className</code> importiert wird, hat die
<format color="%LinkColor%"><a href="10-java-classes.md">Klasse</a></format> nur auf die deklarierte Klasse des Packages
Zugriff.</p>

<code-block lang="java">
    package kesares.print;
    
    public class Printer {
    
        public void printHello() {
            System.out.println("Hello!");
        }
    }
</code-block>

<code-block lang="java">
    package kesares.print;
    
    public class Manager {
    
        public void printHello() {
            System.out.println("Hello!");
        }
    }
</code-block>

<code-block lang="java">
    package kesares.techarchive;
    
    import kesares.print.Printer;
    
    public class kesares.techarchive.Main {
    
        public static void main(String[] args) {
            Test test = new Test();
            test.printHello();
            
            Manager manager = new Manager(); // Compile error!
            manager.printHello();
        }
    }
</code-block>

### Verwendung des vollständig qualifizierten Namens {id="full-qualified-name"}

<p>Auch wenn der vollständige qualifizierte Name einer
<format color="%LinkColor%"><a href="10-java-classes.md">Klasse</a></format> angegeben wird, ist nur diese deklarierte
Klasse zugänglich.</p>

<p>Hierbei ist <code>import</code> nicht notwendig. Allerdings muss jedes Mal der vollständig qualifizierte Name
angegeben werden, wenn auf diese Klasse zugegriffen wird.</p>

<code-block lang="java">
    package kesares.print;
    
    public class Printer {
    
        public void printHello() {
            System.out.println("Hello!");
        }
    }
</code-block>

<code-block lang="java">
    package kesares.techarchive;
    
    public class kesares.techarchive.Main {
    
        public static void main(String[] args) {
            kesares.print.Printer printer = new kesares.print.Printer();
            printer.printHello();
        }
    }
</code-block>

<p>Es wird meistens verwendet, wenn zwei Packages denselben Klassennamen haben. Die Packages <code>java.util</code> und
<code>java.sql</code> enthalten z. B. jeweils eine <code>Date</code>-Klasse.</p>

## Subpackages {id="subpackages"}

<p>Subpackages sind Unterpakete eines Hauptpakets und dienen dazu, den Code besser zu strukturieren und organisieren.
Ein Paket kann beliebig viele Subpackages enthalten und diese wiederum ebenfalls weitere Subpackages.</p>

<p>Im vorherigen Abschnitt
<format color="%LinkColor%"><a href="#access-package-from-another-package">Package-Zugriff aus anderem Package</a></format> haben wir die Subpackages `kesares.techarchive` und `kesares.print` verwendet. Die
Struktur der Subpackages folgt dabei einer hierarchischen Ordnung, die durch Punkte getrennt wird. In einem Dateisystem
fungieren alle Packages wie normale Verzeichnisse oder Ordner. Das vorherige Beispiel würde auf der Festplatte dann
folgendermaßen aussehen.</p>

<code-block lang="text">
    kesares
    ├───techarchive
    │   └───kesares.techarchive.Main.java
    └───print
        └───Printer.java
</code-block>

<p>Anderes Beispiel: Sun Microsystems hat ein Hauptpaket <code>java</code> definiert, welches zahlreiche
<format color="%LinkColor%"><a href="10-java-classes.md">Klassen</a></format> wie <code>System</code>,
<code>String</code>, <code>Reader</code>, <code>Writer</code>, <code>Proxy</code>, <code>Socket</code> und noch viele
mehr enthält. Diese Klassen sind thematisch in verschiedene Gruppen kategorisiert. `Reader` und `Writer` dienen dabei
als Ein- und Ausgabe von Zeichenströmen (character streams), während `Socket` und `Proxy` Klassen für die
Netzwerkkommunikation bereitstellen.</p>

<p>Um die Verwaltung zu erleichtern, wurde das <code>java</code>-Package in mehrere Subpackages unterteilt, darunter
<code>java.lang</code>, <code>java.io</code> und <code>java.net</code>. Die
<format color="%LinkColor%"><a href="10-java-classes.md">Klassen</a></format> <code>Reader</code> und
<code>Writer</code> sind dabei dem <code>java.io</code>-Package und die Klassen <code>Socket</code> und
<code>Proxy</code> dem <code>java.net</code>-Package zugeordnet.</p>

<note>
    <p>Standardmäßig wird <code>domain.company.package.subpackage</code> als Definition für Pakete verwendet.</p> 
    <p>Beispiele: <code>com.fasterxml.jackson.core</code> oder <code>com.google.common</code></p>
</note>

## Das `java.lang`-Package {id="the-java-lang-package"}

<p>Das <code>java.lang</code>-Package ist eines der zentralen und wichtigsten Pakete in der Java-Standardbibliothek. Es
wird automatisch in jedem Java-Programm importiert, sodass die darin enthaltenen
<format color="%LinkColor%"><a href="10-java-classes.md">Klassen</a></format> ohne expliziten Import verwendet werden
können.</p>

<p><code>java.lang</code> stellt unter anderem die folgenden grundlegenden Klassen zur Verfügung, die essenziell für die
Programmierung mit Java sind.</p>

<list>
  <li>
    <p><code>Object</code>: Kennen wir bereits aus
        <format color="%LinkColor%"><a href="14-java-oop.md">Kapitel 14 – OOP: Die Mutter aller Klassen – Object</a></format>.
        Von dieser <format color="%LinkColor%"><a href="10-java-classes.md">Klasse</a></format> erben alle anderen
        Klassen direkt oder indirekt.</p>
</li>
  <li>
    <p><code>String</code>: Auch diese Klasse kennen wir bereits aus
    <format color="%LinkColor%"><a href="05-java-strings.md">Kapitel 5 – Zeichenketten</a></format>, welche zur Arbeit
    mit Zeichenketten dient.</p>
  </li>
  <li>
    <p><code>Math</code>: Die `Math`-Klasse wurde bereits in
    <format color="%LinkColor%"><a href="09-java-methods.md#the-math-class">Kapitel 09 – Methoden: Die <code>Math</code>-Klasse</a></format>
    vorgestellt und bietet unter anderem mathematische Funktionen für Logarithmen und Exponentialrechnung.</p>
  </li>
  <li>
    <p><code>System</code>: Ermöglicht den Zugriff auf Systemressourcen, wie die Standard-Ein- und Ausgabe oder den
    Zugriff auf Umgebungsvariablen.</p>
  </li>
  <li>
    <p><code>Thread</code>: Dient zur Erstellung und Verwaltung von
    <format color="%LinkColor%"><a href="27-java-multithreading.md">Threads</a></format> für die Parallelverarbeitung.
    </p>
  </li>   
</list>

<tip>Da <code>java.lang</code> so grundlegend ist, wird es oft auch als "Kernpaket" (core package) der Java-Plattform
bezeichnet.</tip>

## Statischer Import –`import static` {id="import-static"}

<p>Die statische Importfunktion wurde in Java 5 hinzugefügt und erleichtert das häufige Arbeiten mit statischen
Klassenmitgliedern (<format color="%LinkColor%"><a href="10-java-classes.md#class-methods">Klassenmethoden</a></format>,
<format color="%LinkColor%"><a href="10-java-classes.md#class-variables">Klassenvariablen</a></format> und
<format color="%LinkColor%"><a href="10-java-classes.md#constants">Konstanten</a></format>).</p>

<p>Die Syntax ähnelt der regulären Importanweisung hinsichtlich der durch Punkte getrennten Liste von Paket- und
Unterpaketnamen und es können ebenso einzelne bzw. alle statischen Mitglieder einer
<format color="%LinkColor%"><a href="10-java-classes.md">Klasse</a></format> importiert werden.</p>

<code-block lang="java">
    import static java.lang.Math.PI;  // imports only the static constant PI
    import static java.lang.Math.cos; // imports only the static method cos()
    import static java.lang.Math.*;   // imports all static members of Math
</code-block>

<code-block lang="java">
    import static java.lang.Math.PI;
    import static java.lang.Math.cos;
    
    public class kesares.techarchive.Main {
    
        public static void main(String[] args) {
            double d = cos(PI); // no errors
        }
    }
</code-block>

<warning>
    <p>Werden mehrere statische Mitglieder importiert, die die gleiche Methodensignatur aufweisen, zeigt der
    <tooltip term="Compiler"><format color="%GlossaryLinkColor%">Compiler</format></tooltip> einen Fehler wie im
    folgenden Beispiel an.</p>
    <code-block>
        java: reference to cos is ambiguous
        both method cos(double) in test.Math and method cos(double) in java.lang.Math match
    </code-block>
</warning>

