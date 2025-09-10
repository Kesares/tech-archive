# 10 Java – Klassen

<p>Klassen sind ein wesentlicher Bestandteil der
<format color="%LinkColor%"><a href="14-java-oop.md">OOP – Objektorientierten Programmierung</a></format>. Sie sind
vergleichbar mit Rezepten oder Blueprints und stellen die grundlegende Struktur und den Aufbau von konkret
instanziierten <format color="%LinkColor%"><a href="11-java-objects.md">Objekten</a></format> dar – deren Eigenschaften
(<format color="%LinkColor%"><a href="#object-variables">Objektvariablen</a></format>) und Funktionalitäten
(<format color="%LinkColor%"><a href="#object-methods">Objektmethoden</a></format>). Jede Klasse, die in Java erstellt
wird, <format color="%LinkColor%"><a href="14-java-oop.md#inheritance">erbt</a></format> automatisch von der
<format color="%LinkColor%"><a href="14-java-oop.md#the-mother-of-all-classes-object">Klasse <code>Object</code></a>
</format>.</p>

<p>Alle <format color="%LinkColor%"><a href="03-java-variables.md">Variablen</a></format> und
<format color="%LinkColor%"><a href="09-java-methods.md">Methoden</a></format>, die in Java deklariert werden, sind von
solch einer <format color="%LinkColor%"><a href="#class-structure">Klassendefinition</a></format> ummantelt – unabhängig
davon, ob sie zu einem <format color="%LinkColor%"><a href="11-java-objects.md">Objekt</a></format> gehören oder nicht.
Der Name der Datei muss zudem genauso heißen, wie der Name der Klasse, die sich innerhalb der Datei befindet.</p>

## Klassenaufbau {id="class-structure"}

<p>Der Aufbau einer Klasse ist nicht in Stein gemeißelt. Er kann sich von Unternehmen zu Unternehmen unterscheiden. Eine
weit verbreitete Anordnung sieht folgendermaßen aus.</p>

<code-block lang="java">
    public class ClassName {
    
        // Constants and static or class variables
    
        // Instance or object variables
    
        // Constructors
    
        // Static or class methods
    
        // Instance or object methods
    
        // Getters and setters
    
        // Inner classes
    }
</code-block>

<tip>
    <p>Zudem sollten alle öffentlichen (mit <code>public</code> deklarierten), geschützten (mit <code>protected</code>
    deklarierten) und privaten (mit <code>private</code> deklarierten) Methoden jeweils nahe beieinander stehen.</p>
</tip>

## Klassenvariablen {id="class-variables"}

<p>Klassenvariablen oder auch statische Variablen werden mit dem
<format color="%LinkColor%"><a href="12-java-modifier-access-rights.md">Keyword</a></format> <code>static</code>
 gebildet und sollten ganz oben innerhalb einer Klassendefinition deklariert werden. Sie existieren unabhängig von einem
Objekt und werden meist mit dem Keyword <code>final</code> deklariert. Variablen mit dem Keyword <code>final</code>
 werden <format color="%LinkColor%"><a href="#constants">Konstanten</a></format> genannt, da sich deren Wert nach
Initialisierung nicht mehr ändern kann.</p>

### Konstanten {id="constants"}

<note>
    <p>Alle Konstanten sind Klassenvariablen – aber nicht alle Klassenvariablen sind Konstanten.</p>
</note>

<p>Zwei Beispiel-Konstanten aus der <code>Math</code>-Klasse:</p>

<img src="10_java_classes_1.png" alt="Konstanten aus der Math-Klasse" border-effect="line"/>

## Objektvariablen {id="object-variables"}

<p>Objekt- oder Instanzvariablen werden unterhalb der
<format color="%LinkColor%"><a href="#class-variables">Klassenvariablen</a></format> aber oberhalb von
<format color="%LinkColor%"><a href="#constructors">Konstruktoren</a></format> deklariert. Diese Variablen gehören immer
zu einem konkreten <format color="%LinkColor%"><a href="11-java-objects.md">Objekt</a></format> und dienen als
igenschaften des Objekts wie beispielsweise der Name oder die Farbe eines Tiers. Objektvariablen können nur über ein
bestehendes Objekt angesprochen werden.</p>

<p>Instanzvariablen können sowohl aus
<format color="%LinkColor%"><a href="02-java-data-types.md#primitive-data-types">primitiven Datentypen</a></format> als
auch aus <format color="%LinkColor%"><a href="02-java-data-types.md#reference-data-types-outlook">Referenzdatentypen</a>
</format> wie z. B. <format color="%LinkColor%"><a href="05-java-strings.md">Strings</a></format> bestehen.</p>

<code-block lang="java">
    public class Dog {
    
        public String name;
        public int age;
    }
</code-block>

<p>Die Initialisierung dieser Variablen übernimmt in den meisten Fällen der
<format color="%LinkColor%"><a href="#constructors">Konstruktor</a></format>.</p>

## Konstruktoren {id="constructors"}

<p>Eine spezielle Art der Methode ist der Konstruktor. Er besitzt keinen
<format color="%LinkColor%"><a href="09-java-methods.md#return-type">Rückgabewert</a></format> – nicht mal das
<format color="%LinkColor%"><a href="01-java-token.md#keywords">Keyword</a></format> <code>void</code>. Zudem muss der
Konstruktor denselben Namen wie die Klasse besitzen. Er ist für das eigentliche Initialisieren der
<format color="%LinkColor%"><a href="11-java-objects.md">Objekte</a></format> verantwortlich.</p>

<p>Beim Erstellen eines Objekts wird der Konstruktor aufgerufen. Dabei können ihm Werte mit übergeben werden, mit denen
die <format color="%LinkColor%"><a href="#object-variables">Objektvariablen</a></format> des jeweiligen Objekts
initialisiert werden.</p>

<code-block lang="java">
    public class Dog {
    
        public String name;
        public int age;
    
        public Dog(String name, int age) {
            name = name;
            age = age;
        }
    }
</code-block>

<p>Wurde kein Konstruktor programmiert, wird automatisch der Default-Konstruktor aufgerufen, welcher keine Parameter
erwartet. Dieser kann auch optional selber geschrieben werden.</p>

<code-block lang="java">
    public class Dog {
    
        public String name;
        public int age;
    
        public Dog() {
    
        }
    }
</code-block>

Auch mehrere Konstruktoren sind möglich.

<code-block lang="java">
    public class Dog {
    
        public String name;
        public int age;
    
        public Dog(String name, int age) {
            name = name;
            age = age;
        }
    
        public Dog(String name) {
            name = name;
            age = 0;
        }
    }
</code-block>

<warning>
    In beiden Konstruktoren gibt es jedoch ein Problem.
</warning>

## Verdeckte Variablen {id="shadowed-variables"}

<p>Werden in Codeblöcken neue Variablennamen eingeführt, können diese nicht noch einmal angelegt werden. Heißt die
lokale Variable einer Methode genauso wie eine
<format color="%LinkColor%"><a href="#object-variables">Objektvariable</a></format>, spricht man auch von einer
verdeckten oder <format color="%Highlight%">shadowed Variablen</format>.</p>

<p>An sich besteht in solchen Fällen kein Problem. Der
<tooltip term="Compiler"><format color="%GlossaryLinkColor%">Compiler</format></tooltip> wird dann standardmäßig die
lokale Variable nutzen. Durch dieses Vorgehen können später neu hinzugefügte Objektvariablen keinen schon bestehenden
Code zerstören.</p>

<p>Eine kleine Komplikation besteht nur, wenn die
<format color="%LinkColor%"><a href="#object-variables">Objektvariable</a></format> mit einer lokalen Variablen genutzt
werden soll. In diesem Fall wird der Wert der lokalen Variablen verwendet und erneut der lokalen Variablen zugewiesen.
</p>

<code-block lang="java">
    public class Dog {
    
        public String name;
        public int age;
    
        public Dog(String name, int age) {
            name = name; // &lt;-- here
            age = age;   // &lt;-- here
        }
    
        public Dog(String name) {
            name = name; // &lt;-- here
            age = 0;
        }
    }
</code-block>

<p> Dafür gibt es jedoch eine Lösung.</p>

## Das Keyword `this` {id="the-keyword-this"}

<p>Natürlich können bei solchen Problemen die lokalen oder
<format color="%LinkColor%"><a href="#object-variables">Objektvariablen</a></format> umbenannt werden. Müssen diese an
mehreren Stellen geändert werden, kann der Aufwand jedoch etwas größer werden. Möchte man die beiden
<format color="%LinkColor%"><a href="03-java-variables.md">Variablen</a></format> also gerne gleich benennen, kann das
Keyword <code>this</code> Abhilfe schaffen.</p>

<p>Das Schlüsselwort <code>this</code> funktioniert ähnlich wie eine Referenzvariable, indem es auf ein bestimmtes
<format color="%LinkColor%"><a href="11-java-objects.md">Objekt</a></format> verweist – allerdings in einem spezifischen
Kontext. Anders ausgedrückt: Ein Objekt verweist mit <code>this</code> auf sich selbst. <code>this</code> bezieht sich
auf genau das Objekt, das gerade verwendet wird, bzw. in dessen Kontext (<format color="%Highlight%">Klasse</format>) man
sich aktuell befindet.</p>

<code-block lang="java">
    public class Dog {
    
        public String name;
        public int age;
    
        public Dog(String name, int age) {
            this.name = name;
            this.age = age;
        }
    
        public Dog(String name) {
            this.name = name;
            this.age = 0;
        }
    }
</code-block>

<p>Ein weiterer Vorteil von <code>this</code> ist, dass die folgenden beiden
<format color="%LinkColor%"><a href="#constructors">Konstruktoren</a></format> miteinander verknüpft werden können.
Dadurch wird redundanter Code vermieden.</p>

<code-block lang="java">
    public class Dog {
    
        public String name;
        public int age;
    
        public Dog(String name, int age) {
            this.name = name;
            this.age = age;
        }
    
        public Dog(String name) {
            this(name, 0);
        }
    }
</code-block>

<p>Der untere <format color="%LinkColor%"><a href="#constructors">Konstruktor</a></format> ruft nun den oberen
Konstruktor mit dem ergänzenden Wert auf.</p>

## Klassenmethoden {id="class-methods"}

<p>Im vorherigen <format color="%LinkColor%"><a href="09-java-methods.md">Kapitel 9 – Methoden</a></format> gab es
bereits viele Beispiele zu Klassenmethoden. Klassenmethoden brauchen wie
<format color="%LinkColor%"><a href="#class-variables">Klassenvariablen</a></format> kein bestimmtes
<format color="%LinkColor%"><a href="11-java-objects.md">Objekt</a></format> um auf diese zugreifen zu können. Sie
werden mit dem Keyword <code>static</code> gebildet und werden über den Klassennamen angesprochen.</p>

<code-block lang="java">
    public static void print(String text) {
        System.out.println(text);
    }
    
    public static void main(String[] args) {
        print("Hello World!");
    }
</code-block>

## Objektmethoden {id="object-methods"}

<p>Alle weiteren Objektmethoden sollten nach den <format color="%LinkColor%"><a href="#class-methods">Klassenmethoden
</a></format> stehen und können nur über ein bestehendes <format color="%LinkColor%"><a href="11-java-objects.md">Objekt
</a></format> aufgerufen werden.</p>

<code-block lang="java">
    public class Dog {
    
        public String name;
        public int age;
    
        public Dog(String name, int age) {
            this.name = name;
            this.age = age;
        }
    
        public Dog(String name) {
            this(name, 0);
        }
    
        // Object methods
        public void eat() {
            System.out.println(this.name + " is eating!");
        }
    
        public void bark() {
            System.out.println(this.name + " barks!");
        }
    }
</code-block>

## Getter- & Setter-Methoden {id="getter-and-setter"}

<p>Getter und Getter dienen dazu, <format color="%LinkColor%"><a href="#object-variables">Objektvariablen</a></format>
 abzugreifen (<format color="%Highlight%">get-Methoden</format>) oder deren Werte zu überschreiben bzw. sie zu
initialisieren (<format color="%Highlight%">set-Methoden</format>). Sie können für jede Objektvariable angelegt werden.
Durch diese Methoden kann somit festgelegt werden, ob überhaupt auf die Variablen zugegriffen werden kann, wenn diese
beispielsweise als <code>private</code> deklariert wurden (siehe <format color="%LinkColor%">
<a href="12-java-modifier-access-rights.md">Kapitel 12 – Modifizierer und Zugriffsrechte</a></format>).</p>

<code-block lang="java">
    public class Dog {
    
        private String name; // Not visible outside the class
        private int age;     // Not visible outside the class
    
        public Dog(String name, int age) {
            this.name = name;
            this.age = age;
        }
    
        public Dog(String name) {
            this(name, 0);
        }
    
        public void eat() {
            System.out.println(this.name + " is eating!");
        }
    
        public void bark() {
            System.out.println(this.name + " barks!");
        }
    
        public String getName() {
            return name;
        }
    
        public void setName(String name) {
            this.name = name;
        }
    
        public int getAge() {
            return age;
        }
    }
</code-block>

## Klasseninitialisierer {id="class-initializer"}

<p>Wird eine Klasse vom <code>ClassLoader</code> in die <format color="%Highlight%">Runtime Environment</format> geladen, werden
zunächst die statischen Blöcke von oben nach unten ausgeführt. Dies tritt auf, sobald eine
<format color="%LinkColor%"><a href="#class-variables">Klassenvariable</a></format> oder
<format color="%LinkColor%"><a href="#class-methods">Klassenmethode</a></format> zum ersten Mal aufgerufen oder eine
<format color="%LinkColor%"><a href="11-java-objects.md">Instanz</a></format> der Klasse erstellt wird.</p>

<code-block lang="java">
    public class Main {
    
        static {
            System.out.println("Class initialization block 1");
        }
    
        public static void main(String[] args) {
            System.out.println("Main-Program started...");
        }
    
        static {
            System.out.println("Class initialization block 2");
        }
    }
</code-block>

<code-block>
    Class initialization block 1
    Class initialization block 2
    Main-Program started...
</code-block>

<p>Da die Initialisierung einer Klasse nur ein einziges Mal pro Programmausführung stattfindet, können dadurch auch
<format color="%LinkColor%"><a href="#class-variables">Klassenvariablen</a></format> initialisiert werden.</p>

<p>Zudem ermöglichen Klasseninitialisierer die Ausführung von komplexer Initialisierungslogik, die über einfache
Zuweisungen hinausgeht, z. B. das Einlesen von Konfigurationsdateien oder das Einrichten von sonstigen statischen
Ressourcen.</p>

## Innere Klassen {id="inner-classes"}

<p>Innere Klassen werden innerhalb einer anderen Klasse definiert. Diese inneren Klassen haben Zugriff auf die
Mitglieder der äußeren Klasse, einschließlich mit <code>private</code> deklarierten Methoden und Variablen und bieten eine
Möglichkeit, logische Beziehungen zwischen Klassen zu modellieren. Es gibt verschiedene Arten von inneren Klassen und
jede hat ihren eigenen Anwendungsfall.</p>

### Nicht-statische innere Klassen {id="non-static-inner-classes"}

<p>Wenn eine innere Klasse keine <code>static</code>-Deklaration hat, handelt es sich um eine nicht-statische innere
Klasse. Sie werden innerhalb von einer anderen Klasse definiert, aber außerhalb von
<format color="%LinkColor%"><a href="09-java-methods.md">Methoden</a></format>,
<format color="%LinkColor%"><a href="#constructors">Konstruktoren</a></format> und Anweisungsblöcken (z. B.
<format color="%LinkColor%"><a href="#class-initializer">Klasseninitialisierer</a></format>).</p>

<p>Nicht-statische innere Klassen haben Zugriff auf alle Mitglieder (statische und nicht-statische Variablen und
Methoden) der äußeren Klasse. Ein <format color="%LinkColor%"><a href="11-java-objects.md">Objekt</a></format> der
inneren Klasse ist an ein Objekt der äußeren Klasse gebunden</p>

<code-block lang="java">
    public class Player {
    
        private String name;
        private Properties properties;
    
        public Player(String name) {
            this.name = name;
            this.properties = new Properties(1, new String[] {"jump", "run", "swim"});
        }
    
        public String getName() {
            return name;
        }
    
        public Properties getProperties() {
            return properties;
        }
    
        // Inner non-static class
        public class Properties {
        
            private int level;
            private String[] abilities;
    
            public Properties(int level, String[] abilities) {
                this.level = level;
                this.abilities = abilities;
            }
    
            public int getLevel() {
                return level;
            }
    
            public void setLevel(int level) {
                this.level = level;
            }
    
            public String[] getAbilities() {
                return abilities;
            }
    
            public void setAbilities(String[] abilities) {
                this.abilities = abilities;
            }
        }
    }
</code-block>

<p>Nicht-statische innere Klassen sind nützlich, wenn die innere Klasse stark von der äußeren Klasse abhängt und auf
deren <format color="%LinkColor%"><a href="#object-variables">Objektvariablen</a></format> und
<format color="%LinkColor%"><a href="#object-methods">-methoden</a></format> zugreifen muss. Ein klassisches Beispiel
ist ein <code>Iterator</code>, der als innere Klasse in einer
<format color="%LinkColor%"><a href="19-java-collections.md">Collection</a> </format> wie <code>List</code> oder
<code>Set</code> implementiert ist.</p>

<p>Sie können verwendet werden, um
<tooltip term="Utility-Class"><format color="%GlossaryLinkColor%">Utility-Klassen</format></tooltip> zu erstellen, die
nur von der äußeren Klasse verwendet werden. Diese Hilfsklassen müssen keine eigenständigen Klassen sein und haben
typischerweise außerhalb der äußeren Klasse keinen Sinn (z. B. <code>Player</code>-Klasse ↔
<code>Properties</code>-Klasse).</p>

<p>Wenn eine Klasse riesengroß ist, können nicht-statische innere Klassen verwendet werden, um zusammenhängende Logik in
einer abgeschlossenen Einheit zu kapseln, ohne die äußere Klasse zu überladen.</p>

### Statische innere Klassen {id="static-inner-classes"}

<p>Wenn eine innere Klasse mit dem <format color="%LinkColor%"><a href="01-java-token.md#keywords">Schlüsselwort</a>
</format> <code>static</code> deklariert ist, handelt es sich um eine statische innere Klasse. Auch sie werden innerhalb
von einer anderen Klasse definiert, aber außerhalb von
<format color="%LinkColor%"><a href="09-java-methods.md">Methoden</a></format>,
<format color="%LinkColor%"><a href="#constructors">Konstruktoren</a></format> und Anweisungsblöcken (z. B.
<format color="%LinkColor%"><a href="#class-initializer">Klasseninitialisierer</a></format>).</p>

<p>Eine statische innere Klasse hat Zugriff auf
<format color="%LinkColor%"><a href="#class-variables">Klassenvariablen</a></format> und
<format color="%LinkColor%"><a href="#class-methods">-methoden</a></format>, aber nicht auf die
<format color="%LinkColor%"><a href="#object-variables">Objektvariablen</a></format> und
<format color="%LinkColor%"><a href="#object-methods">-methoden</a></format> der äußeren Klasse. Ein
<format color="%LinkColor%"><a href="11-java-objects.md">Objekt</a></format> der inneren Klasse ist nicht an ein Objekt
der äußeren Klasse gebunden</p>

<code-block lang="java">
    public class Product {
    
        private String name;
        private int quantity;
        private double price;
    
        private Product(Builder builder) {
            this.name = builder.name;
            this.quantity = builder.quantity;
            this.price = builder.price;
        }
    
        // Inner static class
        public static class Builder {
            private String name;
            private int quantity;
            private double price;
    
            public Builder setName(String name) {
                this.name = name;
                return this;
            }
    
            public Builder setQuantity(int quantity) {
                this.quantity = quantity;
                return this;
            }
    
            public Builder setPrice(double price) {
                this.price = price;
                return this;
            }
    
            public Product build() {
                return new Product(this);
            }
        }
    
        @Override
        public String toString() {
            return "Product [name=" + name + ", quantity=" + quantity + ", price=" + price + "]";
        }
    
        public static void main(String[] args) {
            Product product = new Product.Builder()
                .setName("Widget")
                .setQuantity(10)
                .setPrice(19.99)
                .build();
                
            System.out.println(product);
        }
    }
</code-block>

<p>Statische innere Klassen eignen sich gut für
<tooltip term="Utility-Class"><format color="%GlossaryLinkColor%">Utility-Klassen</format></tooltip>, die
<format color="%LinkColor%"><a href="#class-methods">Klassenmethoden</a></format> oder
<format color="%LinkColor%"><a href="#constants">Konstanten</a></format> enthalten und keine Verbindung zum
<format color="%LinkColor%"><a href="11-java-objects.md">Objekt</a></format> der äußeren Klasse benötigen.</p>

<p>Dies wird häufig verwendet, um verschiedene Implementierungen eines
<format color="%LinkColor%"><a href="14-java-oop.md#interfaces">Interfaces</a></format> oder einer
<format color="%LinkColor%"><a href="14-java-oop.md#abstract-classes">abstrakten Klasse</a></format> zu kapseln. Sie
können aber auch dazu verwendet werden, um die Implementierung von Algorithmen oder Datenstrukturen zu kapseln, die nur
innerhalb der äußeren Klasse verwendet werden sollen.</p>

<p>Eine statische innere Klasse wird, wie das obige Beispiel zeigt, auch häufig für ein
<format color="%LinkColor%"><a href="28-java-design-patterns.md#builder-pattern">Builder-Pattern</a></format> verwendet.
Bei dieser Methode wird eine statische innere Klasse verwendet, um die Konstruktion eines komplexen
<format color="%LinkColor%"><a href="11-java-objects.md">Objekts</a></format> zu kapseln. Die statische innere Klasse
fungiert als <code>Builder</code>, der die verschiedenen Teile des Objekts schrittweise konfiguriert und schließlich das
fertige Objekt erstellt.</p>

### Lokale innere Klassen {id="local-inner-classes"}

<p>Lokale innere Klassen werden innerhalb einer Methode oder eines Anweisungsblocks definiert. Sie können auf
<format color="%LinkColor%"><a href="03-java-variables.md">lokale Variablen</a></format> der Methode zugreifen, sofern
diese <code>final</code> oder effektiv <code>final</code> sind und sind nur innerhalb des Bereichs sichtbar, in dem sie
definiert sind.</p>

<code-block lang="java">
    public class EmailSender {
    
        public void sendEmail(String recipient, String message) {
    
            // Inner local class
            class EmailConnection {
            
                public void connect() {
                    System.out.println("Connection to email server established");
                }
    
                public void disconnect() {
                    System.out.println("Connection to email server disconnected");
                }
            }
    
            EmailConnection connection = new EmailConnection();
            connection.connect();
            
            System.out.println("E-Mail sent to " + recipient + " with message: " + message);
            
            connection.disconnect();
        }
    
        public static void main(String[] args) {
            EmailSender sender = new EmailSender();
            sender.sendEmail("example@domain.com", "Hello, this is a test email.");
        }
    }
</code-block>

<p>Lokale innere Klassen sind ideal, wenn eine Klasse nur innerhalb einer
<format color="%LinkColor%"><a href="09-java-methods.md">Methode</a></format> oder eines Anweisungsblocks verwendet
werden soll. Besonders, wenn diese Klasse auf die
<format color="%LinkColor%"><a href="03-java-variables.md">lokalen Variablen</a></format> der Methode zugreifen muss.
</p>

<p>In ereignisgesteuerten Programmiermodellen (Event-driven Programming), wie in
<format color="%LinkColor%"><a href="29-java-gui.md">GUI-Anwendungen</a></format>, können lokale innere Klassen verwendet
werden, um die Ereignisbehandlungslogik in einer Methode zu kapseln.</p>

<p>Sie eignen sich auch zur Implementierung von vorübergehenden Datenstrukturen oder Logiken, die nur in einem kleinen
Kontext benötigt werden und außerhalb der Methode keine Bedeutung haben.</p>

### Anonyme Klassen {id="anonymous-inner-classes"}

<p>Diese Klassen haben keinen Namen und werden gleichzeitig deklariert und initialisiert. Sie werden häufig verwendet,
um <format color="%LinkColor%"><a href="14-java-oop.md#interfaces">Schnittstellen</a></format> oder
<format color="%LinkColor%"><a href="14-java-oop.md#abstract-classes">abstrakte Klassen</a></format> zu implementieren,
wenn nur eine einzelne <format color="%LinkColor%"><a href="11-java-objects.md">Instanz</a></format> benötigt wird.</p>

<code-block lang="java">
    public class Main {
    
        public static void main(String[] args) {
               // Inner anonymous class
            new Runnable() {
                @Override
                public void run() {
                    // Code...
                }
            };
        }
    }
</code-block>

<p>Zudem finden sie häufig in GUI-Umgebungen Anwendung, um Event-Listener zu erstellen, ohne dafür eine benannte Klasse
zu definieren und eignen sich für Aufgaben, die nur einmal ausgeführt werden und für die keine Wiederverwendbarkeit
notwendig ist.</p>

## Records {id="records"}

<p>Records wurden mit Java 14 vorläufig eingeführt und mit dem Feedback der Community in Java 15 und 16 weiterentwickelt
und verbessert, bis sie in Java 16 offiziell als Standfunktion etabliert wurden.</p>

<p>Sie bieten eine kompakte Möglichkeit, unveränderliche Datenklassen zu definieren. Records sind im Wesentlichen eine
Abkürzung für die Erstellung von Klassen, die hauptsächlich zur Speicherung von Daten verwendet werden. Im Gegensatz zu
herkömmlichen Klassen nehmen sie dem Entwickler viel
<tooltip term="Boilerplate-Code"><format color="%GlossaryLinkColor%">Boilerplate-Code</format></tooltip> ab, da sie
automatisch <format color="%LinkColor%"><a href="#constructors">Konstruktoren</a></format>,
<format color="%LinkColor%"><a href="#getter-and-setter">Getter-Methoden</a></format>, <code>equals()</code>,
<code>hashCode()</code> und <code>toString()</code>-Methoden generieren.</p>

<p>Records sind unveränderlich, was in vielen Fällen von Vorteil ist, aber es schränkt auch ihre Verwendung ein, wenn
veränderbare Daten benötigt werden.</p>

<code-block lang="java">
    public record Point(double x, double y) {
    
    }
</code-block>

<code-block lang="java">
    Point point = new Point(34.5, 23.0);
    
    System.out.println(point.x()); // 34.5
    System.out.println(point.y()); // 23.0
    System.out.println(point);     // Point[x=34.5, y=23.0]
</code-block>

### Aktivierung von Records {id="activation-of-records"}

<list>
  <li><p>Für Versionen vor Java 14 sind Records nicht als Sprachfunktion verfügbar.</p></li>
  <li><p>Für die Versionen zwischen Java 14 und 16 kann das Flag <code>--enable-preview</code> verwendet werden, um
    Records zu aktivieren.</p></li>
  <li><p>Für Versionen ab Java 16 und höher sind Records eine Standardfunktion und das Flag
    <code>--enable-preview</code> ist für die Verwendung von Records nicht mehr erforderlich.</p></li>
</list>

<p>Um eine <code>.java</code>-Datei vor Java 16 mit dem Preview Feature zu kompilieren, muss folgender Befehl verwendet
werden:</p>

<code-block lang="console">
    javac --enable-preview --release 14 Main.java
</code-block>

<p>Zum Ausführen dient der folgende Befehl:</p>

<code-block lang="console">
    java --enable-preview Main
</code-block>

## Coding Conventions {id="coding-conventions"}

<list>
  <li><p>Klassen sollten nach der
    <tooltip term="PascalCase-Notation"><format color="%GlossaryLinkColor%">PascalCase-Notation</format></tooltip>
    benannt werden.</p></li>
  <li><p>Jede Art von Methode – siehe <format color="%LinkColor%"><a href="09-java-methods.md#coding-conventions">
    Kapitel 9 – Methoden: Coding-Conventions</a></format>.</p></li>
  <li><p>Jeder Art von Variable (außer <format color="%LinkColor%"><a href="#constants">Konstanten</a></format>) – siehe
    <format color="%LinkColor%"><a href="03-java-variables.md#coding-conventions">
    Kapitel 3 – Variablen: Coding Conventions</a></format>.</p></li>
  <li><p><format color="%LinkColor%"><a href="#constructors">Konstruktoren</a></format> müssen genau wie die Klasse
    benannt werden.</p></li>
  <li><p><format color="%LinkColor%"><a href="#getter-and-setter">Getter & Setter</a></format> sollten mit
    <code>get</code> bzw. mit <code>set</code> beginnen.</p></li>
  <li><p><format color="%LinkColor%"><a href="#getter-and-setter">Getter</a></format> für
    <format color="%LinkColor%"><a href="02-java-data-types.md#data-type-boolean">Booleans</a></format> sollten mit
    <code>is</code> beginnen. Alternativ kann auch <code>has</code> verwendet werden.</p></li>
  <li><p><format color="%LinkColor%"><a href="#constants">Konstanten</a></format> sollten nach der
    <tooltip term="Constants-Notation"><format color="%GlossaryLinkColor%">SCREAMING_SNAKE_CASE-Notation</format>
    </tooltip> geschrieben werden.</p></li>
</list>

