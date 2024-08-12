# 12 Java Modifizierer und Zugriffsrechte

In Java sind Modifizierer (engl. modifiers) <format color="%LinkColor%">[Schlüsselwörter](01-java-token.md#keywords)</format>, die die Eigenschaften von <format color="%LinkColor%">[Klassen](10-java-classes.md)</format>, <format color="%LinkColor%">[Methoden](09-java-methods.md)</format>, <format color="%LinkColor%">[Variablen](03-java-variables.md)</format> und anderen Elementen ändern. Sie beeinflussen den Zugriff, das Verhalten und die Lebensdauer dieser Elemente. Es kann zwischen 6 Kategorien von Modifizieren unterschieden werden.

- <format color="%c1%">[Zugriffsmodifizierer](#access-modifier)</format>
- <format color="%c2%">Klassenmodifizierer</format>
- <format color="%c3%">Feldmodifizierer</format>
- <format color="%c4%">Methodenmodifizierer</format>
- <format color="%c5%">Interface-Modifizierer</format>
- <format color="%c6%">Konstruktormodifizierer</format>

## Zugriffsmodifizierer {id="access-modifier"}

Ob auf <format color="%LinkColor%">[Klassen](10-java-classes.md)</format>, <format color="%LinkColor%">[Schnittstellen](14-java-oop.md#interfaces)</format>, <format color="%LinkColor%">[Methoden](09-java-methods.md)</format> etc. zugegriffen werden kann, wird über die <format color="%Highlight%">Access Modifier</format> gesteuert. Sie können auf fast allen Konstrukten wie Klassen, Interfaces, <format color="%LinkColor%">[Variablen](03-java-variables.md)</format> etc. angewendet werden. Die folgenden vier Access Modifier werden verwendet.

- `public`
- `private`
- `protected`
- `package-private`

> Wird kein <format color="%NoteHighlight%">Access Modifier</format> angegeben, wird intern standardmäßig der `package-private` Modifier angewendet. Dieser kann nicht manuell vom Entwickler vergeben werden.
> {style="note" title="package-private"}

> Es wird empfohlen die <format color="%Highlight%">Access Modifier</format> immer explizit anzugeben.

## Klassenmodifizierer {id="class-modifier"}

Klassen können die folgenden Modifier verwenden.

- <format color="%c1%">[Access Modifier](#access-modifier)</format>
- `abstract`
- `sealed` (Seit Java 17)
- `non-sealed` (Seit Java 17)
- `permits` (Seit Java 17)
- `final`
- `strictfp` (Seit Java 17 redundant)
- `static`

## Feldmodifizierer {id="field-modifier"}

<format color="%LinkColor%">[Klassen-](10-java-classes.md#class-variables)</format> und <format color="%LinkColor%">[Objektvariablen](10-java-classes.md#object-variables)</format> können die folgenden Modifier verwenden.

- <format color="%c1%">[Access Modifier](#access-modifier)</format>
- `static`
- `final`
- `transient`
- `volatile`

## Methodenmodifizierer {id="method-modifier"}

<format color="%LinkColor%">[Methoden](09-java-methods.md)</format> können die folgenden Modifier verwenden.

- <format color="%c1%">[Access Modifier](#access-modifier)</format>
- `abstract`
- `static`
- `final`
- `native`
- `strictfp` (Seit Java 17 redundant)
- `synchronized`

## Interface-Modifizierer {id="interface-modifier"}

<format color="%LinkColor%">[Interfaces](14-java-oop.md#interfaces)</format> können die folgenden Modifier verwenden.

- <format color="%c1%">[Access Modifier](#access-modifier)</format>
- `abstract` (Explizite Angabe redundant, da Methoden intern abstrakt sind)
- `strictfp` (Seit Java 17 redundant)
- `static`
- `sealed` (Seit Java 17)
- `non-sealed` (Seit Java 17)

## Konstruktormodifizierer {id="constructor-modifier"}

Mit Ausnahme der <format color="%c1%">[Access Modifier](#access-modifier)</format> verwenden Konstruktoren keine zusätzlichen Modifier.

## Modifier {id="modifier"}

Folgende Tabelle wurde bereits in <format color="%LinkColor%">[Kapitel 1 – Token: Modifier](01-java-token.md#modifier)</format> gezeigt.

<table>
    <tr>
        <td>Keyword</td>
        <td>Anwendungsbereich</td>
        <td>Beschreibung</td>
    </tr>
    <tr>
        <td><code>abstract</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="09-java-methods.md">Methoden</a></format></p>
            <p><format color="%LinkColor%"><a href="10-java-classes.md">Klassen</a></format></p>
        </td>
        <td>
            <list>
                <li>Enthält eine Klasse mindestens eine abstrakte Methode, muss auch diese Klasse den Modifier tragen.</li>
                <li>Eine <format color="%LinkColor%"><a href="14-java-oop.md#abstract-classes">abstrakte Klasse</a></format> kann nicht instanziiert werden.</li>
                <li>Abstrakte Methoden besitzen keinen Rumpf und müssen von Kindklassen implementiert werden.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>final</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="03-java-variables.md">Variablen</a></format></p>
            <p><format color="%LinkColor%"><a href="10-java-classes.md#constants">Konstanten</a></format></p>
            <p><format color="%LinkColor%"><a href="09-java-methods.md">Methoden</a></format></p>
            <p><format color="%LinkColor%"><a href="10-java-classes.md">Klassen</a></format></p>
        </td>
        <td>
            <list>
                <li>Variablen können nicht überschrieben werden.</li>
                <li>Konstanten können nicht überschrieben werden.</li>
                <li>Methoden können nicht überschrieben werden.</li>
                <li>Von Klassen kann nicht geerbt werden.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>native</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="09-java-methods.md">Methoden</a></format></p>
        </td>
        <td>
            <list>
                <li>Gibt an, dass eine Methode in nativem Code mithilfe von <tooltip term="JNI"><format color="%GlossaryLinkColor%">JNI</format></tooltip> implementiert ist. Die in C oder C++ implementierten Methoden werden native Methoden oder fremde Methoden genannt. <code>native</code> gibt an, dass eine Methode in plattformabhängigem Code implementiert ist, der häufig in diesen Sprachen vorkommt.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>package-private</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="03-java-variables.md">Variablen</a></format></p>
            <p><format color="%LinkColor%"><a href="10-java-classes.md#constants">Konstanten</a></format></p>
            <p><format color="%LinkColor%"><a href="09-java-methods.md">Methoden</a></format></p>
            <p><format color="%LinkColor%"><a href="10-java-classes.md">Klassen</a></format></p>
            <p><format color="%LinkColor%"><a href="10-java-classes.md#constructors">Konstruktoren</a></format></p>
        </td>
        <td>
            <list>
                <li>Wird automatisch intern angewendet, wenn kein anderer <format color="%LinkColor%"><a href="#access-modifier">Access Modifier</a></format> zugewiesen wird. Eine Ausnahme sind Konstruktoren in <format color="%LinkColor%"><a href="13-java-enumerations.md">Enumerationen</a></format>. Dort ist es standardmäßig <code>private</code>.</li>
                <li>Kann nicht von Entwicklern gesetzt werden.</li>
                <li>Konstrukte mit diesem Modifier sind nur innerhalb desselben <format color="%LinkColor%"><a href="16-java-packages-and-imports.md">Package</a></format> sichtbar.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>private</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="03-java-variables.md">Variablen</a></format></p>
            <p><format color="%LinkColor%"><a href="10-java-classes.md#constants">Konstanten</a></format></p>
            <p><format color="%LinkColor%"><a href="09-java-methods.md">Methoden</a></format></p>
            <p><format color="%LinkColor%"><a href="10-java-classes.md#inner-classes">Innere Klassen</a></format></p>
            <p><format color="%LinkColor%"><a href="10-java-classes.md#constructors">Konstruktoren</a></format></p>
        </td>
        <td>
            <list>
                <li>Zugriff nur innerhalb der Klasse.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>protected</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="03-java-variables.md">Variablen</a></format></p>
            <p><format color="%LinkColor%"><a href="10-java-classes.md#constants">Konstanten</a></format></p>
            <p><format color="%LinkColor%"><a href="09-java-methods.md">Methoden</a></format></p>
            <p><format color="%LinkColor%"><a href="10-java-classes.md#inner-classes">Innere Klassen</a></format></p>
            <p><format color="%LinkColor%"><a href="10-java-classes.md#constructors">Konstruktoren</a></format></p>
        </td>
        <td>
            <list>
                <li>Zugriff von Kindklassen</li>
                <li>Zugriff von allem innerhalb desselben <format color="%LinkColor%"><a href="16-java-packages-and-imports.md">Package</a></format>.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>public</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="03-java-variables.md">Variablen</a></format></p>
            <p><format color="%LinkColor%"><a href="10-java-classes.md#constants">Konstanten</a></format></p>
            <p><format color="%LinkColor%"><a href="09-java-methods.md">Methoden</a></format></p>
            <p><format color="%LinkColor%"><a href="10-java-classes.md">Klassen</a></format></p>
            <p><format color="%LinkColor%"><a href="10-java-classes.md#constructors">Konstruktoren</a></format></p>
        </td>
        <td>
            <list>
                <li>Zugriff von überall.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>static</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="03-java-variables.md">Variablen</a></format></p>
            <p><format color="%LinkColor%"><a href="10-java-classes.md#constants">Konstanten</a></format></p>
            <p><format color="%LinkColor%"><a href="09-java-methods.md">Methoden</a></format></p>
            <p><format color="%LinkColor%"><a href="10-java-classes.md#inner-classes">Innere Klassen</a></format></p>
        </td>
        <td>
            <list>
                <li>Objektunabhängiger Zugriff.</li>
                <li>Zugriff über den Klassennamen.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>strictfp</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="09-java-methods.md">Methoden</a></format></p>
            <p><format color="%LinkColor%"><a href="10-java-classes.md">Klassen</a></format></p>
        </td>
        <td>
            <list>
                <li>Sicherstellung, dass Fließkommaoperationen auf allen Plattformen gleich berechnet werden und nicht von der Art des Prozessors oder der Implementierung der <tooltip term="JVM"><format color="%GlossaryLinkColor%">JVM</format></tooltip> abhängen.</li>
                <li>Klassen oder Methoden mit diesem <format color="%LinkColor%"><a href="01-java-token.md#keywords">Keyword</a></format> führen alle Operationen in Übereinstimmung mit dem <tooltip term="JVM"><format color="%GlossaryLinkColor%">IEEE 754</format></tooltip> Standard durch.</li>
                <li>Ab Java 17 werden alle Operationen standardmäßig mit <tooltip term="JVM"><format color="%GlossaryLinkColor%">IEEE 754</format></tooltip> durchgeführt. <code>strictfp</code> ist daher redundant geworden. In speziellen Umgebungen oder in älteren Java-Versionen hat das <format color="%LinkColor%"><a href="01-java-token.md#keywords">Keyword</a></format> möglicherweise noch Relevanz.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>synchronized</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="09-java-methods.md">Methoden</a></format></p>
        </td>
        <td>
            <list>
                <li>Auf Methoden kann immer nur von einem <format color="%LinkColor%"><a href="java-threads.md">Thread</a></format> zugegriffen werden.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>transient</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="03-java-variables.md">Variablen</a></format></p>
            <p><format color="%LinkColor%"><a href="09-java-methods.md">Methoden</a></format></p>
        </td>
        <td>
            <list>
                <li>Variablen eines <format color="%LinkColor%"><a href="11-java-objects.md">Objekts</a></format> werden bei der <tooltip term="Serialization"><format color="%GlossaryLinkColor%">Serialisierung</format></tooltip> nicht berücksichtigt.</li>
                <li>Methoden eines <format color="%LinkColor%"><a href="11-java-objects.md">Objekts</a></format> werden bei der <tooltip term="Serialization"><format color="%GlossaryLinkColor%">Serialisierung</format></tooltip> nicht berücksichtigt.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>volatile</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="03-java-variables.md">Variablen</a></format></p>
            <p><format color="%LinkColor%"><a href="10-java-classes.md#constants">Konstanten</a></format></p>
        </td>
        <td>
            <list>
                <li>Alle <format color="%LinkColor%"><a href="java-threads.md">Threads</a></format> lesen und schreiben den Wert der Variablen direkt aus dem Hauptspeicher, anstatt eine Kopie im <tooltip term="Cache"><format color="%GlossaryLinkColor%">Cache</format></tooltip> zu verwenden. Damit wird sichergestellt, dass die Threads den aktuellen Wert sehen und inkonsistente oder falsche Ergebnisse verhindert werden.</li>
            </list>
        </td>
    </tr>
</table>

> Die Serialisierbarkeit eines Objekts ist gegeben, wenn es in ein Format konvertiert werden kann, das eine Übertragung oder Speicherung des Objekts ermöglicht.
{title="Serialisierbarkeit"}

## `sealed`, `non-sealed` & `permits` {id="sealed-non-sealed-and-permits"}

Seit Java 17 gibt es die Modifier `sealed`, `non-sealed` und `permits`. Obwohl auch diese häufig als <format color="%LinkColor%">[Keywords](01-java-token.md#keywords)</format> bezeichnet werden, ist es zumindest bei `sealed` und `permits` möglich, diese als <format color="%LinkColor%">[Identifier](01-java-token.md#identifier)</format> zu nutzen. Da `non-sealed` einen <format color="%LinkColor%">[Operator](01-java-token.md#operators)</format> enthält, funktioniert dies nicht bei diesem Modifier.

Die Keywords dienen dazu <format color="%LinkColor%">[Klassen](10-java-classes.md)</format> und <format color="%LinkColor%">[Interfaces](14-java-oop.md#interfaces)</format> zu versiegeln und somit die Erweiterbarkeit (<format color="%LinkColor%">[Vererbung](14-java-oop.md#inheritance)</format>) einer Klassenhierarchie einzuschränken. Mehr dazu in <format color="%LinkColor%">[Kapitel 14 – OOP: Versiegelte Klassen und Interfaces](14-java-oop.md#sealed-classes-and-interfaces)</format>.