# 14 Java – OOP
## Was ist OOP? {id="what-is-oop"}

Die objektorientierte Programmierung ist ein Programmierparadigma, dass auf dem Konzept der Objektorientierung und der Verwendung von <format color="%LinkColor%">[Objekten](11-java-objects.md)</format> beruht. Die Grundidee dieses Ansatzes besteht darin, dass die Struktur einer Software an den fundamentalen Bausteinen der realen Welt ausgerichtet wird. Diese Bausteine können sich von Software zu Software unterscheiden und je nach Ansprüchen und Anforderungen einfacher oder komplexer umgesetzt werden.

Um dies zu realisieren, werden die einzelnen Programmfragmente in <format color="%LinkColor%">[Objekte](11-java-objects.md)</format> unterteilt. Diese Objekte können, abhängig von Eigenschaften und Funktionalitäten, eigene Aufgaben erfüllen oder mit weiteren Objekten agieren. In <format color="%LinkColor%">[Kapitel 10 – Klassen](10-java-classes.md)</format> wurde bereits ein kleiner Einblick in die OOP mit der Klasse `Dog` gegeben.

## Ziel der OOP {id="aim-of-oop"}

Ziel der objektorientierten Programmierung ist es modulareren, wartbareren und erweiterbaren Code zu schreiben.

Die Verwendung von <format color="%LinkColor%">[Objekten](11-java-objects.md)</format> ermöglicht es, den Code in kleinere, unabhängige Einheiten zu unterteilen, die jeweils Daten und Verhaltensweisen in sich vereinen. Die <format color="%LinkColor%">[OOP-Prinzipien](#principles-of-oop)</format> tragen dazu bei, indem sie eine klare Trennung zwischen den verschiedenen Komponenten des Systems ermöglichen.

## Prinzipien der OOP {id="principles-of-oop"}

Die grundlegenden Prinzipien der OOP umfassen die folgenden 4 Konzepte.

- <format color="%c1%">[Vererbung](#inheritance)</format>
- <format color="%c2%">[Abstraktion](#abstraction)</format>
- <format color="%c3%">[Kapselung](#encapsulation)</format>
- <format color="%c4%">[Polymorphismus](#polymorphism)</format>

### <format color="%c1%">Vererbung</format> {id="inheritance"}

Durch Vererbung (engl. inheritance) kann eine <format color="%LinkColor%">[Klasse](10-java-classes.md)</format> die <format color="%LinkColor%">[](10-java-classes.md#object-variables)</format>und <format color="%LinkColor%">[-methoden](10-java-classes.md#object-methods)</format> einer anderen Klasse übernehmen, was die Wiederverwendbarkeit von Code ermöglicht. Um eine Klasse von einer anderen Klasse erben zu lassen, wird das <format color="%LinkColor%">[Schlüsselwort](01-java-token.md#keywords)</format> `extends` verwendet.

In <format color="%LinkColor%">[Kapitel 10 – Klassen](10-java-classes.md)</format> haben wir die Klasse `Dog` erstellt. Nun möchten wir jedoch verschiedene Tierarten, wie zum Beispiel Katzen, in einem Spiel darstellen. Sowohl Katzen als auch Hunde haben gemeinsame Eigenschaften, wie einen Namen und ein Alter. Eine Katze hat zusätzlich noch eine Eigenschaft darüber, ob sie ihre Krallen ausgefahren hat.

Um Gemeinsamkeiten zu nutzen, erstellen wir eine übergeordnete Klasse `Animal` (auch Elternklasse oder Superklasse genannt), in der die Eigenschaften `name` und `age` gespeichert werden und verschieben die <format color="%LinkColor%">[Getter und Setter](10-java-classes.md#getter-and-setter)</format> ebenfalls dorthin. Zusätzlich erstellen wir eine neue Klasse `Cat` mit der Eigenschaft `hasExtendedClaws`. In beiden Klassen muss der passende <format color="%LinkColor%">[Konstruktor](10-java-classes.md#constructors)</format> implementiert werden.

In den Kindklassen rufen wir dann den Konstruktor der Elternklasse mit dem Schlüsselwort `super` auf, um die Werte an die Oberklasse zu übergeben und dort zu initialisieren, anstatt dies in der Kindklasse zu tun.

Zudem setzen wir die Objektvariablen `name` und `age` auf `protected`. Dadurch können die Kindklassen direkt auf diese Variablen zugreifen, ohne die <format color="%LinkColor%">[Getter](10-java-classes.md#getter-and-setter)</format> verwenden zu müssen.

> Wenn <format color="%LinkColor%">[Klassen](10-java-classes.md)</format>, die sich im selben <format color="%LinkColor%">[Package](16-java-packages-and-imports.md)</format> wie die Klasse `Animal` befinden, direkt auf die <format color="%LinkColor%">[](10-java-classes.md#object-variables)</format> `name` und `age` zugreifen möchten, ist dies durch die Verwendung von `protected` möglich. Soll dies nicht geschehen, müssen die Objektvariablen auf `private` gesetzt werden.
> 
> Damit geht jedoch auch der direkte Zugriff der Kindklassen verloren und die Kindklassen müssen auf die <format color="%LinkColor%">[Getter und Setter](10-java-classes.md#getter-and-setter)</format> zurückgreifen.
> {title="Zugriff im selben Package"}

```Java
public class Animal {

    protected String name;
    protected int age;

    public Animal(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    public Animal(String name) {
        this(name, 0);
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

Nun sollen die Klassen `Dog` und `Cat` mit `extends` von dieser Klasse erben.

```Java
public class Dog extends Animal {  
  
    public Dog(String name, int age) {  
        super(name, age);  
    }  
  
    public Dog(String name) {  
        super(name);  
    }  
  
    public void eat() {  
        System.out.println(super.name + " is eating!");  
    }  
  
    public void bark() {  
        System.out.println(super.name + " barks!");  
    }  
}
```

Katzen haben zusätzlich zur `eat`-Methode und anstelle der `bark()`-Methode die Fähigkeit zu "miauen". Also wird dafür eine Methode `meow()` in der Klasse `Cat` programmiert.

```Java
public class Cat extends Animal {  
  
    private boolean hasExtendedClaws;
  
    public Cat(String name, int age) {  
        super(name, age);  
    }

    public Cat(String name) {  
        super(name);  
    }
  
    public void eat() {  
        System.out.println(super.name + " is eating!");  
    }  
  
    public void meow() {  
        System.out.println(super.name + " meows!");  
    }
    
    public boolean isHasExtendedClaws() {
        return hasExtendedClaws;
    }

    public void setHasExtendedClaws(boolean hasExtendedClaws) {
        this.hasExtendedClaws = hasExtendedClaws;
    }
}
```

Das Keyword `super` funktioniert prinzipiell wie `this` – siehe <format color="%LinkColor%">[Kapitel 10 – Das Keyword this](10-java-classes.md#the-keyword-this)</format>. Allerdings werden damit der <format color="%LinkColor%">[Konstruktor](10-java-classes.md#constructors)</format>, die <format color="%LinkColor%">[](10-java-classes.md#object-variables)</format> und die <format color="%LinkColor%">[](10-java-classes.md#object-methods)</format> der jeweiligen Superklasse aufgerufen. 

Innerhalb des Konstruktors muss als erste Anweisung der Konstruktor der Oberklasse aufgerufen werden, sofern Attribute übergeben werden.

<note>
    <p>Ab Java 22 ist es möglich, vor dem eigentlichen <code>super()</code>-Aufruf noch weitere Anweisungen zu schreiben.</p>
    <code-block lang="java">
        public Dog(...) {
            System.out.println("Statement before super call") // Allowed since Java 22
            super(...);
        }
    </code-block>
    <warning>
    <p>Bis Java 21 erhält man jedoch einen Error: <format color="%WarningHighlight%">Call to 'super()' must be first statement in constructor body</format></p>
    </warning>
</note>

Passen wir die `main()`-Methode etwas an.

```Java
public class Main {

    public static void main(String[] args) {
        Dog killer = new Dog("Killer", 5);
        Cat nala = new Cat("Nala", 3);

        killer.eat();   // Killer is eating!
        killer.bark();  // Killer barks!
        nala.eat();     // Nala is eating!
        nala.meow();    // Nala meows!

        System.out.println(killer.getName());   // Killer
        System.out.println(killer.getAge());    // 5
        System.out.println(nala.getName());     // Nala
        System.out.println(nala.getAge());      // 3
    }
}
```

#### <format color="%c1%">Die Mutter aller Klassen – `Object`</format> {id="the-mother-of-all-classes-object"}

Wie wir bereits wissen, gibt es in Java eine <format color="%LinkColor%">[Klasse](10-java-classes.md)</format>, die über allen anderen steht: `Object`. Man könnte sie als die "Mutter aller Klassen" bezeichnen. Jede Klasse erbt automatisch von `Object`, auch wenn dies nicht explizit angegeben wird. Das bedeutet, dass alle Klassen direkt oder indirekt Unterklassen von `Object` sind.

`Object` bietet eine gemeinsame Basis für alle <format color="%LinkColor%">Klassen</format>, was die Interoperabilität und Konsistenz zwischen verschiedenen Klassen und <tooltip term="API"><format color="%GlossaryLinkColor%">APIs</format></tooltip> erleichtert. Da jede Klasse von `Object` erbt, haben alle <format color="%LinkColor%">[Objekte](11-java-objects.md)</format> einen gemeinsamen Satz von Methoden, was das Arbeiten mit verschiedenen <format color="%LinkColor%">[Datentypen](02-java-data-types.md)</format> in einer einheitlichen Weise ermöglicht.

Wenn wir eine eigene Klasse erstellen, haben wir die Möglichkeit, diese Methoden zu <format color="%LinkColor%">[überschreiben](#polymorphism)</format>, um das Verhalten der Objekte anzupassen.

##### <format color="%c1%">Grundlegende Methoden der Klasse</format> `Object` {id="basic-methods-of-the-object-class"}

Im Folgenden sind einige Methoden der Klasse `Object` aufgelistet, die überschrieben werden können.

<table>
    <tr>
        <td>Methode</td>
        <td>Beschreibung</td>
    </tr>
    <tr>
        <td><code>equals()</code></td>
        <td>
            <p>Überprüft die Gleichheit von <format color="%LinkColor%"><a href="11-java-objects.md">Objekten</a></format>. Standardmäßig prüft sie, ob zwei Referenzen auf dasselbe Objekt zeigen.</p>
            <p>Wir kennen bereits eine Implementierung dieser Methode bei einem <format color="%LinkColor%"><a href="05-java-strings.md#string-methods">String</a></format>-Objekt.</p>
        </td>
    </tr>
    <tr>
        <td><code>hashCode</code></td>
        <td>Liefert einen Hash-Code für das <format color="%LinkColor%"><a href="11-java-objects.md">Objekt</a></format>, der häufig in Hash-basierten <format color="%LinkColor%"><a href="19-java-collections.md">Collections</a></format> wie <code>HashMap</code> oder <code>HashSet</code> verwendet wird. Wenn <code>equals()</code> überschrieben wird, sollte auch <code>hashCode()</code> überschrieben werden, um sicherzustellen, dass Objekte, die als gleich betrachtet werden, denselben Hash-Code haben.</td>
    </tr>
    <tr>
        <td><code>toString()</code></td>
        <td>
            <p>Gibt eine <format color="%LinkColor%"><a href="05-java-strings.md">String</a></format>-Darstellung des Objekts zurück. Standardmäßig gibt sie den Klassennamen gefolgt von der Speicheradresse des Objekts zurück.</p>
            <p>Auch diese Implementierung kennen wir bereits aus <format color="%LinkColor%"><a href="05-java-strings.md#string-methods">Kapitel 11 – Objekte: Die toString()-Methode</a></format>.</p>
        </td>
    </tr>
    <tr>
        <td><code>clone()</code></td>
        <td>Eine Kopie eines Objekts kann mit dieser Methode erstellt werden. Zu beachten ist jedoch, dass das Klonen in Java spezielle Implementierungen erfordert und nicht für alle Klassen sinnvoll ist. Die Methode selbst ist in der <code>Object</code>-Klasse als <code>native</code> deklariert – siehe <tooltip term="JNI"><format color="%GlossaryLinkColor%">JNI</format></tooltip> und <format color="%LinkColor%"><a href="12-java-modifier-access-rights.md">Kapitel 12 – Modifizierer und Zugriffsrechte</a></format></td>
    </tr>
    <tr>
        <td><code>finalize()</code></td>
        <td>Wird aufgerufen, bevor das <format color="%LinkColor%"><a href="11-java-objects.md#the-garbage-collector">Garbage Collection-Subsystem</a></format> ein Objekt endgültig zerstört. Die Verwendung von <code>finalize()</code> ist jedoch in modernen Java-Anwendungen nicht mehr üblich. Die Methode selbst ist mit <code>@Deprecated</code> markiert und wird zukünftig entfernt werden.</td>
    </tr>
</table>

#### <format color="%c1%">Das Keyword `instanceof`</format> {id="the-keyword-instanceof"}

Das Keyword `instanceof` wird verwendet, um zu überprüfen, ob ein <format color="%LinkColor%">[Objekt](11-java-objects.md)</format> ein Exemplar einer bestimmten <format color="%LinkColor%">[Klasse](10-java-classes.md)</format> oder eines <format color="%LinkColor%">[Interfaces](#interfaces)</format> ist. Trifft dies zu, kann das entsprechende Objekt in den jeweiligen Typ <format color="%LinkColor%">[gecastet](03-java-variables.md#type-casting)</format> werden, um typspezifische Anweisungen durchzuführen.

```Java
Object object = new Dog("Killer", 5);

if (object instanceof Dog) {
    Dog dog = (Dog) object;
    dog.eat();
} else {
    System.out.println("Instance of 'Object' or other class");
}
```

##### <format color="%c1%">Pattern Matching bei `instanceof` ab Java 16</format>

Bislang musste nach jeder Typüberprüfung ein separater <format color="%LinkColor%">[Cast](03-java-variables.md#type-casting)</format> in den entsprechenden Typ erfolgen, der in einer Hilfsvariable gespeichert wurde, um typspezifische Anweisungen ausführen zu können. Seit Java 16 ist dies nun mit einer kürzeren und eleganteren Schreibweise möglich.

<compare>
    <code-block lang="java">
        Object object = new Dog("Killer", 5);
        if (object instanceof Dog) {
            Dog dog = (Dog) object;
            dog.eat();
        } else {
            System.out.println("Instance of 'Object' or other class");
        }
    </code-block>
    <code-block lang="java">
        Object object = new Dog("Killer", 5);
        if (object instanceof Dog dog) {
            dog.eat();
        } else {
            System.out.println("Instance of 'Object' or other class");
        }
    </code-block>
</compare>

### <format color="%c2%">Abstraktion</format> {id="abstraction"}

Abstraktion bedeutet, dass komplexe Systeme auf eine einfachere und klarere Weise dargestellt werden können, indem unnötige Details ausgeblendet werden.

Schaut man sich dazu die Klassen `Animal`, `Dog` und `Cat` an, fällt auf, dass dieses Prinzip bereits teilweise umgesetzt wurde. Denn die gemeinsamen Eigenschaften `name` und `age` wurden in der Oberklasse `Animal` zusammengefasst. Genauso wie deren <format color="%LinkColor%">[Getter und Setter](10-java-classes.md#getter-and-setter)</format>. Somit wurde vermieden, dass die <format color="%LinkColor%">[](10-java-classes.md#object-variables)</format>und <format color="%LinkColor%">[-methoden](10-java-classes.md#object-methods)</format> sowohl in der Klasse `Dog` als auch in der Klasse `Cat` stehen.

Besitzt eine Katze eine Eigenschaft, die ein Hund nicht besitzt, macht es keinen Sinn diese Eigenschaft in der Oberklasse zu speichern. Es reicht aus, diese Eigenschaft nur für <format color="%LinkColor%">[Objekte](11-java-objects.md)</format> der Klasse `Cat` zu speichern.

Die Klassen können allerdings noch weiter abstrahiert werden. Sowohl Hunde als auch Katzen können fressen. Also kann auch die Methode `eat()` in die Oberklasse ausgelagert werden. `super` muss in der Methode `eat()` allerdings noch zu `this` geändert werden, da es keine Eigenschaft `name` in der Oberklasse `Object` gibt.

Befindet sich eine Variable in der Oberklasse, kann mit der entsprechenden Berechtigung auch mit `this` aus der Unterklasse auf diese zugegriffen werden. Es kann natürlich auch ganz weggelassen werden, da es keine <format color="%LinkColor%">[gleichnamige lokale Variable](10-java-classes.md#the-keyword-this)</format> innerhalb dieser <format color="%LinkColor%">[Objektmethode](10-java-classes.md#object-methods)</format> gibt.

> Ich selbst bevorzuge die expliziten Angaben mit `this` für Objektvariablen und Objektmethoden in <format color="%NoteHighlight%">derselben Klasse</format> und `super` für den Aufruf von Objektvariablen und Objektmethoden in der <format color="%NoteHighlight%">Oberklasse</format>. Dadurch wird klarer, in welchen Klassen die Variablen und Methoden deklariert sind.
{style="note" title="Best Practice – Angaben von this und super"}

```Java
public class Animal {

    protected String name;
    protected int age;

    public Animal(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    public Animal(String name) {
        this(name, 0);
    }
    
    public void eat() {  
        System.out.println(this.name + " is eating!");  
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

```Java
public class Dog extends Animal {  
  
    public Dog(String name, int age) {  
        super(name, age);  
    }  
  
    public Dog(String name) {  
        super(name);  
    }  
  
    public void bark() {  
        System.out.println(super.name + " barks!");  
    }  
}
```

```Java
public class Cat extends Animal {  
  
    private boolean hasExtendedClaws;
  
    public Cat(String name, int age) {  
        super(name, age);  
    }

    public Cat(String name) {  
        super(name);  
    }
  
    public void meow() {  
        System.out.println(super.name + " meows!");  
    }
    
    public boolean isHasExtendedClaws() {
        return hasExtendedClaws;
    }

    public void setHasExtendedClaws(boolean hasExtendedClaws) {
        this.hasExtendedClaws = hasExtendedClaws;
    }
}
```

### <format color="%c3%">Kapselung</format> {id="encapsulation"}

Kapselung bedeutet, dass der interne Zustand eines <format color="%LinkColor%">[Objekts](11-java-objects.md)</format> durch eine öffentliche Schnittstelle verborgen wird, um unerwartete Änderungen und Fehler zu vermeiden bzw. das Lesen oder Ändern von Daten einzuschränken.

Auch dieses Konzept wurde bereits in den Klassen `Animal`, `Dog`, und `Cat` angewendet. Dort wurden die <format color="%LinkColor%">[](10-java-classes.md#object-variables)</format> auf `private`, später auf `protected` gesetzt und <format color="%LinkColor%">[Getter und Setter](10-java-classes.md#getter-and-setter)</format> als Kontrollpunkte für den Zugriff auf diese verwendet.

Etwas zu schreiben wie

```Java
nala.age = -10;
```

sollte logischerweise nicht möglich sein.

Dies ist zwar auch durch <format color="%LinkColor%">[Setter](10-java-classes.md#getter-and-setter)</format> möglich, doch durch Setter haben wir den Vorteil, dass wir solche Fälle abfragen können.

```Java
public void setAge(int age) {
    if (age < 0) return;
    this.age = age;
}
```

### <format color="%c4%">Polymorphismus</format> {id="polymorphism"}

Polymorphismus bietet die Möglichkeit, dass verschiedene Typen so agieren, als wären sie derselbe Typ. Das Verhalten jedes Typs ist jedoch unterschiedlich. Klinkt kompliziert?

Schauen wir uns dazu nochmal die Klassen `Animal`, `Dog` und `Cat` an. Fügen wir zur Klasse `Animal` eine Methode `giveLoud()`, ändern die Namen der Methoden `bark()` und `meow()` in den Kindklassen ebenfalls zum Namen `giveLoad()` und passen die `main()`-Methode etwas an.

```Java
public class Animal {
  
    protected String name;
    protected int age;
  
    public Animal(String name, int age) {
        this.name = name;
        this.age = age;
    }
  
    public Animal(String name) {
        this(name, 0);
    }
  
    public void giveLoud() {
        System.out.println(this.name + " makes a sound!");
    }
  
    public void eat() {
        System.out.println(this.name + " is eating!");
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

```Java
public class Dog extends Animal {
  
    public Dog(String name, int age) {
        super(name, age);
    }
  
    public Dog(String name) {
        super(name);
    }

    public void giveLoud() {
        System.out.println(super.name + " bark!");
    }
}
```

```Java
public class Cat extends Animal {  
  
    private boolean hasExtendedClaws;
  
    public Cat(String name, int age) {  
        super(name, age);  
    }

    public Cat(String name) {  
        super(name);  
    }
  
    public void giveLoud() {  
        System.out.println(super.name + " meows!");  
    }
    
    public boolean isHasExtendedClaws() {
        return hasExtendedClaws;
    }

    public void setHasExtendedClaws(boolean hasExtendedClaws) {
        this.hasExtendedClaws = hasExtendedClaws;
    }
}
```

```Java
public class Main {

    public static void main(String[] args) {
        Animal killer = new Dog("Killer", 5);
        Animal nala = new Cat("Nala", 3);

        killer.eat();
        killer.giveLoud();
        nala.eat();
        nala.giveLoud();

        System.out.println(killer.getName());   // Killer
        System.out.println(killer.getAge());    // 5
        System.out.println(nala.getName());     // Nala
        System.out.println(nala.getAge());      // 3
    }
}
```

<tabs group="floating-point-1">
    <tab id="floating-point-division-task-1" title="Aufgabe">
        <p>Welche Objektmethoden werden aufgerufen? Die aus der Elternklasse oder aus der Kindklasse?</p><br/>
    </tab>
    <tab id="floating-point-division-solution-1" title="Lösung">
        <p>Die Methoden der Kindklassen werden aufgerufen.</p>
        <code-block lang="console">
            Bello is eating!
            Bello bark!
            Nala is eating!
            Nala meows!
        </code-block>
        <p>Wir speichern zwar eine Referenz auf die <format color="%LinkColor%"><a href="11-java-objects.md">Objekte</a></format> in einer <format color="%LinkColor%"><a href="03-java-variables.md">lokalen Variablen</a></format> vom Typ <code>Animal</code>, aber die Objekte agieren wie ein <code>Cat</code>- und <code>Dog</code>-Objekt.</p>
    </tab>
</tabs>

Was in diesen <format color="%LinkColor%">[Klassen](10-java-classes.md)</format> nun passiert ist, dass innerhalb der Kindklassen das Verhalten der Klasse `Animal` überschrieben wird, indem die Objektmethode `giveLoad()` mit einer eigenen Implementierung der Kindklasse überschrieben wird. Es werden immer die <format color="%LinkColor%">[](10-java-classes.md#object-methods)</format> der Kindklassen aufgerufen, sofern diese eine eigene Implementierung mitbringen.

> Der <tooltip term="Compiler"><format color="%GlossaryLinkColor%">Compiler</format></tooltip> meckert zwar nicht herum, allerdings zeugt es von sauberem Arbeiten, wenn oberhalb der überschriebenen Methoden die <format color="%NoteLinkColor%">[Annotation](java-annotations.md)</format> `@Override` steht.
{style="note" title="Annotation @Override"}

Es können auch die <format color="%LinkColor%">[](10-java-classes.md#object-methods)</format> der Oberklassen aus den Objektmethoden der Kindklassen aufgerufen werden. Dies macht aber nur Sinn, wenn innerhalb der Methoden der Oberklasse Code geschrieben wurde, der für die jeweilige Kindklasse ebenfalls relevant ist.

```Java
@Override  
public void giveLoud() {
    super.giveLoud();
    System.out.println(super.name + " bark!");  
}
```

#### <format color="%c4%">Abstrakte Klassen</format> {id="abstract-classes"}

Bis jetzt gibt es im obigen Programm nur Hunde und Katzen. Da beide Tiere Laute von sich geben, können die Kindklassen dazu gezwungen werden, die <format color="%LinkColor%">[Objektmethode](10-java-classes.md#object-methods)</format> `giveLoud()` zu implementieren, indem in der Oberklasse `Animal` die Methode `giveLoud()` als `abstract` deklariert wird.

```Java
public abstract void giveLoud();
```

Diese Methode hat jetzt nur noch eine Signatur, jedoch keine eigene Implementierung. Zusätzlich muss der Klasse `Animal` noch das Keyword `abstract` verpasst werden, da mindestens eine Methode existiert, die als `abstract` deklariert wurde.

```Java
public abstract class Animal {
    // ...
}
```

Dadurch wird verhindert, dass ein <format color="%LinkColor%">[Objekt](11-java-objects.md)</format> dieser Klasse erstellt werden kann. Ein neues Objekt muss also immer ein konkretes Tier sein.

<warning>
    <p>Folgendes ist somit nicht mehr erlaubt:</p>
    <code-block lang="java">
        Animal animal = new Animal("Unknown", 10);
    </code-block>
</warning>

Das macht auch Sinn. In der <format color="%LinkColor%">[Klasse](10-java-classes.md)</format> `Animal` haben wir eine Methode mit `abstract` deklariert und somit keine eigene Implementierung mitbringt.

Angenommen wir hätten dennoch die Möglichkeit ein <format color="%LinkColor%">[Objekt](11-java-objects.md)</format> dieser Klasse zu erzeugen und rufen die abstrakte Methode über dieses Objekt auf, was würde passieren? Man weiß es nicht ... und die Methode auch nicht, denn sie hat ja keine Implementierung. Die Methode besitzt keinen ausführbaren Code.

Die Instanziierung und den möglichen Aufruf dieser Methode, wird durch die Deklarierung der Klasse mit `abstract` verhindert.

Werden nun die <format color="%LinkColor%">[](10-java-classes.md#object-methods)</format> aus der Kindklasse entfernt oder werden weitere Klassen erstellt, die von der Klasse `Animal` erben, dann gibt es einen <tooltip term="Compiler"><format color="%GlossaryLinkColor%">Compiler</format></tooltip>-Fehler der folgenden Art, bis die notwendigen Methoden überschrieben wurden.

<warning>
    <p>Class 'Dog' must either be declared abstract or implement abstract method 'giveLoud()' in 'Animal'</p>
</warning>

Dieses Vorgehen ist nützlich, wenn Kindklassen ihre eigenen Implementierungen mitbringen sollen.

#### <format color="%c4%">Interfaces</format> {id="interfaces"}

Eine Alternative zu <format color="%LinkColor%">[abstrakten Klassen](#abstract-classes)</format> sind Interfaces (Schnittstellen). Interfaces dienen dazu, bestimmte Verhalten zu definieren, ohne eine konkrete Implementierung vorzugeben. Solche Methodendeklarationen werden häufig auch Signaturen genannt (wie abstrakte Methoden in abstrakten Klassen).

<format color="%LinkColor%">[Klassen](10-java-classes.md)</format> können diese Interfaces und diese vorgeschriebene Funktionalität dann implementieren, wobei auch die <format color="%LinkColor%">[Keywords](01-java-token.md#keywords)</format> `interface` und `implements` Anwendung finden. Interfaces werden meistens wie <tooltip term="Top-Level-Class"><format color="%GlossaryLinkColor%">Top-Level-Klassen</format></tooltip> in eigenen Dateien geschrieben, können aber auch direkt in einer Klasse definiert werden.

- Alle Methoden die innerhalb von Schnittstellen deklariert werden, sind implizit `public` und `abstract`, außer <format color="%LinkColor%">[Default-Methoden](#default-methods)</format>.
- Alle Variablen die innerhalb von Schnittstellen deklariert werden, sind implizit <format color="%LinkColor%">[Konstanten](10-java-classes.md#constants)</format> (`static final`).

Im obigen Beispiel mit den Tier-Klassen kommt die Verwendung der Method `giveLoud()` zum Einsatz. Wird dies mit Schnittstellen realisiert, sieht das Ganze folgendermaßen aus:

```Java
public interface Loudable {  
  
    void giveLoud();  
}
```

```Java
public abstract class Animal implements Loudable {

    // ...

    public abstract void giveLoud(); // Can be removed

    // ...
}
```

Die Klassen `Dog` und `Cat` behalten ihren Code bei. In der Klasse `Animal` kann die abstrakte Definition der Methode `giveLoud()` jedoch entfernt werden, da diese bereits im Interface `Loudable` existiert. Das Prinzip bleibt also dasselbe.

Hier zeigt sich die wahre Stärke von Interfaces. Angenommen wir haben noch andere <format color="%LinkColor%">[Objekte](11-java-objects.md)</format> die Geräusche erzeugen, jedoch keine Tiere sind – etwa ein Motor. Ein Motor kann Geräusche machen, ist aber kein Tier. Da aber sowohl Tiere als auch Motoren Geräusche machen können, kann sowohl die Klasse `Animal` als auch eine Klasse `Motor` das Interface `Loudable` implementieren.

Dieses Interface ermöglicht es den <format color="%LinkColor%">[Klassen](10-java-classes.md)</format>, die Geräuscherzeugung auf ihre eigene Weise zu implementieren, ohne von einer gemeinsamen Oberklasse erben zu müssen. 

Um einen passenderen Namen für das Interface zu nehmen, könnte man es anstelle von `Loudable` in `Soundable` und die Methode `giveLoud()` in `makeSound()` umbenennen.

Ohne den Kontext zu kennen, ist es schwer zu verstehen, was dieses Interface und seine Methode tun sollen. Umso mehr, wenn es in zwei solch unterschiedlichen Umgebungen verwendet wird. `Loudable` ist kein geläufiger Begriff und `giveLoud()` klingt eher nach einer Anweisung wie "Ton geben", was nicht intuitiv ist.

Im Gegensatz dazu deutet ein Interface namens `Soundable` mit einer Methode `makeSound()` sofort darauf hin, dass es sich um etwas handelt, das Geräusche erzeugen kann. Der Name ist selbsterklärend und macht den Code verständlicher.

##### <format color="%c4%">Wichtige Schnittstellen in der Java-Standardbibliothek</format> {id="important-interfaces"}

<table>
    <tr>
        <td>Interface</td>
        <td>Beschreibung</td>
    </tr>
    <tr>
        <td><code>java.lang.Appendable</code></td>
        <td>Etwas hinzufügen</td>
    </tr>
    <tr>
        <td><code>java.lang.AutoCloseable</code></td>
        <td>Ressourcen automatisch schließen</td>
    </tr>
    <tr>
        <td><code>java.lang.Comparable</code></td>
        <td>Objekt vergleichen</td>
    </tr>
    <tr>
        <td><code>java.lang.Iterable</code></td>
        <td>Elemente in Schleifen durchlaufen</td>
    </tr>
    <tr>
        <td><code>java.lang.Readable</code></td>
        <td>Etwas lesen</td>
    </tr>
    <tr>
        <td><code>java.lang.Runnable</code></td>
        <td>Code nebenläufig ausführen</td>
    </tr>
    <tr>
        <td><code>java.io.Serializeable</code></td>
        <td>Objekt serialisieren</td>
    </tr>
    <tr>
        <td><code>java.nio.file.PathMatcher</code></td>
        <td>Dateien filtern</td>
    </tr>
    <tr>
        <td><code>java.util.Collection</code></td>
        <td>Aufzählungen verwalten</td>
    </tr>
    <tr>
        <td><code>java.util.List</code></td>
        <td>Listen verwalten</td>
    </tr>
    <tr>
        <td><code>java.util.Map</code></td>
        <td>Maps verwalten</td>
    </tr>
    <tr>
        <td><code>java.util.Set</code></td>
        <td>Sets verwalten</td>
    </tr>
    <tr>
        <td><code>java.awt.event.ActionListener</code></td>
        <td>Auf Events reagieren</td>
    </tr>
</table>

##### <format color="%c4%">Funktionale Schnittstellen</format> {id="functional-interfaces"}

Schnittstellen, die nur eine Methode definieren, werden als funktionale Schnittstellen bezeichnet und können mittels <format color="%LinkColor%">[Lambda-Ausdrücken](01-java-token.md#operators)</format> verwendet werden. Wenn Schnittstellen nur eine Methode definieren sollen, kann diese Schnittstelle mit der <format color="%LinkColor%">[Annotation](java-annotations.md)</format> `@FunctionalInterface` versehen werden, sofern keine <format color="%LinkColor%">[Default-Implementierung](#default-methods)</format> verwendet wird. Dadurch überprüft der <tooltip term="Compiler"><format color="%GlossaryLinkColor%">Compiler</format></tooltip>, ob die Regeln für funktionale Schnittstellen eingehalten werden.

```Java
@FunctionalInterface
public interface Soundable {  
    void makeSound();  
}
```

Dies ermöglicht eine vereinfachte Schreibweise beim Aufruf dieser Methoden. Bevor jedoch die <format color="%LinkColor%">[Annotation](java-annotations.md)</format> verwendet wird, sollte man sorgfältig abwägen, ob das Interface später möglicherweise um weitere Methoden erweitert wird.

Falls ja und die Annotation wurde bereits hinzugefügt, könnte dies zu Inkompatibilitäten führen und vorhandenen Code, der das Interface nutzt, beeinträchtigen.

##### <format color="%c4%">Default-Methoden</format> {id="default-methods"}

Interfaces können auch mit einer Default-Implementierung versehen werden. Dabei wir das Keyword `default` verwendet.

```Java
public interface Soundable {  

    default void makeSound(String name) {
        System.out.println(name + " makes a sound!");
    }  
}
```

Dadurch werden die <format color="%LinkColor%">[Klassen](10-java-classes.md)</format>, die dieses Interface implementieren, nicht mehr dazu gezwungen, Methoden zu überschreiben, können dies aber bei Bedarf dennoch tun.

##### <format color="%c4%">Abstrakte Klassen vs. Schnittstellen</format> {id="abstract-classes-vs-interfaces"}

Die prinzipielle Anwendung zwischen Schnittstellen und <format color="%LinkColor%">[abstrakten Klassen](#abstract-classes)</format> bleibt dieselbe und beide besitzen viele Ähnlichkeiten und können auch auf ähnliche Weise eingesetzt werden. Zudem können Interfaces auch von anderen Interfaces erben. Allerdings haben Schnittstellen einen fundamentalen Unterschied.

Während Klassen nur von einer einzigen Klasse erben können (ob direkt oder indirekt), können mehrere Interfaces implementiert werden. Dies ist zwar auch durch mehrstufige Vererbung möglich, allerdings können dadurch tiefe und unübersichtliche Hierarchien entstehen.

## Versiegelte Klassen und Interfaces {id="sealed-classes-and-interfaces"}

Versiegelte <format color="%LinkColor%">[Klassen](10-java-classes.md)</format> und <format color="%LinkColor%">[Interfaces](#interfaces)</format>, eingeführt als Preview in Java 15 und finalisiert mit Java 17, bieten eine neue Möglichkeit, die <format color="%LinkColor%">[Vererbungshierarchie](#inheritance)</format> zu kontrollieren. Sie ermöglichen es Entwicklern klar und präzise festzulegen, welche Klassen oder Interfaces die Möglichkeit haben, eine bestimmte Klasse zu erweitern oder ein Interface zu implementieren.

Eine versiegelte <format color="%LinkColor%">[Klasse](10-java-classes.md)</format> ist eine Klasse, die explizit festlegt, welche anderen Klassen sie erweitern dürfen. Ebenso können versiegelte <format color="%LinkColor%">[Interfaces](#interfaces)</format> bestimmen, welche anderen Interfaces oder Klassen sie implementieren dürfen. Dies erfolgt durch die Verwendung des neuen <format color="%LinkColor%">[Keywords](01-java-token.md#keywords)</format> `sealed` in der Klassendeklaration, gefolgt von dem Schlüsselwort `permits` und einer Liste der zulässigen Subklassen.

```Java
public sealed class Animal permits Dog, Cat {
    // ...
}

public final class Dog extends Animal {
    // ...
}

public final class Cat extends Animal {
    // ...
}
```

Versiegelte Klassen und Interfaces bieten auch Flexibilität, da eine versiegelte Klasse nicht zwingend `final` sein muss. Stattdessen können die erlaubten Subklassen selbst wieder versiegelt sein, was eine kontrollierte Vererbungskette ermöglicht.

```Java
public sealed class Animal permits Dog, Cat {
    // ...
}

public final class Dog extends Animal {
    // ...
}

public sealed class Cat extends Animal permits PersianCat, SiameseCat {
    // ...
}

public final class PersianCat extends Cat {
    // ...
}

public non-sealed class SiameseCat extends Cat {
    // ...
}
```

> Alle Unterklassen die von einer versiegelten Klasse erben, müssen entweder als `sealed`, `non-sealed` oder `final` deklariert werden.
{style="note"}

- Wenn eine (Unter-)Klasse als `final` deklariert wird, kann sie nicht weiter vererbt werden. Das bedeutet, dass diese <format color="%LinkColor%">[Klasse](10-java-classes.md)</format> die Endstation in der Vererbungshierarchie ist.

- Wenn eine Unterklasse wiederum als `sealed` deklariert wird, setzt sie die versiegelte <format color="%LinkColor%">[Vererbungshierarchie](#inheritance)</format> fort. Das bedeutet, dass diese <format color="%LinkColor%">[Klasse](10-java-classes.md)</format> nur von einer definierten Gruppe von Klassen erweitert werden kann, die explizit in der `permits`-Liste angegeben sind. Dies ermöglicht eine weitere Vererbung, jedoch unter strenger Kontrolle, welche Klassen beteiligt sind.

- Wenn eine Unterklasse als `non-sealed` deklariert wird, wird die <format color="%LinkColor%">[Vererbungshierarchie](#inheritance)</format> geöffnet und die Klasse kann wie eine normale Klasse weiter vererbt werden, ohne Beschränkungen.

Im folgenden Beispiel legt das versiegelte Interface `Role` fest, dass nur die <format color="%LinkColor%">[Klassen](10-java-classes.md)</format> `Admin`, `Moderator` und `Guest` eine Rolle im Programm übernehmen können. Die Klasse `Guest` ist als `non-sealed` deklariert, sodass sie von weiteren Klassen erweitert werden kann, falls zusätzliche spezifische Gastrollen erforderlich sind.

```Java
public sealed interface Role permits Admin, Moderator, Guest {
    void access();
}

public final class Admin implements Role {
    @Override
    public void access() {
        System.out.println("Admin has full access");
    }
}

public final class Moderator implements Role {
    @Override
    public void access() {
        System.out.println("Moderator has limited access");
    }
}

public non-sealed class Guest implements Role {
    @Override
    public void access() {
        System.out.println("Guest has minimal access");
    }
}
```