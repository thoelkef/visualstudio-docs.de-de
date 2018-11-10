---
title: Microsoft Help Viewer SDK | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: af324b141815813aec9eaadfcd9982689fdeb467
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51000346"
---
# <a name="microsoft-help-viewer-sdk"></a>Microsoft Help Viewer SDK

Dieser Artikel enthält die folgenden Aufgaben für Visual Studio Help Viewer Integratoren:

-   Erstellen eines Themas (F1-Unterstützung)

-   Erstellen eines Help Viewer Inhalte-branding-Pakets

-   Bereitstellen einer Reihe von Artikeln

-   Hinzufügen von Hilfe zu Visual Studio Shell (integriert oder isoliert)

-   Zusätzliche Ressourcen

### <a name="creating-a-topic-f1-support"></a>Erstellen eines Themas (F1-Unterstützung)
Dieser Abschnitt enthält eine Übersicht über die Komponenten von einem Thema dargestellten, Thema Anforderungen, eine kurze Beschreibung zum Erstellen eines Themas (einschließlich der F1-Supportanforderungen) und schließlich eine Beispielthema durch das gerenderte Ergebnis.

**Help Viewer Themenübersicht**

Wenn ein Thema für das Rendern aufgerufen wird, ruft das branding Paketelemente, die mit dem Thema zum Zeitpunkt der Installation oder der letzten Aktualisierung, zusammen mit dem Thema XHTML, verknüpft sind und kombiniert die beiden, um die angegebene Ansicht "Inhalt" führen Help Viewer (Data branding + Thema-Daten).  Das branding-Paket enthält die Logos, Unterstützung für verschiedene Verhalten und branding-Text (copyright, usw.).  Weitere Informationen zum Paket Brandingelemente finden Sie unter "Erstellen von Branding-Paket" unten.  Im Ereignisprotokoll kein branding Paket ist, das Thema zugeordnet, wird der Help Viewer das fallback branding-Paket befindet sich im Stammverzeichnis Help Viewer-Anwendung (Branding_en-US.mshc) verwendet.

**Help Viewer Thema Anforderungen**

Um ordnungsgemäß innerhalb der Help Viewer gerendert werden soll, muss die unformatierten Themeninhalt W3C grundlegende 1.1 XHTML sein.

Ein Thema enthält in der Regel zwei Abschnitte:

-   Metadaten (Siehe Content Metadatenverweis): Daten über das Thema, z. B. das Thema eindeutige ID, die Schlüsselwort-Wert, das Thema TOC-ID, übergeordnete Knoten-ID usw.

-   Text-Inhalt: einhalten von W3C grundlegende 1.1 XHTML, wozu unterstützt Verhalten (reduzierbarer Bereich, Codeausschnitt, usw. Eine vollständige Liste ist unten dargestellt).

Visual Studio-Branding-Paket unterstützte Steuerelemente:

-   Links

-   CodeSnippet

-   CollapsibleArea

-   Geerbte Member

-   LanguageSpecificText

Unterstützte Sprache-Zeichenfolgen (ohne Beachtung von Groß-/Kleinschreibung):

-   JavaScript

-   CSharp- oder c#

-   Cplusplus oder Visual c++ oder c++

-   JScript

-   VisualBasic- oder vb

-   f#- oder Fsharp oder fs

-   andere – eine Zeichenfolge, der Name einer Sprache darstellt.

**Erstellen eines Themas Help Viewer**

Erstellen Sie ein neues XHTML-Dokument mit dem Namen ContosoTopic4.htm, und umfassen Sie das Title-Tag (siehe unten).

```html
<html>
<head>
<title>Contoso Topic 4</title>
</head>

<body>

</body>
</html>

```

Fügen Sie Daten zu definieren, wie das Thema (selbst mit dem Branding oder nicht), angezeigt werden wie in diesem Thema für F1, verweisen, in dem in diesem Thema im Inhaltsverzeichnis, dessen ID (für den Verweis auf eine andere Themen) vorhanden ist, usw.  Finden Sie unter "Inhaltsmetadaten" der folgenden Tabelle eine vollständige Liste der unterstützten Metadaten.

-   In diesem Fall werden wir unseren eigenen branding-Paket eine Variante des Visual Studio Help Viewer Brandingpakets verwenden.

-   Fügen Sie die F1-Meta-Name und Wert ("Microsoft.Help.F1" Content = "ContosoTopic4") entspricht, die den angegebenen Wert von F1 in der IDE-Eigenschaftensammlung.  (Siehe Abschnitt F1-Unterstützung für Weitere Informationen.)   Dies ist der Wert, der mit dem F1 übereinstimmende rufen Sie in der IDE, die in diesem Thema angezeigt wird, wenn Sie F1 in der IDE ausgewählt wird.

-   Fügen Sie das Thema-ID hinzu Dies ist die Zeichenfolge, die von anderen Themen zum Verknüpfen mit diesem Thema verwendet wird.  Es ist die Hilfe-Viewer-ID in diesem Thema.

-   Fügen Sie für das Inhaltsverzeichnis dieses Themas übergeordneten Knoten, um zu definieren, in diesem Thema Inhaltsverzeichnisknoten angezeigt werden.

-   Fügen Sie für das Inhaltsverzeichnis dieses Themas Knotenreihenfolge hinzu. Wenn der übergeordnete Knoten n-Anzahl von untergeordneten Knoten verfügt, definieren Sie in der Reihenfolge der untergeordneten Knoten Speicherort des Themas. Dieses Thema ist z. B. Anzahl 4 von 4 untergeordneten Themen.)

Abschnitt für Beispiel-Metadaten:

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

**Der Text des Themas**

Seite enthält Links, einen Abschnitt "Hinweis", einem reduzierbaren Bereich, Codeausschnitten und einen sprachspezifischen Textabschnitt enthält der Textkörper (nicht die Kopf- und Fußzeile einschließlich) des Themas.  Finden Sie im Abschnitt "branding" Informationen zu diesen Bereichen des dargestellten Themas.

1.  Fügen Sie ein Thema Title-Tag hinzu:  `<div class="title">Contoso Topic 4</div>`

2.  Fügen Sie einen Hinweis-Abschnitt hinzu: `<div class="alert"> add your table tag and text </div>`

3.  Fügen Sie einem reduzierbaren Bereich hinzu:  `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`

4.  Fügen Sie einen Codeausschnitt hinzu:  `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`

5.  Fügen Sie Code sprachspezifischen Text hinzu: `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` Beachten Sie, dass `devLangnu=` können Sie andere Sprachen eingeben. Z. B. `devLangnu="Fortran"` Fortran zeigt bei der der Codeausschnitt DisplayLanguage Fortran =

6.  Fügen Sie die Seite enthält Links hinzu: `<a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>`

> [!NOTE]
>  Hinweis: für nicht unterstützte neue "Anzeigesprache" (beispielsweise F#, Cobol, Fortran) farbliche Kennzeichnung von Code im Codeausschnitt werden Monochrom.

**Beispiel-Viewer-Hilfethema** der Code wird veranschaulicht, wie Metadaten, einen Codeausschnitt, einen reduzierbaren Bereich und sprachspezifischen Text definieren.

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
        <a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>
    </div>
 </div>
</div>
</div>
</body>
</html>
```

**F1-Unterstützung**

In Visual Studio F1 auswählen, generiert die Werte, die von der Position des Cursors innerhalb der IDE bereitgestellt, und füllt einen "Eigenschaftenbehälter" mit den angegebenen Werten (auf der Grundlage der Cursorposition. Wenn der Cursor über der Funktion X ist, Feature X aktiv/im Fokus ist, und Sie werden Eigenschaftsbehälter mit Werten aufgefüllt.  Wenn F1 aktiviert ist, die Eigenschaftensammlung aufgefüllt, und Visual Studio-F1-Code sieht aus, um festzustellen, ob die Kunden Hilfe Standardquelle oder online ist (online ist die Standardeinstellung), erstellt dann die entsprechende Zeichenfolge basierend auf den Benutzern festlegen (online ist die Standardeinstellung) - Shell ausgeführt. (siehe die Help-Administratorhandbuch für EXE-Datei Parameter starten) mit Parametern für die lokale Hilfe-Viewer + Markierungswolke aus dem Eigenschaftenbehälter lokale Hilfe ist der Standardwert oder die MSDN-URL mit dem Schlüsselwort in der Parameterliste.

Wenn drei Zeichenfolgen für F1 zurückgegeben werden, bezeichnet als eine mehrwertige Zeichenfolge, dem ersten Ausdruck, sehen einen Treffer, akzeptieren, und wenn gefunden, wir fertig sind, Wenn dies nicht der Fall ist, verschieben in die nächste Zeichenfolge.  Reihenfolge von Bedeutung ist. Präsentation der Schlüsselwörter mit mehreren Werten sollte die längste Zeichenfolge, die kürzesten Zeichenfolge sein.  Betrachten Sie dazu bei mehreren Werten bestehenden Schlüsselwörter, die online F1-URL-Zeichenfolge, die das ausgewählte Schlüsselwort enthält.

In Visual Studio 2012 haben wir absichtlich eine stärkere Division zwischen online und offline geschaltet wird, sodass Wenn der Benutzer die Einstellung für Online war, klicken Sie dann wir einfach die F1-Anforderung direkt an den Dienst für die online-Abfrage auf MSDN und anstatt das routing über den Hilfe-Bibliothek-Agent übergeben dass in Visual Studio 2010 werden musste. Wir basieren dann auf einen Zustand der "Hersteller Inhalt installiert = True" zu bestimmen, ob Sie etwas anderes in diesem Kontext. True gibt an, führen Sie dann diese Logik Analyse- und routing, je nachdem, was Sie für Ihre Kunden unterstützen möchten. False gibt an, wechseln Sie dann wir nur auf MSDN. Wenn des Benutzers-Einstellung auf Local festgelegt ist, fahren Sie dann alle Aufrufe an die lokale Hilfe-Engine.

F1-Flussdiagramm:

![F1-Fluss](../../extensibility/internals/media/f1flow.png "F1flow")

Wenn der Help Viewer standardmäßig die Quelle der Hilfeinhalte auf online (Einführung in den Browser) festgelegt ist:

-   Visual Studio-Partner (VSP)-Funktionen auszugeben, einen Wert, der die Eigenschaftensammlung F1 (Eigenschaftenbehälter prefix.keyword und online-URL für das Präfix in der Registrierung gefunden): F1 sendet eine VSP-URL + Parameter an den Browser.

-   Visual Studio-Features (Language-Editor, Visual Studio bestimmte Menüelemente usw.): F1 sendet eine Visual Studio-URL an den Browser.

Wenn der Help Viewer standardmäßig die Quelle der Hilfeinhalte in der lokalen Hilfe (Einführung in Help Viewer) festgelegt ist:

-   VSP-Funktionen, bei denen Schlüsselwort übereinstimmen, zwischen Eigenschaftenbehälter F1 und lokalen columnstore-Index (d. h. die Eigenschaftenbehälter prefix.keyword = der Wert, der im lokalen Speicher Index gefunden): F1 rendert das Thema in Help Viewer.

-   Visual Studio-Funktionen (keine Option zum Überschreiben die Eigenschaftensammlung, die von Visual Studio-Funktionen ausgegeben, der VSP-Datei): F1 wird ein Visual Studio-Thema in Help Viewer gerendert.

Legen Sie die folgenden Registrierungswerte F1-Fallback für Hersteller Hilfeinhalt zu aktivieren. F1-Fallback bedeutet, dass der Help Viewer online nach Inhalten F1-Hilfe gesucht werden soll festgelegt ist, und der Hersteller-Inhalt auf die Festplatte des Benutzers lokal installiert ist. Help Viewer sollten lokale Hilfe für den Inhalt betrachten, auch wenn die Standardeinstellung für die Onlinehilfe ist.

1. Legen Sie die **VendorContent** Wert unter dem Registrierungsschlüssel 2.3 helfen:

   -   Für 32-Bit-Betriebssysteme:

        HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent" = DWORD: 00000001

   -   Für 64-Bit-Betriebssysteme:

        HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

        "VendorContent" = DWORD: 00000001

2. Registrieren Sie den partnernamespace unter dem Registrierungsschlüssel 2.3 helfen:

   - Für 32-Bit-Betriebssysteme:

      HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Partner<em>\\< Namespace\></em>

      "Speicherort"="offline"

   - Für 64-Bit-Betriebssysteme:

      HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Partner<em>\\< Namespace\></em>

      "Speicherort"="offline"

**Basis einheitlichen Namespace analysieren**

Beim Analysieren der systemeigenen Basisnamespace in der Registrierung hinzufügen, um aktivieren einen neuen DWORD-Wert durch den Namen des: BaseNativeNamespaces und setzen ihren Wert auf 1 (unter den Katalog-Schlüssel, die sie unterstützen möchten).  Wenn Sie den Visual Studio-Katalog verwenden möchten, können Sie beispielsweise den Schlüssel auf den Pfad hinzufügen:

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

Wenn ein F1-Schlüsselwort in das Format, die HEADER/Methode gefunden wird, wird das Zeichen '/', analysiert werden, führt das folgende Konstrukt:

-   HEADER: werden der Namespace, der verwendet werden kann, um in der Registrierung zu registrieren.

-   Methode: Dadurch wird das Schlüsselwort sein, das über übergeben wird.

Angenommen, eine benutzerdefinierte Bibliothek CustomLibrary aufgerufen und eine Methode, die MyTestMethod, aufgerufen, wenn eine Anforderung, sich eingeht F1 als formatiert `CustomLibrary/MyTestMethod`.

Ein Benutzer kann Klicken Sie dann CustomLibrary registrieren, wie der Namespace, unter der Partner-Struktur, und geben Sie den Schlüssel für den Speicherort sie erhalten möchten, und das Schlüsselwort, das an die Abfrage übergeben werden MyTestMethod.

**Aktivieren Sie die Hilfe, die debugging-Tools in der IDE**

Fügen Sie den folgenden Registrierungsschlüssel und den Wert ein:

HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Dynamic hilfeschlüssel: Debug-Ausgabe in der Anzeige in Verkaufswert: Ja

Wählen Sie in der IDE unter das Menüelement "Hilfe" "Hilfekontext Debuggen"

**Content-Metadaten**

In der folgenden Tabelle ist eine beliebige Zeichenfolge, die in Klammern steht ein Platzhalter, der von der kein gültiger Wert ersetzt werden muss. Z. B. in \<Meta name="Microsoft.Help.Locale" Inhalt = "[Language-Code]" / >, "[Sprachcode]" ersetzt werden muss durch einen Wert wie z. B. "En-us".


| Eigenschaft (HTML-Darstellung) | Beschreibung |
| - | - |
| \< Meta-name="Microsoft.Help.Locale" Content = "[Language-Code]" / > | Legt ein Gebietsschema für dieses Thema fest. Wenn dieses Tag in einem Thema verwendet wird, muss nur einmal verwendet werden, und sie müssen über alle anderen Tags bei Microsoft Help eingefügt werden. Wenn dieses Tag nicht verwendet wird, wird der Textkörper des Themas indiziert, mithilfe von wörtertrennung, der mit dem Produktgebietsschema zugeordnet ist, wenn er angegeben wird; andernfalls, En-us wörtertrennung verwendet wird. Dieses Tag entspricht ISOC RFC 4646. Um sicherzustellen, dass Microsoft Help ordnungsgemäß funktioniert, verwenden Sie diese Eigenschaft anstelle der allgemeinen Language-Attribut. |
| \< Meta-name="Microsoft.Help.TopicLocale" Content = "[Language-Code]" / > | Legt ein Gebietsschema für dieses Thema fest, wenn auch andere Gebietsschemas verwendet werden. Wenn dieses Tag in einem Thema verwendet wird, muss sie nur einmal verwendet werden. Verwenden Sie dieses Tag aus, wenn der Katalog Inhalt in mehreren Sprachen enthält. Mehrere Themen in einem Katalog können dieselbe ID haben, aber für jeden muss eine eindeutige TopicLocale angeben. Das Thema, das eine TopicLocale gibt an, die dem Gebietsschema des Katalogs entspricht, ist das Thema, das im Inhaltsverzeichnis angezeigt wird. Allerdings werden alle Sprachversionen des Themas in den Suchergebnissen angezeigt. |
| \< Title > [Title] \< /title > | Gibt den Titel dieses Themas. Dieses Tag ist erforderlich und muss nur einmal in einem Thema verwendet werden. Wenn der Text des Themas nicht über einen Titel enthält \<Div > Abschnitt dieser Titel wird im Thema und des Inhaltsverzeichnisses angezeigt. |
| \< Meta-Name = "Microsoft.Help.Keywords" Content = "[aKeywordPhrase]" / > | Gibt den Text eines Links, die im Bereich "Index" von Help Viewer angezeigt wird. Wenn auf der Link geklickt wird, ist das Thema angezeigt. Sie können mehrere Indexschlüsselwörter für ein Thema angeben, oder dieses Tags können Sie weglassen, wenn Sie nicht, dass Links zu diesem Thema im Index enthalten möchten. "K" Schlüsselwörter aus früheren Versionen von Help können an dieser Eigenschaft konvertiert werden. |
| \< Meta-name="Microsoft.Help.Id" Content = "[TopicID]" / > | Legt fest, den Bezeichner für die in diesem Thema. Dieses Tag ist erforderlich und muss nur einmal in einem Thema verwendet werden. Die ID muss für Themen im Katalog eindeutig sein, die das gleiche Gebietsschema festgelegt wurde. In einem anderen Thema können Sie einen Link zu diesem Thema erstellen, indem Sie mit dieser ID an. |
| \< Meta name="Microsoft.Help.F1" content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/ > | Gibt an, das F1-Schlüsselwort in diesem Thema. Sie können mehrere F1-Schlüsselwörter für ein Thema angeben, oder können Sie dieses Tag weglassen, wenn Sie nicht in diesem Thema angezeigt, wenn ein Anwendungsbenutzer F1 drückt möchten. Für ein Thema ist in der Regel nur ein F1-Schlüsselwort angegeben. "F" Schlüsselwörter aus früheren Versionen von Help können an dieser Eigenschaft konvertiert werden. |
| \< Meta-Name = "Beschreibung" Content = "[Thema Description]" / > | Enthält eine kurze Zusammenfassung des Inhalts in diesem Thema. Wenn dieses Tag in einem Thema verwendet wird, muss sie nur einmal verwendet werden. Diese Eigenschaft wird direkt von der Abfrage-Bibliothek zugegriffen werden. Es ist nicht in der Indexdatei gespeichert. |
| Meta-name="Microsoft.Help.TocParent" Content = "[Parent_Id]" / > | Gibt die im übergeordneten Thema dieses Themas im Inhaltsverzeichnis an. Dieses Tag ist erforderlich und muss nur einmal in einem Thema verwendet werden. Der Wert ist die Microsoft.Help.Id des übergeordneten Elements. Ein Thema haben nur eine Position in der Tabelle des Inhalts. Die Themen-ID für den Stamm des Inhaltsverzeichnisses gilt als "-1". In [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)], diese Seite ist die Startseite von Help Viewer. Dies ist aus demselben Grund, dass wir speziell TocParent =-1 hinzufügen, um einige Themen, um sicherzustellen, dass sie am oberen Ebene werden angezeigt. Die Startseite von Help Viewer ist eine System-Seite und daher nicht ersetzbare. Wenn eine VSP versucht, die eine Seite mit der ID 1 hinzugefügt werden, möglicherweise am Inhaltssatz lassen, aber Help Viewer verwendet immer die Seite "System" – Help Viewer – Startseite |
| \< Meta-name="Microsoft.Help.TocOrder" Content = "[positive ganze Zahl]" / > | Gibt an, in dem in der Tabelle der Inhalte in diesem Thema Bezug auf die Peer-Themen angezeigt wird. Dieses Tag ist erforderlich und muss nur einmal in einem Thema verwendet werden. Der Wert ist eine ganze Zahl. Ein Thema, das einen kleineren Wert ganze Zahl gibt an, die über ein Thema, das einen höheren Wert ganze Zahl gibt an, wird angezeigt. |
| \< Meta-name="Microsoft.Help.Product" Content = "[Produktcode]" / > | Gibt das Produkt, das in diesem Thema wird beschrieben, die an. Wenn dieses Tag in einem Thema verwendet wird, muss sie nur einmal verwendet werden. Diese Informationen kann auch als Parameter angegeben werden, der an den Indexer unterstützen übergeben wird. |
| \< Meta-name="Microsoft.Help.ProductVersion" Content = "[Versionsnummer]" / > | Gibt die Version des Produkts, das in diesem Thema wird beschrieben. Wenn dieses Tag in einem Thema verwendet wird, muss sie nur einmal verwendet werden. Diese Informationen kann auch als Parameter angegeben werden, der an den Indexer unterstützen übergeben wird. |
| \< Meta-name="Microsoft.Help.Category" Content = "[String]" / > | Von Produkten verwendet, um Unterabschnitte der Inhalte zu identifizieren. Sie können mehrere Unterabschnitte für ein Thema identifizieren, oder dieses Tags können Sie weglassen, wenn Sie nicht über die Links zu einem der Unterabschnitte identifizieren möchten. Dieses Tag wird verwendet, um die Attribute für "targetos" und TargetFrameworkMoniker speichern, wenn ein Thema von einer früheren Version der Hilfe konvertiert wird. Das Format des Inhalts ist AttributeName:AttributeValue. |
| \< Meta name="Microsoft.Help.TopicVersion Content ="[Thema Version Number]"/ > | Gibt diese Version des Themas an, wenn mehrere Versionen in einem Katalog vorhanden sind. Da Microsoft.Help.Id nicht eindeutig ist unbedingt, ist dieses Tag erforderlich, wenn mehr als eine Version eines Themas in einem Katalog, z. B. liegt, wenn der Katalog ein Thema für .NET Framework 3.5 und ein Thema für .NET Framework 4 enthält und jeweils die gleichen Micro vorläufig. Help.Id. |
| \< Meta-Name = "SelfBranded" Content = "[" true "oder" false "]" / > | Gibt an, ob es sich bei diesem Thema wird der Hilfebibliotheks-Manager starten branding oder branding-Paket, das an das Thema spezifisch ist. Dieses Tag muss entweder "true" oder "false". Ist dies "true", und klicken Sie dann die branding-Paket für das zugeordnete Thema Brandingpakets, die festgelegt wird überschreibt, wenn der Hilfebibliotheks-Manager startet, sodass das Thema gerendert wird, wie beabsichtigt, auch wenn es das Rendern von anderem Inhalt unterscheidet. Wenn es auf "false" ist, wird das aktuelle Thema gemäß Brandingpakets gerendert, die festgelegt wird, wenn der Hilfebibliotheks-Manager wird gestartet. Standardmäßig nimmt der Hilfebibliotheks-Manager selbst branding auf "falsch" sein, es sei denn, die SelfBranded-Variable deklariert wird, als "true"; aus diesem Grund, Sie müssen keine deklarieren \<Meta-Name = "SelfBranded" Content = "FALSE" / >. |

### <a name="creating-a-branding-package"></a>Erstellen eines Pakets branding
Die Visual Studio-Version umfasst eine Anzahl von anderen Visual Studio-Produkten, einschließlich der isoliert und die integrierte Shells für Visual Studio-Partnern.  Jedes dieser Produkte erfordert ein gewisses Maß an themenbasierte Hilfeinhalt branding-Unterstützung für das Produkt eindeutig.  Beispielsweise benötigen Visual Studio-Themen eine Präsentation einheitlichem Branding während der SQL-Studio, das ISO-Shell umhüllt, erfordert einen eigenen eindeutigen Hilfe Inhalte branding für jedes Thema.  Eine integrierte Shell-Partner sollten ihre innerhalb des übergeordneten Elements Hilfeinhalt für Visual Studio-Produkt zu werden, und gleichzeitig ihre eigenen Thema branding-Hilfethemen.

Branding-Pakete werden mit dem Produkt der Help Viewer mit installiert.  Für Visual Studio-Produkte:

-   Ein fallback-branding-Paket (Branding_\<Gebietsschema > .mshc) im Stammverzeichnis Help Viewer 2.3-app installiert ist (Beispiel: C:\Program Files (x86) \Microsoft Help Viewer\v2.3) durch das Help Viewer-Sprachpaket.  Hiermit wird für Fälle, in denen entweder das Produkt aus, die branding-Paket nicht installiert ist (kein Inhalt installiert wurde), oder, in denen das installierte branding-Paket ist beschädigt.  Die Visual Studio-Elemente (Logo und Feedback) werden ignoriert, wenn die Stamm-fallback app Brandingpakets verwendet wird.

-   Wenn Visual Studio-Inhalten aus dem Content-Paket-Dienst installiert ist, wird ein branding-Paket auch (für das erste Szenario der Time-Installation von Inhalt) installiert.  Wenn ein Update für das branding-Paket verfügbar ist, ist das Update installiert, bei der nächsten Aktualisierung von Inhalt oder ein zusätzliches Paket installieren-Aktion geschieht.

Microsoft Help Viewer unterstützt das branding von Themen, die auf der Grundlage Thema Metadaten.

-   In dem Thema Metadaten mit dem Branding des Self-Service definiert = "true", das Thema unverändert zu rendern, nichts Unternehmen (soweit es das branding).

-   In dem Thema Metadaten mit dem Branding des Self-Service definiert = False, verwenden Sie das branding Paket TopicVendor Metadatenwert zugeordnet.

-   Thema-Metadaten definiert, in denen name="Microsoft.Help.TopicVendor" Content =\< branding Paketname in Anbieter diese MSHA >, verwenden Sie das branding-Paket in den "Content"-Wert definiert.

-   Innerhalb der Visual Studio-Katalog wird eine Anwendung mit Priorität der Branding-Pakete.  Erste Visual Studio Standard-Branding des angewendet wird, und klicken Sie dann in den Metadaten Thema definiert und unterstützt das zugeordnete branding-Paket (wie in der Installation Msha definiert), der Anbieter definiert branding als Überschreibung angewendet wird.

Brandingelemente fallen normalerweise in drei Hauptkategorien unterteilt:

-   Header-Elemente (z. B. Feedbacklink, bedingte Haftungsausschlusses, Logo)

-   Inhalt von Verhaltensweisen (Beispiele für erweitern/reduzieren-Steuerelement-Text-Elemente enthalten und Codeelemente Ausschnitt)

-   Footer-Element (z. B. Copyright)

Elemente, die berücksichtigt werden, da organisationsspezifisch angepassten Elementen enthalten (in dieser Spezifikation beschrieben):

-   Katalog/Produktlogo (z. B. Visual Studio)

-   Feedback-Link und e-Mail-Elemente

-   Haftungsausschlusses

-   Copyright text

Unterstützende Dateien in Visual Studio Help Viewer Brandingpakets umfassen:

-   Grafiken (Logos, Symbole usw.).

-   Branding.js - Skript-Dateien unterstützende verschiedene Verhalten

-   Branding.XML - Zeichenfolgen, die konsistent in Kataloginhalt verwendet werden.  Hinweis: für Visual Studio-Lokalisierungs-Textelemente in der branding.xml enthalten _locID = "\<eindeutigen Wert >"

-   Branding.CSS - Formatdefinitionen Präsentation Konsistenz

-   Printing.CSS - Formatdefinitionen konsistente Ausdruck der Präsentation

Wie bereits erwähnt, sind die Branding-Pakete im Thema zugeordnet:

-   Wenn SelfBranded = "false" ist in den Metadaten definiert, wird das Thema erbt den branding-Paket-Katalog

-   Oder wenn SelfBranded = "false", und es wird ein eindeutiger Branding-Paket definiert in der MSHA und ist verfügbar, wenn der Inhalt installiert ist

Für das Implementieren von Paketen mit benutzerdefinierter branding VSPs (VSP Inhalt SelfBranded = True), eine Möglichkeit, um den Vorgang fortzusetzen, starten Sie mit dem fallback branding-Paket (mit Help Viewer installiert), und ändern Sie den Namen der Datei nach Bedarf ist.  Die Branding_\<Gebietsschema > mshc-Datei ist eine Zip-Datei mit der Dateierweiterung, die in mshc geändert, also einfach ändern Sie die Erweiterung in .zip aus mshc und extrahieren Sie den Inhalt.  Finden Sie weiter unten für das branding Paketelemente, und ändern nach Bedarf (z. B. Ändern des Logos für das VSP-Logo und den Verweis auf das Logo in der Datei Branding.xml, Aktualisieren von Branding.xml pro VSP Besonderheiten usw.).

Wenn alle Änderungen abgeschlossen haben, erstellen Sie eine Zip-Datei, die die gewünschten branding-Elemente enthält, und ändern Sie die Erweiterung in mshc.

Erstellen Sie, um benutzerdefinierte Brandingpakets zuzuordnen, die MSHA, die den Verweis auf die branding Mshc-Datei zusammen mit dem Inhalt Mshc (mit den Themen) enthält.  Finden Sie unter "Diese MSHA", wie Sie eine grundlegende diese MSHA erstellen.

Die Branding.xml-Datei enthält eine Liste von Elementen, die zum Rendern konsistent bestimmte Elemente in einem Thema aus, wenn das Thema enthält \<Meta name="Microsoft.Help.SelfBranded" Content = "false" / >.  Die Visual Studio-Liste der Elemente in der Datei Branding.xml sind unten aufgeführt.  Diese Liste soll verwendet werden, wie eine Vorlage für ISO-Shell-Anwender, in dem sie diese Elemente (z. B. Logos, Feedback und Copyright), um ihre eigenen Product branding zu erfüllen ändern muss.

Hinweis: Variablen, die von "{n}" angegeben haben codeabhängigkeiten – entfernen oder Ändern dieser Werte führt dazu, dass Fehler und möglicherweise zum Absturz der Anwendung. Lokalisierung Bezeichner (Beispiel _locID="codesnippet.n") sind in der Visual Studio-Branding-Paket enthalten.

**Branding.Xml**


| | |
| - | - |
| Feature: | **CollapsibleArea** |
| Verwenden: | Erweitern Sie die Text-Inhaltssteuerelement reduziert |
| **Element** | **Wert** |
| ExpandText | Expand |
| CollapseText | Reduzieren |
| Feature: | **CodeSnippet** |
| Verwenden: | Steuerelement codeausschnitttext.  Hinweis: Der Inhalt eines Beispielcodeausschnitts mit "Nicht unterbrechend" Speicherplatz wird Space geändert werden. |
| **Element** | **Wert** |
| CopyToClipboard | In Zwischenablage kopieren |
| ViewColorizedText | Koloriert anzeigen |
| CombinedVBTabDisplayLanguage | Visual Basic (Beispiel) |
| VBDeclaration | Deklaration |
| VBUsage | Verwendung |
| Feature: | **Feedback, Fußzeile und -Logo** |
| Verwenden: | Geben Sie eine Feedback-Steuerelement für Kunden, um Feedback zu das aktuelle Thema per E-mail bereitzustellen.  Copyright Text für den Inhalt.  Logo-Definition. |
| **Element** | **Wert (diese Zeichenfolgen können um Content Adopter-Anforderungen zu erfüllen geändert werden.)** |
| CopyRight | © 2013 Microsoft Corporation. Alle Rechte vorbehalten. |
| SendFeedback | \<ein Href = "{0}" {1}> Feedback senden \< /a > zu diesem Thema an Microsoft. |
| FeedbackLink | |
| LogoTitle | [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] |
| LogoFileName | vs_logo_bk.gif |
| LogoFileNameHC | vs_logo_wh.gif |
| Feature: | **Haftungsausschluss** |
| Verwenden: | Eine Reihe von Groß-/Kleinschreibung-spezifische Haftungsausschlüsse für Computer übersetzten Inhalten. |
| **Element** | **Wert** |
| MT_Editable | In diesem Artikel wurde maschinell übersetzt. Wenn Sie eine Internetverbindung verfügen, wählen Sie "Dieses Thema online anzeigen", um diese Seite in einem bearbeitbaren Modus und zusammen mit den ursprünglichen englischen Inhalt gleichzeitig anzuzeigen. |
| MT_NonEditable | In diesem Artikel wurde maschinell übersetzt. Wenn Sie eine Internetverbindung verfügen, wählen Sie "Dieses Thema online anzeigen", um diese Seite in einem bearbeitbaren Modus und zusammen mit den ursprünglichen englischen Inhalt gleichzeitig anzuzeigen. |
| MT_QualityEditable | In diesem Artikel wurde maschinell übersetzt. Wenn Sie eine Internetverbindung verfügen, wählen Sie "Dieses Thema online anzeigen", um diese Seite in einem bearbeitbaren Modus und zusammen mit den ursprünglichen englischen Inhalt gleichzeitig anzuzeigen. |
| MT_QualityNonEditable | In diesem Artikel wurde maschinell übersetzt. Wenn Sie eine Internetverbindung verfügen, wählen Sie "Dieses Thema online anzeigen", um diese Seite in einem bearbeitbaren Modus und zusammen mit den ursprünglichen englischen Inhalt gleichzeitig anzuzeigen. |
| MT_BetaContents | In diesem Artikel wurde maschinell übersetzt, die für eine vorläufige Version. Wenn Sie eine Internetverbindung verfügen, wählen Sie "Dieses Thema online anzeigen", um diese Seite in einem bearbeitbaren Modus und zusammen mit den ursprünglichen englischen Inhalt gleichzeitig anzuzeigen. |
| MT_BetaRecycledContents | In diesem Artikel wurde für eine Vorabversion manuell übersetzt. Wenn Sie eine Internetverbindung verfügen, wählen Sie "Dieses Thema online anzeigen", um diese Seite in einem bearbeitbaren Modus und zusammen mit den ursprünglichen englischen Inhalt gleichzeitig anzuzeigen. |
| Feature: | **LinkTable** |
| Verwenden: | Unterstützung für onlinethemas links |
| **Element** | **Wert** |
| LinkTableTitle | Verknüpfungstabelle |
| TopicEnuLinkText | Zeigen Sie die englische Version \< /a > dieses Themas, die auf Ihrem Computer verfügbar ist. |
| TopicOnlineLinkText | Dieses Thema anzeigen \<ein Href = "{0}" {1}> online \< /a > |
| OnlineText | Online |
| Feature: | **Video-Audiosteuerelement** |
| Verwenden: | Anzeigen von Elementen und Text für Videoinhalte |
| **Element** | **Wert** |
| MultiMediaNotSupported | Internet Explorer 9 oder höher muss installiert sein, für die Unterstützung {0} Inhalt. |
| VideoText | Video anzeigen |
| AudioText | Audio Streamen |
| OnlineVideoLinkText | \<p > um das Video zu diesem Thema anzuzeigen, klicken Sie auf {0} \<ein Href = "{1}" >{2}hier\</a >.\< / p > |
| OnlineAudioLinkText | \<p > um die Audioinhalte zu diesem Thema überwachen, klicken Sie auf {0} \<ein Href = "{1}" >{2}hier\</a >.\< / p > |
| Feature: | **Inhaltssteuerelement nicht installiert** |
| Verwenden: | Text-Elemente (Zeichenfolgen) für das Rendern von contentnotinstalled.htm verwendet |
| **Element** | **Wert** |
| ContentNotInstalledTitle | Es wurde kein Inhalt auf Ihrem Computer gefunden. |
| ContentNotInstalledDownloadContentText | \<p > um Inhalte auf Ihren Computer herunterladen \<ein Href = "{0}" {1}> Klicken Sie auf der Registerkarte "verwalten"\</a >.\< / p > |
| ContentNotInstalledText | \<p > Es ist kein Inhalt auf Ihrem Computer installiert. Finden Sie Ihren Administrator, um lokal installierte Hilfe-Inhalt zu.  \< /p > |
| Feature: | **Thema wurde nicht gefunden-Steuerelement** |
| Verwenden: | Text-Elemente (Zeichenfolgen) für das Rendern von topicnotfound.htm verwendet |
| **Element** | **Wert** |
| TopicNotFoundTitle | Angeforderte Thema auf Ihrem Computer wurde nicht gefunden. |
| TopicNotFoundViewOnlineText | \<p > die von Ihnen angeforderte Thema wurde nicht gefunden, auf dem Computer, aber Sie können \<ein Href = "{0}" {1}> das Thema online anzeigen\</a >.\< / p > |
| TopicNotFoundDownloadContentText | \<p > finden Sie im Navigationsbereich links zu ähnlichen Themen oder \<ein Href = "{0}" {1}> Klicken Sie auf der Registerkarte "verwalten"\</a >, Inhalte auf Ihren Computer herunterzuladen.\< / p > |
| TopicNotFoundText | \<p > die von Ihnen angeforderte Thema wurde auf dem Computer nicht gefunden.  \< /p > |
| Feature: | **Thema beschädigt Steuerelement** |
| Verwenden: | Text-Elemente (Zeichenfolgen) für das Rendern von topiccorrupted.htm verwendet |
| **Element** | **Wert** |
| TopicCorruptedTitle | Kann nicht das angeforderte Thema angezeigt. |
| TopicCorruptedViewOnlineText | \<p > Help Viewer kann nicht das angeforderte Thema angezeigt wird. Es gibt möglicherweise ein Fehler in der Inhalte des Themas oder einer zugrunde liegenden System-Abhängigkeit.  \< /p > |
| Feature: | **Startseite-Steuerelement** |
| Verwenden: | Text, die Unterstützung der Anzeige des Inhalts der Help Viewer-Knoten der obersten Ebene. |
| **Element** | **Wert** |
| HomePageTitle | Help Viewer – Startseite |
| HomePageIntroduction | \<p > Willkommen bei Microsoft Help Viewer, einer unverzichtbaren Informationsquelle für alle Benutzer, die Microsoft-Tools, Produkte, Technologien und Dienste verwendet. Help Viewer bietet Ihnen Zugriff auf Anleitungen und Referenzinformationen, Beispielcode, technischen Artikeln und mehr. Um den Inhalt zu suchen, den Sie das Inhaltsverzeichnis durchsuchen müssen, verwenden Sie den Volltext-Suchdienst, oder navigieren Sie durch die Inhalte, die mit dem Schlüsselwortindex.  \< /p > |
| HomePageContentInstallText | \<p >\<Br / > verwenden die \<ein Href = "{0}" {1}> Inhalt verwalten\</a > Registerkarte die folgenden Schritte ausführen:\<Ul >\<li > Hinzufügen von Inhalt auf Ihrem Computer.\< / li >\<li > Suchen nach Updates für Ihre lokalen Inhalt.\< / li >\<li > Entfernen Sie Inhalte von Ihrem Computer.\< / li >\</UL > \< /p > |
| HomePageInstalledBooks | Installierte Bücher |
| HomePageNoBooksInstalled | Es wurde kein Inhalt auf Ihrem Computer gefunden. |
| HomePageHelpSettings | Einstellungen für Hilfeinhalt |
| HomePageHelpSettingsText | \<p > die aktuelle Einstellung wird die lokale Hilfe. Help Viewer zeigt Inhalte, die Sie auf Ihrem Computer installiert haben. \<Br / > Wählen Sie zum Ändern Ihrer Quelle der Hilfeinhalte, in der Visual Studio-Menüleiste \<span Style = "{0}" > Hilfe, Hilfeeinstellungen festlegen\</span >.\< Br / > \< /p > |
| MB | MB |

**Branding.js**

Die branding.js-Datei enthält, die von Visual Studio Help Viewer Brandingelemente verwendet JavaScript.  Im folgenden finden eine Liste der Brandingelemente und die unterstützenden JavaScript-Funktion.  Alle Zeichenfolgen, die für diese Datei lokalisiert werden, werden im Abschnitt "Lokalisierbaren Zeichenfolgen" am oberen Rand dieser Datei definiert.  ICL-Datei wurde für die Lokalisierung von Zeichenfolgen in der Datei branding.js erstellt.

||||
|-|-|-|
|**Branding-Funktion**|**JavaScript-Funktion**|**Beschreibung**|
|Var...||Definieren Sie Variablen|
|Die Codesprache des Benutzers abrufen|setUserPreferenceLang|Ordnet einen Index um Codesprache|
|Festlegen und Abrufen von Cookiewerten|GetCookie, setCookie||
|Geerbte Member|changeMembersLabel|Geerbten Member aufklappen/Zuklappen|
|Wenn SelfBranded = "false"|onLoad|Lesen Sie die Abfragezeichenfolge, um festzustellen, ob es sich um eine druckanforderung handelt.  Legen Sie alle Codesnippets bevorzugte Registerkarte "Benutzer" zu konzentrieren.  Wenn es sich um eine druckanforderung handelt, müssen Sie festlegen Sie IsPrinterFriendly auf "true". Suchen Sie nach dem Modus für hohe Kontraste.|
|Codeausschnitt|addSpecificTextLanguageTagSet||
||getIndexFromDevLang||
||Änderungsobjekte||
||setCodesnippetLang||
||setCurrentLang||
||CopyToClipboard||
|CollapsibleArea|addToCollapsibleControlSet|Schreiben Sie alle das reduzierbare Steuerelement-Objekt, in der Liste.|
||CA_Click|basierend auf den Zustand des reduzierbaren Bereich, der definiert, welcher Bild- und präsentieren|
|Kontrast-Unterstützung für Logo|isBlackBackground()|Wird aufgerufen, um festzustellen, ob der Hintergrund Schwarz ist.  Nur präzise, wenn im Modus für hohe Kontraste.|
||isHighContrast()|Verwenden Sie eine farbige Spanne zum Erkennen der Modus für hohe Kontraste|
||onHighContrast(black)|Wird aufgerufen, wenn es sich bei hoher Kontrast erkannt wird|
|LST-Funktion|||
||addToLanSpecTextIdSet(id)||
||updateLST(currentLang)||
||getDevLangFromCodeSnippet(lang)||
|MultiMedia-Funktionalität|Caption (beginnen, Ende, Text, Stil)||
||findAllMediaControls(normalizedId)||
||getActivePlayer(normalizedId)||
||captionsOnOff(id)||
||toSeconds(t)||
||getAllComments(node)||
||StyleRectify (Formatvorlage, StyleValue)||
||showCC(id)||
||Subtitle(ID)||

**HTM-DATEIEN**

Das branding-Paket enthält eine Reihe von HTM-Dateien, die für die Kommunikation von Schlüsselinformationen für Benutzer der Hilfe-Inhalt, z. B. eine Startseite, die enthält einen Abschnitt beschreiben, welche Inhalte legt installiert sind und Seiten, die darüber informiert, dass bei Themen können nicht unterstützen gefunden Sie in der lokalen Gruppe der Themen werden. Diese HTM-Dateien können pro Produkt geändert werden.  ISO-Shell-Anbietern können das Standardpaket von branding und ändern Sie das Verhalten und die Inhalte dieser Seiten in der Suite Ihren.  Diese Dateien finden Sie in ihren jeweiligen branding-Paket in der Reihenfolge für die branding-Tags, die entsprechenden Inhalte aus der Datei branding.xml abzurufen.

||||
|-|-|-|
|**Datei**|**Verwendung**|**Inhaltsquelle angezeigt**|
|Homepage.htm|Dies ist eine Seite, die derzeit installierten Inhalt und alle anderen Nachrichten, die entsprechend dem Benutzer über deren Inhalt angezeigt.  Diese Datei enthält zusätzlichen Meta-Attribut "Microsoft.Help.Id" den Dateninhalt der = "1", das dies oben auf der lokalen Inhalt Inhaltsverzeichnis Inhalt platziert.||
||&LT; META_HOME_PAGE_TITLE_ADD / &GT;|Branding.XML, Tag \<HomePageTitle >|
||&LT; HOME_PAGE_INTRODUCTION_SECTION_ADD / &GT;|Branding.XML, Tag \<HomePageIntroduction >|
||&LT; HOME_PAGE_CONTENT_INSTALL_SECTION_ADD / &GT;|Branding.XML, Tag \<HomePageContentInstallText >|
||&LT; HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD / &GT;|Überschrift des Abschnitts Branding.xml Tag\<HomePageInstalledBooks >, die von der Anwendung generierten Daten \<HomePageNoBooksInstalled > Wenn keine Bücher installiert sind.|
||&LT; HOME_PAGE_SETTINGS_SECTION_ADD / &GT;|Überschrift des Abschnitts Branding.xml Tag \<HomePageHelpSettings >, im Abschnitt Text \<HomePageHelpSettingsText >.|
|topiccorrupted.htm|Wenn ein Thema in der lokalen Gruppe vorhanden ist, aber für den aus irgendeinem Grund nicht angezeigt werden kann (Inhalte beschädigt).||
||&LT; META_TOPIC_CORRUPTED_TITLE_ADD / &GT;|Branding.XML, Tag \<TopicCorruptedTitle >|
||&LT; TOPIC_CORRUPTED_SECTION_ADD / &GT;|Branding.XML, Tag \<TopicCorruptedViewOnlineText >|
|topicnotfound.htm|Wenn ein Thema nicht in den lokalen Inhalt festgelegt werden, noch verfügbar online gefunden wird||
||&LT; META_TOPIC_NOT_FOUND_TITLE_ADD / &GT;|Branding.XML, Tag \<TopicNotFoundTitle >|
||&LT; META_TOPIC_NOT_FOUND_ID_ADD / &GT;|Branding.XML, Tag \<TopicNotFoundViewOnlineText > + \<TopicNotFoundDownloadContentText >|
||&LT; TOPIC_NOT_FOUND_SECTION_ADD / &GT;|Branding.XML, Tag \<TopicNotFoundText >|
|contentnotinstalled.htm|Wenn Sie keinen lokalen Inhalt für das Produkt installiert.||
||&LT; META_CONTENT_NOT_INSTALLED_TITLE_ADD / &GT;|Branding.XML, Tag \<ContentNotInstalledTitle >|
||&LT; META_CONTENT_NOT_INSTALLED_ID_ADD / &GT;|Branding.XML, Tag \<ContentNotInstalledDownloadContentText >|
||&LT; CONTENT_NOT_INSTALLED_SECTION_ADD / &GT;|Branding.XML, Tag \<ContentNotInstalledText >|

**CSS-Dateien**

Die Visual Studio Help Viewer Branding-Paket enthält zwei Css-Dateien, um konsistente Content Hilfe zu Visual Studio-Präsentation zu unterstützen:

-   Branding.CSS - enthält Css-Elemente für das Rendern von Where SelfBranded = "false"

-   Printer.CSS - enthält Css-Elemente für das Rendern von Where SelfBranded = "false"

Branding.CSS-Dateien enthalten Definitionen für die Darstellung der Visual Studio-Thema (Nachteil ist, dass die branding.css in die Branding_ enthalten\<Gebietsschema > mshc aus dem Paketdienst kann sich ändern).

**Grafikdateien**

Inhalte zu Visual Studio zeigt eine Visual Studio-Logo als auch für andere Grafik.  Die vollständige Liste der Grafikdateien in Visual Studio Help Viewer Brandingpakets ist unten dargestellt.

||||
|-|-|-|
|**Datei**|**Verwendung**|**Beispiele**|
|Clear.gif|Zum Rendern von reduzierbaren Bereich verwendet||
|footer_slice.gif|Fußzeile Präsentation||
|info_icon.gif|Zum Anzeigen von Informationen|Haftungsausschluss|
|online_icon.gif|Dieses Symbol ist online Links zugeordnet werden soll||
|tabLeftBD.gif|Verwendet, um den Code-Ausschnitt-Container zu rendern.||
|tabRightBD.gif|Verwendet, um den Code-Ausschnitt-Container zu rendern.||
|vs_logo_bk.gif|Für normale Kontrast-Logo-Verweise verwendet werden, wie im Branding.xml Tag definiert \<LogoFileName >.  Für Visual Studio-Produkten ist die Logo-Name vs_logo_bk.gif.||
|vs_logo_wh.gif|Für normale hohe Logo Verweise verwendet werden, wie im Branding.xml Tag definiert \<LogoFileNameHC >.  Für Visual Studio-Produkten ist die Logo-Name vs_logo_wh.gif.||
|ccOff.png|Grafik zu Untertitel||
|ccOn.png|Grafik zu Untertitel||
|ImageSprite.png|Zum Rendern von reduzierbaren Bereich verwendet|erweitert oder reduziert Grafik|

### <a name="deploying-a-set-of-topics"></a>Bereitstellen einer Reihe von Themen
Dies ist eine einfache und schnelle Tutorial zum Erstellen eines Help Viewer beim Bereitstellen von Inhalt einer diese MSHA-Datei und den Satz der CAB-Dateien oder MSHCs, enthält die Themen umfassen. Die MSHA ist eine XML-Datei, die beschreibt, einen Satz von CAB-Dateien oder MSHC-Dateien. Help Viewer kann die zum Abrufen einer Liste von Inhalten (der. MSHA lesen. CAB-Datei oder. MSHC-Dateien) für die lokale Installation verfügbar.

Dies ist nur eine Einführung, die das einfache XML-Schema für die MSHA-Hilfe-Viewer beschreibt.  Es ist eine Beispiel einer Implementierung unterhalb dieses kurze Übersicht und Beispiel "HelpContentSetup.msha".

Der Name des der MSHA, im Rahmen dieser Einführung ist "HelpContentSetup.msha" (der Name der Datei kann alles mit der Erweiterung sein. DIESE MSHA). "HelpContentSetup.msha" (nachfolgendes Beispiel), sollte eine Liste der CAB-Dateien oder MSHCs verfügbaren enthalten.  Der Dateityp muss innerhalb der MSHA konsistent sein (bietet keine Unterstützung für eine Kombination der Typen für diese MSHA und CAB-Dateien). Für jede CAB-Datei oder MSHC, dürfte eine \<Div-Klasse = "packen" >...  \< /div > (siehe folgendes Beispiel).

Hinweis: in der folgenden Implementierungsbeispiel haben wir das branding-Paket integriert. Dies ist wichtig, aufnehmen, damit um die erforderlichen Visual Studio Inhalt Rendern von Elementen und das Verhalten zu erhalten.

Die Datei "HelpContentSetup.msha" Beispiel: (ersetzen Sie "Inhalt set Name 1" und "Set name 2" usw. mit Ihren Dateinamen Inhalt.)

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

1.  Erstellen Sie lokalen Ordner, etwa "C:\SampleContent"

2.  In diesem Beispiel verwenden wir MSHC-Dateien in den Themen zu enthalten.  Ein MSHC ist eine ZIP-Datei mit der Dateierweiterung in .zip, geändert. MSHC.

3.  Erstellen Sie die unter "HelpContentSetup.msha" als Textdatei (Editor zum Erstellen der Datei verwendet wurde) und speichern Sie sie in den oben genannten Ordner (siehe Schritt 1).

Die Klasse "Branding" ist vorhanden und eindeutig ist. Das Branding Mshc umfasst diese Einführung, damit die installierten Inhalte branding haben und die Verhalten, die in der MSHCs enthalten sind, müssen die entsprechende Unterstützung Elemente in der branding-Paket werden. Ohne diesen Schritt Fehler ausgegeben, wenn das System nach Unterstützung-Elemente, die nicht Teil der kopierten sucht (installiert) sind Inhalte.

Kopieren Sie zum Abrufen der Visual Studio-Paket branding Branding_en-US.mshc-Datei unter C:\Program Files (x86) \Microsoft Help Viewer\v2.3\ Arbeitsordner.

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

Verwenden und erweitern die oben genannten Schritte können VSPs, deren Inhalt legt für die Visual Studio Help Viewer bereitstellen.

### <a name="adding-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Hinzufügen von Hilfe zu Visual Studio Shell (integriert und isoliert)
**Introduction (Einführung)**

In dieser exemplarischen Vorgehensweise veranschaulicht die Hilfe-Inhalt in einer Visual Studio Shell-Anwendung integrieren und diese dann bereitstellen.

**Anforderungen**

1.  [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]

2.  [Visual Studio 2013 isolierte Shell-Redist](http://www.microsoft.com/visualstudio/11/downloads#vs-shell)

**Übersicht**

Die [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell ist eine Version von der [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] IDE, die auf der Grundlage können Sie eine Anwendung. Solche Anwendungen enthalten die Isolated Shell zusammen mit den Erweiterungen, die Sie erstellen. Verwendung der Isolated Shell-Projektvorlagen, die im enthalten sind die [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] SDK verwenden, um das Erweiterungen entwickeln.

Die grundlegenden Schritte zum Erstellen einer Isolated Shell-basierten Anwendung und die dazugehörige Hilfe:

1. Abrufen der [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] ISO Shell redistributable (ein Microsoft-Download).

2. Erstellen Sie in Visual Studio eine Hilfe-Erweiterung, die der Isolated Shell, z. B. basiert, die Contoso-Hilfe-Erweiterung, die weiter unten in dieser exemplarischen Vorgehensweise beschrieben wird.

3. Umschließen Sie die Erweiterung und der ISO-Shell redistributable in eine MSI-Datei (eine Anwendungssetup)-Bereitstellung. In dieser exemplarischen Vorgehensweise umfasst einen Schritt zum Einrichten nicht.

Erstellen Sie einen Visual Studio-Inhaltsspeicher. Ändern Sie für das Szenario Integrated Shell Visual Studio12, der Name des Katalogs Produkt wie folgt:

-   Erstellen Sie Ordner C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15.

-   Erstellen Sie eine Datei mit dem Namen "catalogtype.xml", und fügen sie den Ordner hinzu. Die Datei sollte die folgenden Codezeilen enthalten:

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <catalogType>UserManaged</catalogType>
    ```

Definieren Sie den Content Store in der Registrierung. Ändern Sie für die integrierte Shell VisualStudio15, in der Produktname des Katalogs:

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15

   Schlüssel: LocationPath Zeichenfolgenwert: C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15\

- HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15\en-US

   Schlüssel: CatalogName Zeichenfolgenwert: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Dokumentation

**Erstellen des Projekts**

So erstellen Sie eine isolierte Shell-Erweiterung:

1.  In Visual Studio unter **Datei**, wählen Sie **neues Projekt**unter **andere Projekttypen** wählen **Erweiterbarkeit**, und wählen Sie dann auf  **Visual Studio Shell isoliert**. Nennen Sie das Projekt `ContosoHelpShell`) ein Erweiterbarkeitsprojekt basierend auf der Visual Studio Isolated Shell-Vorlage zu erstellen.

2.  Öffnen Sie im Projektmappen-Explorer im Projekt im Ordner Ressourcendateien ContosoHelpShellUI ApplicationCommands.vsct aus. Stellen Sie sicher, dass (Suchen Sie nach "No_Help") diese Zeile auskommentiert ist: `<!-- <define name="No_HelpMenuCommands"/> -->`

3.  Wählen Sie die F5-Taste zum Kompilieren und ausführen **Debuggen**. Wählen Sie in der experimentellen Instanz der Isolated Shell-IDE, die **Hilfe** Menü. Stellen Sie sicher, dass die **Sicht Ihnen helfen,**, **hinzufügen und Entfernen von Hilfeinhalt**, und **Hilfeeinstellungen festlegen** Befehle angezeigt.

4.  Öffnen Sie im Projektmappen-Explorer im Ordner "Shell-Anpassung"-Projekt ContosHelpShell ContosoHelpShell.pkgdef aus. Um die Contoso-Hilfekatalog zu definieren, fügen Sie die folgenden Zeilen hinzu:

    ```
     [$RootKey$\Help]
    "Product"="Contoso"
    "Catalog"="Contoso"
    "Version"="100"
    "BrandingPackage"="ContosoBrandingPackage.mshc"
    ```

5.  Öffnen Sie im Projektmappen-Explorer im Ordner "Shell-Anpassung"-Projekt ContosHelpShell ContosoHelpShell.Application.pkgdef aus. Um F1-Hilfe zu aktivieren, fügen Sie die folgenden Zeilen hinzu:

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

6.  Wählen Sie im Projektmappen-Explorer im Kontextmenü der Projektmappe ContosoHelpShell der **Eigenschaften** Menüelement. Klicken Sie unter **Konfigurationseigenschaften**Option **Configuration Manager**. In der **Konfiguration** Spalte jeden Wert "Debug" auf "Release" zu ändern.

7.  Erstellen Sie die Projektmappe. Dies erstellt einen Satz von Dateien in einem Releaseordner, der im nächsten Abschnitt verwendet wird.

Um dies zu testen, als ob bereitgestellt:

1. Sie werden auf dem Computer Contoso möchten, installieren Sie das heruntergeladene ISO-Shell (erwähnte) bereitstellen.

2. Erstellen Sie einen Ordner in \\\Program Files (x86)\\, und nennen Sie sie `Contoso`.

3. Kopieren Sie den Inhalt aus dem ContosoHelpShell Freigabeordner auf \\Ordner "\Programme (x86) \Contoso\".

4. Starten des Registrierungs-Editor durch Auswahl **ausführen** in die **starten** Menü und eingeben `Regedit`. Wählen Sie im Registrierungs-Editor, **Datei**, und klicken Sie dann **Import**. Navigieren Sie zu dem Projektordner ContosoHelpShell. Wählen Sie in den Unterordner ContosoHelpShell ContosoHelpShell.reg ein.

5. Erstellen Sie einen Inhaltsspeicher an:

    Erstellen Sie einen Contoso Inhaltsspeicher C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12 für ISO-Shell-

    Für [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Integrated Shell, erstellen Sie Ordner C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15

6. Erstellen von "catalogtype.xml" und fügen Sie auf die Inhaltsspeicher (im vorherigen Schritt) mit:

   ```
   <?xml version="1.0" encoding="UTF-8"?>
   <catalogType>UserManaged</catalogType>
   ```

7. Fügen Sie die folgenden Registrierungsschlüssel hinzu:

    HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15Key: LocationPath-Zeichenfolgenwert:

    Für ISO-Shell:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15

    [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Integrierte Shell:

    C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en-USA

    Schlüssel: CatalogName Zeichenfolgenwert: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Dokumentation. Für ISO-Shell ist dies der Name des Katalogs.

8. Kopieren Sie Ihre Inhalte (CAB-Dateien oder MSHC und diese MSHA) in einen lokalen Ordner.

9. Integrierte Shell Beispielbefehlszeile zum Testen der Inhaltsspeicher. Für ISO-Shell können ändern Sie die Katalog- und LaunchingApp Werte nach Bedarf das Produkt entsprechend.

     "C:\Programme\Microsoft Dateien (x86) \Microsoft Help Viewer\v2.3\HlpViewer.exe" CatalogName VisualStudio15 /helpQuery Methode = "Seite" & Id = ContosoTopic0 "/launchingApp Microsoft VisualStudio, 12.0

10. Starten Sie die Contoso-Anwendung (ausgehend vom Stamm des Contoso-app). Wählen Sie aus ISO-Shell, die **helfen** Menüelement, und ändern Sie die **Hilfeeinstellungen festlegen** zu **verwenden der lokalen Hilfe**.

11. Wählen Sie in der Shell die **Hilfe** Menüelement, klicken Sie dann **Sicht Ihnen helfen,**. Lokale Hilfe-Viewer sollte gestartet werden. Wählen Sie die Registerkarte **Inhalt verwalten** aus. Klicken Sie unter **Installationsquelle**, wählen Sie die **Datenträger** Optionsfeld aus. Wählen Sie die **...**  Schaltfläche, und navigieren Sie zu den lokalen Ordner, der Contoso-Inhalt (in den lokalen Ordner im vorherigen Schritt kopiert) enthält. Wählen Sie die Datei "HelpContentSetup.msha". Contoso sollte jetzt als ein Buch in der Auswahl der Buch angezeigt werden. Wählen Sie **hinzufügen**, und wählen Sie dann die **Update** Schaltfläche (unten rechts).

12. Wählen Sie in der Contoso-IDE die F1-Taste F1 Funktionalität testen.

### <a name="additional-resources"></a>Zusätzliche Ressourcen

Die Common Language Runtime-API, finden Sie unter [Windows-Hilfe-API-](/previous-versions/windows/desktop/helpapi/helpapi-portal).

Weitere Informationen zum Nutzen der Hilfe-API finden Sie unter [Help Viewer-Codebeispiele](https://marketplace.visualstudio.com/items?itemName=RobChandlerHelpMVP.HelpViewer20CodeExamples).

Sie können Vorschläge für Features senden, auf [Entwicklercommunity](https://developercommunity.visualstudio.com/content/idea/post.html?space=8).