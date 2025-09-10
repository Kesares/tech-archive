# 12 Java – Modifizierer und Zugriffsrechte

<p>In Java sind Modifizierer (eng. modifiers)
<format color="%LinkColor%"><a href="01-java-token.md#keywords">Schlüsselwörter</a></format>, welche Eigenschaften von
<format color="%LinkColor%"><a href="10-java-classes.md">Klassen</a></format>,
<format color="%LinkColor%"><a href="09-java-methods.md">Methoden</a></format>,
<format color="%LinkColor%"><a href="03-java-variables.md">Variablen</a></format> und anderen Elementen verändern. Sie
beeinflussen den Zugriff, das Verhalten und die Lebensdauer dieser Elemente. Es kann zwischen 6 Kategorien von
Modifizierern unterschieden werden.</p>

<list>
  <li>
    <p><format color="%c1%"><a href="#access-modifier">Zugriffsmodifizierer</a></format></p>
  </li>
  <li>
    <p><format color="%c2%"><a href="#class-modifier">Klassenmodifizierer</a></format></p>
  </li>
  <li>
    <p><format color="%c3%"><a href="#field-modifier">Feldmodifizierer</a></format></p>
  </li>
  <li>
    <p><format color="%c4%"><a href="#method-modifier">Methodenmodifizierer</a></format></p>
  </li>
  <li>
    <p><format color="%c5%"><a href="#interface-modifier">Interface-Modifizierer</a></format></p>
  </li>
  <li>
    <p><format color="%c6%"><a href="#constructor-modifier">Konstruktormodifizierer</a></format></p>
  </li>
</list>

## <format color="%c1%">Zugriffsmodifizierer</format> {id="access-modifier"}

<p>Ob auf <format color="%LinkColor%"><a href="10-java-classes.md">Klassen</a></format>,
<format color="%LinkColor%"><a href="14-java-oop.md#interfaces">Schnittstellen</a></format>,
<format color="%LinkColor%"><a href="09-java-methods.md">Methoden</a></format> etc. zugegriffen werden kann, wird über
die <format color="%Highlight%">Access Modifier</format> gesteuert. Sie können auf fast allen Konstrukten wie Klassen,
Interfaces, <format color="%LinkColor%"><a href="03-java-variables.md">Variablen</a></format> (außer lokale und
Parametervariablen) etc. angewendet werden. Die folgenden vier Access Modifier werden verwendet.</p>

<list>
  <li><code>public</code></li>
  <li><code>private</code></li>
  <li><code>protected</code></li>
  <li><p>package-private</p></li>
</list>

<note title="package-private">
    <p>Wird kein <format color="%NoteHighlight%">Access Modifier</format> angegeben, wird intern standardmäßig der
    <format color="%NoteHighlight%">package-private</format> Modifier angewendet. Dieser kann nicht manuell vom
    Entwickler vergeben werden.</p>
</note>

<tip>
    <p>Es wird empfohlen die <format color="%Highlight%">Access Modifier</format> immer explizit anzugeben</p>
</tip>

## <format color="%c2%">Klassenmodifizierer</format> {id="class-modifier"}

<p>Klassen können die folgenden Modifier verwenden.</p>

<list>
  <li><format color="%c1%"><a href="#access-modifier">Access Modifier</a></format></li>
  <li><code>abstract</code></li>
  <li><code>sealed</code> (Seit Java 17)</li>
  <li><code>non-sealed</code> (Seit Java 17)</li>
  <li><code>permits</code> (Seit Java 17)</li>
  <li><code>final</code></li>
  <li><code>strictfp</code> (Seit Java 17 redundant)</li>
  <li><code>static</code></li>
</list>

## <format color="%c3%">Feldmodifizierer</format> {id="field-modifier"}

<p><format color="%LinkColor%"><a href="10-java-classes.md#class-variables">Klassen-</a></format> und
<format color="%LinkColor%"><a href="10-java-classes.md#object-variables">Objektvariablen</a></format> können die
folgenden Modifier verwenden.</p>

<list>
  <li><format color="%c1%"><a href="#access-modifier">Access Modifier</a></format></li>
  <li><code>static</code></li>
  <li><code>final</code></li>
  <li><code>transient</code></li>
  <li><code>volatile</code></li>
</list>

## <format color="%c4%">Methodenmodifizierer</format> {id="method-modifier"}

<p><format color="%LinkColor%"><a href="09-java-methods.md">Methoden</a></format> können die folgenden Modifier
verwenden.</p>

<list>
  <li><format color="%c1%"><a href="#access-modifier">Access Modifier</a></format></li>
  <li><code>abstract</code></li>
  <li><code>static</code></li>
  <li><code>final</code></li>
  <li><code>native</code></li>
  <li><code>strictfp</code> (Seit Java 17 redundant)</li>
  <li><code>synchronized</code></li>
</list>

## <format color="%c5%">Interface-Modifizierer</format> {id="interface-modifier"}

<p><format color="%LinkColor%"><a href="14-java-oop.md#interfaces">Interfaces</a></format> können die folgenden
Modifier verwenden.</p>

<list>
  <li><format color="%c1%"><a href="#access-modifier">Access Modifier</a></format></li>
  <li><code>abstract</code> (Explizite Angabe ist redundant, da Methoden intern abstrakt sind und kann daher weggelassen
    werden.)</li>
  <li><code>strictfp</code> (Seit Java 17 redundant)</li>
  <li><code>static</code></li>
  <li><code>sealed</code> (Seit Java 17)</li>
  <li><code>non-sealed</code> (Seit Java 17)</li>
</list>

## <format color="%c6%">Konstruktormodifizierer</format> {id="constructor-modifier"}

<p>Mit Ausnahme der <format color="%c1%"><a href="#access-modifier">Access Modifier</a></format> verwenden Konstruktoren
keine zusätzlichen Modifier.</p>

## Modifier {id="modifier"}

<p>Folgende Tabelle wurde bereits in
<format color="%LinkColor%"><a href="01-java-token.md#modifier">Kapitel 1 – Token: Modifier</a></format> gezeigt.</p>

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
                <li>Enthält eine Klasse mindestens eine abstrakte Methode, muss auch diese Klasse den Modifier tragen.
                </li>
                <li>Eine <format color="%LinkColor%"><a href="14-java-oop.md#abstract-classes">abstrakte Klasse</a>
                </format> kann nicht instanziiert werden.</li>
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
                <li>Von Klassen kann nicht
                <format color="%LinkColor%"><a href="14-java-oop.md#inheritance">geerbt</a></format> werden.</li>
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
                <li>Gibt an, dass eine Methode in nativem Code mithilfe von
                <tooltip term="JNI"><format color="%GlossaryLinkColor%">JNI</format></tooltip> implementiert ist. Die
                in C oder C++ implementierten Methoden werden native Methoden oder fremde Methoden genannt.
                <code>native</code> gibt an, dass eine Methode in plattformabhängigem Code implementiert ist, der häufig
                in diesen Sprachen vorkommt.</li>
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
                <li>Wird automatisch intern angewendet, wenn kein anderer
                <format color="%LinkColor%"><a href="#access-modifier">Access Modifier</a></format> zugewiesen wird.
                Eine Ausnahme sind Konstruktoren in
                <format color="%LinkColor%"><a href="13-java-enumerations.md">Enumerationen</a></format>. Dort ist es
                standardmäßig <code>private</code>.</li>
                <li>Kann nicht von Entwicklern gesetzt werden.</li>
                <li>Konstrukte mit diesem Modifier sind nur innerhalb desselben
                <format color="%LinkColor%"><a href="16-java-packages-and-imports.md">Package</a></format> sichtbar.
                </li>
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
                <li>Zugriff von allem innerhalb desselben
                <format color="%LinkColor%"><a href="16-java-packages-and-imports.md">Package</a></format>.</li>
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
                <li>Sicherstellung, dass Fließkommaoperationen auf allen Plattformen gleich berechnet werden und nicht
                von der Art des Prozessors oder der Implementierung der
                <tooltip term="JVM"><format color="%GlossaryLinkColor%">JVM</format></tooltip> abhängen.</li>
                <li>Klassen oder Methoden mit diesem
                <format color="%LinkColor%"><a href="01-java-token.md#keywords">Keyword</a></format> führen alle
                Operationen in Übereinstimmung mit dem
                <tooltip term="JVM"><format color="%GlossaryLinkColor%">IEEE 754</format></tooltip> Standard durch.</li>
                <li>Ab Java 17 werden alle Operationen standardmäßig mit
                <tooltip term="JVM"><format color="%GlossaryLinkColor%">IEEE 754</format></tooltip> durchgeführt.
                <code>strictfp</code> ist daher redundant geworden. In speziellen Umgebungen oder in älteren
                Java-Versionen hat das
                <format color="%LinkColor%"><a href="01-java-token.md#keywords">Keyword</a></format> möglicherweise noch
                Relevanz.</li>
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
                <li>Auf Methoden kann immer nur von einem
                <format color="%LinkColor%"><a href="27-java-multithreading.md">Thread</a></format> zugegriffen werden.
                </li>
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
                <li>Variablen eines <format color="%LinkColor%"><a href="11-java-objects.md">Objekts</a></format> werden
                bei der <tooltip term="Serialization"><format color="%GlossaryLinkColor%">Serialisierung</format>
                </tooltip> nicht berücksichtigt.</li>
                <li>Methoden eines <format color="%LinkColor%"><a href="11-java-objects.md">Objekts</a></format> werden
                bei der <tooltip term="Serialization"><format color="%GlossaryLinkColor%">Serialisierung</format>
                </tooltip> nicht berücksichtigt.</li>
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
                <li>Alle <format color="%LinkColor%"><a href="27-java-multithreading.md">Threads</a></format> lesen und
                schreiben den Wert der Variablen direkt aus dem Hauptspeicher, anstatt eine Kopie im
                <tooltip term="Cache"><format color="%GlossaryLinkColor%">Cache</format></tooltip> zu verwenden. Damit
                wird sichergestellt, dass die Threads den aktuellen Wert sehen und inkonsistente oder falsche Ergebnisse
                verhindert werden.</li>
            </list>
        </td>
    </tr>
</table>

<tip title="Serialisierbarkeit">
    <p>Die Serialisierbarkeit eines Objekts ist gegeben, wenn es in ein Format konvertiert werden kann, das eine
    Übertragung oder Speicherung des Objekts ermöglicht.</p>
</tip>

## <code>sealed</coce>, <code>non-sealed</code> und <code>permits</code> {id="sealed-non-sealed-and-permits"}

<p>Seit Java 17 gibt es die Modifier <code>sealed</code>, <code>non-sealed</code> und <code>permits</code>. Obwohl auch
diese häufig als <format color="%LinkColor%"><a href="01-java-token.md#keywords">Keywords</a></format> bezeichnet
werden, ist es zumindest bei <code>sealed</code> und <code>permits</code> möglich, diese als
<format color="%LinkColor%"><a href="01-java-token.md#identifier">Identifier</a></format> zu nutzen. Da
<code>non-sealed</code> einen <format color="%LinkColor%"><a href="01-java-token.md#operators">Operator</a></format>
 enthält, funktioniert dies nicht bei diesem Modifier.</p>

<tip>
    <p><code>non-sealed</code> ist das einzige
    <format color="%LinkColor%"><a href="01-java-token.md#keywords">Keyword</a></format>, welches einen
    <format color="%LinkColor%"><a href="01-java-token.md#operators">Operator</a></format> besitzt.</p>
</tip>

<p>Die Keywords dienen dazu <format color="%LinkColor%"><a href="10-java-classes.md">Klassen</a></format> und
<format color="%LinkColor%"><a href="14-java-oop.md#interfaces">Interfaces</a></format> zu versiegeln und somit die
Erweiterbarkeit (<format color="%LinkColor%"><a href="14-java-oop.md#inheritance">Vererbung</a></format>) einer
Klassenhierarchie einzuschränken. Mehr dazu in
<format color="%LinkColor%"><a href="14-java-oop.md#sealed-classes-and-interfaces">Kapitel 14 – OOP: Versiegelte Klassen
und Interfaces</a></format>.</p>