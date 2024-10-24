# 11 Java – Objekte


Nachdem ich euch jetzt gefühlt ein Dutzend Mal das Wort „Objekt“ um die Ohren gehauen habe, wird es höchste Zeit, dass wir uns endlich diesem mysteriösen Thema widmen. Was sind eigentlich Objekte? Fast alles, was in Java existiert, besteht aus Objekten, die auf sogenannten <format color="%LinkColor%">[Referenzdatentypen](02-java-data-types.md#reference-data-types)</format> basieren – die <format color="%LinkColor%">[primitiven Datentypen](02-java-data-types.md#primitive-data-types)</format> wie `int` und `boolean` einmal ausgenommen.

Ein Objekt ist im Wesentlichen eine Instanz einer Klasse und diese Instanz kann so ziemlich alles sein, was ihr euch vorstellen könnt – von Bällen, über Menschen, bis hin zu abstrakten Konzepten wie Aktivitäten oder Dimensionen.

Stellt euch vor, ihr seid im Spielzeugladen: Dort gibt es Bälle, Autos und vielleicht sogar eine mysteriöse Dimension in eine andere Welt. All diese Spielzeuge, äh, Objekte, stammen aus einer Art Bauanleitung – der <format color="%LinkColor%">[Klasse](10-java-classes.md)</format>. Jede dieser Klassen ist ein Nachfahre der Klasse <format color="%LinkColor%">[Object](14-java-oop.md#the-mother-of-all-classes-object)</format> – der Urmutter aller Klassen in Java. Aber keine Sorge. Die Details dazu werden wir in <format color="%LinkColor%">[Kapitel 14 – OOP: Vererbung](14-java-oop.md#inheritance)</format> noch genau unter die Lupe nehmen.

Also egal, ob ein Ball oder eine andere Dimension, in Java ist es immer ein Objekt. Ein Objekt ist nicht nur irgendein zufälliger Datenhaufen, sondern ein Codebaustein der brav die <format color="%LinkColor%">[Regeln der objektorientierten Programmierung](14-java-oop.md#principles-of-oop)</format> befolgt (in den meisten Fällen) und durch die Eigenschaften (<format color="%LinkColor%">[Objektvariablen](10-java-classes.md#object-variables)</format>) und Funktionalitäten (<format color="%LinkColor%">[Objektmethoden](10-java-classes.md#object-methods)</format>) beschrieben wird.

Zwei bestimmte Typen wurden bereits in früheren Kapiteln betrachtet.

- <format color="%LinkColor%">[Kapitel 5 – Zeichenketten](05-java-strings.md)</format>
- <format color="%LinkColor%">[Kapitel 8 – Arrays](08-java-arrays.md)</format>

Auch eigene Objekte bzw. <format color="%LinkColor%">[Referenztypen](02-java-data-types.md)</format> können erstellt werden, wie z.B. ein `Dog` oder `Movie`.

## Initialisierung {id="initialisation"}

In <format color="%LinkColor%">[Kapitel 10 – Klassen](10-java-classes.md)</format> wurde bereits eine Klasse `Dog` erstellt.

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

    public void eat() {
        System.out.println(this.name + " is eating!");
    }

    public void bark() {
        System.out.println(this.name + " barks!");
    }
}
```

Nun werden wir zu dieser Klasse zwei `Dog`-Objekte in der `Main`-Klasse anlegen.

```Java
public class Main {

    public static void main(String[] args) {
        Dog bello = new Dog("Bello");
        Dog killer = new Dog("Killer", 5);
    }
}
```

Die runden Klammern müssen genau die Anzahl der Werte enthalten, die die <format color="%LinkColor%">[Konstruktoren](10-java-classes.md#constructors)</format> erwarten. Da wir einen Konstruktor mit einem Wert und einen mit zwei Werten haben, sind beide Varianten gültig. Mit dem <format color="%LinkColor%">[Keyword](01-java-token.md#keywords)</format> `new` wird ein neues Objekt (Instanz) der <format color="%LinkColor%">[Klasse](10-java-classes.md)</format> erstellt und im <tooltip term="Java-Heap"><format color="%GlossaryLinkColor%">Java-Heap</format></tooltip> allokiert.

## Objektvariablen auslesen und verändern {id="reading-and-changing-object-variables"}

Wollen wir nun die Werte der Objekte auf der Konsole ausgeben, können wir nicht einfach nur das Objekt an die `println()`-Methode übergeben. Dadurch erhalten wir eine ziemlich merkwürdig aussehende Zeichenfolge, die weiter unten im Abschnitt <format color="%LinkColor%">["Die toString()-Methode"](#the-tostring-method)</format> erklärt wird.

```Java
public static void main(String[] args) {
    Dog bello = new Dog("Bello");
    Dog killer = new Dog("Killer", 5);

    System.out.println(bello);  // kesares.techarchive.Dog@65ab7765
    System.out.println(killer); // kesares.techarchive.Dog@1b28cdfa
}
```

Um auf die Variablen zugreifen zu können, sprechen wir einfach über das Objekt den Namen der <format color="%LinkColor%">[Objektvariablen](10-java-classes.md#object-variables)</format> an.

```Java
public static void main(String[] args) {
    Dog bello = new Dog("Bello");
    Dog killer = new Dog("Killer", 5);

    System.out.println(bello.name);  // Bello
    System.out.println(killer.name); // Killer
}
```

Auf diese Weise können wir nicht nur die Werte abgreifen, sondern auch verändern.

```Java
public static void main(String[] args) {
    Dog bello = new Dog("Bello");
    Dog killer = new Dog("Killer", 5);
    
    System.out.println(bello.name);  // Bello
    System.out.println(killer.name); // Killer
    System.out.println(bello.age);   // 0
    System.out.println(killer.age);  // 5
    
    bello.name = "Balu";
    killer.name = "Rocky";
    bello.age = 10;
    killer.age = 3;
    
    System.out.println(bello.name);  // Balu
    System.out.println(killer.name); // Rocky
    System.out.println(bello.age);   // 10
    System.out.println(killer.age);  // 3
}
```

Die beiden Objekte haben jeweils eine Objektvariable für den Namen und eine für das Alter. Die <format color="%LinkColor%">[Objektvariablen](10-java-classes.md#object-variables)</format> sind abhängig von einem konkreten Objekt und somit auch dessen Werte. Werden die Werte eines Objekts verändert, hat dies keine Auswirkungen auf die Werte eines anderen Objekts.

> Bei <format color="%NoteLinkColor%">[Klassenvariablen](10-java-classes.md#class-variables)</format> sieht dies anders aus. Denn sie gehören zur Klasse und nicht zu einem Objekt.
{style="note"}

## Zugriff auf Objektvariablen und Objektmethoden {id="access-to-object-variables-and-methods"}

Aber wollen wir wirklich, dass die Werte der Objekte von überall einfach so verändert werden können? Nein!
Lösung: Wir setzen den Modifier der <format color="%LinkColor%">[Objektvariablen](10-java-classes.md#object-variables)</format> auf `private`.

```Java
private String name;
private int age;
```
Jetzt können die Werte nicht mehr einfach so verändert werden, da sie nur noch innerhalb der Klasse `Dog` sichtbar sind.

```Java
public static void main(String[] args) {
    Dog bello = new Dog("Bello");
    Dog killer = new Dog("Killer", 5);

    System.out.println(bello.name);  // No access
    System.out.println(killer.name); // No access
    System.out.println(bello.age);   // No access
    System.out.println(killer.age);  // No access

    bello.name = "Balu";             // No access
    killer.name = "Rocky";           // No access
    bello.age = 10;                  // No access
    killer.age = 3;                  // No access

    System.out.println(bello.name);  // No access
    System.out.println(killer.name); // No access
    System.out.println(bello.age);   // No access
    System.out.println(killer.age);  // No access
}
```

Nur haben wir jetzt auch keinen Zugriff mehr auf die eigentlichen Werte. Hier kommen die in <format color="%LinkColor%">[Kapitel 10 – Klassen](10-java-classes.md)</format> angesprochenen <format color="%LinkColor%">[get()-Methoden](10-java-classes.md#getter-and-setter)</format> zum Einsatz. In der `main()`-Methode müssen wir jetzt nur noch diese <format color="%LinkColor%">[Objektmethoden](10-java-classes.md#object-methods)</format> über das Objekt aufrufen. Auch alle weiteren Objektmethoden können auf diese Weise aufgerufen werden.

```Java
public String getName() {  
    return name;  
}  
  
public int getAge() {  
    return age;  
}
```

```Java
public static void main(String[] args) {
    Dog bello = new Dog("Bello");
    Dog killer = new Dog("Killer", 5);

    System.out.println(bello.getName());  // Bello
    System.out.println(killer.getName()); // Killer
    System.out.println(bello.getAge());   // 0
    System.out.println(killer.getAge());  // 5

    bello.name = "Balu";                  // No access
    killer.name = "Rocky";                // No access
    bello.age = 10;                       // No access
    killer.age = 3;                       // No access

    System.out.println(bello.name);       // No access
    System.out.println(killer.name);      // No access
    System.out.println(bello.age);        // No access
    System.out.println(killer.age);       // No access
}
```

Für das Starten des Programms müssen jedoch die restlichen Zeilen mit den Errors entfernt oder auskommentiert werden. Andernfalls wird auch auf der Konsole, ein Error ausgegeben, dass die jeweiligen <format color="%LinkColor%">[Objektvariablen](10-java-classes.md#object-variables)</format> nicht sichtbar sind. Abhängig von der <tooltip term="IDE"><format color="%GlossaryLinkColor%">IDE</format></tooltip> kann sich dieser jedoch unterscheiden.

> ```
> java: name has private access in kesares.techarchive.Dog
>```
{style="warning" title="IntelliJ IDEA Error"}

Sollte gewünscht sein, die Werte der Objekte zu ändern, können die dafür vorgesehenen <format color="%LinkColor%">[set()-Methoden](10-java-classes.md#getter-and-setter)</format> verwendet werden. Der Wert muss dann beim Aufruf mit übergeben werden.

```Java
public void setName(String name) {  
    this.name = name;  
}
```

> Die Objektvariablen sollten zu Beginn schon mit `private` versehen werden und <format color="%NoteLinkColor%">[Getter und Setter](10-java-classes.md#getter-and-setter)</format> sollten erst dann hinzukommen, wenn diese wirklich benötigt werden. Andernfalls könnte der Programmcode sehr früh mit unnötigen Zeilen Code gefüllt werden, die keine Verwendung haben.
{style="note" title="Best Practice"}

## Die `toString()`-Methode {id="the-tostring-method"}

Die `toString()`-Methode ist eine <format color="%LinkColor%">[Objektmethode](10-java-classes.md#object-methods)</format> der Klasse `Object`. Da alle Objekte intern von dieser Klasse erben, ist es möglich, diese sowie viele andere Objektmethoden zu überschreiben – siehe <format color="%LinkColor%">[Kapitel 14 – OOP: Polymorphismus](14-java-oop.md#polymorphism)</format>.

```Java
public String toString() {  
    return getClass().getName() + "@" + Integer.toHexString(hashCode());  
}
```

Wird diese Objektmethode von einem Objekt aufgerufen, welche nicht die Objektmethode überschrieben hat, wird ein bestimmter <format color="%LinkColor%">[String](05-java-strings.md)</format> zurückgegeben. Der `String` setzt sich mit dem Namen der aufrufenden <format color="%LinkColor%">[Klasse](10-java-classes.md)</format>, einem `@`-Symbol und einer Adresse des Objekts – dem Hashcode in hexadezimaler Form mit 32 Bits kodiert – in folgender Art zusammen:

```Java
kesares.techarchive.Dog@65ab7765
```

Der Teil vor dem `@` repräsentiert den vollständigen Klassennamen der <format color="%LinkColor%">[Klasse](10-java-classes.md)</format>, inklusive <format color="%LinkColor%">[Package](16-java-packages-and-imports.md)</format>. Der Hashcode wird typischerweise durch die Methode `hashCode()` berechnet, die standardmäßig für jedes Objekt eine eindeutige Kennung zurückgibt.

## Der Garbage Collector {id="the-garbage-collector"}

In Programmiersprachen wie Java spielt der <tooltip term="GC"><format color="%GlossaryLinkColor%">Garbage Collector</format></tooltip> (GC) eine zentrale Rolle bei der Speicherverwaltung. Er sorgt dafür, dass nicht mehr benötigte Objekte aus dem Speicher entfernt werden, um Platz für neue Objekte zu schaffen und den <tooltip term="Java-Heap"><format color="%GlossaryLinkColor%">Heap-Speicher</format></tooltip> effizient zu nutzen.

In einer Welt ohne GC, wie C oder C++, müsstest ihr selbst darauf achten, wann welche Objekte nicht mehr gebraucht und diese manuell aus dem Speicher entfernt werden. Klingt anstrengend, oder? In Java und in vielen anderen Programmiersprachen übernimmt diese Aufgabe der Garbage Collector für euch.

#### Was ist der Heap-Speicher? {id="what-is-the-heap-memory"}

Der <tooltip term="Java-Heap"><format color="%GlossaryLinkColor%">Heap</format></tooltip> ist ein Bereich des Arbeitsspeichers, der zur Laufzeit dynamisch Speicherplatz für Objekte bereitstellt. Immer wenn ein neues Objekt erstellt wird, wird dafür Platz im Heap reserviert. Da der Speicher im Heap begrenzt ist, ist es wichtig, dass nicht mehr benötigte Objekte freigegeben werden, um Speicherlecks zu vermeiden und die Leistung der Anwendung zu erhalten.

#### Wie funktioniert der Garbage Collector? {id="how-does-the-garbage-collector-work"}

Der <tooltip term="GC"><format color="%GlossaryLinkColor%">Garbage Collector</format></tooltip> verfolgt, welche Objekte im <tooltip term="Java-Heap"><format color="%GlossaryLinkColor%">Heap</format></tooltip> noch genutzt werden und welche nicht mehr erreichbar sind. Dies geschieht typischerweise durch Algorithmen wie Mark-and-Sweep oder Generational Garbage Collection.

- <format color="%Highlight%">Mark-and-Sweep</format>: Der GC markiert alle Objekte, die noch von aktiven <format color="%LinkColor%">[Threads](java-multithreading.md)</format> oder anderen Objekten referenziert werden. Danach „fegt“ er den Heap, indem er alle nicht markierten Objekte entfernt und den freigewordenen Speicher zurückgibt.

- <format color="%Highlight%">Generational Garbage Collection</format>: Diese Methode unterteilt den Heap in verschiedene Generationen (Young Generation, Old Generation, Permanent Generation). Objekte, die gerade erst erstellt wurden, landen in der Young Generation und werden dort häufiger überprüft. Objekte, die länger leben, werden in die Old Generation verschoben, wo sie seltener überprüft werden. Objekte, die während der gesamten Laufzeit des Programms existieren, werden in die Permanent Generation verschoben. Dies ist effizient, da viele Objekte nur kurzzeitig existieren und schnell wieder entfernt werden können.

> Wer sich genauer in das Thema <format color="%NoteHighlight%">Garbage Collection</format> in Java einlesen möchte, findet <format color="%NoteLinkColor%">[hier](https://www.oracle.com/webfolder/technetwork/tutorials/obe/java/gc01/index.html)</format> mehr Infos dazu.
{style="note"}

#### Wie erkennt der Garbage Collector ungenutzte Objekte? {id="how-does-the-garbage-collector-detect-unused-objects?"}

Der GC identifiziert zerstörbare Objekte, indem er den Referenzgraphen der Objekte analysiert. Wenn ein Objekt keine Referenzen mehr hat, also von keinem anderen Objekt oder aktiven <format color="%LinkColor%">[Thread](java-multithreading.md)</format> mehr erreicht werden kann, wird es als "garbage" (Müll) betrachtet und zur Entfernung freigegeben. Dies geschieht automatisch, ohne dass der Entwickler sich aktiv um die Speicherfreigabe kümmern muss.

#### Speichermanagement in C/C++ {id="memory-management-in-c-and-cpp"}

In Sprachen wie C und C++ liegt die Speicherverwaltung vollständig in der Hand des Entwicklers. Hier gibt es keinen automatischen Garbage Collector. Stattdessen muss der Entwickler den Speicher manuell verwalten – Speicher für Objekte reservieren und ihn nach Gebrauch explizit wieder freigeben.

Diese manuelle Verwaltung ermöglicht eine sehr feinkörnige Kontrolle über den Speicher, was in einigen Szenarien, wie bei der Systemprogrammierung oder Spielen, Vorteile in Bezug auf Leistung und Speicheroptimierung bieten kann.

Die manuelle Speicherverwaltung ist jedoch anfälliger für Fehler wie Speicherlecks oder Dangling Pointers (Referenzen auf Speicher, der bereits freigegeben wurde). Solche Fehler können schwerwiegende Abstürze oder Sicherheitslücken verursachen.

Im Vergleich dazu bietet ein <tooltip term="GC"><format color="%GlossaryLinkColor%">Garbage Collector</format></tooltip> in Java oder ähnlichen Sprachen den Vorteil, dass der Entwickler sich nicht um die Speicherfreigabe kümmern muss, wodurch das Risiko von Speicherfehlern stark reduziert wird. Allerdings kommt dies oftmals mit einem kleinen Leistungseinbruch daher, da der Speicherverbrauch regelmäßig analysiert und bereinigt werden muss.

![Java vs CPP Memory](11_java_objects_1.jpg){width="400"}

## Objektstruktur im Speicher {id="object-structure-in-memory"}

<format color="%ComingSoonColor%">Coming soon...</format>

## Komplexität von Referenzdatentypen {id="complexity-of-reference-data-types"}

Wie wir am Beispiel unserer `Dog`-Klasse gesehen haben, können <format color="%LinkColor%">[Referenztypen](02-java-data-types.md)</format> auch andere Referenztypen als Eigenschaften besitzen. Der Umfang eines Objekts oder einer Klassenhierarchie kann dabei so flexibel wie die Anforderungen der jeweiligen Anwendung sein – von schlicht und einfach bis hin zu regelrechten Code-Monstern.

Stellen wir uns beispielsweise ein `Motor`-Objekt vor. Dieses könnte durchaus ein weiteres Objekt, sagen wir `Cylinder`, als Eigenschaft haben. Und weil sich Zylinder gerne in Gesellschaft von Schrauben befinden, könnte dieses `Cylinder`-Objekt wiederum ein <format color="%LinkColor%">[Array](08-java-arrays.md)</format> von `Screw`-Objekten beinhalten, um alles schön zusammenzuhalten.

Um einmal ganz kurz das Thema der <format color="%LinkColor%">[Vererbung](14-java-oop.md#inheritance)</format> vorwegzunehmen, könnte es in einem anderen Szenario notwendig sein, eine Anwendung zu entwickeln, die Lebewesen voneinander unterscheidet. Hier könnte man eine Klassenhierarchie aufbauen, in der `Animal` und `Human` von einer übergeordneten Klasse `Creature` erben, während `Dog` von `Animal` abstammt. In einer anderen, weniger komplexen Anwendung, die sich ausschließlich mit Menschen befasst, könnte man es einfach bei einer `Human`-Klasse belassen, ohne tiefer in die Stammesgeschichte abzutauchen.

Kurz gesagt: Die Komplexität und Struktur der Klassen hängt ganz von den Bedürfnissen und Anforderungen eurer Anwendung ab. Braucht ihr eine einfache Lösung, reichen vielleicht ein paar grundlegende Objekte. Wird es komplizierter, könnt ihr eine detailliertere Klassenhierarchie aufbauen und eure <format color="%LinkColor%">[Referenztypen](02-java-data-types.md)</format> nach Herzenslust schachteln. Es ist ein bisschen wie beim Kochen: Manchmal reicht ein Sandwich und manchmal wird es ein Fünf-Gänge-Menü – es kommt ganz darauf an, was ihr auf den Tisch bringen wollt.

> Aber Vorsicht, Freunde der Vererbung! So faszinierend es auch ist, Klassenhierarchien zu bauen, denkt daran, dass zu tiefe Vererbungshierarchien schnell ins Chaos führen können.
{style="note" title="Tiefe Vererbungshierarchien"}