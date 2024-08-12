# 11 Java Objekte


Nachdem ich euch jetzt gefühlt ein Dutzend Mal das Wort „Objekt“ um die Ohren gehauen habe, wird es höchste Zeit, dass wir uns endlich diesem mysteriösen Thema widmen. Was sind eigentlich Objekte? Fast alles, was in Java existiert, besteht aus Objekten, die auf sogenannten <format color="%LinkColor%">[Referenzdatentypen](02-java-data-types.md#reference-data-types)</format> basieren – die <format color="%LinkColor%">[primitiven Datentypen](02-java-data-types.md#primitive-data-types)</format> wie `int` und `boolean` einmal ausgenommen.

Ein Objekt ist im Wesentlichen eine Instanz einer Klasse und diese Instanz kann so ziemlich alles sein, was ihr euch vorstellen könnt – von Bällen, über Menschen, bis hin zu abstrakten Konzepten wie Aktivitäten oder sogar Dimensionen.

Stellt euch vor, ihr seid im Spielzeugladen: Da gibt es Bälle, Figuren, Autos und ja, vielleicht sogar eine mysteriöse Dimension in eine andere Welt. All diese Spielzeuge, äh, Objekte, stammen aus einer Art Bauanleitung – der <format color="%LinkColor%">[Klasse](10-java-classes.md)</format>. Und hier kommt der Clou: Jede dieser Klassen ist ein stolzer Nachfahre der Klasse <format color="%LinkColor%">[Object](14-java-oop.md#the-mother-of-all-classes-object)</format> – der Urmutter aller Klassen in Java. Aber keine Sorge. Die Details dazu werden wir in <format color="%LinkColor%">[Kapitel 14 – OOP: Vererbung](14-java-oop.md#inheritance)</format> noch genau unter die Lupe nehmen.

Also egal, ob ihr euch einen Ball oder eine neue Dimension vorstellen könnt, in Java ist es immer ein Objekt. Dieses Objekt ist nicht nur irgendein zufälliger Datenhaufen, sondern ein ordentlicher Codebaustein der brav die <format color="%LinkColor%">[Regeln der objektorientierten Programmierung](14-java-oop.md#principles-of-oop)</format> befolgt und durch die Eigenschaften (<format color="%LinkColor%">[Objektvariablen](10-java-classes.md#object-variables)</format>) und Funktionalitäten (<format color="%LinkColor%">[Objektmethoden](10-java-classes.md#object-methods)</format>) beschrieben wird.

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

> Bei <format color="%NoteLinkColor%">[Klassenvariablen](10-java-classes.md#class-variables)</format> sieht dies anders aus, da diese von den Objekten geteilt werden.
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

    System.out.println(bello.name);  // no access
    System.out.println(killer.name); // no access
    System.out.println(bello.age);   // no access
    System.out.println(killer.age);  // no access

    bello.name = "Balu";             // no access
    killer.name = "Rocky";           // no access
    bello.age = 10;                  // no access
    killer.age = 3;                  // no access

    System.out.println(bello.name);  // no access
    System.out.println(killer.name); // no access
    System.out.println(bello.age);   // no access
    System.out.println(killer.age);  // no access
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

    bello.name = "Balu";             // no access
    killer.name = "Rocky";           // no access
    bello.age = 10;                  // no access
    killer.age = 3;                  // no access

    System.out.println(bello.name);  // no access
    System.out.println(killer.name); // no access
    System.out.println(bello.age);   // no access
    System.out.println(killer.age);  // no access
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

Der Teil vor dem Klassennamen bezieht sich auf den Speicherort der <format color="%LinkColor%">[Klasse](10-java-classes.md)</format> im Projektverzeichnis. Unter der <format color="%Highlight%">Referenzadresse</format> ist dieses Objekt im <tooltip term="Java-Heap"><format color="%GlossaryLinkColor%">Java-Heap</format></tooltip> abgelegt.

## Komplexität von Referenzdatentypen {id="complexity-of-reference-data-types"}

Wie wir am Beispiel unserer `Dog`-Klasse gesehen haben, können <format color="%LinkColor%">[Referenztypen](02-java-data-types.md)</format> auch andere Referenztypen als Eigenschaften besitzen. Der Umfang eines Objekts oder einer Klassenhierarchie kann dabei so flexibel wie die Anforderungen der jeweiligen Anwendung sein – von schlicht und einfach bis hin zu regelrechten Code-Monstern.

Stellen wir uns beispielsweise ein `Motor`-Objekt vor. Dieses könnte durchaus ein weiteres Objekt, sagen wir `Cylinder`, als Eigenschaft haben. Und weil sich Zylinder gerne in Gesellschaft von Schrauben befinden, könnte dieses `Cylinder`-Objekt wiederum ein <format color="%LinkColor%">[Array](08-java-arrays.md)</format> von `Screw[]`-Objekten beinhalten, um alles schön zusammenzuhalten.

Um einmal ganz kurz das Thema der <format color="%LinkColor%">[Vererbung](14-java-oop.md#inheritance)</format> vorwegzunehmen, könnte es in einem anderen Szenario notwendig sein, eine Anwendung zu entwickeln, die Lebewesen voneinander unterscheidet. Hier könnte man eine Klassenhierarchie aufbauen, in der `Animal` und `Human` von einer übergeordneten Klasse `Creature` erben, während `Dog` von `Animal` abstammt. In einer anderen, weniger komplexen Anwendung, die sich ausschließlich mit Menschen befasst, könnte man es einfach bei einer `Human`-Klasse belassen, ohne tiefer in die Stammesgeschichte abzutauchen.

Kurz gesagt: Die Komplexität und Struktur der Klassen hängt ganz von den Bedürfnissen und Anforderungen eurer Anwendung ab. Braucht ihr eine einfache Lösung, reichen vielleicht ein paar grundlegende Objekte. Wird es komplizierter, könnt ihr eine detailliertere Klassenhierarchie aufbauen und eure <format color="%LinkColor%">[Referenztypen](02-java-data-types.md)</format> nach Herzenslust schachteln. Es ist ein bisschen wie beim Kochen: Manchmal reicht ein Sandwich und manchmal wird es ein Fünf-Gänge-Menü – es kommt ganz darauf an, was ihr auf den Tisch bringen wollt.

> Aber Vorsicht, meine Freunde der Vererbung! So faszinierend es auch ist, Klassenhierarchien zu bauen, denkt daran, dass zu viel des Guten schnell ins Chaos führen kann.
{style="note" title="Tiefe Vererbungshierarchien"}