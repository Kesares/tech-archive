# Java
<primary-label ref="programming-lang"></primary-label>
<secondary-label ref="wip"></secondary-label>

## Was ist Java? {id="what-is-java"}

<p>Java ist wie der berühmte Alleskönner auf einer Party: Du triffst ihn überall und er kann alles – oder zumindest
behauptet er das. Es handelt sich um eine objektorientierte Programmiersprache, die 1995 ursprünglich von James Gosling
und Sun Microsystems entwickelt und 2010 von
<format color="%LinkColor%"><a href="https://www.oracle.com">Oracle</a></format> übernommen wurde. Java wurde mit dem
Ziel entworfen, eine plattformunabhängige Programmiersprache zu sein, welche Programme auf verschiedenen Systemen
ausführen kann – <i>"Write once, run anywhere"</i>.</p>

<p>Im Verhältnis zu anderen Programmiersprachen ist, meiner Meinung nach, Java tatsächlich ziemlich leicht zu lernen. Es
gibt Unmengen an Ressourcen und eine riesige Community, die euch auf eurem Lernweg weiterhelfen können. Das bedeutet,
dass ihr selten allein dasteht, wenn ihr mal nicht weiter wisst.</p>

<p>Natürlich könnte es sein, dass die Einstiegshürde bei dieser Sprache höher liegt als bei Sprachen wie Python, die
eine größere Abstraktionsebene bieten und dadurch leichter zugänglich sind. Aber im Vergleich zu komplexeren Sprachen
wie C++ ist Java eine wohlwollende Einstiegshilfe in die Welt der Programmierung, die später Türen zu vielen anderen
Technologien öffnet.</p>

## JDK, JRE und JVM {id="jdk-jre-jvm"}

<p>Für das Programmieren und Entwickeln von Java-Anwendungen muss Java erst installiert werden. Wer bereits nach der
Installation von Java gegoogelt hat, wird wahrscheinlich schon auf die Begriffe
<tooltip term="JRE"><format color="%GlossaryLinkColor%">JRE</format></tooltip>,
<tooltip term="JDK"><format color="%GlossaryLinkColor%">JDK</format></tooltip> und
<tooltip term="JVM"><format color="%GlossaryLinkColor%">JVM</format></tooltip> gestoßen sein.</p>

<list>
  <li>
    <p>Das <tooltip term="JDK"><format color="%GlossaryLinkColor%">JDK</format></tooltip> (Java Development Kit) wird
    verwendet, um Java-Programme zu entwickeln und liefert eine Sammlung von Werkzeugen, die für die Entwicklung von
    Java-Anwendungen benötigt werden.</p>
  </li>
  <li>
    <p>Die <tooltip term="JRE"><format color="%GlossaryLinkColor%">JRE</format></tooltip> (Java Runtime Environment) ist
    Teil des <tooltip term="JDK"><format color="%GlossaryLinkColor%">JDK</format></tooltip> und wird verwendet, um
    Java-Programme auszuführen. Sie umfasst Klassenbibliotheken und andere Komponenten, die für die Ausführung benötigt
    werden.</p>
  </li>
  <li>
    <p>Die <tooltip term="JVM"><format color="%GlossaryLinkColor%">JVM</format></tooltip> (Java Virtual Machine) ist
    Teil der <tooltip term="JRE"><format color="%GlossaryLinkColor%">JRE</format></tooltip> und für die eigentliche
    Ausführung von Java-Programmen zuständig. Sie wandelt den Java-Bytecode in ausführbare Anweisungen für die
    zugrundeliegende Maschine um.</p>
  </li>
</list>

![JDK JRE & JVM](00_java_started_1.png)

## Download Java {id="download-java"}

<note title="Download und LTS Empfehlung">
    <p>Für die Entwicklung von Java-Programmen ist die OpenJDK-Distribution
    <format color="%NoteLinkColor%">[Eclipse Temurin](https://adoptium.net)</format> von Adoptium und davon die
    Installation eines <format color="%NoteLinkColor%">Long Term Support-OpenJDK</format> zu empfehlen, da dieses über
    einen längeren Zeitraum weiterentwickelt und gepatcht wird.</p>
</note>

<p><format color="%Highlight%">Eclipse Temurin</format> ist eine quelloffene Java Standard Edition-Implementierung und
eine Alternative zum kommerziell lizenzierten OracleJDK von Oracle.</p>

<p>Viele <tooltip term="IDE"><format color="%GlossaryLinkColor%">IDEs</format></tooltip>, wie IntelliJ, bieten die
Möglichkeit, das <tooltip term="JDK"><format color="%GlossaryLinkColor%">JDK</format></tooltip> direkt über die
<tooltip term="IDE"><format color="%GlossaryLinkColor%">IDE</format></tooltip> herunterzuladen und zu installieren.</p>

## Installation des JDK {id="installation-jdk"}

<tabs group="java">
    <tab id="java-windows-install" title="Windows" group-key="windows">
        <note title=".msi-Datei">
            <p>Es wird empfohlen, eine <code>.msi</code>-Datei herunterzuladen, da bei der Installation die
            Umgebungsvariablen automatisch gesetzt werden können. Wenn stattdessen eine <code>.zip</code>-Datei
            heruntergeladen wird, müssen die Umgebungsvariablen manuell konfiguriert werden.</p>
        </note>
        <p>Für die folgende Installation und die weiteren Kapitel wird die LTS-Version des OpenJDK für Java 21
        verwendet.</p>
        <p>Unter <code>Set JAVA_HOME variable</code> sollte die Option <code>Entire feature will be installed on local
        hard drive</code> ausgewählt werden.</p>
        <p>Dies installiert alle Dateien und Ressourcen, die das
        <tooltip term="JDK"><format color="%GlossaryLinkColor%">JDK</format></tooltip> benötigt, auf der lokalen
        Festplatte und setzt automatisch die Umgebungsvariablen.</p>
        <tip>
            <p>Umgebungsvariablen sind spezielle Variablen in einem Betriebssystem, die Einstellungen oder Informationen
            über die Arbeitsumgebung für Prozesse und Anwendungen bereitstellen.</p>
        </tip>
        <img src="00_java_started_2.png" alt="Java Windows Installation"/>
    </tab>
</tabs>

<p>Zum Überprüfen, ob die Umgebungsvariablen für Java und den
<tooltip term="Compiler"><format color="%GlossaryLinkColor%">Compiler</format></tooltip> richtig gesetzt und die
richtige Version installiert wurde, können die folgenden beiden Befehle in der Kommandozeile eingegeben werden.</p>

<code-block lang="console">
    java --version
</code-block>

<code-block lang="console">
    javac --version
</code-block>

<p>Für diese Befehle sollten Ausgaben der folgenden Art erscheinen.</p>

<code-block lang="console">
    openjdk version "21.0.4" 2024-07-16 LTS
    OpenJDK Runtime Environment Temurin-21.0.4+7 (build 21.0.4+7-LTS)
    OpenJDK 64-Bit Server VM Temurin-21.0.4+7 (build 21.0.4+7-LTS, mixed mode, sharing)
</code-block>

<code-block lang="console">
    javac 21.0.4
</code-block>

<p>Java wurde nun richtig installiert. Jetzt kann sich nach einer geeigneten
<tooltip term="IDE"><format color="%GlossaryLinkColor%">IDE</format></tooltip> umgeschaut werden.</p>

<warning title="Installation von mehreren Java-Versionen">
    <p>Es ist möglich, mehrere <tooltip term="JDK"><format color="%GlossaryLinkColor%">JDK</format></tooltip>-Versionen
    parallel zu installieren, wenn verschiedene Projekte unterschiedliche Versionen erfordern. Allerdings sollte darauf
    geachtet werden, dass die Umgebung korrekt konfiguriert wird, um Inkonsistenzen beim Wechsel zwischen den Versionen
    zu vermeiden.</p>
</warning>

<p>Um Probleme zu vermeiden, sollte die jeweilige Version, die für ein bestimmtes Projekt benötigt wird, explizit in den
Umgebungsvariablen und den Pfaden festgelegt werden. Wenn eine alte Version nicht mehr benötigt wird, kann es sinnvoll
sein, diese sauber zu deinstallieren, bevor eine neue Version installiert wird.</p>

## IDE {id="ide"}

<p>Eine <tooltip term="IDE"><format color="%GlossaryLinkColor%">IDE</format></tooltip> (Integrated Development
Environment) ist eine Software für eine optimierte Anwendungsentwicklung, welche gängige Entwicklertools in einer
zentralen grafischen Oberfläche vereint. Prinzipiell reicht zum Programmieren theoretisch ein einfacher Texteditor. Doch
das Arbeiten ist damit auf Dauer sehr mühsam.</p>

<p>Als Alternative zum normalen Texteditor auf Windows, ist
<format color="%LinkColor%"><a href="https://notepad-plus-plus.org">Notepad++</a></format> zu empfehlen. Notepad++
bietet einige Konfigurationsmöglichkeiten und unterstützt Syntax-Highlighting für viele Sprachen.</p>

<tabs group="ides">
    <tab id="intellij-idea" title="IntelliJ IDEA">
        <p>IntelliJ IDEA und viele weitere
        <tooltip term="IDE"><format color="%GlossaryLinkColor%">IDEs</format></tooltip> werden vom Softwareunternehmen
        <format color="%LinkColor%"><a href="https://www.jetbrains.com">JetBrains</a></format> vertrieben. IntelliJ ist
        die <tooltip term="IDE"><format color="%GlossaryLinkColor%">IDE</format></tooltip> die mit am häufigsten in der
        Java-Programmierung verwendet wird und gezielt für diese sowie die Sprachen Kotlin und Groovy weiterentwickelt
        wird. Zudem unterstützt IntelliJ eine Vielzahl von Konfigurationsmöglichkeiten und Plugins (wodurch auch die
        Nutzung von weiteren Sprachen möglich wird).</p>
        <p>IntelliJ ist für Windows, Linux und macOS verfügbar. Seit Version 9.0 gibt es zwei verschiedene Editionen.
        </p>
        <ul>
            <li>
                <p><format color="%Highlight%">IntelliJ IDEA Ultimate</format> ist kostenpflichtig. Es ist jedoch
                möglich eine <format color="%LinkColor%"><a href="https://www.jetbrains.com/community/education">
                kostenlose Bildungslizenz</a></format> für Schüler/Studenten und Lehrende/Professoren zu erhalten. Des
                Weiteren gibt es auch einen 30-tägigen-Trail.</p>
            </li>
            <li>
                <p><format color="%Highlight%">IntelliJ IDEA Community Edition</format> ist kostenlos. Sie bietet zwar
                weniger Features, ist aber dennoch eine sehr empfehlenswerte Alternative.</p>
            </li>
        </ul>
        <p>Eine Auflistung der Unterschiede zwischen IntelliJ IDEA Ultimate und IntelliJ IDEA Community Edition ist
        <format color="%LinkColor%"><a href="https://www.jetbrains.com/products/compare/?product=idea">hier</a></format>
        zu finden.</p>
        <note title="Download IntelliJ IDEA">
            <p>IntelliJ kann <format color="%NoteLinkColor%">
            <a href="https://www.jetbrains.com/idea/download/?section=windows">hier</a></format> heruntergeladen werden.
            Für die Community Edition muss etwas nach unten gescrollt werden. Es wird jedoch empfohlen, die
            <format color="%NoteLinkColor%"><a href="https://www.jetbrains.com/toolbox-app">JetBrains Toolbox</a>
            </format> zu installieren und darüber die passende IntelliJ Edition herunterzuladen.</p>
        </note>
        <h4 id="intellij-installation-without-toolbox">IntelliJ IDEA Installation ohne JetBrains Toolbox</h4>
        <tabs group="intellij-install">
            <tab id="intellij-install-windows" title="Windows">
                <h5>Installing Options</h5>
                <ul>
                    <li>
                        <p><code>Add "bin" folder to PATH</code> <format color="%Highlight%">(obligatorisch)</format>:
                        fügt das Verzeichnis mit den IntelliJ IDEA-Befehlszeilenprogrammen zur Umgebungsvariablen
                        <code>PATH</code> hinzu.</p>
                    </li>
                    <li>
                        <p><code>Add "Open Folder as Project"</code> <format color="%Highlight%">(optional, aber
                        empfohlen)</format>: fügt die Aktion <code>Open Folder as Project</code> zum Systemkontextmenü
                        hinzu, um ein beliebiges Java-Projekt mit Rechtsklick in IntelliJ zu öffnen.</p>
                    </li>
                    <li>
                        <p><code>Create Associations</code> verknüpft bestimmte Dateierweiterungen mit IntelliJ IDEA um
                        sie mit einem Doppelklick öffnen zu können.</p>
                        <ul>
                            <li>
                                <p><code>.java</code> <format color="%Highlight%">(optional, aber empfohlen)</format>:
                                für die Entwicklung mit Java.</p>
                            </li>
                            <li>
                                <p><code>.gradle</code> <format color="%Highlight%">(optional)</format>: für die
                                Entwicklung von Java-Anwendungen mit
                                <format color="%LinkColor%"><a href="https://gradle.org">Gradle</a></format>, ein auf
                                Java basierendes Build-Management-Automatisierungswerkzeug.</p>
                            </li>
                            <li>
                                <p><code>.groovy</code> <format color="%Highlight%">(optional)</format>: für die
                                Entwicklung mit Groovy.</p>
                            </li>
                            <li>
                                <p><code>.kt</code> <format color="%Highlight%">(optional)</format>: normale
                                Quelldateien für die Entwicklung mit Kotlin.</p>
                            </li>
                            <li>
                                <p><code>.kts</code> <format color="%Highlight%">(optional)</format>: Skriptdateien für
                                die Entwicklung mit Kotlin.</p>
                            </li>
                            <li>
                                <p><code>.pom</code> <format color="%Highlight%">(optional)</format>: für die
                                Entwicklung von Java-Anwendungen mit
                                <format color="%LinkColor%"><a href="https://maven.apache.org">Maven</a></format>, einem
                                in Java geschriebenes Build-Tool.</p>
                            </li>
                        </ul>
                    </li>
                </ul>
                <img src="00_java_started_3.png" alt="Windows Java Installation"/>
            </tab>
        </tabs>
        <h4 id="intellij-project-setup">IntelliJ IDEA Projekteinrichtung</h4>
        <tip>
            <p>Es ist sinnvoll, einen Workspace-Ordner zu erstellen, in dem alle Projekte gespeichert werden.</p>
        </tip>
        <p>Wird das erste Mal IntelliJ gestartet, erscheint das Fenster <code>Import IntelliJ IDEA Settings</code>. Hier
        können bestehende Konfigurationen importiert werden. In diesem Fall existieren keine Konfigurationen. Die
        voreingestellte Auswahl wird also bei <code>Do not import settings</code> belassen und auf
        <shortcut>OK</shortcut> geklickt.</p>
        <p>Danach erscheint eine Frage nach dem Teilen von Daten und dem Datenschutz. Dies kann nach eigenem Ermessen
        entschieden werden. In diesem Guide wird auf <shortcut>Don't Send</shortcut> geklickt.</p>
        <p>Nun kann ein neues Projekt in IntelliJ angelegt werden. Für ein Projekt muss</p>
        <ul>
            <li>ein Name,</li>
            <li>ein passendes Workspace-Verzeichnis,</li>
            <li>die Sprache, in diesem Fall Java und</li>
            <li>das Build System gewählt werden.</li>
        </ul>
        <p><format color="%LinkColor%"><a href="https://maven.apache.org/">Maven</a></format> und
        <format color="%LinkColor%"><a href="https://gradle.org">Gradle</a></format> können ausgewählt werden, wenn
        bereits etwas Erfahrung gesammelt wurde, da das Projektverzeichnis bei diesen beiden im Vergleich zum Build
        System IntelliJ anders aufgebaut ist. Daher wird hier IntelliJ als Build System verwendet.</p>
        <p>Falls IntelliJ das erforderliche
        <tooltip term="JDK"><format color="%GlossaryLinkColor%">JDK</format></tooltip> nicht finden kann, muss das
        Verzeichnis manuell ausgewählt werden. Standardmäßig sollte unter Windows das
        <tooltip term="JDK"><format color="%GlossaryLinkColor%">JDK</format></tooltip> in
        <code>C:/Program Files/Eclipse Adoptium/&lt;package&gt;</code> installiert sein.</p>
        <p>Sind alle Einstellungen angepasst, kann rechts unten auf <code>Create</code> geklickt werden und IntelliJ
        erstellt das Projekt.</p>
        <p>Schließt das Fenster <code>Tip of the day</code> Klickt nun mit rechter Maustaste links im Projektverzeichnis
        auf den Ordner <ui-path>src | New | Java Class</ui-path>, gebt z.B. <code>Main</code> als Name für die Klasse
        ein und bestätigt mit <shortcut>Enter</shortcut>.</p>
        <p>Fügt die Code-Zeilen in der folgenden Art hinzu.</p>
        <code-block lang="java">
            public class Main {
                public static void main(String[] args) {
                    System.out.println("Hello World!");
                }
            }
        </code-block>
        <p>Betätigt nun den grünen Play-Button am oberen Fensterrand, was das Programm ausführt. Unterhalb von IntelliJ
        sollte sich jetzt die Konsole öffnen, in der unter anderem die folgende Zeile steht.</p>
        <code-block>Hello World!</code-block>
        <note>Herzlichen Glückwunsch. Ihr habt euer erstes Java-Programm geschrieben.</note>
        <h4 id="intellij-configuration">IntelliJ IDEA Konfiguration (optional)</h4>
        <tldr>
            <p>Settings: <shortcut key="$IntelliJSettings"></shortcut></p>
            <p>Alternativ: <ui-path>Main Menu | Settings</ui-path></p>
        </tldr>
        <p>Im Folgenden stehen einige Konfigurationen, welche ich selbst verwende und empfehlen kann.</p>
        <ul>
            <li>
                <p><ui-path>Settings | Appearance & Behavior | System Settings | Project | Reopen project on startup
                </ui-path> abwählen.</p>
                <p>Wird IntelliJ gestartet, öffnet sich immer zuerst die Ansicht aller zur Verfügung stehenden Projekte.
                </p>
            </li>
            <li>
                <p><ui-path>Settings | Appearance & Behavior | System Settings | Project | Open project in | Ask
                </ui-path> auswählen.</p>
                <p>Soll ein anderes Projekt geöffnet werden, wird nachgefragt, ob es im aktuellen Fenster oder einem
                neuen Fenster geöffnet werden soll.</p>
            </li>
            <li>
                <p><ui-path>Settings | Editor | General | Code Folding | Java | One-line methods</ui-path> abwählen.</p>
                <p>Zeigt Methoden mit einer Codezeile nicht mehr nur in einer Zeile an.</p>
            </li>
            <li>
                <p><ui-path>Settings | Editor | Code Style | Hard wrap at</ui-path> <code>80</code> oder
                <code>120</code> Zeichen.</p>
                <p>Stellt eine vertikale Linie als Orientierung für die horizontale Länge von Codezeilen dar.</p>
            </li>
        </ul>
    </tab>
    <tab id="visual-studio-code" title="Visual Studio Code">
        <p>Auch Visual Studio Code ist unter Windows, Linux und macOS verfügbar. VSC ist ein kostenloser
        Quelltext-Editor von <format color="%LinkColor%"><a href="https://www.microsoft.com">Microsoft</a></format> und
        keine <tooltip term="IDE"><format color="%GlossaryLinkColor%">IDE</format></tooltip>. Allerdings bietet VSC eine
        enorme Anzahl an zusätzlichen Extensions (Erweiterungen), mit denen VSC zu einer vollwertigen
        <tooltip term="IDE"><format color="%GlossaryLinkColor%">IDE</format></tooltip> aufgerüstet werden kann. VSC, als
        praktischer Allrounder, eignet sich für eine Vielzahl von Programmiersprachen und ist der am häufigste
        verwendete Editor in der Softwareentwicklung.</p>
        <note title="Download Visual Studio Code">
            <p>Der Link zum Download von Visual Studio Code ist
            <format color="%NoteLinkColor%"><a href="https://code.visualstudio.com">hier</a></format> zu finden.</p>
        </note>
        <h4 id="visual-studio-code-installation">Visual Studio Code Installation</h4>
        <tabs group="vsc-install">
            <tab id="vsc-install-windows" title="Windows">
                <ul>
                    <li>
                        <p><code>Aktion "Mit Code öffnen" dem Dateikontextmenü von Windows-Explorer hinzufügen</code>
                        <format color="%Highlight%">(optional, aber empfohlen)</format></p>
                    </li>
                    <li>
                        <p><code>Aktion "Mit Code öffnen" dem Verzeichniskontextmenü von Windows-Explorer hinzufügen
                        </code><format color="%Highlight%">(optional, aber empfohlen)</format></p>
                    </li>
                    <li>
                        <p><code>Code als Editor für unterstützte Dateitypen registrieren</code>
                        <format color="%Highlight%">(optional, aber empfohlen)</format></p>
                    </li>
                    <li>
                        <p><code>Zu PATH hinzufügen (nach dem Neustart verfügbar)</code>
                        <format color="%Highlight%">(obligatorisch)</format></p>
                    </li>
                </ul>
            </tab>
        </tabs>
    </tab>
    <tab id="eclipse-ide" title="Eclipse IDE">
        <p>Eine weitere <tooltip term="IDE"><format color="%GlossaryLinkColor%">IDE</format></tooltip> für die
        Entwicklung von Programmen ist Eclipse, welche zudem Open-Source von der
        <format color="%LinkColor%"><a href="https://www.eclipse.org">Eclipse Foundation</a></format> vertrieben wird
        und ebenfalls auf Windows, Linux und macOS installiert werden kann. Ursprünglich wurde Eclipse als
        <tooltip term="IDE"><format color="%GlossaryLinkColor%">IDE</format></tooltip> für Java genutzt. Mittlerweile
        unterstützt Eclipse auch andere Sprachen wie C, C++ oder PHP.</p>
        <note title="Download Eclipse IDE">
            <p>Der Link zum Download vom Eclipse Installer ist
            <format color="%NoteLinkColor%"><a href="https://www.eclipse.org">hier</a></format> zu finden.</p>
        </note>
        <h4 id="eclipse-ide-installation">Eclipse IDE Installation</h4>
        <tabs group="eclipse-install">
            <tab id="eclipse-install-windows" title="Windows">
                <ol>
                    <li>Eclipse Installer herunterladen.</li>
                    <li>Eclipse Installer ausführen.</li>
                    <li>
                        <p>Wählt <code>Eclipse IDE for Java Developers</code> zum Installieren.</p>
                        <img src="00_java_started_4.png" alt="" />
                    </li>
                    <li>
                        <p>Wählt anschließend das Installationsverzeichnis aus.</p>
                        <p>Wurde Java richtig installiert, sollte das <tooltip term="JDK">
                        <format color="%GlossaryLinkColor%">JDK</format></tooltip> bereits unter
                        <code>Java 21+ VM</code> angezeigt werden. Ansonsten muss der Pfad manuell gesetzt werden.</p>
                        <img src="00_java_started_5.png" alt=""/>
                    </li>
                    <li>
                        <p>Die Installation kann einige Minuten dauern. Wartet, bis diese fertig ist und klickt dann auf
                        <shortcut>LAUNCH</shortcut>.</p>
                        <img src="00_java_started_6.png" alt=""/>
                    </li>
                </ol>
            </tab>
        </tabs>
    </tab>
</tabs>
