# 01 Java – Token

Die deutsche Sprache besteht aus Sätzen, welche sich wiederum aus bestimmten Worten und Wortreihenfolgen zusammensetzen. Dies wird als Grammatik bezeichnet. Auch Java (so wie jede andere Programmiersprache) besitzt solch eine Grammatik. Diese wird als Syntax bezeichnet. Der <tooltip term="Compiler"><format color="%GlossaryLinkColor%">Compiler</format></tooltip> zerlegt diese Syntax oder auch Codezeilen in seine Bestandteile und identifiziert diese als Token. Diese Token sind die kleinsten Elemente eines Java-Programms. Unterschieden wird zwischen 6 Token-Arten.

- <format color="%c1%">[Bezeichner](#identifier)</format>
- <format color="%c2%">[Schlüsselwörter](#keywords)</format>
- <format color="%c3%">[Literale](#literals)</format>
- <format color="%c4%">[Operatoren](#operators)</format>
- <format color="%c5%">[Separatoren](#separators)</format>
- <format color="%c6%">[Kommentare](#comments)</format>

## <format color="%c1%">Bezeichner</format> {id="identifier"}
Ein Bezeichner (engl. Identifier) ist im Prinzip ein frei wählbarer Name. Dieser wird unter anderem an <format color="%LinkColor%">[Variablen](03-java-variables.md)</format>, <format color="%LinkColor%">[Methoden](09-java-methods.md)</format>, <format color="%LinkColor%">[Klassen](10-java-classes.md)</format>, etc. vergeben und zu einem späteren Zeitpunkt kann ein Konstrukt mit diesem Bezeichner angesprochen werden.

### <format color="%c1%">Namensregeln</format> {id="naming-rules"}
Java setzt strikte Regeln, welche Zeichen an welcher Stelle für Bezeichner erlaubt sind.

- <format color="%c1%">Bezeichner</format> dürfen nicht mit einer Zahl [0-9] beginnen.
- <format color="%c1%">Bezeichner</format> dürfen keine <format color="%LinkColor%">[Operatoren](#operators)</format> oder <format color="%LinkColor%">[Separatoren](#separators)</format> enthalten.
- Eine `.java`-Datei, deren Klasse und der <format color="%LinkColor%">[Konstruktor](10-java-classes.md#constructors)</format> müssen den gleichen Namen haben.

### <format color="%c1%">Namenskonventionen</format> {id="naming-conventions"}
Konventionen sind keine festen Regeln, sondern Richtlinien. Es kann zwar von ihnen abgewichen werden, es wird jedoch empfohlen, sich an sie zu halten.

- Benennung in englischer Sprache.
- Es sollten keine Schlüsselwörter und auch nicht in abgewandelter Form verwendet werden (Ausnahmen wie z.B. `class` → clazz sind dennoch möglich).
- Es sollten keine Umlaute [Ä, ä, Ö, ö, Ü, ü, ß] verwendet werden.
- Es sollten keine Dollarzeichen `$` verwendet werden.
- Es sollten keine Unterstriche `_` verwendet werden (Ausnahme: <format color="%LinkColor%">[Konstanten](10-java-classes.md#constants)</format>).
- Dollarzeichen `$` und Unterstriche `_` sollten am Anfang nur aus gutem Grund verwendet werden.
- <format color="%LinkColor%">[Variablen](03-java-variables.md)</format> und <format color="%LinkColor%">[Methoden](09-java-methods.md)</format> sollten nach der <tooltip term="CamelCase-Notation"><format color="%GlossaryLinkColor%">CamelCase-Notation</format></tooltip> benannt werden.
- <format color="%LinkColor%">[Klassen](10-java-classes.md)</format> (und damit auch <format color="%LinkColor%">[Konstruktoren](10-java-classes.md#constructors)</format> und Java-Dateien) sollten nach der <tooltip term="PascalCase-Notation"><format color="%GlossaryLinkColor%">PascalCase-Notation</format></tooltip> benannt werden.
- <format color="%LinkColor%">[Konstanten](10-java-classes.md#constants)</format> sollten nach der <tooltip term="Constants-Notation"><format color="%GlossaryLinkColor%">SCREAMING_SNAKE_CASE-Notation</format></tooltip> benannt werden.

> Weitere Konventionen werden in den jeweiligen Kapiteln beschrieben.
> {style="note"}

## <format color="%c2%">Keywords – 57</format> {id="keywords"}

Schlüsselwörter (engl. Keywords) sind reservierte Wörter, die eine spezielle Bedeutung für den <tooltip term="Compiler"><format color="%GlossaryLinkColor%">Compiler</format></tooltip> haben. Diese Wörter dürfen und können im Regelfall nicht als Namen für <format color="%LinkColor%">[Variablen](03-java-variables.md)</format>, <format color="%LinkColor%">[Methoden](09-java-methods.md)</format>, <format color="%LinkColor%">[Klassen](10-java-classes.md)</format> oder andere <format color="%c1%">[Bezeichner](#identifier)</format> verwendet werden, da sie zur Sprachsyntax von Java gehören und bestimmte Aktionen oder Strukturen definieren. Einige Ausnahmen werden im Abschnitt <format color="%c2%">[Kontextbezogene "Keywords"](#contextual-keywords)</format> beschrieben.

<table>
    <tr>
        <td width="100"><p>Keywords</p></td>
        <td width="240"><p>Anwendungsbereich</p></td>
        <td><p>Beschreibung</p></td>
    </tr>
    <tr>
        <td><code>assert</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="06-java-branches.md#assertions">Annahmen</a></format></p>
        </td>
        <td>
            <list>
                <li>Stellt Annahmen über den Zustand des Programms sicher.</li>
                <li>Müssen erst aktiviert werden, um verwendet werden zu können.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>boolean</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="03-java-variables.md">Variablen</a></format></p>
            <p><format color="%LinkColor%"><a href="10-java-classes.md#constants">Konstanten</a></format></p>
            <p><format color="%LinkColor%"><a href="09-java-methods.md#return-type">Methoden (Rückgabetyp)</a></format></p>
            <p><format color="%LinkColor%"><a href="09-java-methods.md#method-signature">Methoden (Parameter)</a></format></p>
        </td>
        <td>
            <list>
                <li><format color="%LinkColor%"><a href="02-java-data-types.md#primitive-data-types">Primitiver Datentyp</a></format></li>
                <li>Datentyp einer Variablen</li>
                <li>Datentyp einer Konstanten</li>
                <li>Rückgabetyp einer Methode</li>
                <li>Parameter einer Methode</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>break</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="07-java-loops.md">Schleifen</a></format></p>
            <p><format color="%LinkColor%"><a href="06-java-branches.md#switch-case">switch-Ausdrücke</a></format></p>
        </td>
        <td>
            <list>
                <li>Beendet die Ausführung einer Schleife.</li>
                <li>Verhindert das "Durchfallen" in einem <code>switch</code>-Ausdruck.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>byte</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="03-java-variables.md">Variablen</a></format></p>
            <p><format color="%LinkColor%"><a href="10-java-classes.md#constants">Konstanten</a></format></p>
            <p><format color="%LinkColor%"><a href="09-java-methods.md#return-type">Methoden (Rückgabetyp)</a></format></p>
            <p><format color="%LinkColor%"><a href="09-java-methods.md#method-signature">Methoden (Parameter)</a></format></p>
        </td>
        <td>
            <list>
                <li><format color="%LinkColor%"><a href="02-java-data-types.md#primitive-data-types">Primitiver Datentyp</a></format></li>
                <li>Datentyp einer Variablen</li>
                <li>Datentyp einer Konstanten</li>
                <li>Rückgabetyp einer Methode</li>
                <li>Parameter einer Methode</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>case</code></td>
        <td><p><format color="%LinkColor%"><a href="06-java-branches.md#switch-case">switch-Ausdrücke</a></format></p></td>
        <td>
            <list>
                <li>Definiert einen <code>case</code> innerhalb eines <code>switch</code>-Ausdrucks, der ausgeführt wird, wenn der Wert der <code>switch</code>-Variablen mit dem Wert des <code>case</code> übereinstimmt.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>catch</code></td>
        <td><p><format color="%LinkColor%"><a href="15-java-exceptions.md">Exceptions</a></format></p></td>
        <td>
            <list>
                <li>Beginnt einen Block, der einen bestimmten Ausnahmetyp behandelt.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>char</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="03-java-variables.md">Variablen</a></format></p>
            <p><format color="%LinkColor%"><a href="10-java-classes.md#constants">Konstanten</a></format></p>
            <p><format color="%LinkColor%"><a href="09-java-methods.md#return-type">Methoden (Rückgabetyp)</a></format></p>
            <p><format color="%LinkColor%"><a href="09-java-methods.md#method-signature">Methoden (Parameter)</a></format></p>
        </td>
        <td>
            <list>
                <li><format color="%LinkColor%"><a href="02-java-data-types.md#primitive-data-types">Primitiver Datentyp</a></format></li>
                <li>Datentyp einer Variablen</li>
                <li>Datentyp einer Konstanten</li>
                <li>Rückgabetyp einer Methode</li>
                <li>Parameter einer Methode</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>class</code></td>
        <td><p><format color="%LinkColor%"><a href="10-java-classes.md">Klassen</a></format></p></td>
        <td>
            <list>
                <li>Deklariert eine Klasse.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>const</code>*</td>
        <td>-</td>
        <td>
            <list>
                <li>Reserviertes, aber nicht verwendetes Keyword.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>continue</code></td>
        <td><p><format color="%LinkColor%"><a href="07-java-loops.md">Schleifen</a></format></p></td>
        <td>
            <list>
                <li>Fährt mit dem nächsten Durchlauf der nächstgelegenen umschließenden Schleife fort.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>default</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="14-java-oop.md#default-methods">Interfaces (Default-Methoden)</a></format></p>
            <p><format color="%LinkColor%"><a href="06-java-branches.md#switch-case">switch-Ausdrücke</a></format></p>
        </td>
        <td>
            <list>
                <li>Methoden mit diesem Modifier bringen in Interfaces Standardimplementierungen mit. Diese Methoden können, müssen aber nicht überschrieben werden, wenn das Interface implementiert wird.</li>
                <li>Bei <format color="%LinkColor%"><a href="06-java-branches.md">Abfragen</a></format> mittels <code>switch</code>-Ausdrücken wird das Schlüsselwort als "else"-Zweig verwendet.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>do</code></td>
        <td><p><format color="%LinkColor%"><a href="07-java-loops.md#do-while-loop">do-while-Schleife</a></format></p></td>
        <td>
            <list>
                <li>Beginnt eine fußgesteuerte <code>do</code>-<code>while</code>-Schleife.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>double</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="03-java-variables.md">Variablen</a></format></p>
            <p><format color="%LinkColor%"><a href="10-java-classes.md#constants">Konstanten</a></format></p>
            <p><format color="%LinkColor%"><a href="09-java-methods.md#return-type">Methoden (Rückgabetyp)</a></format></p>
            <p><format color="%LinkColor%"><a href="09-java-methods.md#method-signature">Methoden (Parameter)</a></format></p>
        </td>
        <td>
            <list>
                <li><format color="%LinkColor%"><a href="02-java-data-types.md#primitive-data-types">Primitiver Datentyp</a></format></li>
                <li>Datentyp einer Variablen</li>
                <li>Datentyp einer Konstanten</li>
                <li>Rückgabetyp einer Methode</li>
                <li>Parameter einer Methode</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>else</code></td>
        <td><p><format color="%LinkColor%"><a href="06-java-branches.md#if-else">if-Abfragen</a></format></p></td>
        <td>
            <list>
                <li>Definiert einen Default-Zweig eines <code>if</code>-Ausdrucks, der ausgeführt wird, wenn alle vorherigen Bedingungen <code>false</code> ergeben.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>enum</code></td>
        <td><p><format color="%LinkColor%"><a href="13-java-enumerations.md">Enumerationen</a></format></p></td>
        <td>
            <list>
                <li>Deklariert ein Enum.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>extends</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="10-java-classes.md">Klassen</a></format></p>
            <p><format color="%LinkColor%"><a href="14-java-oop.md#interfaces">Interfaces</a></format></p>
        </td>
        <td>
            <list>
                <li>Lässt eine Klasse von einer anderen erben.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>finally</code></td>
        <td><p><format color="%LinkColor%"><a href="15-java-exceptions.md">Exceptions</a></format></p></td>
        <td>
            <list>
                <li>Der <code>finally</code>-Block wird optional nach einem <code>try</code>-Block definiert. Dieser wird jedes Mal ausgeführt, unabhängig davon, ob eine Exception geworfen wurde.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>float</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="03-java-variables.md">Variablen</a></format></p>
            <p><format color="%LinkColor%"><a href="10-java-classes.md#constants">Konstanten</a></format></p>
            <p><format color="%LinkColor%"><a href="09-java-methods.md#return-type">Methoden (Rückgabetyp)</a></format></p>
            <p><format color="%LinkColor%"><a href="09-java-methods.md#method-signature">Methoden (Parameter)</a></format></p>
        </td>
        <td>
            <list>
                <li><format color="%LinkColor%"><a href="02-java-data-types.md#primitive-data-types">Primitiver Datentyp</a></format></li>
                <li>Datentyp einer Variablen</li>
                <li>Datentyp einer Konstanten</li>
                <li>Rückgabetyp einer Methode</li>
                <li>Parameter einer Methode</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>for</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="07-java-loops.md#for-loop">for-Schleife</a></format></p>
            <p><format color="%LinkColor%"><a href="07-java-loops.md#for-each-loop">for-each-Schleife</a></format></p>
        </td>
        <td>
            <list>
                <li>Deklariert eine <code>for</code>-Schleife.</li>
                <li>Deklariert eine <code>for</code>-each-Schleife.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>goto</code>*</td>
        <td>-</td>
        <td>
            <list>
                <li>Reserviertes, aber nicht verwendetes Keyword.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>if</code></td>
        <td><p><format color="%LinkColor%"><a href="06-java-branches.md#if-else">if-Abfragen</a></format></p></td>
        <td>
            <list>
                <li>Deklariert eine <code>if</code>-Abfrage.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>implements</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="10-java-classes.md">Klassen</a></format></p>
            <p><format color="%LinkColor%"><a href="14-java-oop.md#interfaces">Interfaces</a></format></p>
        </td>
        <td>
            <list>
                <li>Implementiert ein Interface.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>import</code></td>
        <td><p><format color="%LinkColor%"><a href="16-java-packages-and-imports.md">Importanweisungen</a></format></p></td>
        <td>
            <list>
                <li>Importiert eine oder mehrere <format color="%LinkColor%"><a href="10-java-classes.md">Klassen</a></format> aus einem anderen <format color="%LinkColor%"><a href="16-java-packages-and-imports.md">Package</a></format> zur Verwendung in die aktuelle Datei/Klasse.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>instanceof</code></td>
        <td><p><format color="%LinkColor%"><a href="14-java-oop.md#the-keyword-instanceof">Typüberprüfungen</a></format></p></td>
        <td>
            <list>
                <li>Überprüft eine <format color="%LinkColor%"><a href="03-java-variables.md">Variable</a></format> auf seinen <format color="%LinkColor%"><a href="02-java-data-types.md#reference-data-types">Referenztyp</a></format>.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>int</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="03-java-variables.md">Variablen</a></format></p>
            <p><format color="%LinkColor%"><a href="10-java-classes.md#constants">Konstanten</a></format></p>
            <p><format color="%LinkColor%"><a href="09-java-methods.md#return-type">Methoden (Rückgabetyp)</a></format></p>
            <p><format color="%LinkColor%"><a href="09-java-methods.md#method-signature">Methoden (Parameter)</a></format></p>
        </td>
        <td>
            <list>
                <li><format color="%LinkColor%"><a href="02-java-data-types.md#primitive-data-types">Primitiver Datentyp</a></format></li>
                <li>Datentyp einer Variablen</li>
                <li>Datentyp einer Konstanten</li>
                <li>Rückgabetyp einer Methode</li>
                <li>Parameter einer Methode</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>interface</code></td>
        <td><p><format color="%LinkColor%"><a href="14-java-oop.md#interfaces">Interfaces</a></format></p></td>
        <td>
            <list>
                <li>Deklariert ein Interface.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>long</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="03-java-variables.md">Variablen</a></format></p>
            <p><format color="%LinkColor%"><a href="10-java-classes.md#constants">Konstanten</a></format></p>
            <p><format color="%LinkColor%"><a href="09-java-methods.md#return-type">Methoden (Rückgabetyp)</a></format></p>
            <p><format color="%LinkColor%"><a href="09-java-methods.md#method-signature">Methoden (Parameter)</a></format></p>
        </td>
        <td>
            <list>
                <li><format color="%LinkColor%"><a href="02-java-data-types.md#primitive-data-types">Primitiver Datentyp</a></format></li>
                <li>Datentyp einer Variablen</li>
                <li>Datentyp einer Konstanten</li>
                <li>Rückgabetyp einer Methode</li>
                <li>Parameter einer Methode</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>new</code></td>
        <td><p><format color="%LinkColor%"><a href="11-java-objects.md">Objekterzeugung / Instanziierung</a></format></p></td>
        <td>
            <list>
                <li>Erzeugt ein neues Objekt/Instanz.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>package</code></td>
        <td><p><format color="%LinkColor%"><a href="16-java-packages-and-imports.md">Package-Anweisung</a></format></p></td>
        <td>
            <list>
                <li>Registriert die aktuelle Datei/Klasse für das Dateiverzeichnissystem, damit diese von anderen gefunden werden kann.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>return</code></td>
        <td><p><format color="%LinkColor%"><a href="09-java-methods.md">Methoden</a></format></p></td>
        <td>
            <list>
                <li>Gibt den Rückgabewert an den Aufrufer der Methode zurück.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>short</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="03-java-variables.md">Variablen</a></format></p>
            <p><format color="%LinkColor%"><a href="10-java-classes.md#constants">Konstanten</a></format></p>
            <p><format color="%LinkColor%"><a href="09-java-methods.md#return-type">Methoden (Rückgabetyp)</a></format></p>
            <p><format color="%LinkColor%"><a href="09-java-methods.md#method-signature">Methoden (Parameter)</a></format></p>
        </td>
        <td>
            <list>
                <li><format color="%LinkColor%"><a href="02-java-data-types.md#primitive-data-types">Primitiver Datentyp</a></format></li>
                <li>Datentyp einer Variablen</li>
                <li>Datentyp einer Konstanten</li>
                <li>Rückgabetyp einer Methode</li>
                <li>Parameter einer Methode</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>super</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="10-java-classes.md#object-variables">Objektvariablen</a></format></p>
            <p><format color="%LinkColor%"><a href="10-java-classes.md#object-methods">Objektmethoden</a></format></p>
            <p><format color="%LinkColor%"><a href="10-java-classes.md#constructors">Konstruktoren</a></format></p>
        </td>
        <td>
            <list>
                <li>Ruft Konstruktoren der Oberklasse auf.</li>
                <li>Ruft Objektvariablen der Oberklasse auf.</li>
                <li>Ruft Objektmethoden der Oberklasse auf.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>switch</code></td>
        <td><p><format color="%LinkColor%"><a href="06-java-branches.md#switch-case">switch-Ausdrücke</a></format></p></td>
        <td>
            <list>
                <li>Definiert einen <code>switch</code>-<code>case</code>-Ausdruck.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>this</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="10-java-classes.md#object-variables">Objektvariablen</a></format></p>
            <p><format color="%LinkColor%"><a href="10-java-classes.md#object-methods">Objektmethoden</a></format></p>
            <p><format color="%LinkColor%"><a href="10-java-classes.md#constructors">Konstruktoren</a></format></p>
        </td>
        <td>
            <list>
                <li>Ruft Konstruktoren der Klasse auf.</li>
                <li>Ruft Objektvariablen der Klasse auf.</li>
                <li>Ruft Objektmethoden der Klasse auf.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>throw</code></td>
        <td><p><format color="%LinkColor%"><a href="15-java-exceptions.md">Exceptions</a></format></p></td>
        <td>
            <list>
                <li>"Wirft" eine Exception.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>throws</code></td>
        <td><p><format color="%LinkColor%"><a href="15-java-exceptions.md">Methoden (Ausnahmenweitergabe)</a></format></p></td>
        <td>
            <list>
                <li>Kennzeichnung einer Methode, dass diese eine Exception werfen kann, die welche an den Aufrufer weitergeleitet wird.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>try</code></td>
        <td><p><format color="%LinkColor%"><a href="15-java-exceptions.md">Exceptions</a></format></p></td>
        <td>
            <list>
                <li>Deklariert einen <code>try</code>-<code>catch</code>-Block zum Abfangen von Exceptions.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>void</code></td>
        <td><p><format color="%LinkColor%"><a href="09-java-methods.md">Methoden (Rückgabetyp)</a></format></p></td>
        <td>
            <list>
                <li>Gibt an, dass die Methode keinen Rückgabetyp hat.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>while</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="07-java-loops.md#while-loop">while-Schleife</a></format></p>
            <p><format color="%LinkColor%"><a href="07-java-loops.md#do-while-loop">do-while-Schleife</a></format></p>
        </td>
        <td>
            <list>
                <li>Deklariert eine <code>while</code>-Schleife.</li>
                <li>Deklariert eine <code>do</code>-<code>while</code>-Schleife.</li>
            </list>
        </td>
    </tr>
</table>
                                                                            
### <format color="%c2%">Modifizierer – 12</format> {id="modifier"}

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
                <li>Wird automatisch intern angewendet, wenn kein anderer <format color="%LinkColor%"><a href="12-java-modifier-access-rights.md#access-modifier">Access Modifier</a></format> zugewiesen wird. Eine Ausnahme sind Konstruktoren in <format color="%LinkColor%"><a href="13-java-enumerations.md">Enumerationen</a></format>. Dort ist es standardmäßig <code>private</code>.</li>
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
                <li>Auf Methoden kann immer nur von einem <format color="%LinkColor%"><a href="java-multithreading.md">Thread</a></format> zugegriffen werden.</li>
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
                <li>Alle <format color="%LinkColor%"><a href="java-multithreading.md">Threads</a></format> lesen und schreiben den Wert der Variablen direkt aus dem Hauptspeicher, anstatt eine Kopie im <tooltip term="Cache"><format color="%GlossaryLinkColor%">Cache</format></tooltip> zu verwenden. Damit wird sichergestellt, dass die Threads den aktuellen Wert sehen und inkonsistente oder falsche Ergebnisse verhindert werden.</li>
            </list>
        </td>
    </tr>
</table>

### <format color="%c2%">Kontextbezogene "Keywords" – 6</format> {id="contextual-keywords"}

Alle "Keywords" in der folgenden Tabelle können als <format color="%c1%">[Identifier](#identifier)</format> verwendet werden (mit Ausnahme von `non-sealed`).

<table>
    <tr>
        <td width="100">Keyword</td>
        <td width="180">Anwendungsbereich</td>
        <td>Beschreibung</td>
    </tr>
    <tr>
        <td><code>non-sealed</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="14-java-oop.md#sealed-classes-and-interfaces">Versiegelte Klassen</a></format></p>
            <p><format color="%LinkColor%"><a href="14-java-oop.md#sealed-classes-and-interfaces">Versiegelte Interfaces</a></format></p>
        </td>
        <td>
            <list>
                <li>Der Modifizierer <code>non-sealed</code> wurde als Vorschaufunktion in Java 15 eingeführt und mit Java 17 finalisiert.</li>
                <li>Es öffnet eine Klasse wieder ohne Beschränkungen für weitere Vererbungen.</li>
                <li><code>non-sealed</code> ist das einzige Keyword, welches einen <format color="%c4%"><a href="#operators">Operator</a></format> besitzt und kann deshalb nicht als <format color="%c1%"><a href="#identifier">Identifier</a></format> genutzt werden.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>permits</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="14-java-oop.md#sealed-classes-and-interfaces">Versiegelte Klassen</a></format></p>
            <p><format color="%LinkColor%"><a href="14-java-oop.md#sealed-classes-and-interfaces">Versiegelte Interfaces</a></format></p>
        </td>
        <td>
            <list>
                <li><code>permits</code> wurde als Vorschaufunktion in Java 14 eingeführt und mit Java 16 finalisiert.</li>
                <li>Es ermöglicht in Verbindung mit <code>sealed</code> und die explizite Angabe der Kindklassen, die Vererbung von Klassen einzuschränken.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>record</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="10-java-classes.md#records">Records</a></format></p>
        </td>
        <td>
            <list>
                <li>Der Modifizierer <code>record</code> wurde als Vorschaufunktion in Java 14 eingeführt und mit Java 16 finalisiert.</li>
                <li>Es wird anstelle des <code>class</code>-Schlüsselwortes verwendet, um eine Record-Klasse zu erstellen.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>sealed</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="14-java-oop.md#sealed-classes-and-interfaces">Versiegelte Klassen</a></format></p>
            <p><format color="%LinkColor%"><a href="14-java-oop.md#sealed-classes-and-interfaces">Versiegelte Interfaces</a></format></p>
        </td>
        <td>
            <list>
                <li>Der Modifizierer <code>sealed</code> wurde als Vorschaufunktion in Java 15 eingeführt und mit Java 17 finalisiert.</li>
                <li>Es ermöglicht in Verbindung mit <code>permits</code> und die explizite Angabe der Kindklassen, die Vererbung von Klassen einzuschränken.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>var</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="03-java-variables.md#reserved-type-name-var">Variablen</a></format></p>
        </td>
        <td>
            <list>
                <li>Seit Java 10 gibt es die Möglichkeit eine Variable mit <code>var</code> zu deklarieren.</li>
                <li>Es dient im Rahmen der <format color="%Highlight%">Type Inference</format> als Platzhalter für einen <format color="%LinkColor%"><a href="02-java-data-types.md">Datentyp</a></format>.</li>
                <li>Es wird häufig als <format color="%LinkColor%"><a href="#keywords">Keyword</a></format> verwechselt, ist aber ein <format color="%Highlight%">Reserved Type Name</format>.</li>
            </list>
        </td>
    </tr>
    <tr>
        <td><code>yield</code></td>
        <td>
            <p><format color="%LinkColor%"><a href="06-java-branches.md#switch-case">switch-Ausdrücke</a></format></p>
        </td>
        <td>
            <list>
                <li><code>yield</code> wurde in Java 14 hinzugefügt.</li>
                <li>Es findet nur innerhalb eines <format color="%LinkColor%"><a href="06-java-branches.md#switch-case-yield">switch-Ausdrucks</a></format> als Return-Anweisung Anwendung.</li>
            </list>
        </td>
    </tr>
</table>

## <format color="%c3%">Literale</format> {id="literals"}
Literale (engl. Literals) bzw. Literalkonstanten bezeichnen Werte, die sich im Programm nicht ändern können. Unterschieden wird unter den folgenden 7 Literal-Arten.

<table>
    <tr>
        <td>Kategorie</td>
        <td>Literal</td>
    </tr>
    <tr>
        <td>Ganzzahl-Literal</td>
        <td><code>42</code></td>
    </tr>
    <tr>
        <td>Fließkommazahl-Literal</td>
        <td><code>3.14</code></td>
    </tr>
    <tr>
        <td>Boolean Literal </td>
        <td><code>true</code> <code>false</code></td>
    </tr>
    <tr>
        <td>Zeichen-Literal </td>
        <td><code>@</code></td>
    </tr>
    <tr>
        <td>String Literal</td>
        <td><code>"Hello World!"</code></td>
    </tr>
    <tr>
        <td>Text Block Literal</td>
        <td><code>"""Hello World!"""</code></td>
    </tr>
    <tr>
        <td>Null Literal</td>
        <td><code>null</code></td>
    </tr>
</table>

> Die Literale `true`, `false` und `null` sind zwar keine <format color="%NoteLinkColor%">[Schlüsselwörter](#keywords)</format>, können aber ebenfalls nicht als <format color="%c1%">[Bezeichner](#identifier)</format> verwendet werden.
> {style="note"}

## <format color="%c4%">Operatoren</format> {id="operators"}
Operatoren (engl. Operators) bezeichnen Zeichen(-folgen), welche in der Programmierung und der Mathematik verwendet werden, um Operationen wie Additionen oder Multiplikationen durchzuführen. Diese Operatoren können in <format color="%c4%">unäre</format>, <format color="%c4%">binäre</format> und <format color="%c4%">ternäre</format> Operatoren unterteilt werden. Darüber hinaus gibt es noch Kategorien wie <format color="%c4%">arithmetische Operatoren</format>, <format color="%c4%">Zuweisungsoperatoren</format>, <format color="%c4%">Vergleichsoperatoren</format>, <format color="%c4%">logische Operatoren</format>, <format color="%c4%">Bitoperatoren</format> und <format color="%c4%">In- / Dekrement</format>.

- <format color="%c4%">Unäre Operatoren</format> benötigen nur einen Operanden.
- <format color="%c4%">Binäre Operatoren</format> benötigen zwei Operanden.
- <format color="%c4%">Ternäre Operatoren</format> werden durch drei Operanden verknüpft.

<table>
    <tr>
        <td width="160">Operatoren</td>
        <td width="200">Kategorie</td>
        <td>Beschreibung</td>
    </tr>
    <tr>
        <td><code>+</code> <code>-</code> <code>*</code> <code>/</code> <code>%</code></td>
        <td>Arithmetische Operatoren</td>
        <td>Arithmetische Operatoren führen mathematische Operationen auf numerischen Werten durch.</td>
    </tr>
    <tr>
        <td>
            <code>=</code> <code>+=</code> <code>-=</code> <code>*=</code> <code>/=</code> <code>%=</code> <code>&=</code> <code>|=</code> <code>^=</code> <code>>>=</code> <code>&lt;&lt;=</code> <code>>>>=</code>
        </td>
        <td>Zuweisungsoperatoren</td>
        <td>Zuweisungsoperatoren führen (mal abgesehen von <code>=</code>) erst die geforderte Operation durch und weisen das Ergebnis einer Variablen zu.</td>
    </tr>
    <tr>
        <td><code>&&</code> <code>||</code> <code>!</code></td>
        <td>Logische Operatoren</td>
        <td>Logische Operatoren verknüpfen zwei boolesche Ausdrücke und geben ebenfalls ein boolesches Ergebnis (<code>true</code> oder <code>false</code>) zurück.</td>
    </tr>
    <tr>
        <td>
            <code>></code> <code>&lt;</code> <code>>=</code> <code>&lt;=</code> <code>==</code> <code>!=</code>
        </td>
        <td>Vergleichsoperatoren</td>
        <td>Vergleichsoperatoren vergleichen zwei Operanden und geben ein boolesches Ergebnis (<code>true</code> oder <code>false</code>) zurück.</td>
    </tr>
    <tr>
        <td>
            <code>~</code> <code>|</code> <code>&</code> <code>^</code> <code>&lt;&lt;</code> <code>>></code> <code>>>></code>
        </td>
        <td>Bitoperatoren</td>
        <td>Arbeiten direkt auf den einzelnen Bits eines Datenwerts.</td>
    </tr>
    <tr>
        <td><code>++</code> <code>--</code></td>
        <td>Inkrement / Dekrement</td>
        <td>Erhöht oder verringert einen Wert um <code>1</code>.</td>
    </tr>
    <tr>
        <td><code>? :</code></td>
        <td>Ternäre Operator</td>
        <td>Dient einer verkürzten Schreibweise des <code>if</code>- <code>else</code>-Ausdrucks mit möglichem Rückgabewert.</td>
    </tr>
    <tr>
        <td><code>-></code></td>
        <td>Lambda Operator</td>
        <td>Definiert Lambda-Ausdrücke, welche mit Java 8 hinzugefügt wurden.</td>
    </tr>
</table>

> Der ternäre Operator ist in Java der einzige Operator der drei Operanden verbindet.


## <format color="%c5%">Separatoren</format> {id="separators"}
Separatoren (engl. Separators) dienen dem <tooltip term="Compiler"><format color="%GlossaryLinkColor%">Compiler</format></tooltip> dazu, einzelne <format color="%c1%">[Bezeichner](#identifier)</format> und Anweisungen voneinander trennen zu können.

<table>
    <tr>
        <td>Separator</td>
        <td>Beschreibung</td>
    </tr>
    <tr>
        <td><code>(</code> <code>)</code></td>
        <td>
            <p>Dient als Kennzeichnung der Parameter und Attribute bei <format color="%LinkColor%"><a href="09-java-methods.md#static-method-call">Methodenaufrufen</a></format>, sowie der Änderung der Berechnungsvorschrift.</p>
        </td>
    </tr>
    <tr>
        <td><code>{</code> <code>}</code></td>
        <td>
            <p>Kennzeichnen den Anfang und das Ende eines Anweisungsblocks.</p>
        </td>
    </tr>
    <tr>
        <td><code>[</code> <code>]</code></td>
        <td>
            <p>Dient zur Definition von <format color="%LinkColor%"><a href="08-java-arrays.md">Arrays</a></format>, dessen Größen und den Zugriff auf einzelne Felder des Arrays.</p>
        </td>
    </tr>
    <tr>
        <td><code>;</code></td>
        <td>
            <p>Wird als Abschluss einer Anweisung verwendet.</p>
        </td>
    </tr>
    <tr>
        <td><code>,</code></td>
        <td>
            <p>Dient als Abtrennung zwischen Werten, Anweisungen und Parametern.</p>
        </td>
    </tr>
    <tr>
        <td><code>.</code></td>
        <td>
            <p>Trennt Paketnamen von <format color="%LinkColor%"><a href="16-java-packages-and-imports.md">Unterpaketen</a></format> und <format color="%LinkColor%"><a href="10-java-classes.md">Klassen</a></format>, sowie <format color="%LinkColor%"><a href="03-java-variables.md">Variablen</a></format> von <format color="%LinkColor%"><a href="09-java-methods.md">Methoden</a></format>.</p>
        </td>
    </tr>
    <tr>
        <td><code>...</code></td>
        <td>
            <p>Dient als <format color="%LinkColor%"><a href="09-java-methods.md#varargs">variable Parameterangabe</a></format> bei <format color="%LinkColor%"><a href="09-java-methods.md">Methoden</a></format>.</p>
        </td>
    </tr>
    <tr>
        <td><code>@</code></td>
        <td>
            <p>Wird als Präfix für <format color="%LinkColor%"><a href="java-annotations.md">Annotationen</a></format> verwendet.</p>
        </td>
    </tr>
    <tr>
        <td><code>::</code></td>
        <td>
            <p>Dient als Methodenreferenz und Alternative zu Lambda-Ausdrücken.</p>
        </td>
    </tr>
</table>

## <format color="%c6%">Kommentare</format> {id="comments"}
Kommentare (engl. Comments) können dabei helfen, anderen Entwicklern (und auch einem selbst) den eigenen Code verständlicher zu machen. Dies erhöht die Wartbarkeit, Lesbarkeit und das Verständnis für die Funktion des Codes. Unterschieden wird zwischen drei Kommentararten.

<tabs group="comments">
    <tab id="one-line-comment" title="Einzeiliger Kommentar" group-key="one-line">
        <code-block lang="java">
            // Ich bin ein einzeiliger Kommentar!
        </code-block>
    </tab>
    <tab id="multi-line-comment" title="Mehrzeiliger Kommentar" group-key="multi-line">
        <code-block lang="java">
            /*
             * Ich bin ein
             * mehrzeiliger Kommentar
             */
        </code-block>
    </tab>
    <tab id="java-doc-comment" title="Java-Doc Kommentar" group-key="java-doc">
        <code-block lang="java">
            /**
             * Ich bin ein
             * Java-Doc Kommentar
             */
        </code-block>
    </tab>
</tabs>

Wird in einer <tooltip term="IDE"><format color="%GlossaryLinkColor%">IDE</format></tooltip> (Integrated Development Environment) beispielsweise über einen Klassen- oder Methodennamen gehovert, erscheint ein kleines Fenster – dies ist die Java-Dokumentation. Sie beschreibt den Aufbau und die Funktionsweisen der <format color="%LinkColor%">[Klassen](10-java-classes.md)</format>, <format color="%LinkColor%">[Methoden](09-java-methods.md)</format> etc. genauer.

![](01_java_token_1.jpg){border-effect="line"}

![](01_java_token_2.jpg){border-effect="line"}

> Die <format color="%NoteLinkColor%">Java-Dokumentation</format> ist ein spezielles Tool, welches aus Java-Quellcodes auch automatisch HTML-Dokumentationsdateien erstellen kann.
> {style="note" title="Die Java-Dokumentation"}

## Assoziativität {id="associativity"}

Die <format color="%LinkColor%">[Assoziativität](https://en.wikipedia.org/wiki/Java_syntax#Operators)</format> beschreibt die genaue Reihenfolge, in der die <format color="%c4%">[Operatoren](#operators)</format> und <format color="%c5%">[Separatoren](#separators)</format> ausgewertet werden. Operatoren mit einer höheren Priorität oder Vorrang werden vor Operatoren mit einer niedrigeren Priorität ausgewertet. Besitzen zwei Operatoren die gleiche Priorität, entscheidet die Assoziativität über die Auswertungsreihenfolge.