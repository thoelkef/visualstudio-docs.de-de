---
title: Microsoft Help Viewer SDK | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 721623edabcaf3b395a143dd193cae3fd71d93d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707154"
---
# <a name="microsoft-help-viewer-sdk"></a>Microsoft Help Viewer SDK

Dieser Artikel enthält die folgenden Aufgaben für Visual Studio Help Viewer-Integratoren:

- Erstellen eines Themas (F1-Unterstützung)

- Erstellen eines Help Viewer-Inhaltsbrandingpakets

- Bereitstellen einer Reihe von Artikeln

- Hinzufügen von Hilfe zur Visual Studio-Shell (integriert oder isoliert)

- Weitere Ressourcen

## <a name="create-a-topic-f1-support"></a>Erstellen eines Themas (F1-Unterstützung)

Dieser Abschnitt bietet einen Überblick über die Komponenten eines vorgestellten Themas, Themenanforderungen, eine kurze Beschreibung zum Erstellen eines Themas (einschließlich F1-Supportanforderungen) und schließlich ein Beispielthema mit dem gerenderten Ergebnis.

**Übersicht über Help Viewer Topic**

Wenn ein Thema zum Rendern aufgerufen wird, ruft der Help Viewer die Brandingpaketelemente ab, die dem Thema zum Zeitpunkt der Installation oder letzten Aktualisierung zugeordnet sind, zusammen mit dem Thema XHTML, und kombiniert die beiden, um die angezeigte Inhaltsansicht (Brandingdaten + Themendaten) zu ergeben.  Das Branding-Paket enthält Logos, Unterstützung für Content-Verhalten und Branding-Text (Urheberrecht usw.).  Weitere Informationen zu den Brandingpaketelementen finden Sie unter "Branding-Paket erstellen".  Für den Fall, dass dem Thema kein Brandingpaket zugeordnet ist, verwendet der Help Viewer das Fallback-Brandingpaket im Help Viewer-Anwendungsstamm (Branding_en-US.mshc).

**Help Viewer-Themenanforderungen**

Um im Hilfe-Viewer korrekt gerendert zu werden, muss der unformatierte Themeninhalt W3C Basic 1.1 XHTML sein.

Ein Thema enthält in der Regel zwei Abschnitte:

- Metadaten (siehe Inhaltsmetadatenreferenz): Daten zum Thema, z. B. die eindeutige Id des Themas, den Schlüsselwortwert, das Thema TOC-ID, die übergeordnete Knoten-ID usw.

- Body-Inhalt: kompatibel mit W3C Basic 1.1 XHTML, das unterstützte Inhaltsverhalten (zusammenklappbarer Bereich, Codeausschnitt usw.) enthält. Eine vollständige Liste finden Sie weiter unten).

Visual Studio Branding Package unterstützte Steuerelemente:

- Links

- CodeSnippet

- CollapsibleArea

- Vererbtes Mitglied

- LanguageSpecificText

Unterstützte Sprachzeichenfolgen (ohne Groß-/Kleinschreibung):

- javascript

- csharp oder c #

- cplusplus oder visualc++ oder c++

- jscript

- visualbasic oder vb

- f- oder fsharp oder fs

- Andere - eine Zeichenfolge, die einen Sprachnamen darstellt

**Erstellen eines Help Viewer-Themas**

Erstellen Sie ein neues XHTML-Dokument mit dem Namen ContosoTopic4.htm, und schließen Sie das Titel-Tag (unten) ein.

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

Fügen Sie als Nächstes Daten hinzu, um zu definieren, wie das Thema dargestellt werden soll (selbst gebrandet oder nicht), wie dieses Thema für F1 referenziert werden soll, wo dieses Thema innerhalb des ToC vorhanden ist, seine ID (für Linkverweise durch andere Themen) usw. Eine vollständige Liste der unterstützten Metadaten finden Sie in der Tabelle "Inhaltsmetadaten" weiter unten.

- In diesem Fall verwenden wir unser eigenes Branding-Paket, eine Variante des Visual Studio Help Viewer-Brandingpakets.

- Fügen Sie den F1-Metanamen und -Wert ("Microsoft.Help.F1" content=" ContosoTopic4") hinzu, der dem angegebenen F1-Wert in der IDE-Eigenschaftstasche entspricht. (Weitere Informationen finden Sie im Abschnitt F1-Support.) Dies ist der Wert, der dem F1-Aufruf aus der IDE abgeglichen wird, um dieses Thema anzuzeigen, wenn F1 in der IDE ausgewählt wird.

- Fügen Sie die Themen-ID hinzu. Dies ist die Zeichenfolge, die von anderen Themen verwendet wird, um eine Verknüpfung zu diesem Thema herzustellen. Es ist die Help Viewer-ID für dieses Thema.

- Fügen Sie für das ToC den übergeordneten Knoten dieses Themas hinzu, um zu definieren, wo dieser ToC-Knoten des Themas angezeigt wird.

- Fügen Sie für das Arbeitshäktor die Knotenreihenfolge dieses Themas hinzu. Wenn der übergeordnete `n` Knoten über die Anzahl der untergeordneten Knoten verfügt, definieren Sie in der Reihenfolge der untergeordneten Knoten den Speicherort dieses Themas. Dieses Thema ist z. B. Nummer 4 von 4 untergeordneten Themen.

Beispielmetadatenabschnitt:

```html
<html>
<head>
<title>Contoso Topic 4</title>

<meta name="SelfBranded" content="false" />
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />
    <meta name="Language" content="en-us" />
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />
<meta name="Microsoft.Help.TocOrder" content="4" />

</head>

<body>

</body>
</html>
```

**The Topic Body**

Der Textkörper (ohne Kopf- und Fußzeile) des Themas enthält Seitenlinks, einen Notizabschnitt, einen zusammenklappbaren Bereich, einen Codeausschnitt und einen Abschnitt mit sprachspezifischem Text.  Weitere Informationen zu den Bereichen des vorgestellten Themas finden Sie im Branding-Abschnitt.

1. Hinzufügen eines Thementitel-Tags:`<div class="title">Contoso Topic 4</div>`

2. Fügen Sie einen Notizabschnitt hinzu:`<div class="alert"> add your table tag and text </div>`

3. Fügen Sie einen zusammenklappbaren Bereich hinzu:`<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4. Hinzufügen eines Codeausschnitts:`<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5. Codesprachtext hinzufügen: `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` Hinweis, `devLangnu=` mit dem Sie andere Sprachen eingeben können. Zeigt z. B. Fortran an, `devLangnu="Fortran"` wenn der Codeausschnitt DisplayLanguage = Fortran

6. Seitenlinks hinzufügen:`<a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
> Hinweis: Für nicht unterstützte neue "Display Language" (z. B. F, Cobol, Fortran) ist die Codefärbung im Codeausschnitt monochrom.

**Beispiel-Help Viewer-Thema** Der Code veranschaulicht, wie Metadaten, ein Codeausschnitt, ein zusammenklappbarer Bereich und sprachspezifischer Text definiert werden.

```html
<?xml version="1.0" encoding="utf-8"?>
<html>
<head>
<title>Contoso Topic 4</title>

    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <meta name="Microsoft.Help.Id" content="ContosoTopic4" />
<meta name="Microsoft.Help.F1" content=" ContosoTopic4" />
    <meta name="Language" content="en-us" />
<meta name="Microsoft.Help.TocParent" content="ContosoTopic0" />
<meta name="Microsoft.Help.TocOrder" content="4" />
<meta name="SelfBranded" content="false" />
</head>

<body>
<div class="title">Contoso Topic 4</div>

  <div id="header">
<table id="bottomTable" cellpadding="0" cellspacing="0"  width="100%">
        <tr id="headerTableRow2"><td align="left">
            <span id="nsrTitle">Contoso Topic 1</span>
          </td>
<td align="right">
</td></tr>
<tr id="headerTableRow1"><td align="left">
            <span id="runningHeaderText">Contoso Widgets & Sprockets</span>
          </td></tr>
      </table>
</div>

<h2>Table of Contents</h2>

<ul class="toc">
<li class="tocline1"><a href="#introduction" target="_self">1.0 Introduction</a></li>
<li class="tocline1"><a href="#seealso" target="_self">See Also</a></li>
</ul>

<div class="topic">

<div id="mainSection">
<div id="mainBody">

<a name="introduction"></a>
<h2>1.0 Introduction</h2>
<p>[This documentation is for sample purposes only.]</p>

<p>Contoso Topic 1 contains examples of:
<ul>
<li>Collapsible Area</li>
<li>Bookmark ("See also")</li>
<li>Code Snippets from Branding Package</li>
</ul>
 </p>
<div class="alert"><table><tr><th>
<strong>Note </strong></th></tr>
<tr><td>
<p>This is an example of a <span class="label">Note </span>section.
Call out important items for your reader in this <span class="label">Note </span>box.
</p></td></tr>
</table>
</div>
</div>

<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading">

            <a id="sectionToggle0"><!----></a>

<div>
Example of Collapsible Area
<br/>
Lorem ipsum dolor sit amet...
</div>
</CollapsibleArea>

<div id="snippetGroup" >
<CodeSnippet EnableCopyCode="true" Language="VisualBasic" ContainsMarkup="false" DisplayLanguage="Visual Basic" >
Private Sub ToolStripRenderer1_RenderGrip(sender as Object, e as ToolStripGripRenderEventArgs) _ Handles ToolStripRenderer1.RenderGrip
Dim messageBoxVB as New System.Text.StringBuilder()
    messageBoxVB.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds)
    messageBoxVB.AppendLine()
 ...
    MessageBox.Show(messageBoxVB.ToString(),"RenderGrip Event")
End Sub
</CodeSnippet>

<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" >
private void ToolStripRenderer1_RenderGrip(Object sender, ToolStripGripRenderEventArgs e)
{
System.Text.StringBuilder messageBoxCS = new System.Text.StringBuilder();
messageBoxCS.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds );
messageBoxCS.AppendLine();
...
MessageBox.Show(messageBoxCS.ToString(), "RenderGrip Event" );
}
</CodeSnippet>

<CodeSnippet EnableCopyCode="true" Language="fsharp" ContainsMarkup="false" DisplayLanguage="F#" >
some F# code
</CodeSnippet>
</div>

<h4 class="subHeading">Example of code specific text</h4>Language = <LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />

<a name="seealso"></a>
<h1 class="heading">See Also</h1>

    <div id="seeAlsoSection" class="section">
    <div class="seeAlsoStyle">
        <a href="ms-xhelp:///?Id=ContosoTopic1">Main Topic</a>
    </div>
 </div>
</div>
</div>
</body>
</html>
```

**F1-Unterstützung**

In Visual Studio generiert die Auswahl von F1 Werte, die aus der Platzierung des Cursors innerhalb der IDE bereitgestellt werden, und füllt einen "Eigenschaftsbeutel" mit den angegebenen Werten (basierend auf der Cursorposition). Wenn der Cursor über Feature x ist, ist Feature x aktiv/im Fokus und füllt den Eigenschaftenbeutel mit Werten auf.  Wenn F1 ausgewählt ist, wird der Eigenschaftenbeutel aufgefüllt, und Visual Studio F1-Code sucht nach lokalen oder onlineen Informationen für die standardmäßige Hilfequelle der Kunden (Online ist die Standardeinstellung), und erstellt die entsprechende Zeichenfolge basierend auf der Benutzereinstellung (online ist die Standardeinstellung) - Shellausführung (siehe Hilfe-Administratorhandbuch für Exe-Startparameter) mit Parametern für den lokalen Hilfebetrachter + Schlüsselwörter aus der Eigenschaftentasche, wenn die lokale Hilfe die Standardeinstellung ist. , oder die MSDN-URL mit dem Schlüsselwort in der Parameterliste.

Wenn drei Zeichenfolgen für F1 zurückgegeben werden, die als Zeichenfolge mit mehreren Werten bezeichnet werden, nehmen Sie den ersten Begriff, suchen Sie nach einem Treffer, und wenn gefunden, sind wir fertig. Wenn nicht, wechseln Sie zur nächsten Zeichenfolge.  Ordnung zählt. Die Darstellung der Mehrwertschlüsselwörter sollte die längste Zeichenfolge bis zur kürzesten Zeichenfolge sein.  Um dies bei Mehrwertschlüsselwörtern zu überprüfen, sehen Sie sich die Online-URL-Zeichenfolge F1 an, die das ausgewählte Schlüsselwort enthält.

In Visual Studio 2012 haben wir absichtlich eine stärkere Trennung zwischen Online und Offline hergestellt, sodass wir, wenn die Einstellung des Benutzers für Online war, die F1-Anforderung einfach direkt an unseren Onlineabfragedienst auf MSDN weitergeleitet haben, anstatt über den Hilfebibliotheks-Agent zu routing, den wir in Visual Studio 2010 hatten. Wir verlassen uns dann auf den Status "Vendor content installed = true", um zu bestimmen, ob in diesem Kontext etwas anderes zu tun ist. Wenn true, führen wir diese Analyse- und Routinglogik in Abhängigkeit davon aus, was Sie für Ihre Kunden unterstützen möchten. Wenn falsch, dann gehen wir einfach zu MSDN. Wenn die Einstellung des Benutzers auf Lokal ist, gehen alle Anrufe an das lokale Hilfemodul.

F1 Strömungsdiagramm:

![F1-Fluss](../../extensibility/internals/media/f1flow.png "F1flow")

Wenn die Standardmäßige Hilfeinhaltsquelle für die Hilfe auf online festgelegt ist (Start im Browser):

- Visual Studio Partner (VSP)-Features geben einen Wert für die F1-Eigenschaftstasche aus (Eigenschaftbag prefix.keyword und Online-URL für das präfix in der Registrierung gefunden): F1 sendet eine VSP-URL+-Parameter an den Browser.

- Visual Studio-Funktionen (Spracheditor, Visual Studio-spezifische Menüelemente usw.): F1 sendet eine Visual Studio-URL an den Browser.

Wenn die standardmäßige Hilfeinhaltsquelle der Hilfe auf lokale Hilfe festgelegt ist (Start in Help Viewer):

- VSP-Features, bei denen das Schlüsselwort zwischen F1-Eigenschaftsbeutel und lokalem Speicherindex übereinstimmt (d. h. das Eigenschaftenbeutelpräfix.keyword = der Wert, der im lokalen Speicherindex gefunden wird): F1 rendert das Thema in der Hilfeanzeige.

- Visual Studio-Features (keine Option für den VSP zum Überschreiben der von Visual Studio-Features emittierten Eigenschaftentasche): F1 rendert ein Visual Studio-Thema im Hilfe-Viewer.

Legen Sie die folgenden Registrierungswerte fest, um F1 Fallback für Kreditorenhilfeinhalte zu aktivieren. F1 Fallback bedeutet, dass der Hilfe-Viewer online nach F1-Hilfeinhalten suchen und der Herstellerinhalt lokal auf der Festplatte der Benutzer installiert wird. Der Hilfe-Viewer sollte sich die lokale Hilfe für den Inhalt ansehen, auch wenn die Standardeinstellung für die Onlinehilfe gilt.

1. Legen Sie den **VendorContent-Wert** unter dem Registrierungsschlüssel Help 2.3 fest:

   - Für 32-Bit-Betriebssysteme:

        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent"=dword:00000001

   - Für 64-Bit-Betriebssysteme:

        HKEY_LOCAL_MACHINE-SOFTWARE-Wow6432-Knoten-Microsoft-Hilfe, V2.3-Kataloge, VisualStudio15

        "VendorContent"=dword:00000001

2. Registrieren Sie den Partnernamespace unter dem Registrierungsschlüssel Help 2.3:

   - Für 32-Bit-Betriebssysteme:

      HKEY_LOCAL_MACHINE-SOFTWARE-,Microsoft-Hilfe-Hilfe-<em> \\<-Namespace\></em>

      "location"="offline"

   - Für 64-Bit-Betriebssysteme:

      HKEY_LOCAL_MACHINE-SOFTWARE-Wow6432-Knoten-Microsoft-Hilfe,<em> \\<-Namespace\></em>

      "location"="offline"

**Basis-Native Namespace-Analyse**

Um die systemeigene Namespaceanalyse der Basis zu aktivieren, fügen Sie in der Registrierung ein neues DWORD mit dem Namen BaseNativeNamespaces hinzu, und legen Sie den Wert auf 1 fest (unter dem Katalogschlüssel, den sie unterstützen möchten).  Wenn Sie z. B. den Visual Studio-Katalog verwenden möchten, können Sie den Schlüssel zum Pfad hinzufügen:

HKEY_LOCAL_MACHINE-SOFTWARE-Wow6432-Knoten-Microsoft-Hilfe, V2.3-Kataloge, VisualStudio15

Wenn ein F1-Schlüsselwort im Format HEADER/METHOD gefunden wird, wird das Zeichen '/' analysiert, was zu folgendem Konstrukt führt:

- HEADER: ist der Namespace, der zur Registrierung in der Registrierung verwendet werden kann

- METHODE: Dies wird das Schlüsselwort, das durchgereicht wird.

Wenn z. B. eine benutzerdefinierte Bibliothek namens CustomLibrary und eine Methode namens MyTestMethod `CustomLibrary/MyTestMethod`vorhanden sind, wird sie als formatiert.

Ein Benutzer kann CustomLibrary dann als Namespace unter der Partnerstruktur registrieren und den gewünschten Standortschlüssel angeben, und das Schlüsselwort, das an die Abfrage übergeben wird, ist MyTestMethod.

**Aktivieren des Hilfe-Debugging-Tools in der IDE**

Fügen Sie den folgenden Registrierungsschlüssel und -wert hinzu:

::: moniker range="vs-2017"

**HKEY_CURRENT_USER-Software-Microsoft-VisualStudio-Hilfe 15,0, Dynamische Hilfe**

::: moniker-end

::: moniker range=">=vs-2019"

**HKEY_CURRENT_USER-Software-Hilfe für Microsoft-VisualStudio-16,0-Dynamische Hilfe**

::: moniker-end

Wert: Debugausgabe in Einzelhandelsdaten anzeigen: JA

Wählen Sie in der IDE unter dem Menüpunkt Hilfe die Option **Hilfekontext debuggen**aus.

**Inhaltsmetadaten**

In der folgenden Tabelle ist jede Zeichenfolge, die zwischen Klammern angezeigt wird, ein Platzhalter, der durch einen erkannten Wert ersetzt werden muss. Beispielsweise muss \<in meta name="Microsoft.Help.Locale" content="[sprachcode]" /> "[Sprachcode]" durch einen Wert wie "en-us" ersetzt werden.

| Eigenschaft (HTML-Darstellung) | BESCHREIBUNG |
| - | - |
| \<meta name="Microsoft.Help.Locale" content="[sprachcode]" /> | Legt ein Gebietsschema für dieses Thema fest. Wenn dieses Tag in einem Thema verwendet wird, muss es nur einmal verwendet und über allen anderen Microsoft-Hilfe-Tags eingefügt werden. Wenn dieses Tag nicht verwendet wird, wird der Textkörper des Themas mithilfe eines Worttrenners indiziert, der dem Produktgebietsschema zugeordnet ist, sofern er angegeben ist. Andernfalls wird der en-us Worttrenner verwendet. Dieses Tag entspricht ISOC RFC 4646. Um sicherzustellen, dass die Microsoft-Hilfe ordnungsgemäß funktioniert, verwenden Sie diese Eigenschaft anstelle des allgemeinen Language-Attributs. |
| \<meta name="Microsoft.Help.TopicLocale" content="[sprachcode]" /> | Legt ein Gebietsschema für dieses Thema fest, wenn auch andere Gebietsschemas verwendet werden. Wenn dieses Tag in einem Thema verwendet wird, muss es nur einmal verwendet werden. Verwenden Sie dieses Tag, wenn der Katalog Inhalt in mehr als einer Sprache enthält. Mehrere Themen in einem Katalog können dieselbe ID haben, aber jedes muss ein eindeutiges TopicLocale angeben. Das Thema, das ein TopicLocale angibt, das dem Gebietsschema des Katalogs entspricht, ist das Thema, das im Inhaltsverzeichnis angezeigt wird. Alle Sprachversionen des Themas werden jedoch in den Suchergebnissen angezeigt. |
| \<Titel>[Titel]\</titel> | Gibt den Titel dieses Themas an. Dieses Tag ist erforderlich und muss nur einmal in einem Thema verwendet werden. Wenn der Text des Themas \<keinen Titel div> Abschnitt enthält, wird dieser Titel im Thema und im Inhaltsverzeichnis angezeigt. |
| \<meta name=" Microsoft.Help.Keywords" content="[aKeywordPhrase]"/> | Gibt den Text eines Links an, der im Indexbereich der Hilfeanzeige angezeigt wird. Wenn auf den Link geklickt wird, wird das Thema angezeigt. Sie können mehrere Indexschlüsselwörter für ein Thema angeben, oder Sie können dieses Tag weglassen, wenn keine Verknüpfungen zu diesem Thema im Index angezeigt werden sollen. "K"-Schlüsselwörter aus früheren Versionen der Hilfe können in diese Eigenschaft konvertiert werden. |
| \<meta name="Microsoft.Help.Id" content="[TopicID]"/> | Legt den Bezeichner für dieses Thema fest. Dieses Tag ist erforderlich und muss nur einmal in einem Thema verwendet werden. Die ID muss unter den Themen im Katalog eindeutig sein, die dieselbe Gebietsschemaeinstellung haben. In einem anderen Thema können Sie mithilfe dieser ID einen Link zu diesem Thema erstellen. |
| \<meta name="Microsoft.Help.F1" content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/> | Gibt das Schlüsselwort F1 für dieses Thema an. Sie können mehrere F1-Schlüsselwörter für ein Thema angeben, oder Sie können dieses Tag weglassen, wenn dieses Thema nicht angezeigt werden soll, wenn ein Anwendungsbenutzer F1 drückt. In der Regel wird nur ein F1-Schlüsselwort für ein Thema angegeben. "F"-Schlüsselwörter aus früheren Versionen der Hilfe können in diese Eigenschaft konvertiert werden. |
| \<meta name="Description" content="[Themenbeschreibung]" /> | Enthält eine kurze Zusammenfassung des Inhalts in diesem Thema. Wenn dieses Tag in einem Thema verwendet wird, muss es nur einmal verwendet werden. Auf diese Eigenschaft wird direkt von der Abfragebibliothek zugegriffen. Sie wird nicht in der Indexdatei gespeichert. |
| meta name="Microsoft.Help.TocParent" content="[parent_Id]"/> | Gibt das übergeordnete Thema dieses Themas im Inhaltsverzeichnis an. Dieses Tag ist erforderlich und muss nur einmal in einem Thema verwendet werden. Der Wert ist die Microsoft.Help.Id des übergeordneten Elements. Ein Thema kann nur eine Position im Inhaltsverzeichnis haben. "-1" wird als Themen-ID für den TOC-Stamm betrachtet. In [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]ist diese Seite Help Viewer-Startseite. Dies ist der gleiche Grund, warum wir speziell TocParent=-1 zu einigen Themen hinzufügen, um sicherzustellen, dass sie auf der obersten Ebene angezeigt werden. Die Help Viewer-Startseite ist eine Systemseite und daher nicht austauschbar. Wenn ein VSP versucht, eine Seite mit der ID -1 hinzuzufügen, wird er möglicherweise dem Inhaltssatz hinzugefügt, aber Help Viewer verwendet immer die Systemseite - Help Viewer Home |
| \<meta name="Microsoft.Help.TocOrder" content="[positive ganze Zahl]"/> | Gibt an, wo im Inhaltsverzeichnis dieses Thema relativ zu seinen Peerthemen angezeigt wird. Dieses Tag ist erforderlich und muss nur einmal in einem Thema verwendet werden. Der Wert ist eine ganze Zahl. Ein Thema, das eine ganzzahlige Datei mit einem niedrigeren Wert angibt, wird über einem Thema angezeigt, das eine ganzzahlhöhere Zahl angibt. |
| \<meta name="Microsoft.Help.Product" content="[Produktcode]"/> | Gibt das Produkt an, das in diesem Thema beschrieben wird. Wenn dieses Tag in einem Thema verwendet wird, muss es nur einmal verwendet werden. Diese Informationen können auch als Parameter angegeben werden, der an den Hilfeindexer übergeben wird. |
| \<meta name="Microsoft.Help.ProductVersion" content="[Versionsnummer]"/> | Gibt die Version des Produkts an, die in diesem Thema beschrieben wird. Wenn dieses Tag in einem Thema verwendet wird, muss es nur einmal verwendet werden. Diese Informationen können auch als Parameter angegeben werden, der an den Hilfeindexer übergeben wird. |
| \<meta name="Microsoft.Help.Category" content="[string]"/> | Wird von Produkten verwendet, um Unterabschnitte des Inhalts zu identifizieren. Sie können mehrere Unterabschnitte für ein Thema identifizieren, oder Sie können dieses Tag weglassen, wenn Sie keine Verknüpfungen zum Identifizieren von Unterabschnitten wünschen. Dieses Tag wird verwendet, um die Attribute für TargetOS und TargetFrameworkMoniker zu speichern, wenn ein Thema aus einer früheren Version der Hilfe konvertiert wird. Das Format des Inhalts ist AttributeName:AttributeValue. |
| \<meta name="Microsoft.Help.TopicVersion content="[topic versionsnummer]"/> | Gibt diese Version des Themas an, wenn mehrere Versionen in einem Katalog vorhanden sind. Da Microsoft.Help.Id nicht garantiert eindeutig ist, ist dieses Tag erforderlich, wenn mehr als eine Version eines Themas in einem Katalog vorhanden ist, z. B. wenn ein Katalog ein Thema für .NET Framework 3.5 und ein Thema für .NET Framework 4 enthält und beide die gleiche Microsoft.Help.Id haben. |
| \<meta name="SelfBranded" content="[TRUE oder FALSE]"/> | Gibt an, ob in diesem Thema das Startbrandingpaket Help Library Manager oder ein für das Thema spezifisches Brandingpaket verwendet wird. Dieses Tag muss entweder TRUE oder FALSE sein. Wenn es TRUE ist, überschreibt das Brandingpaket für das zugeordnete Thema das Brandingpaket, das beim Starten des Hilfebibliotheks-Managers festgelegt wird, sodass das Thema wie beabsichtigt gerendert wird, auch wenn es sich vom Rendern anderer Inhalte unterscheidet. Wenn es sich um FALSE handelt, wird das aktuelle Thema entsprechend dem Brandingpaket gerendert, das beim Starten des Hilfebibliotheks-Managers festgelegt wird. Standardmäßig geht Help Library Manager davon aus, dass Selfbranding falsch ist, es sei denn, die SelfBranded-Variable wird als TRUE deklariert. Daher müssen Sie meta \<name="SelfBranded" content="FALSE"/> nicht deklarieren. |

## <a name="create-a-branding-package"></a>Erstellen eines Brandingpakets

Die Visual Studio-Version umfasst eine Reihe verschiedener Visual Studio-Produkte, einschließlich der isolierten und integrierten Shells für Visual Studio-Partner.  Jedes dieser Produkte erfordert ein gewisses Maß an themenbasierter Unterstützung für das Branding von Hilfeinhalten, die für das Produkt einzigartig ist.  Beispielsweise müssen Visual Studio-Themen über eine konsistente Markenpräsentation verfügen, während SQL Studio, das DIE ISO-Shell umschließt, für jedes Thema ein eigenes eindeutiges Help-Inhaltsbranding erfordert.  Ein integrierter Shellpartner möchte möglicherweise, dass sich seine Hilfethemen im übergeordneten Visual Studio-Produkthilfeinhalt enthalten, während er sein eigenes Themenbranding beibehält.

Brandingpakete werden von dem Produkt installiert, das den Hilfe-Viewer enthält.  Für Visual Studio-Produkte:

- Ein Fallback-Brandingpaket\<(Branding_ Gebietsschema>.mshc) wird im Help Viewer 2.3-App-Stamm installiert (z. B. C:-Programmdateien (x86) und Microsoft Help Viewer-V2.3) vom Help Viewer-Sprachpaket.  Dies wird für Fälle verwendet, in denen entweder das Produktbrandingpaket nicht installiert ist (kein Inhalt wurde installiert) oder wenn das installierte Brandingpaket beschädigt ist.  Die Visual Studio-Elemente (Logo und Feedback) werden ignoriert, wenn das App-Root-Fallback-Brandingpaket verwendet wird.

- Wenn Visual Studio-Inhalte aus dem Inhaltspaketdienst installiert werden, wird auch ein Brandingpaket installiert (zum ersten Mal für die Inhaltsinstallation).  Wenn ein Update für das Brandingpaket vorhanden ist, wird das Update installiert, wenn die nächste Inhaltsaktualisierung oder zusätzliche Paketinstallationsaktion stattfindet.

Microsoft Help Viewer unterstützt das Branding von Themen basierend auf Themenmetadaten.

- Wenn Themenmetadaten Self branded = true definieren, rendern Sie das Thema so, wie es ist, tun Sie nichts (bis zum Branding).

- Wenn Themenmetadaten Self Branded = false definieren, verwenden Sie das Brandingpaket, das dem TopicVendor-Metadatenwert zugeordnet ist.

- Wenn Themenmetadaten name="Microsoft.Help.TopicVendor" content=\< Brandingpaketname in Kreditor MSHA> definieren, verwenden Sie das brandingpaket, das im Inhaltswert definiert ist.

- Innerhalb des Visual Studio-Katalogs gibt es eine prioritätsbewertende Anwendung von Brandingpaketen.  Zuerst wird das Visual Studio-Standardbranding angewendet, und wenn es in den Themenmetadaten definiert und mit dem zugehörigen Brandingpaket unterstützt wird (wie in der Installations-Msha definiert), wird das vom Hersteller definierte Branding als Außerkraftsetzung angewendet.

Brandingelemente lassen sich in der Regel in drei Hauptkategorien einteilen:

- Header-Elemente (Beispiele sind Feedback-Link, bedingter Haftungsausschlusstext, Logo)

- Inhaltsverhalten (Beispiele sind Erweiterungs-/Kollaps-Steuerelementtextelemente und Codeausschnittelemente)

- Fußzeilenelemente (Beispiel Copyright)

Zu den als Markenelementen betrachteten Elementen gehören (in dieser Spezifikation aufgeführt):

- Katalog-/Produktlogo (Beispiel Visual Studio)

- Feedback-Link und E-Mail-Elemente

- Haftungsausschlusstext

- Copyright-Text

Zu den unterstützenden Dateien im Visual Studio Help Viewer-Brandingpaket gehören:

- Grafiken (Logos, Symbole usw.)

- Branding.js - Skriptdateien, die das Verhalten von Inhalten unterstützen

- Branding.xml - Zeichenfolgen, die konsistent für katalogbasierte Inhalte verwendet werden.  Hinweis: Für Visual Studio-Lokalisierungstextelemente in der\<branding.xml,include _locID=" eindeutigen Wert>"

- Branding.css - Stildefinitionen für Präsentationskonsistenz

- Printing.css - Stildefinitionen für konsistente gedruckte Präsentation

Wie oben erwähnt, sind Branding-Pakete mit dem Thema verknüpft:

- Wenn SelfBranded = false in den Metadaten definiert ist, erbt das Thema das Katalogbrandingpaket

- Oder wenn SelfBranded = false und es ein eindeutiges Branding-Paket im MSHA definiert und verfügbar ist, wenn der Inhalt installiert wird

Für VSPs, die benutzerdefinierte Brandingpakete (VSP-Inhalt, SelfBranded=True) implementieren, besteht eine Möglichkeit, mit dem Fallback-Brandingpaket (installiert mit dem Hilfe-Viewer) zu beginnen und den Namen der Datei entsprechend zu ändern.  Die\<Branding_-Gebietsschema>.mshc Datei ist eine ZIP-Datei mit der Dateierweiterung geändert .mshc, so ändern Sie einfach die Erweiterung von .mshc zu .zip und extrahieren Sie den Inhalt.  Siehe unten für Branding-Paketelemente und ändern Sie je nach Bedarf (z. B. ändern Sie das Logo in das VSP-Logo und den Verweis auf das Logo in der Datei Branding.xml, aktualisieren Branding.xml pro VSP-Spezifikationen usw.).

Wenn alle Änderungen vorgenommen sind, erstellen Sie eine ZIP-Datei mit den gewünschten Branding-Elementen und ändern Sie die Erweiterung in .mshc.

Um das benutzerdefinierte Brandingpaket zuzuordnen, erstellen Sie die MSHA, die den Verweis auf die Branding-mshc-Datei zusammen mit dem Inhalt mshc (enthält die Themen) enthält.  Siehe unten "MSHA" für das Erstellen eines grundlegenden MSHA.

Die Datei Branding.xml enthält eine Liste von Elementen, die zum \<konsistenten Rendern bestimmter Elemente in einem Thema verwendet werden, wenn das Thema meta name="Microsoft.Help.SelfBranded" content="false"/> enthält.  Die Visual Studio-Liste der Elemente in der Datei Branding.xml ist unten aufgeführt.  Diese Liste soll als Vorlage für ISO Shell-Anwender verwendet werden, wo sie diese Elemente (z. B. Logo, Feedback und Copyright) ändern, um ihre eigenen Produkt-Branding-Anforderungen zu erfüllen.

Hinweis: Variablen, die von "n" notiert werden, haben Codeabhängigkeiten - das Entfernen oder Ändern dieser Werte führt zu Fehlern und möglicherweise zum Absturz der Anwendung. Lokalisierungsbezeichner (beispielhaft _locID="codesnippet.n") sind im Visual Studio Branding Package enthalten.

**Branding.xml**

| | |
| - | - |
| Feature: | **CollapsibleArea** |
| Verwendung: | Erweitern reduziert Inhaltssteuerungstext |
| **Element** | **Wert** |
| ExpandText | Expand |
| CollapseText | Reduzieren |
| Feature: | **CodeSnippet** |
| Verwendung: | Codeausschnitt-Steuertext.  Hinweis: Codeausschnittinhalte mit "Non-Breaking"-Leerzeichen werden in Leerzeichen geändert. |
| **Element** | **Wert** |
| CopyToClipboard | In Zwischenablage kopieren |
| ViewColorizedText | Farbfarben anzeigen |
| KombinierteVBTabDisplayLanguage | Visual Basic (Beispiel) |
| VB-Deklaration | Deklaration |
| VBUsage | Verwendung |
| Feature: | **Feedback, Fußzeile und Logo** |
| Verwendung: | Geben Sie dem Kunden ein Feedback-Steuerelement an, um Feedback zum aktuellen Thema per E-Mail zu geben.  Copyright-Text für den Inhalt.  Logo-Definition. |
| **Element** | **Wert (Diese Zeichenfolgen können geändert werden, um die Anforderungen des Inhaltsannehmers zu erfüllen.)** |
| Copyright | © 2013 Microsoft Corporation. Alle Rechte vorbehalten. |
| SendFeedback | \<a{0}href=" {1} "\<>Feedback /a> zu diesem Thema an Microsoft senden. |
| FeedbackLink | |
| LogoTitle | [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] |
| LogoFileName | vs_logo_bk.gif |
| LogoFileNameHC | vs_logo_wh.gif |
| Feature: | **Haftungsausschluss** |
| Verwendung: | Eine Reihe von fallspezifischen Haftungsausschlüssen für maschinell übersetzte Inhalte. |
| **Element** | **Wert** |
| MT_Editable | Dieser Artikel wurde maschinell übersetzt. Wenn Sie über eine Internetverbindung verfügen, wählen Sie "Dieses Thema online anzeigen", um diese Seite gleichzeitig im bearbeitbaren Modus mit dem ursprünglichen englischen Inhalt anzuzeigen. |
| MT_NonEditable | Dieser Artikel wurde maschinell übersetzt. Wenn Sie über eine Internetverbindung verfügen, wählen Sie "Dieses Thema online anzeigen", um diese Seite gleichzeitig im bearbeitbaren Modus mit dem ursprünglichen englischen Inhalt anzuzeigen. |
| MT_QualityEditable | Dieser Artikel wurde manuell übersetzt. Wenn Sie über eine Internetverbindung verfügen, wählen Sie "Dieses Thema online anzeigen", um diese Seite gleichzeitig im bearbeitbaren Modus mit dem ursprünglichen englischen Inhalt anzuzeigen. |
| MT_QualityNonEditable | Dieser Artikel wurde manuell übersetzt. Wenn Sie über eine Internetverbindung verfügen, wählen Sie "Dieses Thema online anzeigen", um diese Seite gleichzeitig im bearbeitbaren Modus mit dem ursprünglichen englischen Inhalt anzuzeigen. |
| MT_BetaContents | Dieser Artikel wurde maschinell für eine vorläufige Version übersetzt. Wenn Sie über eine Internetverbindung verfügen, wählen Sie "Dieses Thema online anzeigen", um diese Seite gleichzeitig im bearbeitbaren Modus mit dem ursprünglichen englischen Inhalt anzuzeigen. |
| MT_BetaRecycledContents | Dieser Artikel wurde manuell für eine vorläufige Version übersetzt. Wenn Sie über eine Internetverbindung verfügen, wählen Sie "Dieses Thema online anzeigen", um diese Seite gleichzeitig im bearbeitbaren Modus mit dem ursprünglichen englischen Inhalt anzuzeigen. |
| Feature: | **LinkTable** |
| Verwendung: | Unterstützung für Online-Themenlinks |
| **Element** | **Wert** |
| LinkTableTitle | Linktabelle |
| ThemaEnuLinkText | Zeigen Sie\<die englische Version /a> dieses Themas an, die auf Ihrem Computer verfügbar ist. |
| ThemaOnlineLinkText | Dieses Thema \<finden Sie{0} {1} unter\<a href=" ">online /a> |
| OnlineText | Online |
| Feature: | **Video-Audio-Steuerung** |
| Verwendung: | Anzeigen von Elementen und Text für Videoinhalte |
| **Element** | **Wert** |
| MultiMediaNotSupported | Internet Explorer 9 oder höher {0} muss installiert sein, um Inhalte zu unterstützen. |
| VideoText | Anzeigen von Videos |
| AudioText | Streaming von Audio |
| OnlineVideoLinkText | \<p>Um das mit diesem {0} \<Thema verknüpfte{1}Video {2}\<anzuzeigen, klicken Sie auf a href=" ">hier /a>. \</p> |
| OnlineAudioLinkText | \<p>Um die mit diesem Thema {0} \<verknüpften{1}Audiodaten {2}\<anzuhören, klicken Sie auf a href=" ">hier /a>. \</p> |
| Feature: | **Content Not Installed-Steuerelement** |
| Verwendung: | Textelemente (Zeichenfolgen), die zum Rendern von contentnotinstalled.htm verwendet werden |
| **Element** | **Wert** |
| ContentNotInstalledTitle | Auf Ihrem Computer wurden keine Inhalte gefunden. |
| ContentNotInstalledDownloadContentText | \<p>Um Inhalte auf \<Ihren Computer{0} {1} herunterzuladen,>\<sie auf die Registerkarte Verwalten /a> klicken. \</p> |
| ContentNotInstalledText | \<p>Auf Ihrem Computer sind keine Inhalte installiert. Wenden Sie sich an die Installation von lokalen Hilfeinhalten an Ihren Administrator. \</p> |
| Feature: | **Thema nicht gefundenes Steuerelement** |
| Verwendung: | Textelemente (Zeichenfolgen), die für das Rendern von topicnotfound.htm verwendet werden |
| **Element** | **Wert** |
| TopicNotFoundTitle | Das angeforderte Thema kann auf Ihrem Computer nicht gefunden werden. |
| ThemaNotFoundViewOnlineText | \<p>Das von Ihnen angeforderte Thema wurde \<auf Ihrem{0} {1} Computer nicht gefunden, aber Sie können das Thema>online\</a> anzeigen. \</p> |
| ThemaNotFoundDownloadContentText | \<p>Siehe Navigationsbereich für Links \<zu ähnlichen{0}Themen, oder a href=" " {1} klicken Sie>auf die Registerkarte\<Verwalten /a>, um Inhalte auf Ihren Computer herunterzuladen. \</p> |
| TopicNotFoundText | \<p>Das angeforderte Thema wurde auf Ihrem Computer nicht gefunden. \</p> |
| Feature: | **Thema Beschädigte Steuerung** |
| Verwendung: | Textelemente (Zeichenfolgen), die zum Rendern von topiccorrupted.htm verwendet werden |
| **Element** | **Wert** |
| ThemaCorruptedTitle | Das angeforderte Thema kann nicht angezeigt werden. |
| ThemaCorruptedViewOnlineText | \<p>Help Viewer kann das angeforderte Thema nicht anzeigen. Möglicherweise liegt ein Fehler im Inhalt des Themas oder eine zugrunde liegende Systemabhängigkeit vor. \</p> |
| Feature: | **Homepage-Steuerung** |
| Verwendung: | Text, der die Anzeige des Knoteninhalts der obersten Ebene des Help Viewers unterstützt. |
| **Element** | **Wert** |
| HomePageTitle | Hilfe Viewer Home |
| HomePageEinführung | \<p>Willkommen im Microsoft Help Viewer, einer wichtigen Informationsquelle für alle, die Microsoft-Tools, -Produkte, -Technologien und -Dienste verwenden. Mit dem Hilfe-Viewer erhalten Sie Zugriff auf Anleitungs- und Referenzinformationen, Beispielcode, technische Artikel und mehr. Um den benötigten Inhalt zu finden, durchsuchen Sie das Inhaltsverzeichnis, verwenden Sie die Volltextsuche oder navigieren Sie mithilfe des Schlüsselwortindex durch den Inhalt. \</p> |
| HomePageContentInstallText | \<p \<>br />Verwenden \<Sie die Registerkarte a{0}href=" " {1}>Verwalten von Inhalten\</a>, um Folgendes zu tun:\<ul>\<li>Hinzufügen von Inhalten zu Ihrem Computer. \</li \<>li>Überprüfen Sie, ob Ihre lokalen Inhalte aktualisiert wurden. \</li \<>li>Entfernen Sie Inhalte von Ihrem Computer. \</li \<>/ul>\</p> |
| HomePageInstalledBooks | Installierte Bücher |
| HomePageNoBooksInstalliert | Auf Ihrem Computer wurden keine Inhalte gefunden. |
| HomePageHelpSettings | HilfeInhaltseinstellungen |
| HomePageHelpSettingsText | \<p>Ihre aktuelle Einstellung ist lokale Hilfe. Der Hilfe-Viewer zeigt Inhalte an, die Sie auf Ihrem Computer installiert haben. \<br />Um die Quelle des Hilfeinhalts zu ändern, wählen \<{0}Sie in der Visual\<Studio-Menüleiste span style=" ">Hilfe, Hilfeeinstellung /span> festlegen. \<br />\</p> |
| MegaByte | MB |

**branding.js**

Die Datei branding.js enthält JavaScript, das von den Visual Studio Help Viewer-Brandingelementen verwendet wird.  Im Folgenden finden Sie eine Liste der Branding-Elemente und der unterstützenden JavaScript-Funktion.  Alle Zeichenfolgen, die für diese Datei lokalisiert werden sollen, werden im Abschnitt "Localizable Strings" oben in dieser Datei definiert.  Die ICL-Datei wurde für Loc-Zeichenfolgen in der Datei branding.js erstellt.

||||
|-|-|-|
|**Branding-Funktion**|**JavaScript-Funktion**|**Beschreibung**|
|Var...||Definieren von Variablen|
|Abrufen der Benutzercodesprache|setUserPreferenceLang|Ordnet einen Index der Codesprache zu|
|Festlegen und Abrufen von Cookie-Werten|getCookie, setCookie||
|Vererbtes Mitglied|changeMembersLabel|Erbliches Mitglied erweitern/reduzieren|
|Wenn SelfBranded=False|onLoad|Lesen Sie die Abfragezeichenfolge, um zu überprüfen, ob es sich um eine Druckanforderung handelt.  Legen Sie alle Codenippets fest, um die vom Benutzer bevorzugte Registerkarte zu fokussieren.  Wenn es sich um eine Druckanforderung handelt, wird die Datei "PrinterFriendly" auf true festgelegt. Überprüfen Sie den Modus mit hohem Kontrast.|
|Codeausschnitt|addSpecificTextLanguageTagSet||
||getIndexFromDevLang||
||ChangeTab||
||setCodesnippetLang||
||setCurrentLang||
||CopyToClipboard||
|CollapsibleArea|addToCollapsibleControlSet|Schreiben Sie das gesamte zusammenklappbare Steuerobjekt in die Liste.|
||CA_Click|bestimmt, welches Bild und welcher Text|
|Kontrastunterstützung für Logo|isBlackBackground()|Wird aufgerufen, um zu bestimmen, ob der Hintergrund schwarz ist.  Nur genau, wenn im Modus mit hohem Kontrast.|
||isHighContrast()|Verwenden einer farbigen Spanne zum Erkennen des Modus mit hohem Kontrast|
||onHighContrast(schwarz)|Wird aufgerufen, wenn ein hoher Kontrast erkannt wird|
|LST-Funktionalität|||
||addToLanSpecTextIdSet(id)||
||updateLST(currentLang)||
||getDevLangFromCodeSnippet(lang)||
|MultiMedia-Funktionalität|caption (Anfang, Ende, Text, Stil)||
||findAllMediaControls(normalizedId)||
||getActivePlayer(normalizedId)||
||captionsOnOff(id)||
||toSeconds(t)||
||getAllComments(knoten)||
||styleRectify(styleName, styleValue)||
||showCC(id)||
||untertitel(id)||

**HTM-DATEIEN**

Das Brandingpaket enthält eine Reihe von HTM-Dateien, die Szenarien für die Kommunikation von Schlüsselinformationen an Inhaltsbenutzer unterstützen, z. B. eine Homepage, die einen Abschnitt enthält, der beschreibt, welche Inhaltssätze installiert werden, und Seiten, die dem Benutzer mitteilen, wann Themen nicht im lokalen Themensatz gefunden werden können. Diese HTM-Dateien können pro Produkt geändert werden.  ISO Shell-Anbieter sind in der Lage, das Standard-Branding-Paket zu übernehmen und das Verhalten und den Inhalt dieser Seiten zu ändern, um ihren Bedarf zu decken.  Diese Dateien beziehen sich auf ihr jeweiliges Branding-Paket, damit die Branding-Tags den entsprechenden Inhalt aus der Datei branding.xml abrufen können.

||||
|-|-|-|
|**File**|**Verwenden**|**Angezeigte Inhaltsquelle**|
|homepage.htm|Dies ist eine Seite, die derzeit installierten Inhalt und jede andere Nachricht anzeigt, die dem Benutzer über seinen Inhalt angezeigt werden soll.  Diese Datei verfügt über das zusätzliche Metadatenattribut "Microsoft.Help.Id" content="-1", das diesen Inhalt an der Spitze des lokalen InhaltsinhaltsinhaltsInhalts gibt.||
||<META_HOME_PAGE_TITLE_ADD />|Branding.xml, \<Tag HomePageTitle>|
||<HOME_PAGE_INTRODUCTION_SECTION_ADD />|Branding.xml, \<Tag HomePageEinführung>|
||<HOME_PAGE_CONTENT_INSTALL_SECTION_ADD />|Branding.xml, \<Tag HomePageContentInstallText>|
||<HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD />|Heading-Abschnitt Branding.xml-Tag\<HomePageInstalledBooks>, \<die aus der Anwendung generierten Daten, HomePageNoBooksInstalled> wenn keine Bücher installiert sind.|
||<HOME_PAGE_SETTINGS_SECTION_ADD HOME_PAGE_SETTINGS_SECTION_ADD />|Überschriftabschnitt Branding.xml-Tag \<HomePageHelpSettings \<>, Abschnittstext HomePageHelpSettingsText>.|
|topiccorrupted.htm|Wenn ein Thema im lokalen Satz vorhanden ist, aber aus irgendeinem Grund nicht angezeigt werden kann (beschädigter Inhalt).||
||<META_TOPIC_CORRUPTED_TITLE_ADD />|Branding.xml, \<Tag TopicCorruptedTitle>|
||<TOPIC_CORRUPTED_SECTION_ADD />|Branding.xml, \<Tag TopicCorruptedViewOnlineText>|
|topicnotfound.htm|Wenn ein Thema nicht im lokalen Inhaltssatz gefunden wird oder online verfügbar ist||
||<META_TOPIC_NOT_FOUND_TITLE_ADD />|Branding.xml, \<Tag TopicNotFoundTitle>|
||<META_TOPIC_NOT_FOUND_ID_ADD />|Branding.xml, \<tag TopicNotFoundViewOnlineText \<> + TopicNotFoundDownloadContentText>|
||<TOPIC_NOT_FOUND_SECTION_ADD />|Branding.xml, \<Tag TopicNotFoundText>|
|contentnotinstalled.htm|Wenn kein lokaler Inhalt für das Produkt installiert ist.||
||<META_CONTENT_NOT_INSTALLED_TITLE_ADD />|Branding.xml, \<Tag ContentNotInstalledTitle>|
||<META_CONTENT_NOT_INSTALLED_ID_ADD />|Branding.xml, \<Tag ContentNotInstalledDownloadContentText>|
||<CONTENT_NOT_INSTALLED_SECTION_ADD />|Branding.xml, \<Tag ContentNotInstalledText>|

**CSS-Dateien**

Das Visual Studio Help Viewer Branding Package enthält zwei css-Dateien zur Unterstützung einer konsistenten Visual Studio-Hilfeinhaltspräsentation:

- Branding.css - enthält css-Elemente zum Rendern, wobei SelfBranded=false

- Printer.css - enthält css-Elemente zum Rendern, wobei SelfBranded=false

Branding.css-Dateien enthalten Definitionen für Visual Studio-Themenpräsentation (Einschränkung ist,\<dass sich die branding.css, die im Branding_ Gebietsschema enthalten sind,>.mshc aus dem Paketdienst ändern können).

**Grafikdateien**

Visual Studio-Inhalte zeigen ein Visual Studio-Logo sowie andere Grafiken an.  Die vollständige Liste der Grafikdateien im Visual Studio Help Viewer-Brandingpaket wird unten angezeigt.

||||
|-|-|-|
|**File**|**Verwenden**|**Beispiele**|
|clear.gif|Wird verwendet, um den zusammenklappbaren Bereich zu rendern||
|footer_slice.gif|Fußzeilenpräsentation||
|info_icon.gif|Wird beim Anzeigen von Informationen verwendet|Haftungsausschluss|
|online_icon.gif|Dieses Symbol ist mit Online-Links in Verbindung zu stellen||
|tabLeftBD.gif|Wird verwendet, um den Codeausschnittcontainer zu rendern||
|tabRightBD.gif|Wird verwendet, um den Codeausschnittcontainer zu rendern||
|vs_logo_bk.gif|Wird für normale Kontrastlogo-Referenzen verwendet, \<wie in Branding.xml-Tag LogoFileName> definiert.  Bei Visual Studio-Produkten lautet der Logoname vs_logo_bk.gif.||
|vs_logo_wh.gif|Wird für normale hohe Logo-Referenzen verwendet, wie in Branding.xml-Tag \<LogoFileNameHC> definiert.  Bei Visual Studio-Produkten lautet der Logoname vs_logo_wh.gif.||
|ccOff.png|Beschriftungsgrafik||
|ccOn.png|Beschriftungsgrafik||
|BildSprite.png|Wird verwendet, um den zusammenklappbaren Bereich zu rendern|Erweiterte oder Reduzierte Grafik|

## <a name="deploy-a-set-of-topics"></a>Bereitstellen einer Reihe von Themen

Dies ist ein einfaches und schnelles Tutorial zum Erstellen eines Help Viewer-Inhaltsbereitstellungssatzes, der aus einer MSHA-Datei und dem Satz von Cabs oder MSHCs besteht, die die Themen enthalten. Die MSHA ist eine XML-Datei, die eine Reihe von Cabs oder MSHC-Dateien beschreibt. Der Hilfe-Viewer kann die MSHA lesen, um eine Inhaltsliste (die . CAB oder . MSHC-Dateien) für die lokale Installation verfügbar.

Dies ist nur ein Primer, der das sehr grundlegende XML-Schema für den Help Viewer MSHA beschreibt.  Es gibt eine Beispielimplementierung unter dieser kurzen Übersicht und Beispiel HelpContentSetup.msha.

Der Name der MSHA für die Zwecke dieses Primers ist HelpContentSetup.msha (der Name der Datei kann alles sein, mit der Erweiterung . MSHA). HelpContentSetup.msha (Beispiel unten) sollte eine Liste der verfügbaren Cabs oder MSHCs enthalten.  Der Dateityp muss innerhalb des MSHA konsistent sein (unterstützt keine Kombination aus MSHA- und CAB-Dateitypen). Für jedes CAB oder MSHC \<sollte es eine div class="package">... \</div> (siehe Beispiel unten).

Hinweis: Im folgenden Implementierungsbeispiel haben wir das Branding-Paket aufgenommen. Dies ist wichtig, um die erforderlichen Visual Studio-Inhaltsrenderingelemente und Inhaltsverhalten zu erhalten.

Beispiel Datei HelpContentSetup.msha: (Ersetzen Sie "Inhaltssatzname 1" und "Inhaltssatzname 2" usw. durch Ihre Dateinamen.)

```html
<html>
<head />
<body class="vendor-book">
<div class="details">
<span class="vendor">Your Company</span>
<span class="locale">en-us</span>
<span class="product">Your Company Help Content</span>
<span class="name">Your Company Help Content</span>
</div>
<div class="package-list">
<div class="package">
<span class="name">Your_Company _Content_Set_1</span>
<span class="deployed">True</span>
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>
</div>
<div class="package">
<span class="name">Your_Company _Content_Set_2</span>
<span class="deployed">True</span>
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>
</div>.
```

1. Erstellen eines lokalen Ordners, so etwas wie "C:-SampleContent"

2. In diesem Beispiel verwenden wir MSHC-Dateien, um die Themen zu enthalten.  Ein MSHC ist ein ZIP mit der Dateierweiterung von .zip in geändert . MSHC.

3. Erstellen Sie die folgende HelpContentSetup.msha als Textdatei (Notizblock wurde zum Erstellen der Datei verwendet) und speichern Sie sie in dem oben genannten Ordner (siehe Schritt 1).

Die Klasse "Branding" existiert und ist einzigartig. Das Branding-mshc ist in diesem Primer enthalten, sodass der installierte Inhalt über Branding verfügt und die in den MSHCs enthaltenen Inhaltsverhalten die entsprechenden Supportelemente im Brandingpaket enthalten. Andernfalls treten Fehler auf, wenn das System nach Supportelementen sucht, die nicht Teil des gerissenen (installierten) Inhalts sind.

Um das Visual Studio-Brandingpaket abzuerhalten, kopieren Sie Branding_en-US.mshc-Datei unter C:-Programmdateien (x86) .

```html
<html>
<head />
<body class="vendor-book">
<div class="details">
<span class="vendor">Your Company</span>
<span class="locale">en-us</span>
<span class="product">Your Company Help Content</span>
<span class="name">Your Company Help Content</span>
</div>
<div class="package-list">
<div class="package">
<span class="name">Your_Company _Content_Set_1</span>
<span class="deployed">True</span>
<a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a>
</div>
<div class="package">
<span class="name">Your_Company _Content_Set_2</span>
<span class="deployed">True</span>
<a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a>
</div>
<div class="package">
<span class="packageType">branding</span>
<span class="name">Branding_en-US</span>
<span class="deployed">True</span>
<a class="current-link" href="Branding_en-US.mshc">Branding_en-US.mshc</a>
</div>
</div>
</body>
</html>
```

**Zusammenfassung**

Wenn Sie die oben genannten Schritte verwenden und erweitern, können VSPs ihre Inhaltssätze für den Visual Studio Help Viewer bereitstellen.

### <a name="add-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Hilfe zur Visual Studio-Shell hinzufügen (integriert und isoliert)

**Einführung**

In dieser exemplarischen Vorgehensweise wird veranschaulicht, wie Sie Hilfeinhalte in eine Visual Studio Shell-Anwendung integrieren und dann bereitstellen.

**Anforderungen**

1. [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]

2. [Visual Studio 2013 Isolierte Shell Redist](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)

**Übersicht**

Die [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell ist eine [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Version der IDE, auf der Sie eine Anwendung basieren können. Solche Anwendungen enthalten die isolierte Shell zusammen mit Erweiterungen, die Sie erstellen. Verwenden Sie isolierte Shell-Projektvorlagen, [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] die im SDK enthalten sind, um Erweiterungen zu erstellen.

Die grundlegenden Schritte zum Erstellen einer isolierten Shell-basierten Anwendung und ihrer Hilfe:

1. Erhalten [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Sie die ISO-Shell-Verteilerung (ein Microsoft-Download).

2. Erstellen Sie in Visual Studio eine Hilfeerweiterung, die auf der isolierten Shell basiert, z. B. die Contoso-Hilfeerweiterung, die weiter unten in dieser exemplarischen Vorgehensweise beschrieben wird.

3. Umschließen Sie die Erweiterung und die ISO-Shell wird in eine Bereitstellungs-MSI (ein Anwendungs-Setup) verstellt. Diese exemplarische Vorgehensweise enthält keinen Einrichtungsschritt.

Erstellen Sie einen Visual Studio-Inhaltsspeicher. Ändern Sie für das Szenario "Integrierte Shell" Visual Studio12 wie folgt in den Produktkatalognamen:

- Erstellen Sie den Ordner C:-Programmdaten,Microsoft-HelpLibrary2-Kataloge, VisualStudio15.

- Erstellen Sie eine Datei mit dem Namen CatalogType.xml, und fügen Sie sie dem Ordner hinzu. Die Datei sollte die folgenden Codezeilen enthalten:

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

Definieren Sie den Inhaltsspeicher in der Registrierung. Ändern Sie für die integrierte Shell VisualStudio15 in den Produktkatalognamen:

- HKLM-SOFTWARE-Wow6432-Knoten-Microsoft-Hilfe, V2.3-Kataloge, VisualStudio15

   Schlüssel: LocationPath-Zeichenfolgenwert: C:-ProgrammDaten-Microsoft-HelpLibrary2-Kataloge, VisualStudio15

- HKLM-SOFTWARE-Wow6432-Knoten-Microsoft-Hilfe, V2.3-Kataloge, VisualStudio15- und -de

   Schlüssel: CatalogName String-Wert: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Dokumentation

**Erstellen des Projekts**

So erstellen Sie eine isolierte Shell-Erweiterung:

1. Wählen Sie in Visual Studio unter **Datei**die Option **Neues Projekt**aus, wählen Sie unter **Andere Projekttypen** **Erweiterbarkeit**aus, und wählen Sie dann **Visual Studio Shell Isolated**aus. Benennen Sie `ContosoHelpShell`das Projekt ), um ein Erweiterbarkeitsprojekt basierend auf der Visual Studio Isolated Shell-Vorlage zu erstellen.

2. Öffnen Sie im Projektmappen-Explorer im ContosoHelpShellUI-Projekt im Ordner Ressourcendateien ApplicationCommands.vsct. Stellen Sie sicher, dass diese Zeile auskommentiert ist (suchen Sie nach "No_Help"):`<!-- <define name="No_HelpMenuCommands"/> -->`

3. Wählen Sie den F5-Schlüssel aus, um **Debug**zu kompilieren und auszuführen. Wählen Sie in der experimentellen Instanz der isolierten Shell-IDE das **Hilfemenü** aus. Stellen Sie sicher, dass die Befehle **"Hilfe anzeigen**", **Hilfeinhalte hinzufügen und entfernen "** und **Hilfeeinstellungen festlegen "** angezeigt werden.

4. Öffnen Sie im Projektmappen-Explorer im ContosHelpShell-Projekt im Ordner Shell-Anpassung ContosoHelpShell.pkgdef. Um den Contoso-Hilfekatalog zu definieren, fügen Sie die folgenden Zeilen hinzu:

    ```
     [$RootKey$\Help]
    "Product"="Contoso"
    "Catalog"="Contoso"
    "Version"="100"
    "BrandingPackage"="ContosoBrandingPackage.mshc"
    ```

5. Öffnen Sie im Projektmappen-Explorer im ContosHelpShell-Projekt im Ordner Shell-Anpassung ContosoHelpShell.Application.pkgdef. Um die F1-Hilfe zu aktivieren, fügen Sie die folgenden Zeilen hinzu:

    ```
    // F1 Help Provider

    [$RootKey$\HelpProviders\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]
    "Name"="13407"
    "Package"="{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}"
    @="Help3 Provider"
    [$RootKey$\HelpProviders]
    @="{C99BDC23-FF29-46bf-9658-ADD634CCAED8}"
    [$RootKey$\Services\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}]
    "Name"="Help3 Provider"
    @="{4A791146-19E4-11D3-B86B-00C04F79F802}"
    ```

6. Wählen Sie im Projektmappen-Explorer im Kontextmenü der ContosoHelpShell-Lösung das Menüelement **Eigenschaften** aus. Wählen Sie unter **Konfigurationseigenschaften** **Configuration Manager**aus. Ändern Sie in der Spalte **Konfiguration** jeden "Debug"-Wert in "Release".

7. Erstellen Sie die Projektmappe. Dadurch wird eine Reihe von Dateien in einem Freigabeordner erstellt, die im nächsten Abschnitt verwendet werden.

So testen Sie dies wie bereitgestellt:

1. Installieren Sie auf dem Computer, auf dem Sie Contoso bereitstellen, die heruntergeladene (von oben) ISO-Shell.

2. Erstellen Sie \\einen Ordner in "Programmdateien" (x86)\\, und benennen Sie ihn `Contoso`.

3. Kopieren Sie den Inhalt aus dem ContosoHelpShell-Freigabeordner in \\den Ordner "Programmdateien "x86".

4. Starten Sie den Registrierungs-Editor, indem `Regedit`Sie im **Startmenü** **ausführen** auswählen und eingeben. Wählen Sie im Registrierungseditor **Datei**aus, und **importieren**Sie dann . Navigieren Sie zum ContosoHelpShell-Projektordner. Wählen Sie im Unterordner ContosoHelpShell die Option ContosoHelpShell.reg aus.

5. Erstellen eines Inhaltsspeichers:

    Für ISO-Shell- Erstellen eines Contoso-Inhaltsspeichers C:-ProgrammDaten,Microsoft-HelpLibrary2-Kataloge, ContosoDev12

    Erstellen [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Sie für die integrierte Shell den Ordner C:-Programmdaten, Microsoft, HelpLibrary2, Kataloge, VisualStudio15.

6. Erstellen Sie CatalogType.xml, und fügen Sie dem Inhaltsspeicher (vorheriger Schritt) folgendes hinzu:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <catalogType>UserManaged</catalogType>
   ```

7. Fügen Sie die folgenden Registrierungsschlüssel hinzu:

    HKLM-SOFTWARE-Wow6432-Knoten-Microsoft-Hilfe, V2.3-Kataloge, VisualStudio15Key: LocationPath-Zeichenfolgenwert:

    Für ISO Shell:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15

    [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]Integrierte Shell:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en-US

    Schlüssel: CatalogName String-Wert: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Dokumentation. Für ISO Shell ist dies der Name Ihres Katalogs.

8. Kopieren Sie Ihre Inhalte (Cabs oder MSHC und MSHA) in einen lokalen Ordner.

9. Beispiel Integrierte Shell-Befehlszeile zum Testen des Inhaltsspeichers. Ändern Sie für ISO Shell den Katalog, und starten Sie die App-Werte entsprechend dem Produkt.

     "C:-Programmdateien (x86)-Microsoft-Hilfe-Viewer,V2.3-HlpViewer.exe" /catalogName VisualStudio15 /helpQuery-Methode="Seite&id=ContosoTopic0" /launchingApp Microsoft,VisualStudio,12.0

10. Starten Sie die Contoso-Anwendung (aus dem Contoso-App-Stamm). Wählen Sie in der ISO-Shell das **Menüelement Hilfe** aus, und ändern Sie die **Hilfeeinstellung festlegen,** um die lokale Hilfe zu **verwenden.**

11. Wählen Sie in der Shell das **Menüelement Hilfe** aus, und zeigen Sie dann die **Hilfe an.** Der lokale Hilfebetrachter sollte gestartet werden. Wählen Sie die Registerkarte **Inhalt verwalten** aus. Wählen Sie unter **Installationsquelle**die Schaltfläche **Datenträgeroption** aus. Wählen Sie die Schaltfläche **...** und navigieren Sie zum lokalen Ordner mit Contoso-Inhalt (im obigen Schritt in den lokalen Ordner kopiert). Wählen Sie HelpContentSetup.msha aus. Contoso sollte nun als Buch in der Buchauswahl erscheinen. Wählen Sie **Hinzufügen**aus , und wählen Sie dann die Schaltfläche **Aktualisieren** (untere rechte Ecke).

12. Wählen Sie in der Contoso-IDE die Taste F1 aus, um die F1-Funktionalität zu testen.

## <a name="additional-resources"></a>Zusätzliche Ressourcen

Informationen zur Laufzeit-API finden Sie unter [Windows-Hilfe-API](/previous-versions/windows/desktop/helpapi/helpapi-portal).

Weitere Informationen zur Nutzung der Hilfe-API finden Sie unter [Help Viewer-Codebeispiele](https://marketplace.visualstudio.com/items?itemName=RobChandlerHelpMVP.HelpViewer20CodeExamples).

Sie können Feature-Vorschläge in der [Developer Community](https://developercommunity.visualstudio.com/content/idea/post.html?space=8)einreichen.
