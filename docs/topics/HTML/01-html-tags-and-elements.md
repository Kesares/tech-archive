# 01 HTML – Tags und Elemente

Grundlegend besteht ein Element aus drei Teilen.
- Öffnungs-Tag
- Inhalt
- Schließungs-Tag

```html
<tag>Content</tag>
```

<table>
    <tr>
        <td width="30">Nr.</td>
        <td width="130">Tag</td>
        <td width="140">Ausschreibung</td>
        <td>Kategorien</td>
        <td>Beschreibung</td>
    </tr>
    <tr>
        <td>1</td>
        <td><code>&lt;a&gt;</code></td>
        <td>hyperlink</td>
        <td>Link- und Navigations-Tags</td>
        <td>Definiert einen Hyperlink.</td>
    </tr>
    <tr>
        <td>2</td>
        <td><code>&lt;abbr&gt;</code></td>
        <td>abbreviation</td>
        <td>Semantische Tags</td>
        <td>Kennzeichnet Abkürzungen oder Akronyme.</td>
    </tr>
    <tr>
        <td>3</td>
        <td><code>&lt;address&gt;</code></td>
        <td>address</td>
        <td>
            <p>Strukturierende Tags</p>
            <p>Semantische Tags</p>
        </td>
        <td>Kennzeichnet Kontaktinformationen für den Autor eines Dokuments oder einen Abschnitt davon.</td>
    </tr>
    <tr>
        <td>4</td>
        <td><code>&lt;area&gt;</code></td>
        <td>area</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>5</td>
        <td><code>&lt;article&gt;</code></td>
        <td>article</td>
        <td>
            <p>Strukturierende Tags</p>
            <p>Semantische Tags</p>
        </td>
        <td>Semantischer Container, der verschiedene Arten von Inhalten strukturiert.</td>
    </tr>
    <tr>
        <td>6</td>
        <td><code>&lt;aside&gt;</code></td>
        <td>aside</td>
        <td>
            <p>Strukturierende Tags</p>
            <p>Semantische Tags</p>
        </td>
        <td>Semantischer Container, der verschiedene Arten von Inhalten strukturiert.</td>
    </tr>
    <tr>
        <td>7</td>
        <td><code>&lt;audio&gt;</code></td>
        <td>audio</td>
        <td>Multimedia-Tags</td>
        <td>Bindet eine Audiodatei ein.</td>
    </tr>
    <tr>
        <td>8</td>
        <td><code>&lt;b&gt;</code></td>
        <td>bold</td>
        <td>Textformatierungstags</td>
        <td>Definiert fetten Text.</td>
    </tr>
    <tr>
        <td>9</td>
        <td><code>&lt;base&gt;</code></td>
        <td>base</td>
        <td>Textformatierungstags</td>
        <td>Definiert fetten Text.</td>
    </tr>
    <tr>
        <td>10</td>
        <td><code>&lt;bdi&gt;</code></td>
        <td>bidirectional isolate</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>11</td>
        <td><code>&lt;bdo&gt;</code></td>
        <td>bidirectional override</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>12</td>
        <td><code>&lt;blockquote&gt;</code></td>
        <td>blockquote</td>
        <td>Textformatierungstags</td>
        <td>Für blockweise Zitate.</td>
    </tr>
    <tr>
        <td>13</td>
        <td><code>&lt;body&gt;</code></td>
        <td>body</td>
        <td>Strukturierende Tags</td>
        <td>Enthält den sichtbaren Inhalt der Webseite.</td>
    </tr>
    <tr>
        <td>14</td>
        <td><code>&lt;br&gt;</code></td>
        <td>break</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>15</td>
        <td><code>&lt;button&gt;</code></td>
        <td>button</td>
        <td>Formulareingabetags</td>
        <td>Definiert eine Schaltfläche.</td>
    </tr>
    <tr>
        <td>16</td>
        <td><code>&lt;canvas&gt;</code></td>
        <td>canvas</td>
        <td>Multimedia-Tags</td>
        <td>Ermöglicht das Zeichnen von Grafiken mittels Scripting (z.B. JavaScript).</td>
    </tr>
    <tr>
        <td>17</td>
        <td><code>&lt;caption&gt;</code></td>
        <td>caption</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>18</td>
        <td><code>&lt;cite&gt;</code></td>
        <td>cite</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>19</td>
        <td><code>&lt;code&gt;</code></td>
        <td>code</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>20</td>
        <td><code>&lt;col&gt;</code></td>
        <td>column</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>21</td>
        <td><code>&lt;colgroup&gt;</code></td>
        <td>column group</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>22</td>
        <td><code>&lt;data&gt;</code></td>
        <td>data</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>23</td>
        <td><code>&lt;datalist&gt;</code></td>
        <td>data list</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>24</td>
        <td><code>&lt;dd&gt;</code></td>
        <td>description details</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>25</td>
        <td><code>&lt;del&gt;</code></td>
        <td>deleted</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>26</td>
        <td><code>&lt;details&gt;</code></td>
        <td>details</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>27</td>
        <td><code>&lt;dfn&gt;</code></td>
        <td>definition</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>28</td>
        <td><code>&lt;dialog&gt;</code></td>
        <td>dialog</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>29</td>
        <td><code>&lt;div&gt;</code></td>
        <td>division element</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>30</td>
        <td><code>&lt;dl&gt;</code></td>
        <td>description list</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>31</td>
        <td><code>&lt;dt&gt;</code></td>
        <td>description term</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>32</td>
        <td><code>&lt;em&gt;</code></td>
        <td>emphasis</td>
        <td>
            <p>Textformatierungstags</p>
            <p>Semantische Tags</p>
        </td>
        <td>...</td>
    </tr>
    <tr>
        <td>33</td>
        <td><code>&lt;embed&gt;</code></td>
        <td>embed</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>34</td>
        <td><code>&lt;fieldset&gt;</code></td>
        <td>fieldset</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>35</td>
        <td><code>&lt;figcaption&gt;</code></td>
        <td>figure caption</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>36</td>
        <td><code>&lt;figure&gt;</code></td>
        <td>figure</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>37</td>
        <td><code>&lt;footer&gt;</code></td>
        <td>footer</td>
        <td>Strukturierende Tags</td>
        <td>Definiert den Fußbereich einer Seite oder eines Abschnitts.</td>
    </tr>
    <tr>
        <td>38</td>
        <td><code>&lt;form&gt;</code></td>
        <td>form</td>
        <td>Formulareingabetags</td>
        <td>Definiert ein Formular.</td>
    </tr>
    <tr>
        <td>39</td>
        <td><code>&lt;h1&gt;</code> bis <code>&lt;h6&gt;</code></td>
        <td>heading</td>
        <td>Textformatierungstags</td>
        <td>Definiert Überschriften von groß <code>&lt;h1&gt;</code> bis klein <code>&lt;h6&gt;</code>.</td>
    </tr>
    <tr>
        <td>40</td>
        <td><code>&lt;head&gt;</code></td>
        <td>head</td>
        <td>Strukturierende Tags</td>
        <td>Enthält Metainformationen und Links zu Stylesheets, Skripten etc.</td>
    </tr>
    <tr>
        <td>41</td>
        <td><code>&lt;header&gt;</code></td>
        <td>header</td>
        <td>Strukturierende Tags</td>
        <td>Definiert den Kopfbereich einer Seite oder eines Abschnitts.</td>
    </tr>
    <tr>
        <td>42</td>
        <td><code>&lt;hgroup&gt;</code></td>
        <td>heading group</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>43</td>
        <td><code>&lt;hr&gt;</code></td>
        <td>horizontal rule</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>44</td>
        <td><code>&lt;html&gt;</code></td>
        <td>hypertext markup language</td>
        <td>Strukturierende Tags</td>
        <td>Das Wurzelelement des HTML-Dokuments.</td>
    </tr>
    <tr>
        <td>45</td>
        <td><code>&lt;i&gt;</code></td>
        <td>italic</td>
        <td>Textformatierungstags</td>
        <td>Definiert kursiven Text.</td>
    </tr>
    <tr>
        <td>46</td>
        <td><code>&lt;iframe&gt;</code></td>
        <td>inline frame</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>47</td>
        <td><code>&lt;img&gt;</code></td>
        <td>image</td>
        <td>Multimedia-Tags</td>
        <td>Bindet eine Bild ein.</td>
    </tr>
    <tr>
        <td>48</td>
        <td><code>&lt;input&gt;</code></td>
        <td>input</td>
        <td>Formulareingabetags</td>
        <td>Definiert ein Eingabefeld.</td>
    </tr>
    <tr>
        <td>49</td>
        <td><code>&lt;ins&gt;</code></td>
        <td>insert text</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>50</td>
        <td><code>&lt;kbd&gt;</code></td>
        <td>keyboard</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>51</td>
        <td><code>&lt;label&gt;</code></td>
        <td>label</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>52</td>
        <td><code>&lt;legend&gt;</code></td>
        <td>legend</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>53</td>
        <td><code>&lt;li&gt;</code></td>
        <td>list item</td>
        <td>Listen-Tags</td>
        <td>Definiert ein Listenelement.</td>
    </tr>
    <tr>
        <td>54</td>
        <td><code>&lt;link&gt;</code></td>
        <td>link</td>
        <td>
            <p>Metadaten-Tags</p>
            <p>Skript- und Stil-Tags</p>
        </td>
        <td>Verknüpft das Dokument mit externen Ressourcen (z.B. CSS).</td>
    </tr>
    <tr>
        <td>55</td>
        <td><code>&lt;main&gt;</code></td>
        <td>main</td>
        <td>Strukturierende Tags</td>
        <td>Definiert den Hauptinhalt einer Webseite.</td>
    </tr>
    <tr>
        <td>56</td>
        <td><code>&lt;map&gt;</code></td>
        <td>map</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>57</td>
        <td><code>&lt;mark&gt;</code></td>
        <td>mark</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>58</td>
        <td><code>&lt;math&gt;</code></td>
        <td>math</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>59</td>
        <td><code>&lt;menu&gt;</code></td>
        <td>menu</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>60</td>
        <td><code>&lt;meta&gt;</code></td>
        <td>meta</td>
        <td>Metadaten-Tags</td>
        <td>Definiert Metadaten.</td>
    </tr>
    <tr>
        <td>61</td>
        <td><code>&lt;meter&gt;</code></td>
        <td>meter</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>62</td>
        <td><code>&lt;nav&gt;</code></td>
        <td>navigation</td>
        <td>
            <p>Strukturierende Tags</p>
            <p>Semantische Tags</p>
        </td>
        <td>Semantischer Container, der eine Gruppe von Navigationslinks definiert.</td>
    </tr>
    <tr>
        <td>63</td>
        <td><code>&lt;noscript&gt;</code></td>
        <td>no script</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>64</td>
        <td><code>&lt;object&gt;</code></td>
        <td>object</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>65</td>
        <td><code>&lt;ol&gt;</code></td>
        <td>ordered list</td>
        <td>Listen-Tags</td>
        <td>Definiert eine geordnete Liste.</td>
    </tr>
    <tr>
        <td>66</td>
        <td><code>&lt;optgroup&gt;</code></td>
        <td>options group</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>67</td>
        <td><code>&lt;option&gt;</code></td>
        <td>option</td>
        <td>Formulareingabetags</td>
        <td>Definiert ein Dropdown-Menü.</td>
    </tr>
    <tr>
        <td>68</td>
        <td><code>&lt;output&gt;</code></td>
        <td>output</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>69</td>
        <td><code>&lt;p&gt;</code></td>
        <td>paragraph</td>
        <td>Textformatierungstags</td>
        <td>Definiert einen Absatz.</td>
    </tr>
    <tr>
        <td>70</td>
        <td><code>&lt;param&gt;</code></td>
        <td>parameter</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>71</td>
        <td><code>&lt;picture&gt;</code></td>
        <td>picture</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>72</td>
        <td><code>&lt;pre&gt;</code></td>
        <td>preformatted text</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>73</td>
        <td><code>&lt;progress&gt;</code></td>
        <td>progress</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>74</td>
        <td><code>&lt;q&gt;</code></td>
        <td>quotation</td>
        <td>Textformatierungstags</td>
        <td>Für Zitate.</td>
    </tr>
    <tr>
        <td>75</td>
        <td><code>&lt;rp&gt;</code></td>
        <td>ruby parentheses</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>76</td>
        <td><code>&lt;rt&gt;</code></td>
        <td>ruby text</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>77</td>
        <td><code>&lt;ruby&gt;</code></td>
        <td>ruby</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>78</td>
        <td><code>&lt;s&gt;</code></td>
        <td>strikethrough</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>79</td>
        <td><code>&lt;samp&gt;</code></td>
        <td>sample</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>80</td>
        <td><code>&lt;script&gt;</code></td>
        <td>script</td>
        <td>Skript- und Stil-Tags</td>
        <td>Bindet JavaScript-Code ein.</td>
    </tr>
    <tr>
        <td>81</td>
        <td><code>&lt;search&gt;</code></td>
        <td>search</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>82</td>
        <td><code>&lt;section&gt;</code></td>
        <td>section</td>
        <td>
            <p>Strukturierende Tags</p>
            <p>Semantische Tags</p>
        </td>
        <td>Semantischer Container, der verschiedene Arten von Inhalten strukturiert.</td>
    </tr>
    <tr>
        <td>83</td>
        <td><code>&lt;select&gt;</code></td>
        <td>select</td>
        <td>Formulareingabetags</td>
        <td>Definiert ein Dropdown-Menü.</td>
    </tr>
    <tr>
        <td>84</td>
        <td><code>&lt;slot&gt;</code></td>
        <td>slot</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>85</td>
        <td><code>&lt;small&gt;</code></td>
        <td>small</td>
        <td>Textformatierungstags</td>
        <td>Definiert kleineren Text.</td>
    </tr>
    <tr>
        <td>86</td>
        <td><code>&lt;source&gt;</code></td>
        <td>source</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>87</td>
        <td><code>&lt;span&gt;</code></td>
        <td>span</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>88</td>
        <td><code>&lt;strong&gt;</code></td>
        <td>strong</td>
        <td>
            <p>Textformatierungstags</p>
            <p>Semantische Tags</p>
        </td>
        <td>Definiert fetten Text.</td>
    </tr>
    <tr>
        <td>89</td>
        <td><code>&lt;style&gt;</code></td>
        <td>style</td>
        <td>Skript- und Stil-Tags</td>
        <td>Definiert eingebettete CSS-Styles.</td>
    </tr>
    <tr>
        <td>90</td>
        <td><code>&lt;sub&gt;</code></td>
        <td>subscript</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>91</td>
        <td><code>&lt;summary&gt;</code></td>
        <td>summary</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>92</td>
        <td><code>&lt;sup&gt;</code></td>
        <td>superscript </td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>93</td>
        <td><code>&lt;svg&gt;</code></td>
        <td>scalable vector graphic</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>94</td>
        <td><code>&lt;table&gt;</code></td>
        <td>table</td>
        <td>Tabellen-Tags</td>
        <td>Definiert eine Tabelle.</td>
    </tr>
    <tr>
        <td>95</td>
        <td><code>&lt;tbody&gt;</code></td>
        <td>table body</td>
        <td>Tabellen-Tags</td>
        <td>Strukturiert den Körper einer Tabelle.</td>
    </tr>
    <tr>
        <td>96</td>
        <td><code>&lt;td&gt;</code></td>
        <td>table data</td>
        <td>Tabellen-Tags</td>
        <td>Definiert eine Tabellenzelle.</td>
    </tr>
    <tr>
        <td>97</td>
        <td><code>&lt;template&gt;</code></td>
        <td>template</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>98</td>
        <td><code>&lt;textarea&gt;</code></td>
        <td>textarea</td>
        <td>Formulareingabetags</td>
        <td>Definiert ein mehrzeiliges Eingabefeld.</td>
    </tr>
    <tr>
        <td>99</td>
        <td><code>&lt;tfoot&gt;</code></td>
        <td>table footer</td>
        <td>Tabellen-Tags</td>
        <td>Strukturiert den Fußbereich einer Tabelle.</td>
    </tr>
    <tr>
        <td>100</td>
        <td><code>&lt;th&gt;</code></td>
        <td>table header</td>
        <td>Tabellen-Tags</td>
        <td>Definiert eine Tabellenkopfzelle.</td>
    </tr>
    <tr>
        <td>101</td>
        <td><code>&lt;thead&gt;</code></td>
        <td>table head</td>
        <td>Tabellen-Tags</td>
        <td>Strukturiert den Kopfbereich einer Tabelle.</td>
    </tr>
    <tr>
        <td>102</td>
        <td><code>&lt;time&gt;</code></td>
        <td>time</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>103</td>
        <td><code>&lt;title&gt;</code></td>
        <td>title</td>
        <td>Metadaten-Tags</td>
        <td>Definiert den Titel des Dokuments.</td>
    </tr>
    <tr>
        <td>104</td>
        <td><code>&lt;tr&gt;</code></td>
        <td>table row</td>
        <td>Tabellen-Tags</td>
        <td>Definiert eine Tabellenzeile.</td>
    </tr>
    <tr>
        <td>105</td>
        <td><code>&lt;track&gt;</code></td>
        <td>track</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>106</td>
        <td><code>&lt;u&gt;</code></td>
        <td>underline</td>
        <td>Textformatierungstags</td>
        <td>Definiert unterstrichenen Text.</td>
    </tr>
    <tr>
        <td>107</td>
        <td><code>&lt;ul&gt;</code></td>
        <td>unordered list</td>
        <td>Listen-Tags</td>
        <td>Definiert eine ungeordnete Liste.</td>
    </tr>
    <tr>
        <td>108</td>
        <td><code>&lt;var&gt;</code></td>
        <td>variable</td>
        <td>...</td>
        <td>...</td>
    </tr>
    <tr>
        <td>109</td>
        <td><code>&lt;video&gt;</code></td>
        <td>video</td>
        <td>Multimedia-Tags</td>
        <td>Bindet eine Videodatei ein.</td>
    </tr>
    <tr>
        <td>110</td>
        <td><code>&lt;wbr&gt;</code></td>
        <td>word break</td>
        <td>...</td>
        <td>...</td>
    </tr>
</table>

## Veraltete Elemente {id="deprecated-elements"}
## Semantische Elemente {id="semantic-elements"}
## Neutrale Elemente {id="neutral-elements"}
## Leere Elemente {id="self-closing-tags"}
## Elementstrukturen