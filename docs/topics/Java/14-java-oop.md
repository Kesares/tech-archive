# 14 Java – OOP
## Was ist OOP? {id="what-is-oop"}

<p>Die objektorientierte Programmierung ist ein Programmierparadigma, dass auf dem Konzept der Objektorientierung und
der Verwendung von <format color="%LinkColor%"><a href="11-java-objects.md">Objekten</a></format> beruht. Die Grundidee
dieses Ansatzes besteht darin, dass die Struktur einer Software an den fundamentalen Bausteinen der realen Welt
ausgerichtet wird. Diese Bausteine können sich von Software zu Software unterscheiden und je nach Ansprüchen und
Anforderungen einfacher oder komplexer umgesetzt werden.</p>

<p>Um dies zu realisieren, werden die einzelnen Programmfragmente in
<format color="%LinkColor%"><a href="11-java-objects.md">Objekte</a></format> unterteilt. Diese Objekte können, abhängig
von Eigenschaften und Funktionalitäten, eigene Aufgaben erfüllen oder mit weiteren Objekten agieren. In
<format color="%LinkColor%"><a href="10-java-classes.md">Kapitel 10 – Klassen</a></format> wurde bereits ein kleiner
Einblick in die OOP mit der Klasse <code>Dog</code> gegeben.</p>

## Ziel der OOP {id="aim-of-oop"}

<p>Ziel der objektorientierten Programmierung ist es, modularen, wartbaren und erweiterbaren Code zu schreiben.</p>

<p>Die Verwendung von <format color="%LinkColor%"><a href="11-java-objects.md">Objekten</a></format> ermöglicht es, den
Code in kleinere, unabhängige Einheiten zu unterteilen, die jeweils Daten und Verhaltensweisen in sich vereinen. Die
<format color="%LinkColor%"><a href="#principles-of-oop">OOP-Prinzipien</a></format> tragen dazu bei, indem sie eine
klare Trennung zwischen den verschiedenen Komponenten des Systems ermöglichen.</p>

## Prinzipien der OOP {id="principles-of-oop"}

<p>Die grundlegenden Prinzipien der OOP umfassen die folgenden 4 Konzepte.</p>

<list>
  <li>
    <format color="%c1%"><a href="#inheritance">Vererbung</a></format>
  </li>
  <li>
    <format color="%c2%"><a href="#abstraction">Abstraktion</a></format>
  </li>
  <li>
    <format color="%c3%"><a href="#encapsulation">Kapselung</a></format>
  </li>
  <li>
    <format color="%c4%"><a href="#polymorphism">Polymorphismus</a></format>
  </li>
</list>

### <format color="%c1%">Vererbung</format> {id="inheritance"}

<p>Durch Vererbung (eng. inheritance) kann eine
<format color="%LinkColor%"><a href="10-java-classes.md">Klasse</a></format> die
<format color="%LinkColor%"><a href="10-java-classes.md#object-variables">Objektvariablen</a></format> und
<format color="%LinkColor%"><a href="10-java-classes.md#object-methods">-methoden</a></format> einer anderen Klasse
übernehmen, was die Wiederverwendbarkeit von Code ermöglicht. Um eine Klasse von einer anderen Klasse erben zu lassen,
wird das <format color="%LinkColor%">[Schlüsselwort](01-java-token.md#keywords)</format> <code>extends</code> verwendet.
</p>

<p>In <format color="%LinkColor%"><a href="10-java-classes.md">Kapitel 10 – Klassen</a></format> haben wir die Klasse
<code>Dog</code> erstellt. Nun möchten wir jedoch verschiedene Tierarten, wie zum Beispiel Katzen, in einem Spiel
darstellen. Sowohl Katzen als auch Hunde haben gemeinsame Eigenschaften, wie einen Namen und ein Alter. Eine Katze hat
zusätzlich noch eine Eigenschaft darüber, ob sie ihre Krallen ausgefahren hat.</p>

<p>Um Gemeinsamkeiten zu nutzen, erstellen wir eine übergeordnete Klasse <code>Animal</code> (auch Elternklasse oder
Superklasse genannt), in der die Eigenschaften <code>name</code> und <code>age</code> gespeichert werden und verschieben
die <format color="%LinkColor%"><a href="10-java-classes.md#getter-and-setter">Getter und Setter</a></format> ebenfalls
dorthin. Zusätzlich erstellen wir eine neue Klasse <code>Cat</code> mit der Eigenschaft <code>hasExtendedClaws</code>.
In beiden Klassen muss der passende
<format color="%LinkColor%"><a href="10-java-classes.md#constructors">Konstruktor</a></format>
 implementiert werden.</p>

<p>In den Kindklassen rufen wir dann den Konstruktor der Elternklasse mit dem Schlüsselwort <code>super</code> auf, um
die Werte an die Oberklasse zu übergeben und dort zu initialisieren, anstatt dies in der Kindklasse zu tun.</p>

<p>Zudem setzen wir die Objektvariablen <code>name</code> und <code>age</code> auf <code>protected</code>. Dadurch
können die Kindklassen direkt auf diese Variablen zugreifen, ohne die
<format color="%LinkColor%"><a href="10-java-classes.md#getter-and-setter">getter</a></format> verwenden zu müssen.</p>

<tip title="Zugriff im selben Package">
<p>Wenn <format color="%LinkColor%"><a href="10-java-classes.md">Klassen</a></format>, die sich im selben
<format color="%LinkColor%"><a href="16-java-packages-and-imports.md">Package</a></format> wie die Klasse
<code>Animal</code> befinden, direkt auf die
<format color="%LinkColor%"><a href="10-java-classes.md#object-variables">Objektvariablen</a></format> <code>name</code>
 und <code>age</code> zugreifen möchten, ist dies durch die Verwendung von <code>protected</code> möglich. Soll dies
nicht geschehen, müssen die Objektvariablen auf <code>private</code> gesetzt werden.</p>
<p>Damit geht jedoch auch der direkte Zugriff der Kindklassen verloren und den Kindklassen bleibt für den Zugriff nur noch
die Nutzung der
<format color="%LinkColor%"><a href="10-java-classes.md#getter-and-setter">Getter und Setter</a></format> der
Oberklasse.</p></tip>

<code-block lang="java">
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
</code-block>

<p>Nun sollen die <format color="%LinkColor%"><a href="10-java-classes.md">Klassen</a></format> <code>Dog</code> und
<code>Cat</code> mit <code>extends</code> von der Klasse <code>Animal</code> erben.</p>

<code-block lang="java">
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
</code-block>

<p>Katzen haben zusätzlich zur <code>eat</code>-Methode und anstelle der <code>bark()</code>-Methode die Fähigkeit zu
"miauen". Also wird dafür eine Methode <code>meow()</code> in der Klasse <code>Cat</code> programmiert.</p>

<code-block lang="java">
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
</code-block>

<p>Das Keyword <code>super</code> funktioniert prinzipiell wie <code>this</code> – siehe
<format color="%LinkColor%"><a href="10-java-classes.md#the-keyword-this">Kapitel 10 – Das Keyword this</a></format>.
Allerdings werden damit der
<format color="%LinkColor%"><a href="10-java-classes.md#constructors">Konstruktor</a></format>, die
<format color="%LinkColor%"><a href="10-java-classes.md#object-variables">Objektvariablen</a></format> und die
<format color="%LinkColor%"><a href="10-java-classes.md#object-methods">Objektmethoden</a></format> der jeweiligen
Superklasse aufgerufen.</p> 

<p>Innerhalb des Konstruktors muss als erste Anweisung der Konstruktor der Oberklasse aufgerufen werden, sofern
Attribute übergeben werden.</p>

<note>
    <p>Ab Java 22 ist es möglich, vor dem eigentlichen <code>super()</code>-Aufruf noch weitere Anweisungen zu schreiben.</p>
    <code-block lang="java">
        public Dog(...) {
            System.out.println("Statement before super call") // Allowed since Java 22
            super(...);
        }
    </code-block>
</note>

<warning>
    <p>Bis Java 21 erhält man jedoch einen Error: <format color="%WarningHighlight%">Call to 'super()' must be first statement in constructor body</format></p>
</warning>

<p>Passen wir die <code>main()</code>-Methode etwas an.</p>

<code-block lang="java">
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
</code-block>

#### <format color="%c1%">Die Mutter aller Klassen – `Object`</format> {id="the-mother-of-all-classes-object"}

<p>Wie wir bereits wissen, gibt es in Java eine
<format color="%LinkColor%"><a href="10-java-classes.md">Klasse</a></format>, die über allen anderen steht:
<code>Object</code>. Man könnte sie als die "Mutter aller Klassen" bezeichnen. Jede Klasse erbt automatisch von
<code>Object</code>, auch wenn dies nicht explizit angegeben wird. Das bedeutet, dass alle Klassen direkt oder indirekt
Unterklassen von <code>Object</code> sind.</p>

<p><code>Object</code> bietet eine gemeinsame Basis für alle
<format color="%LinkColor%"><a href="10-java-classes.md">Klassen</a></format>, was die Interoperabilität und Konsistenz
zwischen verschiedenen Klassen und <tooltip term="API"><format color="%GlossaryLinkColor%">APIs</format></tooltip>
 erleichtert. Da jede Klasse von <code>Object</code> erbt, haben alle
<format color="%LinkColor%"><a href="11-java-objects.md">Objekte</a></format> einen gemeinsamen Satz von Methoden, was
das Arbeiten mit verschiedenen <format color="%LinkColor%"><a href="02-java-data-types.md">Datentypen</a></format> in
einer einheitlichen Weise ermöglicht.</p>

<p>Wenn wir eine eigene Klasse erstellen, haben wir die Möglichkeit, diese Methoden zu
<format color="%LinkColor%"><a href="#polymorphism">überschreiben</a></format>, um das Verhalten der Objekte anzupassen.
</p>

##### <format color="%c1%">Grundlegende Methoden der Klasse</format> `Object` {id="basic-methods-of-the-object-class"}

<p>Im Folgenden sind einige Methoden der Klasse <code>Object</code> aufgelistet, die überschrieben werden können.</p>

<table>
    <tr>
        <td>Methode</td>
        <td>Beschreibung</td>
    </tr>
    <tr>
        <td><code>equals()</code></td>
        <td>
            <p>Überprüft die Gleichheit von
            <format color="%LinkColor%"><a href="11-java-objects.md">Objekten</a></format>. Standardmäßig prüft sie, ob
            zwei Referenzen auf dasselbe Objekt zeigen.</p>
            <p>Wir kennen bereits eine Implementierung dieser Methode bei einem
            <format color="%LinkColor%"><a href="05-java-strings.md#string-methods">String</a></format>-Objekt.</p>
        </td>
    </tr>
    <tr>
        <td><code>hashCode()</code></td>
        <td>Liefert einen Hash-Code für das
        <format color="%LinkColor%"><a href="11-java-objects.md">Objekt</a></format>, der häufig in Hash-basierten
        <format color="%LinkColor%"><a href="19-java-collections.md">Collections</a></format> wie <code>HashMap</code>
        oder <code>HashSet</code> verwendet wird. Wenn <code>equals()</code> überschrieben wird, sollte auch
        <code>hashCode()</code> überschrieben werden, um sicherzustellen, dass Objekte, die als gleich betrachtet
        werden, denselben Hash-Code haben.</td>
    </tr>
    <tr>
        <td><code>toString()</code></td>
        <td>
            <p>Gibt eine <format color="%LinkColor%"><a href="05-java-strings.md">String</a></format>-Darstellung des
            Objekts zurück. Standardmäßig gibt sie den Klassennamen gefolgt von einer hexadezimalen Darstellung des
            Hashcodes eines Objekts zurück.</p>
            <p>Auch diese Implementierung kennen wir bereits aus
            <format color="%LinkColor%"><a href="05-java-strings.md#string-methods">Kapitel 11 – Objekte: Die
            toString()-Methode</a></format>.</p>
        </td>
    </tr>
    <tr>
        <td><code>clone()</code></td>
        <td>Eine Kopie eines Objekts kann mit dieser Methode erstellt werden. Zu beachten ist jedoch, dass das Klonen in
        Java spezielle Implementierungen erfordert und nicht für alle Klassen sinnvoll ist. Die Methode selbst ist in
        der <code>Object</code>-Klasse als <code>native</code> deklariert – siehe
        <tooltip term="JNI"><format color="%GlossaryLinkColor%">JNI</format></tooltip> und
        <format color="%LinkColor%"><a href="12-java-modifier-access-rights.md">Kapitel 12 – Modifizierer und
        Zugriffsrechte</a></format></td>
    </tr>
    <tr>
        <td><code>finalize()</code></td>
        <td>Wird aufgerufen, bevor das <format color="%LinkColor%"><a href="11-java-objects.md#the-garbage-collector">
        Garbage Collection-Subsystem</a></format> ein Objekt endgültig zerstört. Die Verwendung von
        <code>finalize()</code> ist jedoch in modernen Java-Anwendungen nicht mehr üblich. Die Methode selbst ist mit
        <code>@Deprecated</code> markiert und wird zukünftig entfernt werden.</td>
    </tr>
</table>

#### <format color="%c1%">Das Keyword `instanceof`</format> {id="the-keyword-instanceof"}

<p>Das Keyword <code>instanceof</code> wird verwendet, um zu überprüfen, ob ein
<format color="%LinkColor%"><a href="11-java-objects.md">Objekt</a></format> ein Exemplar einer bestimmten
<format color="%LinkColor%"><a href="10-java-classes.md">Klasse</a></format> oder eines
<format color="%LinkColor%"><a href="#interfaces">Interfaces</a></format> ist. Trifft dies zu, kann das entsprechende
Objekt in den jeweiligen Typ
<format color="%LinkColor%"><a href="03-java-variables.md#type-casting">gecastet</a></format> werden, um typspezifische
Anweisungen durchzuführen.</p>

<code-block lang="java">
    Object object = new Dog("Killer", 5);
    
    if (object instanceof Dog) {
        Dog dog = (Dog) object;
        dog.eat();
    } else {
        System.out.println("Instance of 'Object' or other class");
    }
</code-block>

##### <format color="%c1%">Pattern Matching bei `instanceof` ab Java 16</format> {id="java-16-pattern-matching-instanceof"}

<p>Bislang musste nach jeder Typüberprüfung ein separater
<format color="%LinkColor%"><a href="03-java-variables.md#type-casting">Cast</a></format> in den entsprechenden Typ
erfolgen, der in einer Hilfsvariable gespeichert wurde, um typspezifische Anweisungen ausführen zu können. Seit Java 16
ist dies nun mit einer kürzeren und eleganteren Schreibweise möglich.</p>

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

<p>Abstraktion bedeutet, dass komplexe Systeme auf eine einfachere und klarere Weise dargestellt werden können, indem
unnötige Details ausgeblendet werden.</p>

<p>Schaut man sich dazu die <format color="%LinkColor%"><a href="10-java-classes.md">Klassen</a></format>
<code>Animal</code>, <code>Dog</code> und <code>Cat</code> an, fällt auf, dass dieses Prinzip bereits teilweise
umgesetzt wurde. Denn die gemeinsamen Eigenschaften <code>name</code> und <code>age</code> wurden in der Oberklasse
<code>Animal</code> zusammengefasst. Genauso wie deren
<format color="%LinkColor%"><a href="10-java-classes.md#getter-and-setter">Getter und Setter</a></format>. Somit wurde
vermieden, dass die
<format color="%LinkColor%"><a href="10-java-classes.md#object-variables">Objektvariablen</a></format> und
<format color="%LinkColor%"><a href="10-java-classes.md#object-methods">-methoden</a></format> sowohl in der Klasse
<code>Dog</code> als auch in der Klasse <code>Cat</code> stehen.</p>

<p>Besitzt eine Katze eine Eigenschaft, die ein Hund nicht besitzt, ergibt es keinen Sinn diese Eigenschaft in der
Oberklasse zu speichern. Es reicht aus, diese Eigenschaft nur für
<format color="%LinkColor%"><a href="11-java-objects.md">Objekte</a></format> der Klasse <code>Cat</code> zu speichern.
</p>

<p>Die Klassen können allerdings noch weiter abstrahiert werden. Sowohl Hunde als auch Katzen können fressen. Also kann
auch die Methode <code>eat()</code> in die Oberklasse ausgelagert werden. <code>super</code> muss in der Methode
<code>eat()</code> allerdings noch zu <code>this</code> geändert werden, da es keine Eigenschaft <code>name</code> in
der Oberklasse <code>Object</code> gibt.</p>

<p>Befindet sich eine Variable in der Oberklasse, kann mit der entsprechenden Berechtigung auch mit <code>this</code>
 aus der Unterklasse auf diese zugegriffen werden. Es kann natürlich auch ganz weggelassen werden, da es keine
<format color="%LinkColor%"><a href="10-java-classes.md#the-keyword-this">gleichnamige lokale Variable</a></format>
 innerhalb dieser <format color="%LinkColor%"><a href="10-java-classes.md#object-methods">Objektmethode</a></format>
 gibt.</p>

<note title="Angaben von this und super – Best Practice">Ich selbst bevorzuge die expliziten Angaben mit
<code>this</code> für Objektvariablen und Objektmethoden in <format color="%NoteHighlight%">derselben Klasse</format>
 und <code>super</code> für den Aufruf von Objektvariablen und Objektmethoden in der
<format color="%NoteHighlight%">Oberklasse</format>. Dadurch wird klarer, in welchen Klassen die Variablen und Methoden
deklariert sind.</note>

<code-block lang="java">
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
</code-block>

<code-block lang="java">
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
</code-block>

<code-block lang="java">
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
</code-block>

### <format color="%c3%">Kapselung</format> {id="encapsulation"}

<p>Kapselung bedeutet, dass der interne Zustand eines
<format color="%LinkColor%"><a href="11-java-objects.md">Objekts</a></format> durch eine öffentliche Schnittstelle
verborgen wird, um unerwartete Änderungen und Fehler zu vermeiden bzw. das Lesen oder Ändern von Daten einzuschränken.
</p>

<p>Auch dieses Konzept wurde bereits in den Klassen <code>Animal</code>, <code>Dog</code>, und <code>Cat</code>
 angewendet. Dort wurden die
<format color="%LinkColor%"><a href="10-java-classes.md#object-variables">Objektvariablen</a></format> auf
<code>private</code>, später auf <code>protected</code> gesetzt und
<format color="%LinkColor%"><a href="10-java-classes.md#getter-and-setter">Getter und Setter</a></format> als
Kontrollpunkte für den Zugriff auf diese verwendet.</p>

<p>Etwas zu schreiben wie</p>

<code-block lang="java">
    nala.age = -10;
</code-block>

<p>sollte logischerweise nicht möglich sein.</p>

<p>Dies ist zwar auch durch
<format color="%LinkColor%"><a href="10-java-classes.md#getter-and-setter">Setter</a></format> möglich, doch durch
Setter haben wir den Vorteil, dass wir solche Fälle abfragen können.</p>

<code-block lang="java">
    public void setAge(int age) {
        if (age &lt; 0) return;
        this.age = age;
    }
</code-block>

### <format color="%c4%">Polymorphismus</format> {id="polymorphism"}

<p>Polymorphismus bietet die Möglichkeit, dass verschiedene Typen so agieren, als wären sie derselbe Typ. Das Verhalten
jedes Typs ist jedoch unterschiedlich. Klinkt kompliziert?</p>

<p>Schauen wir uns dazu nochmal die <format color="%LinkColor%"><a href="10-java-classes.md">Klassen</a></format>
<code>Animal</code>, <code>Dog</code> und <code>Cat</code> an. Fügen wir zur Klasse <code>Animal</code> eine Methode
<code>giveLoud()</code>, ändern die Namen der Methoden <code>bark()</code> und <code>meow()</code> in den Kindklassen
ebenfalls zum Namen <code>giveLoad()</code> und passen die <code>main()</code>-Methode etwas an.</p>

<code-block lang="java">
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
</code-block>

<code-block lang="java">
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
</code-block>

<code-block lang="java">
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
</code-block>

<code-block lang="java">
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
</code-block>

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
        <p>Wir speichern zwar eine Referenz auf die
        <format color="%LinkColor%"><a href="11-java-objects.md">Objekte</a></format> in einer
        <format color="%LinkColor%"><a href="03-java-variables.md">lokalen Variablen</a></format> vom Typ
        <code>Animal</code>, aber die Objekte agieren wie ein <code>Cat</code>- und <code>Dog</code>-Objekt.</p>
    </tab>
</tabs>

<p>Was in diesen <format color="%LinkColor%"><a href="10-java-classes.md">Klassen</a></format> nun passiert ist, dass
innerhalb der Kindklassen das Verhalten der Klasse <code>Animal</code> überschrieben wird, indem die
<format color="%LinkColor%"><a href="10-java-classes.md#object-methods">Objektmethode</a></format>
<code>giveLoad()</code> mit einer eigenen Implementierung der Kindklasse überschrieben wird. Es werden immer die
Objektmethoden der Kindklassen aufgerufen, sofern diese eine eigene Implementierung mitbringen.</p>

<note title="Annotation @Override – Best Practice">Der
<tooltip term="Compiler"><format color="%GlossaryLinkColor%">Compiler</format></tooltip> meckert zwar nicht herum,
allerdings zeugt es von sauberem Arbeiten, wenn oberhalb der überschriebenen Methoden die
<format color="%NoteLinkColor%"><a href="26-java-annotations.md">Annotation</a></format> <code>@Override</code> steht.
</note>

<p>Es können auch die
<format color="%LinkColor%"><a href="10-java-classes.md#object-methods">Objektmethoden</a></format> der Oberklassen aus
den Objektmethoden der Kindklassen aufgerufen werden. Dies ergibt aber nur Sinn, wenn innerhalb der Methoden der
Oberklasse Code geschrieben wurde, der für die jeweilige Kindklasse ebenfalls relevant ist.</p>

<code-block lang="java">
    @Override  
    public void giveLoud() {
        super.giveLoud();
        System.out.println(super.name + " bark!");  
    }
</code-block>

#### <format color="%c4%">Abstrakte Klassen</format> {id="abstract-classes"}

<p>Bis jetzt gibt es im obigen Programm nur Hunde und Katzen. Da beide Tiere Laute von sich geben, können die
Kindklassen dazu gezwungen werden, die
<format color="%LinkColor%"><a href="10-java-classes.md#object-methods">Objektmethode</a></format>
<code>giveLoud()</code> zu implementieren, indem in der Oberklasse <code>Animal</code> die Methode
<code>giveLoud()</code> als <code>abstract</code> deklariert wird.</p>

<code-block lang="java">
    public abstract void giveLoud();
</code-block>

<p>Diese Methode hat jetzt nur noch eine Signatur, jedoch keine eigene Implementierung. Zusätzlich muss der Klasse
<code>Animal</code> noch das Keyword <code>abstract</code> verpasst werden, da mindestens eine Methode existiert, die
als <code>abstract</code> deklariert wurde.</p>

<code-block lang="java">
    public abstract class Animal {
        // ...
    }
</code-block>

<p>Dadurch wird verhindert, dass ein <format color="%LinkColor%"><a href="11-java-objects.md">Objekt</a></format> dieser
Klasse erstellt werden kann. Ein neues Objekt muss also immer ein konkretes Tier sein.</p>

<warning>
    <p>Folgendes ist somit nicht mehr erlaubt:</p>
    <code-block lang="java">
        Animal animal = new Animal("Unknown", 10);
    </code-block>
</warning>

<p>Das ergibt auch Sinn. In der <format color="%LinkColor%"><a href="10-java-classes.md">Klasse</a></format>
<code>Animal</code> haben wir eine Methode mit <code>abstract</code> deklariert und die somit keine eigene
Implementierung mitbringt.</p>

<p>Angenommen, wir hätten dennoch die Möglichkeit ein
<format color="%LinkColor%"><a href="11-java-objects.md">Objekt</a></format> dieser Klasse zu erzeugen und rufen die
abstrakte Methode über dieses Objekt auf, was würde passieren? Man weiß es nicht … und die Methode auch nicht, denn
sie hat ja keine Implementierung. Die Methode besitzt keinen ausführbaren Code.</p>

<p>Die Instanziierung und den möglichen Aufruf dieser Methode, wird durch die Modifizierung der Klasse mit
<code>abstract</code> verhindert.</p>

<p>Werden nun die <format color="%LinkColor%"><a href="10-java-classes.md#object-methods">Objektmethoden</a></format>
 aus der Kindklasse entfernt oder werden weitere Klassen erstellt, die von der Klasse <code>Animal</code> erben, dann
gibt es einen <tooltip term="Compiler"><format color="%GlossaryLinkColor%">Compiler</format></tooltip>-Fehler der
folgenden Art, bis die notwendigen Methoden überschrieben wurden.</p>

<warning>
    <p>Class 'Dog' must either be declared abstract or implement abstract method 'giveLoud()' in 'Animal'</p>
</warning>

<p>Dieses Vorgehen ist nützlich, wenn Kindklassen ihre eigenen Implementierungen mitbringen sollen.</p>

#### <format color="%c4%">Interfaces</format> {id="interfaces"}

<p>Eine Alternative zu <format color="%LinkColor%"><a href="#abstract-classes">abstrakten Klassen</a></format> sind
Interfaces (Schnittstellen). Interfaces dienen dazu, ein bestimmtes Verhalten zu definieren, ohne eine konkrete
Implementierung vorzugeben. Solche Methodendeklarationen werden häufig auch Signaturen genannt (wie abstrakte Methoden
in abstrakten Klassen).</p>

<p><format color="%LinkColor%"><a href="10-java-classes.md">Klassen</a></format> können diese Interfaces und diese
vorgeschriebene Funktionalität dann implementieren, wobei auch die
<format color="%LinkColor%"><a href="01-java-token.md#keywords">Keywords</a></format> <code>interface</code> und
<code>implements</code> Anwendung finden. Interfaces werden meistens wie
<tooltip term="Top-Level-Class"><format color="%GlossaryLinkColor%">Top-Level-Klassen</format></tooltip> in eigenen
Dateien geschrieben, können aber auch direkt in einer Klasse definiert werden.</p>

<list>
  <li>
    <p>Alle Methoden, die innerhalb von Schnittstellen deklariert werden, sind implizit <code>public</code> und
    <code>abstract</code>, außer <format color="%LinkColor%"><a href="#default-methods">Default-Methoden</a></format>.</p>
  </li>
  <li>
    <p>Alle Variablen, die innerhalb von Schnittstellen deklariert werden, sind implizit
    <format color="%LinkColor%"><a href="10-java-classes.md#constants">Konstanten</a></format>
    (<code>static final</code>).</p>
  </li>
</list>

<p>Im obigen Beispiel mit den Tier-Klassen kommt die Verwendung der Methode <code>giveLoud()</code> zum Einsatz. Wird
dies mit Schnittstellen realisiert, sieht das Ganze folgendermaßen aus:</p>

<code-block lang="java">
    public interface Loudable {
        void giveLoud();  
    }
</code-block>

<code-block lang="java">
    public abstract class Animal implements Loudable {
    
        // ...
    
        public abstract void giveLoud(); // Can be removed
    
        // ...
    }
</code-block>

<p>Die <format color="%LinkColor%"><a href="10-java-classes.md">Klassen</a></format> <code>Dog</code> und
<code>Cat</code> behalten ihren Code bei. In der Klasse <code>Animal</code> kann die abstrakte Definition der Methode
<code>giveLoud()</code> jedoch entfernt werden, da diese bereits im Interface <code>Loudable</code> existiert. Das
Prinzip bleibt also dasselbe.</p>

<p>Hier zeigt sich die wahre Stärke von Interfaces. Angenommen wir haben noch andere
<format color="%LinkColor%"><a href="11-java-objects.md">Objekte</a></format> die Geräusche erzeugen, jedoch keine
Tiere sind – etwa ein Motor. Ein Motor kann Geräusche machen, ist aber kein Tier. Da aber sowohl Tiere als auch Motoren
Geräusche machen können, kann sowohl die Klasse <code>Animal</code> als auch eine Klasse <code>Motor</code> das
Interface <code>Loudable</code> implementieren.</p>

<p>Dieses Interface ermöglicht es den <format color="%LinkColor%"><a href="10-java-classes.md">Klassen</a></format>, die
Geräuscherzeugung auf ihre eigene Weise zu implementieren, ohne von einer gemeinsamen Oberklasse erben zu müssen.</p> 

<p>Um einen passenderen Namen für das Interface zu nehmen, könnte man es anstelle von <code>Loudable</code> in
<code>Soundable</code> und die Methode <code>giveLoud()</code> in <code>makeSound()</code> umbenennen.</p>

<p>Ohne den Kontext zu kennen, ist es schwer zu verstehen, was dieses Interface und seine Methode tun sollen. Umso mehr,
wenn es in zwei solch unterschiedlichen Umgebungen verwendet wird. <code>Loudable</code> ist kein geläufiger Begriff und
<code>giveLoud()</code> klingt eher nach einer Anweisung wie "Ton geben", was nicht intuitiv ist.</p>

<p>Im Gegensatz dazu deutet ein Interface namens <code>Soundable</code> mit einer Methode <code>makeSound()</code>
 sofort darauf hin, dass es sich um etwas handelt, das Geräusche erzeugen kann. Der Name ist selbsterklärend und macht
den Code verständlicher.</p>

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
        <td><code>java.io.Serializable</code></td>
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

<p>Schnittstellen, die nur eine Methode definieren, werden als funktionale Schnittstellen bezeichnet und können mittels
<format color="%LinkColor%"><a href="18-java-lambda-expressions.md">Lambda-Ausdrücken</a></format> verwendet werden.
Wenn Schnittstellen nur eine Methode definieren sollen, kann diese Schnittstelle mit der
<format color="%LinkColor%"><a href="26-java-annotations.md">Annotation</a></format> <code>@FunctionalInterface</code>
 versehen werden, sofern keine
<format color="%LinkColor%"><a href="#default-methods">Default-Implementierung</a></format> verwendet wird. Dadurch
berprüft der <tooltip term="Compiler"><format color="%GlossaryLinkColor%">Compiler</format></tooltip>, ob die Regeln für
funktionale Schnittstellen eingehalten werden.</p>

<code-block lang="java">
    @FunctionalInterface
    public interface Soundable {  
        void makeSound();  
    }
</code-block>

<p>Dies ermöglicht eine vereinfachte Schreibweise beim Aufruf dieser Methoden. Bevor jedoch die
<format color="%LinkColor%"><a href="26-java-annotations.md">Annotation</a></format> verwendet werden, sollte man
sorgfältig abwägen, ob das Interface später um weitere Methoden ergänzt werden könnte.</p>

<p>Falls ja und die Annotation wurde bereits hinzugefügt, könnte dies zu Inkompatibilitäten führen und vorhandenen Code,
der das Interface nutzt, beeinträchtigen.</p>

##### <format color="%c4%">Default-Methoden</format> {id="default-methods"}

<p>Interfaces können auch mit einer Default-Implementierung versehen werden. Dabei wir das Keyword <code>default</code>
 verwendet.</p>

<code-block lang="java">
    public interface Soundable {  
    
        default void makeSound(String name) {
            System.out.println(name + " makes a sound!");
        }  
    }
</code-block>

<p>Dadurch werden die <format color="%LinkColor%"><a href="10-java-classes.md">Klassen</a></format>, die dieses
Interface implementieren, nicht mehr dazu gezwungen, Methoden zu überschreiben, können dies aber bei Bedarf dennoch tun.
</p>

##### <format color="%c4%">Abstrakte Klassen vs. Schnittstellen</format> {id="abstract-classes-vs-interfaces"}

<p>Die prinzipielle Anwendung zwischen Schnittstellen und
<format color="%LinkColor%"><a href="#abstract-classes">abstrakten Klassen</a></format> bleibt dieselbe und beide
besitzen viele Ähnlichkeiten und können auch auf ähnliche Weise eingesetzt werden. Zudem können Interfaces auch von
anderen Interfaces erben. Allerdings haben Schnittstellen einen fundamentalen Unterschied.</p>

<p>Während Klassen nur von einer einzigen <format color="%LinkColor%"><a href="10-java-classes.md">Klasse</a></format>
 erben können (ob direkt oder indirekt), können mehrere Interfaces implementiert werden. Dies ist zwar auch durch
mehrstufige Vererbung möglich, allerdings können dadurch tiefe und unübersichtliche Hierarchien entstehen.</p>

<p>Auch wenn Interfaces mehr Flexibilität bezüglich des Verhaltens von Objekten in unterschiedlichen Klassenhierarchien
mitbringen, muss noch ein weiteres Konzept bedacht werden. Wie bereits weiter oben erwähnt, sind alle "Variablen",
welche innerhalb eines Interfaces definiert werden, implizit
<format color="%LinkColor%"><a href="10-java-classes.md#constants">Konstanten</a></format>.</p>

<note>
    <p>Interfaces können also keine Objektzustände speichern.</p>
</note>

## Versiegelte Klassen und Interfaces {id="sealed-classes-and-interfaces"}

<p>Versiegelte <format color="%LinkColor%"><a href="10-java-classes.md">Klassen</a></format> und
<format color="%LinkColor%"><a href="#interfaces">Interfaces</a></format>, eingeführt als Preview in Java 15 und
finalisiert mit Java 17, bieten eine neue Möglichkeit, die
<format color="%LinkColor%"><a href="#inheritance">Vererbungshierarchie</a></format> zu kontrollieren. Sie ermöglichen
es Entwicklern klar und präzise festzulegen, welche Klassen oder Interfaces die Möglichkeit haben, eine bestimmte Klasse
zu erweitern oder ein Interface zu implementieren.</p>

<p>Eine versiegelte <format color="%LinkColor%"><a href="10-java-classes.md">Klasse</a></format> ist eine Klasse, die
explizit festlegt, welche anderen Klassen sie erweitern dürfen. Ebenso können versiegelte
<format color="%LinkColor%"><a href="#interfaces">Interfaces</a></format> bestimmen, welche anderen Interfaces oder
Klassen sie implementieren dürfen. Dies erfolgt durch die Verwendung des neuen
<format color="%LinkColor%"><a href="01-java-token.md#keywords">Keywords</a></format> <code>sealed</code> in der
Klassendeklaration, gefolgt von dem Schlüsselwort <code>permits</code> und einer Liste der zulässigen Subklassen.</p>

<code-block lang="java">
    public sealed class Animal permits Dog, Cat {
        // ...
    }
    
    public final class Dog extends Animal {
    // ...
    }
    
    public final class Cat extends Animal {
    // ...
    }
</code-block>

<p>Versiegelte Klassen und Interfaces bieten auch Flexibilität, da eine versiegelte Klasse nicht zwingend
<code>final</code> sein muss. Stattdessen können die erlaubten Subklassen selbst wieder versiegelt sein, was eine
kontrollierte Vererbungskette ermöglicht.</p>

<code-block lang="java">
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
</code-block>

<note>
    <p>Alle Unterklassen, welche von einer versiegelten Klasse erben, müssen entweder als <code>sealed</code>,
    <code>non-sealed</code> oder <code>final</code> deklariert werden.</p>
</note>

<list>
  <li>
    <p>Wenn eine (Unter-)Klasse als <code>final</code> deklariert wird, kann sie nicht weiter vererbt werden. Das
    bedeutet, dass diese <format color="%LinkColor%"><a href="10-java-classes.md">Klasse</a></format> die Endstation in
    der Vererbungshierarchie ist.</p>
  </li>
  <li>
    <p>Wenn eine Unterklasse wiederum als <code>sealed</code> deklariert wird, setzt sie die versiegelte
    <format color="%LinkColor%"><a href="#inheritance">Vererbungshierarchie</a></format> fort. Das bedeutet, dass diese
    <format color="%LinkColor%"><a href="10-java-classes.md">Klasse</a></format> nur von einer definierten Gruppe von
    Klassen erweitert werden kann, die explizit in der <code>permits</code>-Liste angegeben sind. Dies ermöglicht eine
    weitere Vererbung, jedoch unter strenger Kontrolle, welche Klassen beteiligt sind.</p>
  </li>
  <li>
    <p>Wenn eine Unterklasse als <code>non-sealed</code> deklariert wird, wird die
    <format color="%LinkColor%"><a href="#inheritance">Vererbungshierarchie</a></format> geöffnet und die Klasse kann
    wie eine normale Klasse weiter vererbt werden, ohne Beschränkungen.</p>
  </li>
</list>

<p>Im folgenden Beispiel legt das versiegelte Interface <code>Role</code> fest, dass nur die
<format color="%LinkColor%"><a href="10-java-classes.md">Klassen</a></format> <code>Admin</code>, <code>Moderator</code>
 und <code>Guest</code> eine Rolle im Programm übernehmen können. Die Klasse <code>Guest</code> ist als
<code>non-sealed</code> deklariert, sodass sie von weiteren Klassen erweitert werden kann, falls zusätzliche spezifische
Gastrollen erforderlich sind.</p>

<code-block lang="java">
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
</code-block>