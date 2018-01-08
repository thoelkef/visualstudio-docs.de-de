---
title: Microsoft Help Viewer SDK | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
caps.latest.revision: "33"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7c15956bc861f9eb20267dc97446cf5ea49cae31
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="microsoft-help-viewer-sdk"></a>Microsoft Help Viewer SDK
Dieser Artikel enthält die folgenden Aufgaben für Visual Studio Help Viewer Integratoren:  
  
-   Erstellen ein Thema (F1-Unterstützung)  
  
-   Erstellen eines Pakets für die Hilfe-Viewer-Inhalt-branding  
  
-   Bereitstellen einer Reihe von Artikeln  
  
-   Hinzufügen von Hilfe für die Visual Studio-Shell (integriert oder isoliert)  
  
-   Zusätzliche Ressourcen  
  
### <a name="creating-a-topic-f1-support"></a>Erstellen ein Thema (F1-Unterstützung)  
Dieser Abschnitt enthält eine Übersicht über die Komponenten von einem Thema vorgestellt, die Thema-Anforderungen, die eine kurze Beschreibung zum Erstellen eines Themas (einschließlich Supportanforderungen F1) und schließlich eine Beispielthema durch das gerenderte Ergebnis.  
  
**Hilfeanzeige Thema (Übersicht)**  
  
Wenn ein Thema für das Rendering aufgerufen wird, ruft das branding Paketelemente, die im Thema zum Zeitpunkt der Installation oder der letzten Aktualisierung, zusammen mit dem Thema XHTML, zugeordnet sind und kombiniert die beiden um in der dargestellten Inhaltsansicht führen Help Viewer (branding Daten + themendaten).  Brandingpakets enthält Logos, Unterstützung für Inhalt Verhalten und Brandingtext (copyright usw.).  Weitere Informationen zu den branding Paketelemente finden Sie unter "Erstellen von Branding-Paket" unten.  Im Ereignisprotokoll kein branding Paket mit dem Thema verknüpft sind ist, wird der Hilfeviewer fallback Brandingpakets befindet sich im Stammverzeichnis Help Viewer-Anwendung (Branding_en US.mshc) verwenden.  
  
**Hilfe-Viewer Thema Anforderungen**  
  
Ordnungsgemäß in der Hilfe-Viewer gerendert werden, muss der Inhalt für unformatierte Thema W3C grundlegende 1.1 XHTML.  
  
Ein Thema enthält in der Regel zwei Abschnitte:  
  
-   Metadaten (Siehe Content Metadatenverweis): Daten zum Thema, z. B. das Thema eindeutige ID, die Schlüsselwort-Wert, der Thema TOC-ID, übergeordneten Knoten-ID usw.  
  
-   Text-Inhalt: W3C grundlegende 1.1 XHTML einhalten inklusive unterstützt Inhalt Verhaltensweisen (reduzierbaren Bereich, Codeausschnitt, usw. Eine vollständige Liste wird unten gezeigt).  
  
Visual Studio-Branding-Paket unterstützt Steuerelemente:  
  
-   Links  
  
-   CodeSnippet  
  
-   CollapsibleArea  
  
-   Geerbte Member  
  
-   LanguageSpecificText  
  
Unterstützte sprachenzeichenfolgen (ohne Beachtung von Groß-/Kleinschreibung):  
  
-   JavaScript  
  
-   CSharp oder c#  
  
-   Cplusplus oder Visual c++ oder c ++  
  
-   JScript  
  
-   VisualBasic oder vb  
  
-   f#- oder Fsharp oder fs  
  
-   andere – eine Zeichenfolge, einen Sprachnamen darstellt.  
  
**Erstellen ein Thema Help Viewer**  
  
Erstellen Sie ein neues XHTML-Dokument mit dem Namen ContosoTopic4.htm, und schließen Sie das Title-Tag (siehe unten).  
  
```html  
<html>  
<head>  
<title>Contoso Topic 4</title>  
</head>  
  
<body>  
  
</body>  
</html>  
  
```  
  
Als Nächstes fügen Sie Daten zum definieren, wie im Thema (Selbstprofil Marke oder nicht), dargestellt werden soll wie zu diesem Thema für F1 verweisen, in dem in diesem Thema im Inhaltsverzeichnis, dessen ID (für Verknüpfungsverweis durch andere Themen) vorhanden ist, usw.  Finden Sie unter "Inhaltsmetadaten" der nachfolgenden Tabelle eine vollständige Liste der unterstützten Metadaten.  
  
-   In diesem Fall werden wir unser eigenes branding-Paket eine Variante des Visual Studio Help Viewer Brandingpakets verwenden.  
  
-   Fügen Sie die F1-Meta-Name und Wert ("Microsoft.Help.F1" Content = "ContosoTopic4"), wird den angegebenen Wert von F1 in der Eigenschaftensammlung IDE entsprechen.  (Siehe Abschnitt F1-Unterstützung für Weitere Informationen.)   Dies ist der Wert, der mit F1 übereinstimmende rufen Sie in der IDE, in diesem Thema angezeigt wird, wenn Sie F1 in der IDE ausgewählt wird.  
  
-   Fügen Sie die Thema-ID. Dies ist die Zeichenfolge, die von anderen Themen verwendet wird, für die Verbindung zu diesem Thema.  Es ist die Hilfe-Viewer-ID in diesem Thema.  
  
-   Fügen Sie für das Inhaltsverzeichnis in diesem Thema übergeordneten Knoten, um zu definieren, wo dieses Thema Inhaltsverzeichnisknoten angezeigt wird.  
  
-   Fügen Sie für das Inhaltsverzeichnis Knotenreihenfolge in diesem Thema. Wenn der übergeordnete Knoten n: die Anzahl der untergeordneten Knoten verfügt, definieren Sie in der Reihenfolge der untergeordneten Knoten Speicherort des Themas. Dieses Thema ist deutet, Anzahl 4 4 untergeordneten Themen.)  
  
Beispiel-Metadaten-Abschnitt:  
  
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
  
Der Text (einschließlich nicht die Kopf- und Fußzeile) des Themas enthält Seitenlinks, einen Abschnitt Hinweis, einen reduzierbaren Bereich, einen Codeausschnitt und einen Abschnitt eines bestimmten Text in einer Sprache.  Finden Sie im Abschnitt branding Informationen zu diesen Bereichen der im vorliegenden Thema.  
  
1.  Fügen Sie ein Thema-Tag hinzu:`<div class="title">Contoso Topic 4</div>`  
  
2.  Fügen Sie einen Hinweis-Abschnitt hinzu:`<div class="alert"> add your table tag and text </div>`  
  
3.  Fügen Sie einem reduzierbaren Bereich hinzu:`<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`  
  
4.  Fügen Sie einen Codeausschnitt an:`<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`  
  
5.  Fügen Sie Code Sprache bestimmtem Text hinzu: `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` Beachten Sie, DevLangnu = können Sie andere Sprachen eingeben. Beispielsweise DevLangnu = "Fortran" zeigt Fortran bei der Codeausschnitt DisplayLanguage = Fortran  
  
6.  Fügen Sie die Seite enthält Links hinzu:`<a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>`  
  
> [!NOTE]
>  Hinweis: für nicht unterstützte neue "Anzeigesprache" (z. B., f#, Cobol, Fortran) wird der farbliche Kennzeichnung von Code im Codeausschnitt Monochrom sein.  
  
**Beispiel-Viewer-Hilfethema** im Code wird veranschaulicht, wie Sie Metadaten, einen Codeausschnitt, einen reduzierbaren Bereich und Text in einer bestimmten Sprache zu definieren.  
  
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
  
In Visual Studio F1 auswählen, wird von der Position des Cursors in der IDE übergebenen Werte generiert, und füllt eine "Eigenschaftensammlung" mit den angegebenen Werten (auf der Grundlage der Cursorposition. Wenn sich der Cursor über Funktion X befindet, Feature X aktiv/im Fokus ist, und Eigenschaftenbehälter mit Werten aufgefüllt.  Wenn F1 ausgewählt wird, die Eigenschaftensammlung wird aufgefüllt, und Visual Studio-F1-Code sieht, um festzustellen, ob die Kunden Hilfe Standardquelle lokalen oder online ist (online ist die Standardeinstellung), erstellt dann die entsprechende Zeichenfolge basierend auf den Benutzer festlegen (online ist die Standardeinstellung) - Verwaltungsshell ausführen (Siehe im Hilfe-Administratorhandbuch Exe Parameter starten) mit Parametern für die lokale Hilfe-Viewer + Schlüsselwörter aus dem Eigenschaftenbehälter lokale Hilfe ist der Standardwert oder die MSDN-URL mit dem Schlüsselwort in der Parameterliste.  
  
Wenn drei Zeichenfolgen für F1 zurückgegeben werden, bezeichnet als eine mehrwertige Zeichenfolge dem ersten Ausdruck suchen einen Treffer akzeptieren, und wenn gefunden, wir fertig sind; Wenn dies nicht der Fall ist, auf die nächste Zeichenfolge verschieben.  Reihenfolge von Bedeutung. Präsentation der Schlüsselwörter mit mehreren Werten sollte die längste Zeichenfolge, die kürzeste Zeichenfolge sein.  Um dies bei mehreren Werten bestehenden Schlüsselwörter zu überprüfen, sehen Sie sich die online F1 URL-Zeichenfolge, die das ausgewählte Schlüsselwort enthalten.  
  
In Visual Studio 2012 treffen wir diese absichtlich eine stärkere Division zwischen dem Online- und offline geschaltet wird, sodass, wenn der Benutzer-Einstellung für Online war, klicken Sie dann wir einfach die F1-Anforderung direkt an unsere online-Abfragedienst auf MSDN, statt Weiterleitung durch den Bibliothek-Agent übergeben dass wir in Visual Studio 2010 veraltet. Wir dann basieren auf den Status "Hersteller Inhalt installiert =" true "" bestimmt, ob eine Aktion in diesem Kontext unterschiedlich. Bei "true", bieten wir diese Logik Analyse- und routing, je nachdem, was Sie für Ihre Kunden unterstützen möchten. Wenn "false", wechseln Sie dann wir nur auf MSDN. Wenn lokale-Einstellung des Benutzers handelt, gehen alle Aufrufe einfach an das Modul für die lokale Hilfe.  
  
F1-Flussdiagramm:  
  
![F1-Fluss](../../extensibility/internals/media/f1flow.png "F1flow")  
  
Wenn der Help Viewer standardmäßig die Quelle der Hilfeinhalte auf online (Start im Browser) festgelegt ist:  
  
-   Funktionen von Visual Studio-Partner (VSP) ausgeben, einen Wert auf der Eigenschaftensammlung F1 (Eigenschaftenbehälter prefix.keyword und online-URL für das Präfix, das in der Registrierung gefunden): F1 sendet eine VSP-URL-Parameter an den Browser.  
  
-   Visual Studio-Funktionen (Sprach-Editor, Visual Studio bestimmte Menüelemente usw.): F1 sendet eine Visual Studio-URL an den Browser.  
  
Wenn der Help Viewer standardmäßig die Quelle der Hilfeinhalte auf lokale Hilfe (im Help Viewer starten) festgelegt ist:  
  
-   VSP-Funktionen, bei denen Schlüsselwort übereinstimmen, zwischen Eigenschaftenbehälter F1 und lokalen columnstore-Index (d. h. die Eigenschaftenbehälter prefix.keyword = der Wert in der lokalen columnstore-Index gefunden): F1 rendert das Thema in der Hilfe-Viewer.  
  
-   Visual Studio-Funktionen (keine Option für die VSP überschreiben die Eigenschaftensammlung ausgegeben, die von Visual Studio-Features): F1 rendert ein Visual Studio-Thema in der Hilfe-Viewer.  
  
Legen Sie die folgenden Registrierungswerte F1 Fallback für Hersteller Hilfeinhalt zu aktivieren. F1 Fallback bedeutet, dass der Help Viewer F1-Hilfe Inhalt gesucht online festgelegt ist, und der Hersteller-Inhalt auf der benutzerfestplatte lokal installiert ist. Help Viewer sollten lokale Hilfe für den Inhalt betrachten, obwohl die Standardeinstellung für online-Hilfe ist.  
  
1.  Legen Sie die **VendorContent** Wert unter dem Registrierungsschlüssel 2.3 helfen:  
  
    -   Für 32-Bit-Betriebssysteme:  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Catalogs\VisualStudio15  
  
         "VendorContent" = DWORD: 00000001  
  
    -   Für 64-Bit-Betriebssysteme:  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15  
  
         "VendorContent" = DWORD: 00000001  
  
2.  Registrieren Sie den Partner-Namespace unter dem Registrierungsschlüssel 2.3 helfen:  
  
    -   Für 32-Bit-Betriebssysteme:  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.3\Partner*\\< Namespace\>*  
  
         "Speicherort"="offline"  
  
    -   Für 64-Bit-Betriebssysteme:  
  
         HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Partner*\\< Namespace\>*  
  
         "Speicherort"="offline"  
  
**Analysieren von einheitlichen Namespace basieren**  
  
Um native Basisnamespace Analyse zu aktivieren, in der Registrierung hinzufügen einen neuen DWORD-Wert mit dem Namen: BaseNativeNamespaces und legen Sie dessen Wert auf 1 (unter dem Katalog-Schlüssel, die sie unterstützen möchten).  Wenn Sie den Visual Studio-Katalog verwenden möchten, können Sie z. B. den Schlüssel auf den Pfad hinzufügen:  
  
HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15
  
Wenn ein F1-Schlüsselwort in das Format, das HEADER-Methode gefunden wird, wird das Zeichen '/', analysiert werden, führt das folgende Konstrukt:  
  
-   HEADER: werden der Namespace, der verwendet werden kann, um in der Registrierung zu registrieren.  
  
-   Methode: Dadurch wird das Schlüsselwort darstellen, das über übergeben werden.  
  
Angenommen, eine benutzerdefinierte Bibliothek CustomLibrary aufgerufen und eine Methode namens "MyTestMethod", wenn eine Anforderung, darin eingeht F1 formatiert `CustomLibrary/MyTestMethod`.  
  
Ein Benutzer kann dann CustomLibrary als Namespace Hive Partner registrieren, und geben Sie den Speicherort-Schlüssel, die sie erhalten möchten, und das Schlüsselwort, das an die Abfrage übergeben wird "MyTestMethod" verwendet werden.  
  
**Aktivieren Sie Hilfe-Tool in der IDE Debuggen**  
  
Fügen Sie den folgenden Registrierungsschlüssel und den Wert an:  
  
Hilfe-Taste HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\15.0\Dynamic: Debug-Ausgabe im Einzelhandel Wert anzeigen: Ja  
  
Wählen Sie in der IDE unter das Hilfemenüelement "Hilfekontext Debuggen"  
  
**Inhaltsmetadaten**  
  
In der folgenden Tabelle ist eine Zeichenfolge, die zwischen den Klammern angezeigt ein Platzhalter, der von einem bekannten Wert ersetzt werden muss. Z. B. in \<Meta name="Microsoft.Help.Locale" Content = "[Sprachcode]" / >, "[Sprachcode]" ersetzt werden muss durch einen Wert wie "En-us".  
  
|Eigenschaft (HTML-Darstellung)|Beschreibung|  
|--------------------------------------|-----------------|  
|\<Meta-name="Microsoft.Help.Locale" Content = "[Sprachcode]" / >|Legt ein Gebietsschema in diesem Thema. Wenn dieses Tag in einem Thema verwendet wird, muss nur einmal verwendet werden und müssen Sie über keine anderen Microsoft Help Tags eingefügt werden. Wenn dieses Tag nicht verwendet wird, wird der Textkörper des Themas indiziert, mithilfe von wörtertrennung, die das Produktgebietsschema zugeordnet ist, wenn er angegeben wird; andernfalls, die En-us wörtertrennung verwendet wird. Dieses Tag entspricht dem Standard RFC 4646 ISOC. Um sicherzustellen, dass Microsoft Help ordnungsgemäß funktioniert, verwenden Sie diese Eigenschaft anstelle der allgemeinen Language-Attribut.|  
|\<Meta-name="Microsoft.Help.TopicLocale" Content = "[Sprachcode]" / >|Legt ein Gebietsschema für dieses Thema, wenn auch andere Gebietsschemas verwendet werden. Wenn dieses Tag in einem Thema verwendet wird, muss sie nur einmal verwendet werden. Verwenden Sie dieses Tag, wenn der Katalog Inhalt in mehr als einer Sprache enthält. Mehrere Themen in einem Katalog können dieselbe ID haben, aber jeder muss eine eindeutige TopicLocale angeben. Das Thema, das eine TopicLocale angibt, die dem Gebietsschema des Katalogs entspricht, ist das Thema, das im Inhaltsverzeichnis angezeigt wird. Allerdings werden alle Sprachversionen des Themas in den Suchergebnissen angezeigt.|  
|\<Titel > [Title] \< /title >|Gibt den Titel dieses Themas. Dieses Tag ist erforderlich und muss nur einmal in einem Thema verwendet werden. Wenn der Text des Themas keinen Titel \<Div > Abschnitt dieser Titel wird in diesem Thema und im Inhaltsverzeichnis angezeigt.|  
|\<Meta Name = "Microsoft.Help.Keywords" Content = "[aKeywordPhrase]" / >|Gibt den Text einer Verknüpfung, die im Index Bereich des Help Viewers angezeigt wird. Wenn auf der Link geklickt wird, wird das Thema angezeigt. Sie können mehrere Indexschlüsselwörter für ein Thema angeben, oder Sie können dieses Tag weglassen, wenn Sie nicht, dass Links zu diesem Thema im Index angezeigt werden möchten. "K" Schlüsselwörter aus früheren Versionen von Hilfe können an dieser Eigenschaft konvertiert werden.|  
|\<Meta-name="Microsoft.Help.Id" Content = "[TopicID]" / >|Legt fest, den Bezeichner für die in diesem Thema. Dieses Tag ist erforderlich und muss nur einmal in einem Thema verwendet werden. Die ID muss für Themen im Katalog eindeutig sein, die die gleiche Gebietsschema festgelegt wurde. In einem anderen Thema können Sie einen Link zu diesem Thema erstellen, indem Sie mit dieser ID an.|  
|\<Meta-name="Microsoft.Help.F1" content="[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator]"/ >|Gibt die F1-Schlüsselwort in diesem Thema. Sie können mehrere F1-Schlüsselwörter für ein Thema angeben, oder Sie können dieses Tag weglassen, wenn Sie nicht in diesem Thema angezeigt, wenn ein Anwendungsbenutzer F1 drückt möchten. In der Regel wird nur ein F1-Schlüsselwort für ein Thema angegeben. "F" Schlüsselwörter aus früheren Versionen von Hilfe können an dieser Eigenschaft konvertiert werden.|  
|\<Meta Name = "Description" Content = "[Thema Description]" / >|Enthält eine kurze Zusammenfassung des Inhalts in diesem Thema. Wenn dieses Tag in einem Thema verwendet wird, muss sie nur einmal verwendet werden. Diese Eigenschaft wird direkt von der Abfrage-Bibliothek zugegriffen; Es ist nicht in die Indexdatei gespeichert.|  
 Meta-name="Microsoft.Help.TocParent" Content = "[Parent_Id]" / >|Gibt das übergeordnete Thema in diesem Thema im Inhaltsverzeichnis an. Dieses Tag ist erforderlich und muss nur einmal in einem Thema verwendet werden. Der Wert ist die Microsoft.Help.Id des übergeordneten Elements. Ein Thema kann nur einem Ort in der Tabelle der Inhalte verfügen. Themen-ID für den Stammknoten Inhaltsverzeichnis gilt als "-1". In [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)], diese Seite ist die Startseite der Hilfe-Viewer. Dies ist aus demselben Grund, dass es insbesondere TocParent =-1 hinzufügen, auf einige Themen, um sicherzustellen, dass sie auf der obersten Ebene angezeigt. Die Startseite der Hilfe-Viewer wird eine Seite "System" und daher nicht austauschbare. Wenn eine VSP versucht, eine Seite mit der ID "-1" hinzufügen, es möglicherweise Inhaltssatzes hinzugefügt, aber Hilfeviewer verwendet immer die Seite "System" – Startseite der Hilfe-Viewer|  
|\<Meta-name="Microsoft.Help.TocOrder" Content = "[positive ganze Zahl]" / >|Gibt an, wo in der Tabelle der Inhalte in diesem Thema relativ zu dessen Peer Themen angezeigt wird. Dieses Tag ist erforderlich und muss nur einmal in einem Thema verwendet werden. Der Wert ist eine ganze Zahl. Ein Thema, das eine kleineren Wert ganze Zahl angibt wird über ein Thema, das eine höheren Wert ganze Zahl angibt.|  
|\<Meta-name="Microsoft.Help.Product" Content = "[Produktcode]" / >|Gibt das Produkt, das in diesem Thema wird beschrieben, an. Wenn dieses Tag in einem Thema verwendet wird, muss sie nur einmal verwendet werden. Diese Informationen kann auch als Parameter angegeben werden, der dem Indexer Hilfe übergeben wird.|  
|\<Meta-name="Microsoft.Help.ProductVersion" Content = "[Versionsnummer]" / >|Gibt die Version des Produkts, das in diesem Thema beschrieben. Wenn dieses Tag in einem Thema verwendet wird, muss sie nur einmal verwendet werden. Diese Informationen kann auch als Parameter angegeben werden, der dem Indexer Hilfe übergeben wird.|  
|\<Meta-name="Microsoft.Help.Category" Content = "String" / >|Von Produkten verwendet, um Unterabschnitte der Inhalt zu identifizieren. Sie können mehrere Unterabschnitte für ein Thema identifizieren, oder können Sie dieses Tag weglassen, wenn Sie nicht, dass Links zu jeder Unterabschnitte zu identifizieren möchten. Dieses Tag wird verwendet, speichern Sie die Attribute für TargetOS und TargetFrameworkMoniker, wenn von einer früheren Version der Hilfe ein Themas konvertiert wird. Das Format des Inhalts ist AttributeName:AttributeValue.|  
|\<Meta name="Microsoft.Help.TopicVersion Content ="[Thema Version Number]"/ >|Diese Version des Themas gibt, wenn in einem Katalog mehrere Versionen vorhanden sind. Da Microsoft.Help.Id nicht eindeutig ist unbedingt, ist dieses Tag erforderlich, wenn mehrere Versionen eines Themas in einem Katalog, z. B. liegt vor, wenn ein Katalog ein Thema für .NET Framework 3.5 und ein Thema für .NET Framework 4 enthält und beide verfügen über die gleichen Micro Weiche. Help.Id.|  
|\<Meta Name = "SelfBranded" Content = "[" true "oder" false "]" / >|Gibt an, ob in diesem Thema verwendet den Hilfebibliotheks-Manager Nachschlagealgorithmus branding oder branding-Paket, das an das Thema spezifisch ist. Dieses Tag muss entweder "true" oder "false". Wenn "true", und klicken Sie dann das branding-Paket für im entsprechenden Thema Brandingpakets, die festgelegt wird überschreibt, wenn der Hilfebibliotheks-Manager startet, sodass das Thema gerendert wird, wie beabsichtigt, auch wenn es das Rendering von anderen Inhalten unterscheidet ist. Ist er "false", wird das aktuelle Thema gemäß Brandingpakets gerendert, die festgelegt wird, wenn der Hilfebibliotheks-Manager wird gestartet. Standardmäßig nimmt der Hilfebibliotheks-Manager auf "falsch" sein, es sei denn, die SelfBranded-Variable deklariert wird, als "true" Self-branding; aus diesem Grund Sie keine deklarieren \<Meta Name = "SelfBranded" Content = "FALSE" / >.|  
  
### <a name="creating-a-branding-package"></a>Erstellen eines Pakets, branding  
Die Visual Studio-Version umfasst eine Anzahl von anderen Visual Studio-Produkten, einschließlich isoliert und integrierte Shells für Visual Studio-Partner.  Jedes dieser Produkte erfordert ein gewisses Maß an themenbasierte Hilfeinhalt branding-Unterstützung für das Produkt eindeutig.  Beispielsweise müssen Visual Studio-Themen eine konsistente Brand-Präsentation sein, während SQL Studio, das ISO-Shell umbrochen wird, erfordert einen eigenen eindeutigen Hilfe Content branding für jedes Thema.  Eine integrierte Shell Partner sollten ihre innerhalb des übergeordneten Elements Hilfeinhalt für Visual Studio-Produkt werden und gleichzeitig ihre eigenen Thema branding-Hilfethemen.  
  
Branding-Pakete werden vom Produkt der Help Viewer mit installiert.  Für Visual Studio-Produkte:  
  
-   Ein fallback Brandingpakets (Branding_\<Gebietsschema > mshc) in der Hilfe-Viewer 2.3 app Stamm installiert ist (Beispiel: C:\Program Files (x86) \Microsoft Help Viewer\v2.3) durch das Sprachpaket für die Hilfe-Viewer.  Dient zum, wenn entweder das Produkt branding Paket nicht installiert ist (kein Inhalt installiert wurde) oder, in dem das installierte branding-Paket ist beschädigt.  Beachten Sie, dass die Visual Studio-Elemente (Logo und Feedback) ignoriert werden, wenn das app-Stamm-Fallback branding Paket verwendet wird.  
  
-   Wenn Visual Studio-Inhalte aus dem Content-Paket-Dienst installiert ist, wird ein branding-Paket (für das erste Mal Inhaltsinstallation-Szenario) ebenfalls installiert.  Ist ein Update für das branding-Paket, wird das Update installiert, wenn die nächste Inhaltsupdate oder ein zusätzliches Paket installieren-Aktion geschieht.  
  
Microsoft Help Viewer unterstützt das branding der Themen, die basierend auf Metadaten Thema.  
  
-   Wobei Thema Metadaten selbst die Marke definiert = "true", rendern das Thema ist, werden keine Aktionen ausgeführt (so weit wie branding).  
  
-   Wobei Thema Metadaten selbst die Marke definiert = "false", verwenden Sie das branding Paket TopicVendor Metadatenwert zugeordnet.  
  
-   Thema Metadaten definiert, in denen name="Microsoft.Help.TopicVendor" Content =\< branding Paketnamen Hersteller diese MSHA >, verwenden Sie das branding-Paket in der Inhaltswert definiert.  
  
-   Beachten Sie, dass innerhalb des Visual Studio-Katalogs, gibt es eine vorrangige Anwendung Branding Pakete.  Erste Visual Studio Standard-branding angewendet wird, und klicken Sie dann, wenn in den Metadaten des Thema definiert und unterstützt das zugeordnete branding-Paket (wie in der Installation Msha definiert), der Anbieter definiert branding als Überschreibung angewendet wird.  
  
Branding-Elemente werden in der Regel in drei Hauptkategorien unterteilt:  
  
-   Header-Elemente (z. B. Link "Feedback", bedingte Haftungsausschluss-, Logo)  
  
-   Inhalts-Verhalten (Beispiele für erweitern/reduzieren-Steuerelement-Text-Elemente enthalten und code Snippet-Elemente)  
  
-   Footer-Element (z. B. Copyright)  
  
Elemente berücksichtigt, da mit Branding versehene Elemente beinhalten (in dieser Spezifikation ä.):  
  
-   Katalog/Produktlogo (z. B. Visual Studio)  
  
-   Feedback-Link und e-Mail-Elemente  
  
-   Haftungsausschluss-  
  
-   Copyright text  
  
Unterstützende Dateien in Visual Studio Help Viewer Brandingpakets umfassen:  
  
-   Grafiken (Logos, Symbole usw.).  
  
-   Branding.js - Dateien Skript unterstützende Content-Verhalten  
  
-   Branding.XML - Zeichenfolgen, die über Kataloginhalt einheitlich verwendet werden.  Hinweis: für Visual Studio Lokalisierung Textelemente in der branding.xml enthalten _locID = "\<eindeutigen Wert >"  
  
-   Branding.CSS - Formatdefinitionen, Konsistenzgründen Präsentation  
  
-   Printing.CSS - Formatdefinitionen konsistent gedruckte Präsentation  
  
Wie oben bereits erwähnt, sind Pakete Branding Thema zugeordnet:  
  
-   Wenn SelfBranded = "false" ist in den Metadaten definiert ist, werden im Thema erbt den Katalog branding-Paket  
  
-   Oder wenn SelfBranded = "false", und es wird eine eindeutige Paket-Branding definiert in der MSHA vorhanden und verfügbar, wenn der Inhalt installiert ist  
  
Für das Implementieren von Paketen mit benutzerdefinierter branding VSPs (VSP-Inhalt, SelfBranded = "true"), eine Möglichkeit zu fortfahren ist mit fallback Brandingpakets (installiert mit der Hilfe-Viewer) beginnen und den Namen der Datei nach Bedarf ändern.  Die Branding_\<Gebietsschemas > mshc-Datei ist eine Zip-Datei mit der Erweiterung in mshc geändert, daher einfach ändern Sie die Erweiterung zu ZIP aus mshc und extrahieren Sie den Inhalt.  Finden Sie weiter unten Paketelemente branding und je nach Bedarf ändern (beispielsweise ändern Sie das Logo in die VSP-Logo und der Verweis auf das Logo in der Datei Branding.xml, aktualisieren Branding.xml pro VSP Besonderheiten usw.).  
  
Wenn alle Änderungen abgeschlossen haben, erstellen Sie eine Zip-Datei, die die gewünschten Brandingelemente enthält, und ändern Sie die Erweiterung zu mshc.  
  
Erstellen Sie, um benutzerdefinierte Brandingpakets zuzuordnen, die MSHA, die den Verweis auf das branding Mshc-Datei zusammen mit dem Inhalt Mshc (mit den Themen) enthält.  Finden Sie unter "Diese MSHA" zum Erstellen einer grundlegenden diese MSHA.  
  
Die Branding.xml-Datei enthält eine Listenelemente für bestimmte Elemente in einem Thema konsistent zu rendern, wenn das Thema enthält \<Meta name="Microsoft.Help.SelfBranded" Content = "false" / >.  Die Visual Studio-Liste der Elemente in der Datei Branding.xml wird unten aufgeführt.  Beachten Sie, dass diese Liste vorgesehen ist, werden als Vorlage für ISO-Shell-Anwender, ändern sie diese Elemente (z. B. Logo, Feedback und Copyright), um ihren eigenen Product branding Anforderungen zu erfüllen.  
  
Hinweis: "{n}" vermerkt Variablen haben codeabhängigkeiten – entfernen oder ändern diese Werte führt dazu, dass Fehler und möglicherweise zum Absturz der Anwendung. Lokalisierung Bezeichner (Beispiel _locID="codesnippet.n") sind in der Visual Studio-Branding-Paket enthalten.  
  
**Branding.Xml**  
  
|||  
|-|-|  
|Feature:|**CollapsibleArea**|  
|Verwenden:|Erweitern Sie die Text-Inhaltssteuerelement reduziert|  
|**Element**|**Wert**|  
|ExpandText|Expand|  
|CollapseText|Reduzieren|  
|Feature:|**CodeSnippet**|  
|Verwenden:|Code Snippet-Steuerelementtext.  Hinweis: Code Snippet Inhalte mit "Nicht unterbrechend" Speicherplatz wird Space geändert werden.|  
|**Element**|**Wert**|  
|CopyToClipboard|In Zwischenablage kopieren|  
|ViewColorizedText|Farbig hervorgehoben anzeigen|  
|CombinedVBTabDisplayLanguage|Visual Basic (Beispiel)|  
|VBDeclaration|Deklaration|  
|VBUsage|Verwendung|  
|Feature:|**Feedback, Footer und -Logo**|  
|Verwenden:|Geben Sie ein Steuerelement Feedback für Kunden Bereitstellen von Feedback für das aktuelle Thema per E-mail an.  Copyright Text für den Inhalt.  Logo-Definition.|  
|**Element**|**Wert (diese Zeichenfolgen können zum erfüllen Content Adopter-Anforderung geändert werden.)**|  
|CopyRight|© 2013 Microsoft Corporation. Alle Rechte vorbehalten.|  
|SendFeedback|\<ein Href = "{0}" \ {1\} > Feedback senden \< /a > zu diesem Thema an Microsoft.|  
|FeedbackLink||  
|LogoTitle|[!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]|  
|LogoFileName|vs_logo_bk.gif|  
|LogoFileNameHC|vs_logo_wh.gif|  
|Feature:|**Haftungsausschluss**|  
|Verwenden:|Eine Reihe von Groß-/Kleinschreibung bestimmte Haftungsausschlüsse für Computer übersetzt Inhalt.|  
|**Element**|**Wert**|  
|MT_Editable|In diesem Artikel wurde maschinell übersetzt. Wenn Sie eine Internetverbindung verfügen, wählen Sie "In diesem Thema online anzeigen" zum Anzeigen dieser Seite im bearbeitbaren Modus mit dem ursprünglichen englischen Inhalt gleichzeitig.|  
|MT_NonEditable|In diesem Artikel wurde maschinell übersetzt. Wenn Sie eine Internetverbindung verfügen, wählen Sie "In diesem Thema online anzeigen" zum Anzeigen dieser Seite im bearbeitbaren Modus mit dem ursprünglichen englischen Inhalt gleichzeitig.|  
|MT_QualityEditable|In diesem Artikel wurde maschinell übersetzt. Wenn Sie eine Internetverbindung verfügen, wählen Sie "In diesem Thema online anzeigen" zum Anzeigen dieser Seite im bearbeitbaren Modus mit dem ursprünglichen englischen Inhalt gleichzeitig.|  
|MT_QualityNonEditable|In diesem Artikel wurde maschinell übersetzt. Wenn Sie eine Internetverbindung verfügen, wählen Sie "In diesem Thema online anzeigen" zum Anzeigen dieser Seite im bearbeitbaren Modus mit dem ursprünglichen englischen Inhalt gleichzeitig.|  
|MT_BetaContents|In diesem Artikel wurde maschinell übersetzt für eine vorläufige Version. Wenn Sie eine Internetverbindung verfügen, wählen Sie "In diesem Thema online anzeigen" zum Anzeigen dieser Seite im bearbeitbaren Modus mit dem ursprünglichen englischen Inhalt gleichzeitig.|  
|MT_BetaRecycledContents|In diesem Artikel wurde für eine vorläufige Version manuell übersetzt. Wenn Sie eine Internetverbindung verfügen, wählen Sie "In diesem Thema online anzeigen" zum Anzeigen dieser Seite im bearbeitbaren Modus mit dem ursprünglichen englischen Inhalt gleichzeitig.|  
|Feature:|**LinkTable**|  
|Verwenden:|Unterstützung für onlinethemas links|  
|**Element**|**Wert**|  
|LinkTableTitle|Link-Tabelle|  
|TopicEnuLinkText|Zeigen Sie die englische Version \< /a > dieses Themas, die auf dem Computer verfügbar ist.|  
|TopicOnlineLinkText|In diesem Thema zeigen \<eine Href = "{0}" \ {1\} > online \< /a >|  
|OnlineText|Online|  
|Feature:|**Video-Audiosteuerelement**|  
|Verwenden:|Anzeigen von Elementen und Text für Videoinhalten|  
|**Element**|**Wert**|  
|MultiMediaNotSupported|InternetExplorer 9 oder höher muss installiert sein, um {0} Inhalt zu unterstützen.|  
|VideoText|Video anzeigen|  
|AudioText|Streaming von audio|  
|OnlineVideoLinkText|\<p > um das Video mit diesem Thema verknüpften anzuzeigen, klicken Sie auf {0}\<eine Href = "\ {1\}" > {2}here\</a >.\< / p >|  
|OnlineAudioLinkText|\<p > das Audio in diesem Thema zugeordneten überwacht werden, klicken Sie auf {0}\<eine Href = "\ {1\}" > {2}here\</a >.\< / p >|  
|Feature:|**Inhaltssteuerelement nicht installiert**|  
|Verwenden:|Textelemente (Zeichenfolgen), die für das Rendern des contentnotinstalled.htm verwendet|  
|**Element**|**Wert**|  
|ContentNotInstalledTitle|Auf Ihrem Computer ist kein Inhalt gefunden.|  
|ContentNotInstalledDownloadContentText|\<p > zum Herunterladen von Inhalt auf Ihren Computer \<eine Href = "{0}" \ {1\} > Klicken Sie auf der Registerkarte "verwalten"\</a >.\< / p >|  
|ContentNotInstalledText|\<p > kein Inhalt auf Ihrem Computer installiert ist. Weitere Informationen finden Sie Ihren Administrator, um lokale Hilfe Inhaltsinstallation.  \< /p >|  
|Feature:|**Thema Nichtgefunden-Steuerelement**|  
|Verwenden:|Textelemente (Zeichenfolgen), die für das Rendern des topicnotfound.htm verwendet|  
|**Element**|**Wert**|  
|TopicNotFoundTitle|Angeforderte Thema auf Ihrem Computer wurde nicht gefunden.|  
|TopicNotFoundViewOnlineText|\<p > die angeforderte Thema wurde nicht auf Ihrem Computer gefunden, Sie können jedoch \<ein Href = "{0}" \ {1\} > finden Sie die Onlinedokumentation\</a >.\< / p >|  
|TopicNotFoundDownloadContentText|\<p > finden Sie im Navigationsbereich links zu Themen, die ähnliche oder \<eine Href = "{0}" \ {1\} > Klicken Sie auf der Registerkarte "verwalten"\</a > zum Herunterladen von Inhalt auf Ihrem Computer.\< / p >|  
|TopicNotFoundText|\<p > die angeforderte Thema auf Ihrem Computer nicht gefunden.  \< /p >|  
|Feature:|**Thema beschädigt Steuerelement**|  
|Verwenden:|Textelemente (Zeichenfolgen), die für das Rendern des topiccorrupted.htm verwendet|  
|**Element**|**Wert**|  
|TopicCorruptedTitle|Kann nicht das gewünschte Thema angezeigt.|  
|TopicCorruptedViewOnlineText|\<p > Hilfe-Viewer kann nicht das gewünschte Thema angezeigt wird. Es gibt möglicherweise ein Fehler in das Thema Inhalt oder eine zugrunde liegende System-Abhängigkeit.  \< /p >|  
|Feature:|**Startseite-Steuerelement**|  
|Verwenden:|Text unterstützen die Anzeige des Inhalts der Help Viewer-Knoten der obersten Ebene.|  
|**Element**|**Wert**|  
|HomePageTitle|Startseite der Hilfe-Viewer|  
|HomePageIntroduction|\<p > Willkommen bei Microsoft Help Viewer eine wesentliche Informationsquelle für alle Entwickler, die Microsoft-Tools, Produkte, Technologien und Dienste verwendet. Der Help Viewer erhalten Sie Zugriff auf die exemplarische Vorgehensweise und Referenzinformationen, Beispielcode und technische Artikel. Um den Inhalt zu suchen, den Sie das Inhaltsverzeichnis durchsuchen müssen, verwenden Sie den Volltext-Suchdienst, oder navigieren Sie durch den Inhalt mit dem Schlüsselwortindex.  \< /p >|  
|HomePageContentInstallText|\<p >\<Br / > Verwenden der \<eine Href = "{0}" \ {1\} > Inhalt verwalten\</a > Registerkarte die folgenden Schritte ausführen:\<Ul >\<li > Hinzufügen von Inhalt auf Ihrem Computer.\< / li >\<li > Suchen nach Updates für Ihre lokalen Inhalte.\< / li >\<li > Inhalt vom Computer entfernen.\< / li >\</UL > \< /p >|  
|HomePageInstalledBooks|Installierten Büchern|  
|HomePageNoBooksInstalled|Auf Ihrem Computer ist kein Inhalt gefunden.|  
|HomePageHelpSettings|Inhaltseinstellungen für Hilfe|  
|HomePageHelpSettingsText|\<p > die aktuelle Einstellung wird die lokale Hilfe. Der Help Viewer zeigt Inhalte, die auf Ihrem Computer installiert ist. \<Br / > So ändern Sie Ihre Quelle der Hilfeinhalte, in der Visual Studio-Menüleiste auswählen \<span Style = "{0}" > Hilfe, Hilfeeinstellungen festlegen\</span >.\< Br / > \< /p >|  
|MB|MB|  
  
**Branding.js**  
  
Die branding.js-Datei enthält, JavaScript, die durch die Visual Studio Help Viewer-branding-Elemente verwendet wird.  Im folgenden finden Sie eine Liste mit branding-Elemente und die unterstützenden JavaScript-Funktion.  Alle Zeichenfolgen, die für diese Datei lokalisiert werden, werden im Abschnitt "Lokalisierbaren Zeichenfolgen" am oberen Rand dieser Datei definiert.  Beachten Sie, dass für die Lokalisierung von Zeichenfolgen in der Datei branding.js ICL-Datei erstellt wurde.  
  
||||  
|-|-|-|  
|**Branding-Funktion**|**JavaScript-Funktion**|**Beschreibung**|  
|Var...||Definieren Sie Variablen|  
|Die Codesprache Benutzer abrufen|setUserPreferenceLang|Ordnet einen Index um Codesprache|  
|Festlegen und Abrufen von Cookiewerte|GetCookie setCookie||  
|Geerbte Member|changeMembersLabel|Geerbten Member erweitern/reduzieren|  
|Wenn SelfBranded = "false"|onLoad|Lesen Sie die Abfragezeichenfolge, um festzustellen, ob es sich um eine druckanforderung ist.  Legen Sie alle Codesnippets auf der Registerkarte "Benutzer bevorzugte" konzentrieren.  Wenn es sich um einen Druckvorgang ist Anforderung können Sie IsPrinterFriendly auf "true" festlegen. Überprüfen Sie den Modus für hohe Kontraste.|  
|Codeausschnitt|addSpecificTextLanguageTagSet||  
||getIndexFromDevLang||  
||Änderungsobjekte||  
||setCodesnippetLang||  
||setCurrentLang||  
||CopyToClipboard||  
|CollapsibleArea|addToCollapsibleControlSet|Schreiben Sie alle reduzierbaren Control-Objekt in der Liste aus.|  
||CA_Click|basierend auf den Zustand des reduzierbaren Bereichs, der definiert, welche ImageAndText zum Präsentieren von|  
|Kontrast-Unterstützung für Logo|isBlackBackground()|Wird aufgerufen, um festzustellen, ob der Hintergrund Schwarz ist.  Nur präzise, wenn im Modus für hohe Kontraste.|  
||isHighContrast()|Verwenden Sie eine farbige Spanne Modus für hohe Kontraste erkennen|  
||onHighContrast(black)|Wird aufgerufen, wenn der hohe Kontrast erkannt wird|  
|LST-Funktion|||  
||addToLanSpecTextIdSet(id)||  
||updateLST(currentLang)||  
||getDevLangFromCodeSnippet(lang)||  
|MultiMedia-Funktionalität|Caption (begin, Ende, Text, Stil)||  
||findAllMediaControls(normalizedId)||  
||getActivePlayer(normalizedId)||  
||captionsOnOff(id)||  
||toSeconds(t)||  
||getAllComments(node)||  
||StyleRectify (Formatvorlage, StyleValue)||  
||showCC(id)||  
||Subtitle(ID)||  
  
**HTM-DATEIEN**  
  
Branding-Paket enthält eine Reihe von HTM-Dateien, die Szenarien für die Kommunikation wichtige Informationen zum Inhalt helfen den Benutzern, z. B. eine Startseite, die enthält einen Abschnitt beschreiben, welche Inhalte legt installiert sind und Seiten, die darüber informiert, dass wenn Themen können nicht unterstützen gefunden Sie in der lokalen Gruppe der Themen werden. Beachten Sie, dass diese HTM-Dateien pro Produkt geändert werden können.  ISO-Shell-Anbieter können die Standard-branding-Paket erstellen und ändern Sie das Verhalten und die Inhalte dieser Seiten in der Suite entsprechenden Bedarf an.  Diese Dateien finden Sie in ihren jeweiligen Brandingpakets in Reihenfolge für das branding Tags aus, um den entsprechenden Inhalt aus der Datei branding.xml abzurufen.  
  
||||  
|-|-|-|  
|**Datei**|**Verwendung**|**Inhaltsquelle angezeigt**|  
|Homepage.htm|Dies ist eine Seite, die derzeit installierten Inhalt und allen anderen Nachrichten, die dem Benutzer über ihre Inhalte angezeigt.  Diese Datei enthält zusätzliche Meta Data-Attribut "Microsoft.Help.Id" Content = "1", wodurch dies am Anfang der lokalen Inhalt Inhaltsverzeichnis Inhalt platziert.||  
||< META_HOME_PAGE_TITLE_ADD / >|Branding.XML, Tag \<HomePageTitle >|  
||< HOME_PAGE_INTRODUCTION_SECTION_ADD / >|Branding.XML, Tag \<HomePageIntroduction >|  
||< HOME_PAGE_CONTENT_INSTALL_SECTION_ADD / >|Branding.XML, Tag \<HomePageContentInstallText >|  
||< HOME_PAGE_BOOKS_INSTALLED_SECTION_ADD / >|Überschrift des Abschnitts Branding.xml Tag\<HomePageInstalledBooks >, die von der Anwendung generierten Daten \<HomePageNoBooksInstalled > Wenn keine Bücher installiert sind.|  
||< HOME_PAGE_SETTINGS_SECTION_ADD / >|Überschrift des Abschnitts Branding.xml Tag \<HomePageHelpSettings >, Abschnitt Text \<HomePageHelpSettingsText >.|  
|topiccorrupted.htm|Wenn ein Thema in der lokalen Gruppe vorhanden ist, aber für aus irgendeinem Grund nicht angezeigt werden kann (Inhalt beschädigt).||  
||< META_TOPIC_CORRUPTED_TITLE_ADD / >|Branding.XML, Tag \<TopicCorruptedTitle >|  
||< TOPIC_CORRUPTED_SECTION_ADD / >|Branding.XML, Tag \<TopicCorruptedViewOnlineText >|  
|topicnotfound.htm|Wenn ein Thema nicht im lokalen Inhalt festgelegt, noch verfügbar online gefunden wird||  
||< META_TOPIC_NOT_FOUND_TITLE_ADD / >|Branding.XML, Tag \<TopicNotFoundTitle >|  
||< META_TOPIC_NOT_FOUND_ID_ADD / >|Branding.XML, Tag \<TopicNotFoundViewOnlineText > + \<TopicNotFoundDownloadContentText >|  
||< TOPIC_NOT_FOUND_SECTION_ADD / >|Branding.XML, Tag \<TopicNotFoundText >|  
|contentnotinstalled.htm|Wenn es keinen lokalen Inhalt für das Produkt installiert ist.||  
||< META_CONTENT_NOT_INSTALLED_TITLE_ADD / >|Branding.XML, Tag \<ContentNotInstalledTitle >|  
||< META_CONTENT_NOT_INSTALLED_ID_ADD / >|Branding.XML, Tag \<ContentNotInstalledDownloadContentText >|  
||< CONTENT_NOT_INSTALLED_SECTION_ADD / >|Branding.XML, Tag \<ContentNotInstalledText >|  
  
**CSS-Dateien**  
  
Der Visual Studio-Hilfe-Viewer Branding-Paket enthält zwei Css-Dateien, um konsistente Visual Studio-Hilfekatalogs Content-Präsentation zu unterstützen:  
  
-   Branding.CSS - enthält Css-Elemente für das Rendern von Where SelfBranded = "false"  
  
-   Printer.CSS - enthält Css-Elemente für das Rendern von Where SelfBranded = "false"  
  
Branding.CSS Dateien enthält Definitionen für Visual Studio Thema Präsentation (muss allerdings berücksichtigt werden, dass die branding.css in der Branding_ enthalten\<Gebietsschemas > mshc aus dem Paketdienst können geändert werden).  
  
**Grafik-Dateien**  
  
Visual Studio-Inhalte zeigt ein Logo aus Visual Studio sowie andere Grafik.  Die vollständige Liste der Grafikdateien in Visual Studio Help Viewer Brandingpakets ist unten dargestellt.  
  
||||  
|-|-|-|  
|**Datei**|**Verwendung**|**Beispiele**|  
|Clear.gif|Reduzierbaren Bereich gerendert.||  
|footer_slice.gif|Fußzeile Präsentation||  
|info_icon.gif|Beim Anzeigen von Informationen verwendet|Haftungsausschluss|  
|online_icon.gif|Dieses Symbol ist online Links zugeordnet werden soll||  
|tabLeftBD.gif|Verwendet zum Rendern des Code Snippet-Containers||  
|tabRightBD.gif|Verwendet zum Rendern des Code Snippet-Containers||  
|vs_logo_bk.gif|Verwendet für normale Kontrast Logo Verweise gemäß Branding.xml Tag \<LogoFileName >.  Für Visual Studio-Produkten ist Logo Namen vs_logo_bk.gif.||  
|vs_logo_wh.gif|Verwendet für normale hohe Logo Verweise gemäß Branding.xml Tag \<LogoFileNameHC >.  Für Visual Studio-Produkten ist Logo Namen vs_logo_wh.gif.||  
|ccOff.png|Grafik zu Untertitel||  
|ccOn.png|Grafik zu Untertitel||  
|ImageSprite.png|Reduzierbaren Bereich gerendert.|erweitert oder reduziert Grafik|  
  
### <a name="deploying-a-set-of-topics"></a>Eine Reihe von Themen bereitstellen  
Dies ist eine sehr einfache und schnelle Lernprogramm zum Erstellen einer inhaltsbereitstellung Help Viewer, legen Sie diese MSHA-Datei und den Satz von Cabs comprised oder MSHC, die in den Themen enthält. Die MSHA ist eine XML-Datei, die einen Satz von Cabs beschreibt oder MSHC-Dateien. Der Help Viewer erhalten die MSHA zum Abrufen einer Liste von Inhalten (der. CAB-Datei oder. MSHC-Dateien) für die lokale Installation verfügbar.  
  
Dies ist nur eine Einführung in sehr einfachen XML-Schema für die Hilfe-Viewer diese MSHA beschrieben.  Beachten Sie, dass eine beispielimplementierung unterhalb dieser kurze Übersicht und sample "HelpContentSetup.msha".  
  
Der Name des der MSHA im Rahmen dieser Einführung ist "HelpContentSetup.msha" (der Name der Datei kann, mit der Erweiterung sein. DIESE MSHA). "HelpContentSetup.msha (nachfolgendes Beispiel)" sollte eine Liste der CAB-Dateien oder MSHCs verfügbaren enthalten.  Beachten Sie, dass der Dateityp in der MSHA konsistent sein muss (bietet keine Unterstützung für eine Kombination von Typen für diese MSHA und CAB-Datei). Für jede CAB-Datei oder MSHC, es darf eine \<Div-Klasse "Paket" = >...  \< /div > (siehe folgendes Beispiel).  
  
Hinweis: in der folgenden Implementierungsbeispiel haben wir Brandingpakets enthalten. Dies ist wichtig, zu enthalten, damit Sie um die erforderlichen Visual Studio Inhalt Rendern von Elementen und Inhalt Verhalten zu erhalten.  
  
Beispieldatei für "HelpContentSetup.msha": (ersetzen Sie "Inhalt set Name 1" und "Content Set name 2" usw. mit den Dateinamen.)  
  
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
  
1.  Erstellen von lokalen Ordner, z. B. "C:\SampleContent"  
  
2.  In diesem Beispiel verwenden wir MSHC-Dateien in den Themen enthalten.  Ein MSHC ist eine ZIP-Datei mit der Erweiterung zu ZIP geändert. MSHC.  
  
3.  Erstellen Sie die unter "HelpContentSetup.msha" als Textdatei (Editor zum Erstellen der Datei verwendet wurde) und speichern Sie sie in den oben angegebenen Ordner (siehe Schritt 1).  
  
Beachten Sie, dass die Klasse "Branding" vorhanden und eindeutig ist. Das Branding Mshc ist in dieser Einführung in enthalten, sodass branding des installierten Inhalts müssen und die Content-Verhalten, die in der MSHCs enthalten sind, entsprechende Unterstützung Elemente im Brandingpakets müssen. Ohne diesen Schritt Fehler ausgegeben, wenn das System für Support-Artikel, die nicht Teil der kopierten sieht (installiert) sind Inhalt.  
  
Kopieren Sie zum Abrufen der Visual Studio-Paket branding Branding_en US.mshc Datei am C:\Program Files (x86) \Microsoft Help Viewer\v2.3\ an den Arbeitsordner.  
  
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
  
### <a name="adding-help-to-the-visual-studio-shell-integrated-and-isolated"></a>Hinzufügen von Hilfe zu Visual Studio Shell (integrierter Modus und isoliert)  
**Introduction (Einführung)**  
  
In dieser exemplarischen Vorgehensweise veranschaulicht die Hilfeinhalte in einer Visual Studio-Shell-Anwendung zu integrieren und bereitstellen.  
  
**Anforderungen**  
  
1.  [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]  
  
2.  [Visual Studio 2013 isolierte Shell Redist](http://www.microsoft.com/visualstudio/11/downloads#vs-shell)  
  
**Übersicht**  
  
Die [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Shell ist eine Version von den [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] IDE auf dem eine Anwendung basieren können. Solche Anwendungen enthalten die Isolated Shell zusammen mit Erweiterungen, die Sie erstellen. Verwenden Sie Isolated Shell-Projektvorlagen, die in enthalten sind die [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] SDK, um Erweiterungen zu erstellen.  
  
Die grundlegenden Schritte zum Erstellen einer isolierten Shell-basierten Anwendung und die dazugehörige Hilfe:  
  
1.  Abrufen der [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] ISO Shell redistributable (ein Microsoft-Download).  
  
2.  Erstellen Sie in Visual Studio eine Hilfe-Erweiterung, die z. B. auf die isolierte Shell basiert, die Contoso-Hilfe-Erweiterung, die weiter unten in dieser exemplarischen Vorgehensweise beschrieben wird.  
  
3.  Umschließen Sie die Erweiterung und die ISO-Shell redistributable in eine MSI-Datei (eine Anwendungssetup)-Bereitstellung. In dieser exemplarischen Vorgehensweise umfasst einen Schritt Setup nicht.  
  
Erstellen Sie einen Visual Studio-Inhaltsspeicher. Ändern Sie für das Szenario integrierte Shell von Visual Studio12, der Name des Katalogs Produkt wie folgt:  
  
-   Erstellen Sie Ordner C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15.  
  
-   Erstellen Sie eine Datei mit dem Namen "catalogtype.xml", und fügen sie zu dem Ordner hinzu. Die Datei muss die folgenden Codezeilen enthalten:  
  
    ```xml
    <?xml version="1.0" encoding="UTF-8"?>  
    <catalogType>UserManaged</catalogType>  
    ```  
  
Definieren Sie die Inhaltsspeicher in der Registrierung. Ändern Sie für die integrierte Shell VisualStudio15, in der Produktname des Katalogs:  
  
-   HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15  
  
     Schlüssel: LocationPath Zeichenfolgenwert: C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15\  
  
-   HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15\en-US  
  
     Schlüssel: CatalogName Zeichenfolgenwert: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Dokumentation  
  
**Erstellen des Projekts**  
  
So erstellen Sie eine isolierte Shell-Erweiterung  
  
1.  In Visual Studio unter **Datei**, wählen Sie **neues Projekt**unter **andere Projekttypen** auswählen **Erweiterbarkeit**, und wählen Sie dann  **Visual Studio Shell Isolated**. Nennen Sie das Projekt `ContosoHelpShell`) erstellen Sie ein Erweiterungsprojekt, basierend auf der Visual Studio Isolated Shell-Vorlage.  
  
2.  Öffnen Sie im Projektmappen-Explorer im Projekt ContosoHelpShellUI im Ordner Ressourcendateien ApplicationCommands.vsct aus. Stellen Sie sicher, dass (Suchen Sie "No_Help") die folgende Zeile auskommentiert ist:`<!-- <define name="No_HelpMenuCommands"/> -->`  
  
3.  Wählen Sie zum Kompilieren und führen Sie die Taste F5 **Debuggen**. Wählen Sie in der experimentellen Instanz von isolierten Shell-IDE, die **Hilfe** Menü. Stellen Sie sicher, dass die **Sicht Ihnen helfen,**, **Hilfeinhalte hinzufügen und Entfernen von**, und **Hilfeeinstellungen festlegen** Befehle angezeigt.  
  
4.  Öffnen Sie im Projektmappen-Explorer im Projekt ContosHelpShell im Ordner "Shell-Anpassung" ContosoHelpShell.pkgdef aus. Um die Contoso-Hilfekatalog zu definieren, fügen Sie die folgenden Zeilen ein:  
  
    ```  
     [$RootKey$\Help]  
    "Product"="Contoso"  
    "Catalog"="Contoso"  
    "Version"="100"  
    "BrandingPackage"="ContosoBrandingPackage.mshc"  
    ```  
  
5.  Öffnen Sie im Projektmappen-Explorer im Projekt ContosHelpShell im Ordner "Shell-Anpassung" ContosoHelpShell.Application.pkgdef aus. Um F1-Hilfe zu aktivieren, fügen Sie die folgenden Zeilen hinzu:  
  
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
  
7.  Erstellen Sie die Projektmappe. Dies erstellt einen Satz von Dateien in einem Ordner Version, die im nächsten Abschnitt verwendet wird.  
  
Um dies zu testen, als ob bereitgestellt:  
  
1.  Auf dem Computer stellen Sie Contoso ein, um das heruntergeladene (von oberhalb) ISO-Verwaltungsshell installieren.  
  
2.  Erstellen Sie einen Ordner in \\\Program Files (x86)\\, und nennen Sie sie `Contoso`.  
  
3.  Kopieren Sie den Inhalt aus dem ContosoHelpShell Version Ordner \\(x86) \Contoso\ Ordner \Programme.  
  
4.  Starten des Registrierungs-Editor durch Auswahl **ausführen** in der **starten** Menü- und Eingeben von `Regedit`. Wählen Sie in den Registrierungs-Editor **Datei**, und klicken Sie dann **Import**. Navigieren Sie zum Projektordner ContosoHelpShell. Wählen Sie in der ContosoHelpShell Unterordner ContosoHelpShell.reg aus.  
  
5.  Erstellen Sie einen Inhaltsspeicher an:  
  
     Erstellen Sie einen Contoso Inhaltsspeicher C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\ContosoDev12 für ISO-Shell-  
  
     Für [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] integrierte Shell erstellen Sie Ordner C:\ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio15  
  
6.  "Catalogtype.xml" erstellen und zu der Inhaltsspeicher (vorigen Schritt), hinzufügen:  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?>  
    <catalogType>UserManaged</catalogType>  
    ```  
  
7.  Fügen Sie die folgenden Registrierungsschlüssel hinzu:  
  
     HKLM\SOFTWARE\Wow6432Node\Microsoft\Help\v2.3\Catalogs\VisualStudio15Key: LocationPath Zeichenfolgenwert:  
  
     Für ISO-Shell:  
  
     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15  
  
     [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)]Integrierte Shell:  
  
     C:ProgramDataMicrosoftHelpLibrary2CatalogsVisualStudio15en-USA  
  
     Schlüssel: CatalogName Zeichenfolgenwert: [!INCLUDE[vs_dev12](../../extensibility/includes/vs_dev12_md.md)] Dokumentation. Für ISO-Shell ist dies der Name des Katalogs.  
  
8.  Kopieren Sie Ihre Inhalte (CAB-Dateien oder MSHC und diese MSHA) in einen lokalen Ordner.  
  
9. Integrierte Shell Beispielbefehlszeile für das Testen von Inhaltsspeicher. Ändern Sie die Katalog- und LaunchingApp Werte nach Bedarf entsprechend das Produkt, für ISO-Shell.  
  
     "C:\Programme\Microsoft Dateien (x86) \Microsoft Help Viewer\v2.3\HlpViewer.exe" /catalogName VisualStudio15 /helpQuery Methode = "Seite" & Id = ContosoTopic0 "/launchingApp Microsoft VisualStudio, 12.0  
  
10. Starten Sie die Contoso-Anwendung (ausgehend vom Stamm des Contoso-app). In ISO-Shell, wählen Sie die **Hilfe** Menüelement, und Ändern der **Hilfeeinstellungen festlegen** auf **verwenden lokale Hilfe**.  
  
11. Wählen Sie in der Befehlsshell die **Hilfe** Menüelement, klicken Sie dann **Sicht Ihnen helfen,**. Die lokale Hilfe-Viewer starten sollte. Wählen Sie die Registerkarte **Inhalt verwalten** aus. Klicken Sie unter **Installationsquelle**, wählen Sie die **Datenträger** Optionsfeld. Wählen Sie die **...**  Schaltfläche aus, und navigieren Sie zu den lokalen Ordner mit Contoso-Inhalten (für den lokalen Ordner im vorherigen Schritt kopiert haben). Wählen Sie die "HelpContentSetup.msha" aus. Contoso sollte jetzt als ein Buch in der Auswahl der Buch angezeigt. Wählen Sie **hinzufügen**, und wählen Sie dann die **Update** Schaltfläche (rechts unten).  
  
12. Wählen Sie die F1-Taste F1-Funktionalität zu testen, in der Contoso-IDE.  
  
### <a name="additional-resources"></a>Zusätzliche Ressourcen  
Der Laufzeit-API finden Sie unter [Windows-Hilfe-API](http://msdn.microsoft.com/library/windows/desktop/hh447318\(v=vs.85\).aspx).  
  
Weitere Informationen zum Nutzen der Hilfe-API finden Sie unter [Hilfe-Viewer-Codebeispiele](http://visualstudiogallery.msdn.microsoft.com/f08f296f-7076-4aec-8da3-8f0fbe04461e)  
  
Um Feedback zu diesen Komponenten bereitzustellen, verwenden Sie [Microsoft Connect](http://connect.microsoft.com/).  
  
Bitte senden Sie Vorschläge zum [Microsoft User Voice](http://visualstudio.uservoice.com/forums/121579-visual-studio)  
  
Um zusätzliche Hilfe abzurufen, verwenden Sie die [Foren von MSDN Developer Documentation and Help System](http://social.msdn.microsoft.com/Forums/devdocs/threads)  
  
Updates über wichtige Problem finden Sie unter der [Hilfe-Viewer-Infodatei](http://go.microsoft.com/fwlink/?LinkID=231397&clcid=0x409)  
  
Um die Hilfe-Viewer-Uhr-Team direkt kontaktiert, senden Sie per E-mail anhlpfdbk@microsoft.com