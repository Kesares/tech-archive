# 13 Java – Enumerationen

<p>Enumerationen sind spezielle <format color="%LinkColor%"><a href="10-java-classes.md">Klassen</a></format>, welche
mit dem <format color="%LinkColor%"><a href="01-java-token.md#keywords">Keyword</a></format> <code>enum</code> gebildet
werden. Sie repräsentieren eine Ansammlung von
<format color="%LinkColor%"><a href="10-java-classes.md#constants">Konstanten</a></format> – also unveränderliche
Variablen. Jedes Element darf nur einmal vorkommen. Enumerationen werden meistens wie
<tooltip term="Top-Level-Class"><format color="%GlossaryLinkColor%">Top-Level-Klassen</format></tooltip> in eigenen
Dateien geschrieben, können aber auch direkt in einer Klasse definiert werden.</p>

<code-block lang="java">
    public enum Direction {
        NORTH,
        SOUTH,
        EAST,
        WEST
    }
</code-block>

<p>Die Werte innerhalb von Enumerationen sind statisch. Sie werden also über den Klassennamen angesprochen.</p>

<code-block lang="java">
    Direction.NORTH
</code-block>

## Erweiterte Enumerationen {id="advanced-enumerations"}

<p>Auch Enumerationen können
<format color="%LinkColor%"><a href="10-java-classes.md#constructors">Konstruktoren</a></format> haben. Diese Art von
Enumerationen werden auch Advanced Enumerations genannt.</p>

<code-block lang="java">
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
</code-block>

## Methoden {id="methods"}

<p>Jede <format color="%LinkColor%"><a href="10-java-classes.md">Klasse</a></format> erbt intern bekanntlich von der
Klasse <code>Object</code>. Jede Enumeration erbt von der Klasse <code>Enum</code>, welche wiederum von der Klasse
<code>Object</code> erbt. Somit können auch hier
<format color="%LinkColor%"><a href="09-java-methods.md">Methoden</a></format> wie die <code>toString()</code>-Methode
überschrieben werden. Die <code>toString()</code>-Methode ruft die <code>name()</code>-Methode auf. Diese kann nicht
überschrieben werden.</p>

<p>Die Methode <code>values()</code> ist statisch und liefert alle Elemente einer Enumeration als
<format color="%LinkColor%"><a href="08-java-arrays.md">Array</a></format>. Diese können dann in einer
<format color="%LinkColor%"><a href="07-java-loops.md">Schleife</a></format> durchlaufen werden.</p>

<code-block lang="java">
    public static void main(String[] args) {
        for (Element element : Element.values()) {
            System.out.println(element);
        }
    }
</code-block>

<p>Die <format color="%LinkColor%"><a href="09-java-methods.md">Methode</a></format> <code>ordinal()</code> gibt die
Ordinalzahl (Ordnungszahl) des jeweiligen Elements zurück. Die Position des Elements entspricht der Ordnungszahl
beginnend bei <code>0</code>. Die <code>compareTo()</code>-Methode vergleicht Aufzählungswerte über die Differenz der
Ordinalzahlen.</p>

<p>Die <code>valueOf()</code>-Methode gibt den
<format color="%LinkColor%"><a href="02-java-data-types.md">Datentyp</a></format> der spezifischen
<code>Enum</code>-Konstante über den jeweiligen Namen zurück. Der
<format color="%LinkColor%"><a href="05-java-strings.md">String</a></format> muss genau mit dem
<format color="%LinkColor%"><a href="01-java-token.md#identifier">Identifier</a></format> der
<format color="%LinkColor%"><a href="10-java-classes.md#constants">Konstanten</a></format> übereinstimmen, der während
der Deklarierung dieser Enumerationskonstante an sie vergeben wurde.</p>

<code-block lang="java">
    public static void main(String[] args) {
        Element element = Element.valueOf("GOLD");
    }
</code-block>

## Methodenüberschreibung bei Enumerationen {id="method-overriding-with-enums"}

<p>Jede <code>Enum</code>- <format color="%LinkColor%"><a href="10-java-classes.md#constants">Konstante</a></format> ist
eine <format color="%LinkColor%"><a href="11-java-objects.md">Instanz</a></format> der <code>Enum</code>-
<format color="%LinkColor%"><a href="10-java-classes.md">Klasse</a></format>. Diese Konstanten bieten die Möglichkeit,
neben den gemeinsamen Methoden, die alle Konstanten verwenden können, auch
<format color="%LinkColor%"><a href="09-java-methods.md">Methoden</a></format> zu überschreiben oder spezifische
Implementierungen hinzuzufügen.</p>

<code-block lang="java">
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
</code-block>