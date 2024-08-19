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

Jede <format color="%LinkColor%">[Klasse](10-java-classes.md)</format> erbt intern bekanntlich von der Klasse `Object`. Jede Enumeration, die erstellt wird, erbt von der Klasse `Enum`, welche wiederum von der Klasse `Object` erbt. Somit können auch hier <format color="%LinkColor%">[Methoden](09-java-methods.md)</format> wie die `toString()`-Methode überschrieben werden. Die `toString()`-Methode ruft die `name()`-Methode auf. Diese kann nicht überschrieben werden.

Die Methode `values()` ist statisch und liefert alle Elemente einer Enumeration als <format color="%LinkColor%">[Array](08-java-arrays.md)</format>. Diese können dann in einer <format color="%LinkColor%">[Schleife](07-java-loops.md)</format> durchlaufen werden.

```Java
public static void main(String[] args) {
    for (Element element : Element.values()) {
        System.out.println(element);
    }
}
```

Die Methode `ordinal()` gibt die Ordinalzahl (Ordnungszahl) des jeweiligen Elements zurück. Die Position des Elements entspricht der Ordnungszahl beginnend bei `0`. Die `compareTo()`-Methode vergleicht Aufzählungswerte über die Differenz der Ordinalzahlen.