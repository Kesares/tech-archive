# 10 Java – Klassen

Klassen sind ein wesentlicher Bestandteil der <format color="%LinkColor%">[OOP – Objektorientierten Programmierung](14-java-oop.md)</format>. Sie sind vergleichbar mit Rezepten oder Blueprints und stellen die grundlegende Struktur und den Aufbau von konkret instanziierten <format color="%LinkColor%">[Objekten](11-java-objects.md)</format> dar – deren Eigenschaften (<format color="%LinkColor%">[Objektvariablen](#object-variables)</format>) und Funktionalitäten (<format color="%LinkColor%">[Objektmethoden](#object-methods)</format>). Jede Klasse, die in Java erstellt wird, <format color="%LinkColor%">[erbt](14-java-oop.md#inheritance)</format> automatisch von der <format color="%LinkColor%">[Klasse `Object`](14-java-oop.md#the-mother-of-all-classes-object)</format>.

Alle <format color="%LinkColor%">[Variablen](03-java-variables.md)</format> und <format color="%LinkColor%">[Methoden](09-java-methods.md)</format>, die in Java deklariert werden, sind von solch einer <format color="%LinkColor%">[Klassendefinition](#class-structure)</format> ummantelt – unabhängig davon, ob sie zu einem <format color="%LinkColor%">[Objekt](11-java-objects.md)</format> gehören oder nicht. Der Name der Datei muss zudem genauso heißen, wie der Name der Klasse, die sich innerhalb der Datei befindet.

## Klassenaufbau {id="class-structure"}

Der Aufbau einer Klasse ist nicht in Stein gemeißelt. Er kann sich von Unternehmen zu Unternehmen unterscheiden. Eine weit verbreitete Anordnung sieht folgendermaßen aus.

```Java
public class ClassName {

    // Constants and static or class variables

    // Instance or object variables

    // Constructors

    // Static or class methods

    // Instance or object methods

    // Getters and setters

    // Inner classes
}
```

> Zudem sollten alle öffentlichen (mit `public` deklariert), geschützten (mit `protected` deklariert) und privaten (mit `private` deklariert) Methoden jeweils nahe beieinander stehen.

## Klassenvariablen {id="class-variables"}

Klassenvariablen oder auch statische Variablen werden mit dem <format color="%LinkColor%">[Keyword](12-java-modifier-access-rights.md)</format> `static` gebildet und sollten ganz oben innerhalb einer Klassendefinition deklariert werden. Sie existieren unabhängig von einem Objekt und werden meist mit dem Keyword `final` deklariert. Variablen mit dem Keyword `final` werden <format color="%LinkColor%">[Konstanten](#constants)</format> genannt, da sich deren Wert nach Initialisierung nicht mehr ändern kann.

### Konstanten {id="constants"}

<note>
    Alle Konstanten sind Klassenvariablen – aber nicht alle Klassenvariablen sind Konstanten.
</note>

Zwei Beispiel-Konstanten aus der `Math`-Klasse:

![](10_java_classes_1.png){border-effect="line"}

## Objektvariablen {id="object-variables"}

Objekt- oder Instanzvariablen werden unterhalb der <format color="%LinkColor%">[Klassenvariablen](#class-variables)</format> aber oberhalb von <format color="%LinkColor%">[Konstruktoren](#constructors)</format> deklariert. Diese Variablen gehören immer zu einem konkreten <format color="%LinkColor%">[Objekt](11-java-objects.md)</format> und dienen als Eigenschaften des Objekts wie beispielsweise der Name oder die Farbe eines Tiers. Objektvariablen können nur über ein bestehendes Objekt angesprochen werden.

Instanzvariablen können sowohl aus <format color="%LinkColor%">[primitiven Datentypen](02-java-data-types.md#primitive-data-types)</format> als auch aus <format color="%LinkColor%">[Referenzdatentypen](02-java-data-types.md#reference-data-types)</format> wie z.B. Strings bestehen.

```Java
public class Dog {

    public String name;
    public int age;
}
```

Die Initialisierung dieser Variablen übernimmt in den meisten Fällen der <format color="%LinkColor%">[Konstruktor](#constructors)</format>.

## Konstruktoren {id="constructors"}

Eine spezielle Art der Methode ist der Konstruktor. Er besitzt keinen <format color="%LinkColor%">[Rückgabewert](09-java-methods.md#return-type)</format> – nicht mal das <format color="%LinkColor%">[Keyword](01-java-token.md#keywords)</format> `void`. Zudem muss der Konstruktor denselben Namen wie die Klasse besitzen. Er ist für das eigentliche Initialisieren der <format color="%LinkColor%">[Objekte](11-java-objects.md)</format> verantwortlich.

Beim Erstellen eines Objekts wird der Konstruktor aufgerufen. Dabei können ihm Werte mit übergeben werden, mit denen die <format color="%LinkColor%">[Objektvariablen](#object-variables)</format> des jeweiligen Objekts initialisiert werden.

```Java
public class Dog {

    public String name;
    public int age;

    public Dog(String name, int age) {
        name = name;
        age = age;
    }
}
```

Wurde kein Konstruktor programmiert, wird automatisch der Default-Konstruktor aufgerufen, welcher keine Parameter erwartet. Dieser kann auch optional selber geschrieben werden.

```Java
public class Dog {

    public String name;
    public int age;

    public Dog() {

	}
}
```

Auch mehrere Konstruktoren sind möglich.

```Java
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
```

<warning>
    In beiden Konstruktoren gibt es jedoch ein Problem.
</warning>

## Verdeckte Variablen {id="shadowed-variables"}

Werden in Codeblöcken neue Variablennamen eingeführt, können diese nicht noch einmal angelegt werden. Heißt die lokale Variable einer Methode genauso wie eine <format color="%LinkColor%">[Objektvariable](#object-variables)</format>, spricht man auch von einer verdeckten oder <format color="%Highlight%">shadowed Variablen</format>.

An sich besteht in solchen Fällen kein Problem. Der <tooltip term="Compiler"><format color="%GlossaryLinkColor%">Compiler</format></tooltip> wird dann standardmäßig die lokale Variable nutzen. Durch dieses Vorgehen können später neu hinzugefügte Objektvariablen keinen schon bestehenden Code zerstören.

Eine kleine Komplikation besteht nur, wenn die <format color="%LinkColor%">[Objektvariable](#object-variables)</format> mit einer lokalen Variable genutzt werden soll. In diesem Fall wird der Wert der lokalen Variable verwendet und erneut der lokalen Variable zugewiesen.

```Java
public class Dog {

    public String name;
    public int age;

    public Dog(String name, int age) {
        name = name; // <-- here
        age = age;   // <-- here
    }

    public Dog(String name) {
        name = name; // <-- here
        age = 0;
    }
}
```

Dafür gibt es jedoch eine Lösung.

## Das Keyword `this` {id="the-keyword-this"}

Natürlich können bei solchen Problemen die lokalen oder <format color="%LinkColor%">[Objektvariablen](#object-variables)</format> umbenannt werden. Müssen diese an mehreren Stellen geändert werden, kann der Aufwand jedoch etwas größer werden. Möchte man die beiden <format color="%LinkColor%">[Variablen](03-java-variables.md)</format> also gerne gleich benennen, kann das Keyword `this` Abhilfe schaffen.

Das Schlüsselwort `this` funktioniert ähnlich wie eine Referenzvariable, indem es auf ein bestimmtes <format color="%LinkColor%">[Objekt](09-java-methods.md)</format> verweist – allerdings in einem spezifischen Kontext. Anders ausgedrückt: Ein Objekt verweist mit `this` auf sich selbst. `this` bezieht sich auf genau das Objekt, das gerade verwendet wird bzw. in dessen Kontext (<format color="%Highlight%">Klasse</format>) man sich aktuell befindet.

```Java
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
```

Ein weiterer Vorteil von `this` ist, dass die folgenden beiden <format color="%LinkColor%">[Konstruktoren](#constructors)</format> miteinander verknüpft werden können. Dadurch wird redundanter Code vermieden.

```Java
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
```

Der untere <format color="%LinkColor%">[Konstruktor](#constructors)</format> ruft nun den oberen Konstruktor mit dem ergänzenden Wert auf.

## Klassenmethoden {id="class-methods"}

Im vorherigen <format color="%LinkColor%">[Kapitel 9 – Methoden](09-java-methods.md)</format> gab es bereits viele Beispiele zu Klassenmethoden. Klassenmethoden brauchen wie <format color="%LinkColor%">[Klassenvariablen](#class-variables)</format> kein bestimmtes <format color="%LinkColor%">[Objekt](09-java-methods.md)</format> um auf diese zugreifen zu können. Sie werden mit dem Keyword `static` gebildet und werden über den Klassennamen angesprochen.

```Java
public static void print(String text) {
    System.out.println(text);
}

public static void main(String[] args) {
    print("Hello World!");
}
```

## Objektmethoden {id="object-methods"}

Alle weiteren Objektmethoden sollten nach den <format color="%LinkColor%">[Klassenmethoden](#class-methods)</format> stehen und können nur über ein bestehendes <format color="%LinkColor%">[Objekt](09-java-methods.md)</format> aufgerufen werden.

```Java
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
```

## Getter- & Setter-Methoden {id="getter-and-setter"}

Getter und Getter dienen dazu, <format color="%LinkColor%">[Objektvariablen](#object-variables)</format> abzugreifen (<format color="%Highlight%">get-Methoden</format>) oder deren Werte zu überschreiben bzw. sie zu initialisieren (<format color="%Highlight%">set-Methoden</format>). Sie können für jede Objektvariable angelegt werden. Durch diese Methoden kann somit festgelegt werden, ob überhaupt auf die Variablen zugegriffen werden kann, wenn diese beispielsweise als `private` deklariert wurden (siehe <format color="%LinkColor%">[Kapitel 12 – Modifizierer und Zugriffsrechte](12-java-modifier-access-rights.md)</format>).

```Java
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
```

## Klasseninitialisierer {id="class-initializer"}

Wird eine Klasse vom `ClassLoader` in die <format color="%Highlight%">Runtime Environment</format> geladen, werden zunächst die statischen Blöcke von oben nach unten ausgeführt. Dies tritt auf, sobald eine <format color="%LinkColor%">[Klassenvariable](#class-variables)</format> oder <format color="%LinkColor%">[Klassenmethode](#class-methods)</format> zum ersten Mal aufgerufen oder eine <format color="%LinkColor%">[Instanz](11-java-objects.md)</format> der Klasse erstellt wird.

```Java
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
```

```Console
Class initialization block 1
Class initialization block 2
Main-Program started...
```

Da die Initialisierung einer Klasse nur ein einziges Mal pro Programmausführung stattfindet, können dadurch auch <format color="%LinkColor%">[Klassenvariablen](#class-variables)</format> initialisiert werden.

Zudem ermöglichen Klasseninitialisierer die Ausführung von komplexer Initialisierungslogik, die über einfache Zuweisungen hinausgeht, z. B. das Einlesen von Konfigurationsdateien oder das Einrichten von sonstigen statischen Ressourcen.

## Innere Klassen {id="inner-classes"}

Innere Klassen werden innerhalb einer anderen Klasse definiert. Diese inneren Klassen haben Zugriff auf die Mitglieder der äußeren Klasse, einschließlich mit `private` deklarierten Methoden und Variablen und bieten eine Möglichkeit, logische Beziehungen zwischen Klassen zu modellieren. Es gibt verschiedene Arten von inneren Klassen und jede hat ihren eigenen Anwendungsfall.

### Nicht-statische innere Klassen {id="non-static-inner-classes"}

Wenn eine innere Klasse keine `static`-Deklaration hat, handelt es sich um eine nicht-statische innere Klasse. Sie werden innerhalb von einer anderen Klasse definiert, aber außerhalb von <format color="%LinkColor%">[Methoden](09-java-methods.md)</format>, <format color="%LinkColor%">[Konstruktoren](#constructors)</format> und Anweisungsblöcken (z.B. <format color="%LinkColor%">[Klasseninitialisierer](#class-initializer)</format>).

Nicht-statische innere Klasse haben Zugriff auf alle Mitglieder (statische und nicht-statische Variablen und Methoden) der äußeren Klasse. Ein <format color="%LinkColor%">[Objekt](09-java-methods.md)</format> der inneren Klasse ist an ein Objekt der äußeren Klasse gebunden

```Java
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
```

Nicht-statische innere Klassen sind nützlich, wenn die innere Klasse stark von der äußeren Klasse abhängt und auf deren <format color="%LinkColor%">[Objektvariablen](#object-variables)</format> und <format color="%LinkColor%">[-methoden](#object-methods)</format> zugreifen muss. Ein klassisches Beispiel ist ein `Iterator`, der als innere Klasse in einer <format color="%LinkColor%">[Collection](19-java-collections.md)</format> wie `List` oder `Set` implementiert ist.

Sie können verwendet werden, um <tooltip term="Utility-Class"><format color="%GlossaryLinkColor%">Utility-Klassen</format></tooltip> zu erstellen, die nur von der äußeren Klasse verwendet werden. Diese Hilfsklassen müssen keine eigenständigen Klassen sein und haben typischerweise außerhalb der äußeren Klasse keinen Sinn (z.B. `Player`-Klasse ↔ `Properties`-Klasse).

Wenn eine Klasse sehr groß ist, können nicht-statische innere Klassen verwendet werden, um zusammenhängende Logik in einer abgeschlossenen Einheit zu kapseln, ohne die äußere Klasse zu überladen.

### Statische innere Klassen {id="static-inner-classes"}

Wenn eine innere Klasse mit dem <format color="%LinkColor%">[Schlüsselwort](02-java-data-types.md)</format> `static` deklariert ist, handelt es sich um eine statische innere Klasse. Auch sie werden innerhalb von einer anderen Klasse definiert, aber außerhalb von <format color="%LinkColor%">[Methoden](09-java-methods.md)</format>, <format color="%LinkColor%">[Konstruktoren](#constructors)</format> und Anweisungsblöcken (z.B. <format color="%LinkColor%">[Klasseninitialisierer](#class-initializer)</format>).

Eine statische innere Klasse hat Zugriff auf <format color="%LinkColor%">[Klassenvariablen](#class-variables)</format> und <format color="%LinkColor%">[-methoden](#class-methods)</format>, aber nicht auf die <format color="%LinkColor%">[Objektvariablen](#object-variables)</format> und <format color="%LinkColor%">[-methoden](#object-methods)</format> der äußeren Klasse. Ein <format color="%LinkColor%">[Objekt](09-java-methods.md)</format> der inneren Klasse ist nicht an ein Objekt der äußeren Klasse gebunden

```Java
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

```

Statische innere Klassen eignen sich gut für <tooltip term="Utility-Class"><format color="%GlossaryLinkColor%">Utility-Klassen</format></tooltip>, die <format color="%LinkColor%">[Klassenmethoden](#class-methods)</format> oder <format color="%LinkColor%">[Konstanten](#constants)</format> enthalten und keine Verbindung zum <format color="%LinkColor%">[Objekt](11-java-objects.md)</format> der äußeren Klasse benötigen.

Dies wird häufig verwendet, um verschiedene Implementierungen eines <format color="%LinkColor%">[Interfaces](14-java-oop.md#interfaces)</format> oder einer <format color="%LinkColor%">[abstrakten Klasse](14-java-oop.md#abstract-classes)</format> zu kapseln. Sie können aber auch dazu verwendet werden, um die Implementierung von Algorithmen oder Datenstrukturen zu kapseln, die nur innerhalb der äußeren Klasse verwendet werden sollen.

Eine statische innere Klasse wird, wie das obige Beispiel zeigt, auch häufig für ein <format color="%LinkColor%">[](java-design-patterns.md#builder-pattern)</format>verwendet. Bei dieser Methode wird eine statische innere Klasse verwendet, um die Konstruktion eines komplexen <format color="%LinkColor%">[Objekts](11-java-objects.md)</format> zu kapseln. Die statische innere Klasse fungiert als `Builder`, der die verschiedenen Teile des Objekts schrittweise konfiguriert und schließlich das fertige Objekt erstellt.

### Lokale innere Klassen {id="local-inner-classes"}

Lokale innere Klassen werden innerhalb einer Methode order eines Anweisungsblocks definiert. Sie können auf <format color="%LinkColor%">[lokale Variablen](03-java-variables.md)</format> der Methode zugreifen, sofern diese `final` oder effektiv `final` sind und sind nur innerhalb des Bereichs sichtbar, in dem sie definiert sind.

```Java
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
```

Lokale innere Klassen sind ideal, wenn eine Klasse nur innerhalb einer <format color="%LinkColor%">[Methode](09-java-methods.md)</format> oder eines Anweisungsblocks verwendet werden soll. Besonders, wenn diese Klasse auf die <format color="%LinkColor%">[lokalen Variablen](03-java-variables.md)</format> der Methode zugreifen muss.

In ereignisgesteuerten Programmiermodellen (Event-driven Programming), wie in <format color="%LinkColor%">[GUI-Anwendungen](java-gui.md)</format>, können lokale innere Klassen verwendet werden, um die Ereignisbehandlungslogik in einer Methode zu kapseln.

Sie eignen sich auch zur Implementierung von vorübergehenden Datenstrukturen oder Logiken, die nur in einem kleinen Kontext benötigt werden und außerhalb der Methode keine Bedeutung haben.

### Anonyme Klassen {id="anonymous-inner-classes"}

Diese Klassen haben keinen Namen und werden gleichzeitig deklariert und initialisiert. Sie werden häufig verwendet, um <format color="%LinkColor%">[Schnittstellen](14-java-oop.md#interfaces)</format> oder <format color="%LinkColor%">[abstrakte Klassen](14-java-oop.md#abstract-classes)</format> zu implementieren, wenn nur eine einzelne <format color="%LinkColor%">[Instanz](11-java-objects.md)</format> benötigt wird.

```Java
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
```

Zudem finden sie häufig in GUI-Umgebungen Anwendung, um Event-Listener zu erstellen, ohne dafür eine benannte Klasse zu definieren und eignen sich für Aufgaben, die nur einmal ausgeführt werden und für die keine Wiederverwendbarkeit notwendig ist.

## Records {id="records"}

Records wurden mit Java 14 vorläufig eingeführt und mit dem Feedback der Community in Java 15 und 16 weiterentwickelt und verbessert, bis sie in Java 16 offiziell als Standfunktion etabliert wurden.

Sie bieten eine kompakte Möglichkeit, unveränderliche Datenklassen zu definieren. Records sind im Wesentlichen eine Abkürzung für die Erstellung von Klassen, die hauptsächlich zur Speicherung von Daten verwendet werden. Im Gegensatz zu herkömmlichen Klassen nehmen sie dem Entwickler viel <tooltip term="Boilerplate-Code"><format color="%GlossaryLinkColor%">Boilerplate-Code</format></tooltip> ab, da sie automatisch <format color="%LinkColor%">[Konstruktoren](#constructors)</format>, <format color="%LinkColor%">[Getter-Methoden](#getter-and-setter)</format>, `equals()`, `hashCode()` und `toString()`-Methoden generieren.

Records sind unveränderlich, was in vielen Fällen von Vorteil ist, aber es schränkt auch ihre Verwendung ein, wenn veränderbare Daten benötigt werden.

```Java
public record Point(double x, double y) {

}
```

```Java
Point point = new Point(34.5, 23.0);

System.out.println(point.x()); // 34.5
System.out.println(point.y()); // 23.0
System.out.println(point);     // Point[x=34.5, y=23.0]
```

### Aktivierung von Records {id="activation-of-records"}

- Für Versionen vor Java 14 sind Records nicht als Sprachfunktion verfügbar.
- Für die Versionen zwischen Java 14 und 16 das Flag `--enable-preview` verwendet werden, um Records zu verwenden.
- Für Versionen ab Java 16 und höher sind Records eine Standardfunktion und das Flag `--enable-preview` ist für die Verwendung von Records nicht mehr erforderlich.

Um eine `.java`-Datei vor Java 16 mit dem Preview Feature zu kompilieren, muss folgender Befehl verwendet werden:

```Console
javac --enable-preview --release 14 Main.java
```

Zum Ausführen dient der folgende Befehl:

```Console
java --enable-preview Main
```

## Coding Conventions {id="coding-conventions"}

- Klassen sollten nach der <tooltip term="PascalCase-Notation"><format color="%GlossaryLinkColor%">PascalCase-Notation</format></tooltip> benannt werden.
- Jede Art von Methode – siehe <format color="%LinkColor%">[Kapitel 9 – Methoden: Coding-Conventions](09-java-methods.md#coding-conventions)</format>.
- Jeder Art von Variable (außer <format color="%LinkColor%">[Konstanten](#constants)</format>) – siehe <format color="%LinkColor%">[Kapitel 3 – Variablen: Coding Conventions](03-java-variables.md#coding-conventions).</format>
- <format color="%LinkColor%">[Konstruktoren](#constructors)</format> müssen genau wie die Klasse benannt werden.
- <format color="%LinkColor%">[Getter & Setter](#getter-and-setter)</format> sollten mit `get` bzw. mit `set` beginnen.
- <format color="%LinkColor%">[Getter](#getter-and-setter)</format> für <format color="%LinkColor%">[Booleans](02-java-data-types.md#data-type-boolean)</format> sollten mit `is` beginnen. Alternativ kann auch `has` verwendet werden.
- <format color="%LinkColor%">[Konstanten](#constants)</format> sollten nach der <tooltip term="Constants-Notation"><format color="%GlossaryLinkColor%">SCREAMING_SNAKE_CASE-Notation</format></tooltip> geschrieben werden.

