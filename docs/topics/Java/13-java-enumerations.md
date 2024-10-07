# 13 Java – Enumerationen

Enumerationen sind spezielle <format color="%LinkColor%">[Klassen](10-java-classes.md)</format>, welche mit dem <format color="%LinkColor%">[Keyword](01-java-token.md#keywords)</format> `enum` gebildet werden. Sie repräsentieren eine Ansammlung von <format color="%LinkColor%">[Konstanten](10-java-classes.md#constants)</format> – also unveränderliche Variablen. Jedes Element darf nur einmal vorkommen. Enumerationen werden meistens wie <tooltip term="Top-Level-Class"><format color="%GlossaryLinkColor%">Top-Level-Klassen</format></tooltip> in eigenen Dateien geschrieben, können aber auch direkt in einer Klasse definiert werden.

<code-block lang="java">
public enum Direction {
    NORTH,
    SOUTH
    EAST,
    WEST
}
</code-block>

Die Werte innerhalb von Enumerationen sind statisch. Sie werden also über den Klassennamen angesprochen.

<code-block lang="java">
    Direction.NORTH
</code-block>

## Erweiterte Enumerationen {id="advanced-enumerations"}

Auch Enumerationen können <format color="%LinkColor%">[Konstruktoren](10-java-classes.md#constructors)</format> haben. Diese Art von Enumerationen werden auch Advanced Enumerations genannt.

```Java
public enum Element {

    GOLD("Au"),
    IRON("Fe"),
    TITANIUM("Ti");

    private final String symbol;

    public Element(String symbol) {
        this.symbol = symbol;
    }

    public String getSymbol() {
        return this.symbol;
    }
}
```

## Methoden

Jede <format color="%LinkColor%">[Klasse](10-java-classes.md)</format> erbt intern bekanntlich von der Klasse `Object`. Jede Enumeration erbt von der Klasse `Enum`, welche wiederum von der Klasse `Object` erbt. Somit können auch hier <format color="%LinkColor%">[Methoden](09-java-methods.md)</format> wie die `toString()`-Methode überschrieben werden. Die `toString()`-Methode ruft die `name()`-Methode auf. Diese kann nicht überschrieben werden.

Die Methode `values()` ist statisch und liefert alle Elemente einer Enumeration als <format color="%LinkColor%">[Array](08-java-arrays.md)</format>. Diese können dann in einer <format color="%LinkColor%">[Schleife](07-java-loops.md)</format> durchlaufen werden.

```Java
public static void main(String[] args) {
    for (Element element : Element.values()) {
        System.out.println(element);
    }
}
```

Die <format color="%LinkColor%">[Methode](09-java-methods.md)</format> `ordinal()` gibt die Ordinalzahl (Ordnungszahl) des jeweiligen Elements zurück. Die Position des Elements entspricht der Ordnungszahl beginnend bei `0`. Die `compareTo()`-Methode vergleicht Aufzählungswerte über die Differenz der Ordinalzahlen.

Die `valueOf()`-Methode gibt den <format color="%LinkColor%">[Datentyp](02-java-data-types.md)</format> der spezifischen `Enum`-Konstante über den jeweiligen Namen zurück. Der <format color="%LinkColor%">[String](05-java-strings.md)</format> muss genau mit dem <format color="%LinkColor%">[Identifier](01-java-token.md#identifier)</format> der <format color="%LinkColor%">[Konstanten](10-java-classes.md#constants)</format> übereinstimmen, der während der Deklarierung dieser Enumerationskonstante an sie vergeben wurde.

```Java
public static void main(String[] args) {
    Element element = Element.valueOf("GOLD");
}
```

## Methodenüberschreibung bei Enumerationen {id="method-overriding-with-enums"}

Jede `Enum`-<format color="%LinkColor%">[Konstante](10-java-classes.md#constants)</format> ist eine <format color="%LinkColor%">[Instanz](11-java-objects.md)</format> der `Enum`-<format color="%LinkColor%">[Klasse](10-java-classes.md)</format>. Diese Konstanten bieten die Möglichkeit, neben den gemeinsamen Methoden, die alle Konstanten verwenden können, auch <format color="%LinkColor%">[Methoden](09-java-methods.md)</format> zu überschreiben oder spezifische Implementierungen hinzuzufügen.

```Java
public enum Operation {

    ADDITION {
        @Override
        public double apply(double x, double y) {
            return x + y;
        }
    },
    
    SUBTRACTION {
        @Override
        public double apply(double x, double y) {
            return x - y;
        }
    };

    public abstract double apply(double x, double y);
}
```