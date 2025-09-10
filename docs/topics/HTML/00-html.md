# HTML
<primary-label ref="markup-lang"></primary-label>
<secondary-label ref="wip"></secondary-label>
<secondary-label ref="beta"></secondary-label>

## Was ist HTML? {id="what-is-html"}

<p>HTML (HyperText Markup Language) ist die Standard-Auszeichnungssprache, um Webseiten und Webanwendungen zu erstellen.
HTML strukturiert den Inhalt einer Webseite durch sogenannte
<format color="%LinkColor%"><a href="01-html-tags-and-elements.md">Tags</a></format>, die angeben, wie der Inhalt
dargestellt und strukturiert werden soll.</p>

<p>HTML hat seine Wurzeln in der Sprache
<format color="%LinkColor%"><a href="https://wiki.selfhtml.org/wiki/SGML">SGML</a></format> (Standard Generalized Markup
Language). SGML ist eine Metasprache, die im Wesentlichen eine Bauanleitung dafür darstellt, wie andere
Auszeichnungssprachen, die ähnliche Zwecke wie HTML verfolgen, entwickelt werden können.</p>

<p>Auf Basis von SGML sind in HTML bestimmte
<format color="%LinkColor%"><a href="01-html-tags-and-elements.md">Elemente</a></format>,
<format color="%LinkColor%"><a href="02-html-attributes-and-values.md">Attribute und Werte</a></format> definiert, die
den grundlegenden Sprachumfang von HTML bilden.</p>

## HTML vs. XML vs. XHTML {id="html-vs-xml-vs-xhtml"}

<list>
  <li>
    <p><format color="%Highlight%">HTML (HyperText Markup Language)</format> ist eine Sprache zur Strukturierung von
    Multimedia-Inhalten und unterteilt sich in mehrere Versionen von HTML 1 bis 5. Sie bietet einen lockeren Umgang der
    Syntaxregeln und besitzt eine festgelegte Zahl von HTML-Elementen, die bei Bedarf jedoch erweitert werden können.
    </p>
  </li>
  <li>
    <p><format color="%Highlight%">XML (Extensible Markup Language)</format> ist eine Sprache zur Strukturierung von
    Daten. Der sprachliche Umfang ist selbst definierbar und die Syntaxregeln werden strikter umgesetzt.</p>
  </li>
  <li>
    <p><format color="%Highlight%">XHTML (Extensible Hypertext Markup Language)</format> ist eine Sprache, die eine
    strengere und standardisierte Form von HTML darstellt. Sie wurde entwickelt, um die Prinzipien von HTML mit den
    Regeln von XML zu kombinieren.</p>
  </li>
</list>

## Was ist die DTD? {id="what-is-the-dtd"}

<p>Eine DTD (Document Type Definition) spielt für das Bilden des grundlegenden Sprachumfangs von HTML eine wichtige
Rolle, da sie genau festlegt, welche <format color="%LinkColor%"><a href="01-html-tags-and-elements.md">Elemente</a>
</format> es in HTML gibt, welche <format color="%LinkColor%"><a href="02-html-attributes-and-values.md">Attribute</a>
</format> diesen zugeordnet sind und welche <format color="%LinkColor%"><a href="02-html-attributes-and-values.md">Werte
</a></format> sie annehmen dürfen. Darüber hinaus beschreibt eine DTD präzise, welche Elemente an welchen Positionen
innerhalb eines HTML-Dokuments verwendet werden können und welche nicht.</p>

<p>DTDs sind jedoch für das grundlegende Verständnis von HTML nicht unmittelbar erforderlich. Möglicherweise wird es zu
einem späteren Zeitpunkt einen separaten Abschnitt dazu geben.</p>

<note>
    <p>Während es für HTML 4 noch ein DTD-Schema gab, wird für HTML 5 keins mehr benötigt. HTML 5 hat stattdessen eine
    einfache Doctype-Deklaration, die sicherstellt, dass der Browser das Dokument im Standard-Modus rendert, ohne die
    Komplexität von DTDs.</p>
    <compare first-title="HTML 4.01" second-title="HTML 5">
        <code-block>
            <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
        </code-block>
        <code-block>
            <!DOCTYPE html>
        </code-block>
    </compare>
</note>

## Was ist das DOM? {id="what-is-the-dom"}

<p>Das DOM (Document Object Model) ist eine Programmierschnittstelle, welche die Struktur eines HTML- oder XML-Dokuments
in einer baumartigen Form darstellt. Es ermöglicht Programmen auf das Dokument zuzugreifen, dessen Struktur und Inhalt
auszulesen und zu manipulieren.</p>