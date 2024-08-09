# 10 Java Klassen

Klassen sind ein wesentlicher Bestandteil der <format color="%LinkColor%">[OOP – Objektorientierten Programmierung](14-java-oop.md)</format>. Sie sind vergleichbar mit Rezepten oder Blueprints und stellen die grundsätzliche Struktur und den Aufbau von konkret instanziierten <format color="%LinkColor%">[Objekten](11-java-objects.md)</format> dar – deren Eigenschaften (<format color="%LinkColor%">[Objektvariablen](#object-variables)</format>) und Funktionalitäten (<format color="%LinkColor%">[Objektmethoden](#object-methods)</format>).

Alle <format color="%LinkColor%">[Variablen](03-java-variables.md)</format> und <format color="%LinkColor%">[Methoden](09-java-methods.md)</format>, die in Java deklariert werden, sind von solch einer <format color="%LinkColor%">[Klassendefinition](#class-structure)</format> ummantelt – unabhängig davon, ob sie zu einem <format color="%LinkColor%">[Objekt](11-java-objects.md)</format> gehören oder nicht. Der Name der Datei muss zudem genauso heißen, wie der Name der Klasse, die sich innerhalb der Datei befindet.

## Klassenaufbau {id="class-structure"}

Der Aufbau einer Klasse ist nicht in Stein gemeißelt. Er kann sich von Unternehmen zu Unternehmen unterscheiden. Eine weit verbreitete Anordnung sieht folgendermaßen aus.

```Console
public class ClassName {

    // Konstanten und statische bzw. Klassenvariablen

    // Instanz- bzw. Objektvariablen

    // Konstruktoren

    // Statische bzw. Klassenmethoden

    // Instanz- bzw. Objektmethoden

    // Getter & Setter

    // Innere Klassen
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
## Das Keyword `this` {id="the-keyword-this"}
## Klassenmethoden {id="class-methods"}
## Objektmethoden {id="object-methods"}
## Setter- & Getter-Methoden {id="setter-and-getter"}
## Klasseninitialisierer {id="class-initializer"}
## Innere Klassen {id="inner-classes"}
## Lokale Klassen {id="local-classes"}
## Anonyme Klassen {id="anonymous-classes"}
## Coding Conventions {id="coding-conventions"}