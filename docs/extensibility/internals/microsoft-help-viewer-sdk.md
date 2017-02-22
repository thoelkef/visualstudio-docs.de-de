---
title: "Microsoft Help Viewer SDK | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 620d7dcd-d462-475e-a449-fbfa06ff12c5
caps.latest.revision: 33
caps.handback.revision: 33
ms.author: "gregvanl"
manager: "ghogen"
---
# Microsoft Help Viewer SDK
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Dieser Artikel enthält die folgenden Aufgaben für Visual Studio Help Viewer Integratoren:  
  
-   Erstellen eines Themas \(F1\-Unterstützung\)  
  
-   Erstellen eines Pakets für die Hilfe\-Viewer\-Inhalt\-branding  
  
-   Bereitstellen von einer Reihe von Artikeln  
  
-   Hinzufügen von Hilfe für die Visual Studio\-Shell \(integriert oder isoliert\)  
  
-   Zusätzliche Ressourcen  
  
### Erstellen eines Themas \(F1\-Unterstützung\)  
 Dieser Abschnitt enthält eine Übersicht über die Komponenten eines Themas präsentiert, Thema Anforderungen, eine kurze Beschreibung für ein Thema \(einschließlich der F1\-Anforderungen\) und schließlich ein Thema wird durch das gerenderte Ergebnis zu erstellen.  
  
 **Hilfeanzeige Thema \(Übersicht\)**  
  
 Wenn ein Thema für das Rendern aufgerufen wird, wird der Help Viewer Ruft das branding Paketelemente, die zum Zeitpunkt der Installation oder der letzten Aktualisierung, zusammen mit dem Thema XHTML, mit dem Thema verknüpft sind und kombiniert die beiden um Ihre Darstellung in der Ansicht Inhalt \(branding Daten \+ Thema Daten\) führen.  Die branding\-Paket enthält Logos, Unterstützung für Content Verhaltensweisen und branding\-Text \(copyright usw.\).  Weitere Informationen zum Paket Brandingelemente finden Sie unter "Erstellen von Branding\-Paket" unten.  Im Ereignisprotokoll kein branding\-Paket mit dem Thema verknüpft ist ist, wird der Help Viewer die fallback branding\-Paket befindet sich im Stammverzeichnis Help Viewer\-Anwendung \(Branding\_en US.mshc\) verwenden.  
  
 **Hilfe\-Viewer Thema Anforderungen**  
  
 Um die Hilfe\-Viewer ordnungsgemäß gerendert werden, muss raw Themeninhalt W3C grundlegende 1.1 XHTML sein.  
  
 Ein Thema enthält in der Regel zwei Abschnitte:  
  
-   Metadaten \(Siehe Content Metadatenverweis\): Daten zum Thema, z. B. das Thema eindeutige ID, die Schlüsselwort\-Wert, das Thema TOC\-ID, übergeordnete Knoten\-ID usw..  
  
-   Text\-Inhalt: Einhaltung der W3C grundlegende 1.1 XHTML darunter unterstützt Inhalt Verhaltensweisen \(reduzierbaren Bereich, Codeausschnitt, usw. Eine vollständige Liste ist unten dargestellt\).  
  
 Visual Studio\-Branding\-Paket unterstützt Steuerelemente:  
  
-   Links  
  
-   CodeSnippet  
  
-   CollapsibleArea  
  
-   Geerbte Member  
  
-   LanguageSpecificText  
  
 Unterstützt die Sprachen\-Zeichenfolgen \(ohne Beachtung von Groß\-\/Kleinschreibung\):  
  
-   JavaScript  
  
-   CSharp oder c\#  
  
-   Cplusplus oder VisualC\+\+\- oder c\+\+  
  
-   JScript  
  
-   VisualBasic oder vb  
  
-   f\#\- oder Fsharp oder fs  
  
-   andere – eine Zeichenfolge, die Sprachnamen einer darstellt  
  
 **Erstellen eines Themas Help Viewer**  
  
 Erstellen Sie ein neues XHTML\-Dokument mit dem Namen ContosoTopic4.htm, und fügen Sie das Title\-Tag \(siehe unten\).  
  
```html  
<html> <head> <title>Contoso Topic 4</title> </head> <body> </body> </html>  
  
```  
  
 Als Nächstes Hinzufügen von Daten zu definieren, wie im Thema \(self Marke oder nicht\), dargestellt werden wie auf F1, in diesem Thema verweisen, in dem dieses Thema im Inhaltsverzeichnis, dessen ID \(zu Referenzzwecken Link von anderen Themen\) vorhanden ist, usw..  Finden Sie unter "Content\-Metadaten" der folgenden Tabelle eine vollständige Liste der unterstützten Metadaten.  
  
-   In diesem Fall verwenden wir unser eigenes branding\-Paket eine Variante von Visual Studio Help Viewer\-branding\-Paket.  
  
-   Fügen Sie die F1\-Meta Name und Wert \("Microsoft.Help.F1" Content \= "ContosoTopic4"\) entspricht, die den angegebenen Wert von F1 in der IDE\-Eigenschaftensammlung.  \(Siehe Abschnitt F1\-Unterstützung für Weitere Informationen.\)   Dies ist der Wert, der mit der F1 übereinstimmende rufen Sie in der IDE in diesem Thema angezeigt wird, wenn Sie F1 in der IDE ausgewählt ist.  
  
-   Fügen Sie die Thema\-ID. Dies ist die Zeichenfolge, die von anderen Themen verwendet wird, für die Verbindung zu diesem Thema.  Es ist die Hilfe\-Viewer\-ID für dieses Thema.  
  
-   Fügen Sie für das Inhaltsverzeichnis dieses Thema übergeordneten Knoten, um zu definieren, in diesem Thema Inhaltsverzeichnisknoten angezeigt werden.  
  
-   Fügen Sie für das Inhaltsverzeichnis hinzu, die Reihenfolge der in diesem Thema. Wenn der übergeordnete Knoten n Anzahl von untergeordneten Knoten verfügt, definieren Sie in der Reihenfolge der untergeordneten Knoten Speicherort des Themas. Dieses Thema ist z. B. Nummer 4 von 4 untergeordneten Themen.\)  
  
 Beispiel für Metadaten\-Abschnitt:  
  
```html  
<html> <head> <title>Contoso Topic 4</title> <meta name="SelfBranded" content="false" /> <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" /> <meta name="Microsoft.Help.Id" content="ContosoTopic4" /> <meta name="Microsoft.Help.F1" content=" ContosoTopic4" /> <meta name="Language" content="en-us" /> <meta name="Microsoft.Help.TocParent" content="ContosoTopic0" /> <meta name="Microsoft.Help.TocOrder" content="4" /> </head> <body> </body> </html>  
  
```  
  
 **Der Text des Themas**  
  
 Text \(mit Ausnahme der Kopf\- und Fußzeile\) des Themas enthält die Seite enthält Links, einen Abschnitt "Hinweis", einem reduzierbaren Bereich, einen Codeausschnitt und einen Abschnitt eines bestimmten Text in Sprache.  Finden Sie im Abschnitt Informationen zu diesen Bereichen des Themas dargestellten branding.  
  
1.  Fügen Sie ein Thema Title\-Tag hinzu:  `<div class="title">Contoso Topic 4</div>`  
  
2.  Fügen Sie einen Hinweis\-Abschnitt hinzu: `<div class="alert"> add your table tag and text </div>`  
  
3.  Fügen Sie einem reduzierbaren Bereich hinzu:  `<CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> add text  </CollapsibleArea>`  
  
4.  Fügen Sie einen Codeausschnitt hinzu:  `<CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > a block of code </CodeSnippet>`  
  
5.  Hinzufügen von Code bestimmten Text in Sprache:  `<LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" />` beachten, DevLangnu \= können Sie andere Sprachen eingeben. Z. B. DevLangnu \= "Fortran" zeigt Fortran bei der Codeausschnitt DisplayLanguage \= Fortran  
  
6.  Seitenlinks hinzufügen: `<a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a>`  
  
> [!NOTE]
>  Hinweis: für nicht unterstützte neue "Anzeigesprache" \(z. B. f\#, Cobol, Fortran\) wird die farbliche im Codeausschnitt Monochrom sein.  
  
 **Beispiel\-Viewer\-Hilfethema** im Code wird veranschaulicht, wie Metadaten, einen Codeausschnitt, einen reduzierbaren Bereich und Text in einer bestimmten Sprache zu definieren.  
  
```  
<?xml version="1.0" encoding="utf-8"?> <html> <head> <title>Contoso Topic 4</title> <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" /> <meta name="Microsoft.Help.Id" content="ContosoTopic4" /> <meta name="Microsoft.Help.F1" content=" ContosoTopic4" /> <meta name="Language" content="en-us" /> <meta name="Microsoft.Help.TocParent" content="ContosoTopic0" /> <meta name="Microsoft.Help.TocOrder" content="4" /> <meta name="SelfBranded" content="false" /> </head> <body> <div class="title">Contoso Topic 4</div> <div id="header"> <table id="bottomTable" cellpadding="0" cellspacing="0"  width="100%"> <tr id="headerTableRow2"><td align="left"> <span id="nsrTitle">Contoso Topic 1</span> </td> <td align="right"> </td></tr> <tr id="headerTableRow1"><td align="left"> <span id="runningHeaderText">Contoso Widgets & Sprockets</span> </td></tr> </table> </div> <h2>Table of Contents</h2> <ul class="toc"> <li class="tocline1"><a href="#introduction" target="_self">1.0 Introduction</a></li> <li class="tocline1"><a href="#seealso" target="_self">2.1 See Also</a></li> </ul> <div class="topic"> <div id="mainSection"> <div id="mainBody"> <a name="introduction"></a> <h2>1.0 Introduction</h2> <p>[This documentation is for sample purposes only.]</p> <p>Contoso Topic 1 contains examples of: <ul> <li>Collapsible Area</li> <li>Bookmark ("See also")</li> <li>Code Snippets from Branding Package</li> </ul> </p> <div class="alert"><table><tr><th> <strong>Note </strong></th></tr> <tr><td> <p>This is an example of a <span class="label">Note </span>section. Call out important items for your reader in this <span class="label">Note </span>box. </p></td></tr> </table> </div> </div> <CollapsibleArea Expanded="1" Title="Collapsible Area Test Heading"> <a id="sectionToggle0"><!----></a> <div> Example of Collapsible Area <br/> Lorem ipsum dolor sit amet... </div> </CollapsibleArea> <div id="snippetGroup" > <CodeSnippet EnableCopyCode="true" Language="VisualBasic" ContainsMarkup="false" DisplayLanguage="Visual Basic" > Private Sub ToolStripRenderer1_RenderGrip(sender as Object, e as ToolStripGripRenderEventArgs) _ Handles ToolStripRenderer1.RenderGrip Dim messageBoxVB as New System.Text.StringBuilder() messageBoxVB.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds) messageBoxVB.AppendLine() ... MessageBox.Show(messageBoxVB.ToString(),"RenderGrip Event") End Sub </CodeSnippet> <CodeSnippet EnableCopyCode="true" Language="CSharp" ContainsMarkup="false" DisplayLanguage="C#" > private void ToolStripRenderer1_RenderGrip(Object sender, ToolStripGripRenderEventArgs e) { System.Text.StringBuilder messageBoxCS = new System.Text.StringBuilder(); messageBoxCS.AppendFormat("{0} = {1}", "GripBounds", e.GripBounds ); messageBoxCS.AppendLine(); ... MessageBox.Show(messageBoxCS.ToString(), "RenderGrip Event" ); } </CodeSnippet> <CodeSnippet EnableCopyCode="true" Language="fsharp" ContainsMarkup="false" DisplayLanguage="F#" > some F# code </CodeSnippet> </div> <h4 class="subHeading">Example of code specific text</h4>Language = <LanguageSpecificText devLangcs="CS" devLangvb="VB" devLangcpp="C++" devLangnu="F#" /> <a name="seealso"></a> <h1 class="heading">See Also</h1> <div id="seeAlsoSection" class="section"> <div class="seeAlsoStyle"> <a href="ms-xhelp://?Id=ContosoTopic1">Main Topic</a> </div> </div> </div> </div> </body> </html>  
  
```  
  
 **F1\-Unterstützung**  
  
 In Visual Studio F1 auswählen, generiert die Werte von der Position des Cursors innerhalb der IDE, und füllt eine "Eigenschaftensammlung" mit den angegebenen Werten \(auf der Grundlage der Cursorposition. Wird der Cursor über die Funktion X, Funktion X aktiv\/im Fokus ist, und Sie werden Eigenschaftensammlung mit Werten aufgefüllt.  Wenn F1 ausgewählt ist, die Eigenschaftensammlung wird aufgefüllt, und Visual Studio\-F1\-Code sieht, um festzustellen, ob die Kunden Hilfe Standardquelle oder online ist \(online ist die Standardeinstellung\), erstellt dann die entsprechende Zeichenfolge, die auf der Basis der Benutzer festlegen \(online ist die Standardeinstellung\) – Shell ausführen \(siehe die Help\-Administratorhandbuch für EXE\-Datei Parameter starten\) mit Parametern für die lokale Hilfe\-Viewer \+ Schlüsselwörter aus dem Eigenschaftenbehälter lokale Hilfe ist die Standardeinstellung , oder die MSDN\-URL mit dem Schlüsselwort in der Parameterliste.  
  
 Wenn drei Zeichenfolgen F1 zurückgegeben werden, bezeichnet als Zeichenfolge mit mehreren Werten, die erste Bezeichnung suchen einen Treffer werden und wenn gefunden, wir haben; Wenn dies nicht der Fall ist, verschieben Sie in die nächste Zeichenfolge.  Reihenfolge ist wichtig. Präsentation der Schlüsselwörter mit mehreren Werten sollte die längste Zeichenfolge kürzesten sein.  Um dies bei mehrwertigen Schlüsselwörter zu überprüfen, sehen Sie sich die online F1 URL\-Zeichenfolge, die das ausgewählte Schlüsselwort enthält.  
  
 In Visual Studio 2012 wurde absichtlich eine stärkere Division zwischen online und offline, damit war die Einstellung des Benutzers für Online, dann wir einfach übergeben die F1\-Anforderung direkt an den Dienst online\-Abfrage auf MSDN, statt routing über den Hilfebibliotheks\-Agent, die in Visual Studio 2010 werden musste. Wir benötigen dann einen Zustand der "Vendor Inhalt installiert \= True" fest, ob etwas anderes in diesem Kontext ausführen. Wenn true, führen wir dann diese Logik Analyse\- und routing, je nachdem, was Sie für Ihre Kunden unterstützen möchten. Bei false werden dann wir nur MSDN. Wenn lokale Einstellung des Benutzers handelt, gehen alle Aufrufe einfach auf die lokale Hilfe\-Engine.  
  
 F1\-Flussdiagramm:  
  
 ![F1 flow](../../extensibility/internals/media/f1flow.png "F1flow")  
  
 Wenn der Help Viewer standardmäßig die Quelle der Hilfeinhalte auf online \(Starten im Browser\) festgelegt wird:  
  
-   Features von Visual Studio\-Partner \(VSP\) einen Wert der Eigenschaftensammlung F1 \(Eigenschaftenbehälter prefix.keyword und online\-URL für das Präfix in der Registrierung gefunden\) ausgeben: F1 einer VSP\-URL\-Parameter an den Browser gesendet.  
  
-   Visual Studio\-Funktionen \(Sprach\-Editor, Visual Studio bestimmte Menüelemente usw.\): F1 ein Visual Studio\-URL an den Browser gesendet.  
  
 Wenn der Help Viewer standardmäßig die Quelle der Hilfeinhalte auf lokale Hilfe \(im Help Viewer starten\) festgelegt ist:  
  
-   VSP\-Funktionen, bei denen Schlüsselwort übereinstimmen, zwischen Eigenschaftenbehälter F1 und lokalen Speicher \(d. h. die Eigenschaftenbehälter prefix.keyword \= Wert in den lokalen Speicher Index\): F1 rendert das Thema in der Hilfe\-Viewer.  
  
-   Visual Studio\-Funktionen \(keine Option für die VSP überschreiben die Eigenschaftensammlung, die aus Visual Studio\-Features\): F1 rendert ein Visual Studio\-Thema im Hilfe\-Viewer.  
  
 Legen Sie die folgenden Registrierungswerte F1 Fallback für Hersteller Hilfeinhalt zu aktivieren. F1\-Fallback bedeutet, dass im Hilfe\-Viewer für die F1\-Hilfe Inhalt suchen online festgelegt ist und der Hersteller Inhalt auf die Festplatte des Benutzers lokal installiert ist. Der Help Viewer sollten lokale Hilfe für den Inhalt überprüfen, obwohl die online\-Hilfe ist.  
  
1.  Legen Sie die **VendorContent** Wert unter dem Registrierungsschlüssel Help 2.1:  
  
    -   Für 32\-Bit\-Betriebssysteme:  
  
         HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12  
  
         "VendorContent" \= DWORD: 00000001  
  
    -   Für 64\-Bit\-Betriebssysteme:  
  
         HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12  
  
         "VendorContent" \= DWORD: 00000001  
  
2.  Registrieren Sie den Partner\-Namespace unter dem Registrierungsschlüssel Help 2.1:  
  
    -   Für 32\-Bit\-Betriebssysteme:  
  
         HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Help\\v2.1\\Partner*\\ \< Namespace \>*  
  
         "Speicherort"\="offline"  
  
    -   Für 64\-Bit\-Betriebssysteme:  
  
         HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Partner*\\ \< Namespace \>*  
  
         "Speicherort"\="offline"  
  
 **Systemeigene Basisnamespace analysieren**  
  
 Zum Aktivieren der systemeigenen Basisnamespace Analyse in der Registrierung hinzufügen einen neuen DWORD\-Wert mit dem Namen: BaseNativeNamespaces und legen Sie seinen Wert auf 1 \(unter dem Katalog\-Schlüssel, die sie unterstützen möchten\).  Wenn Sie den Visual Studio\-Katalog verwenden möchten, können Sie z. B. den Schlüssel auf den Pfad hinzufügen:  
  
 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12  
  
 Wenn ein F1\-Schlüsselwort in das Format, das HEADER\-Methode gefunden wird, wird das Zeichen '\/', analysiert werden, was das folgende Konstrukt:  
  
-   HEADER: werden der Namespace, der verwendet werden kann, um in der Registrierung registrieren  
  
-   Methode: Dadurch werden das Schlüsselwort verwendet, das über übergeben wird.  
  
 Angenommen, eine benutzerdefinierte Bibliothek namens CustomLibrary und eine Methode namens "MyTestMethod", wenn eine in diesem Anforderung F1 formatiert `CustomLibrary/MyTestMethod`.  
  
 Ein Benutzer kann dann CustomLibrary als Namespace Hive Partner registrieren, und geben Sie beliebige gewünschte Speicherort\-Schlüssel, und das Schlüsselwort an die Abfrage übergeben werden MyTestMethod.  
  
 **Aktivieren der Hilfe debugging\-Tools in der IDE**  
  
 Fügen Sie den folgenden Schlüssel und Wert hinzu:  
  
 HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\12.0\\Dynamic Hilfetaste: Debug\-Ausgabe in Verkaufswert anzeigen: Ja  
  
 Wählen Sie in der IDE unter das Hilfemenüelement "Hilfekontext Debuggen"  
  
 **Content\-Metadaten**  
  
 In der folgenden Tabelle ist eine Zeichenfolge, die in Klammern steht ein Platzhalter, der durch einen gültigen Wert ersetzt werden muss. Z. B. in \< Meta name\="Microsoft.Help.Locale" Content \= "\[Sprachcode\]" \/ \>, "\[Sprachcode\]" muss z. B. durch einen Wert ersetzt werden "En\-us".  
  
|Eigenschaft \(HTML\-Darstellung\)|Beschreibung|  
|---------------------------------------|------------------|  
|\< Meta name\="Microsoft.Help.Locale" Content \= "\[Sprachcode\]" \/ \>|Legt ein Gebietsschema für dieses Thema. Wenn dieses Tag in einem Thema verwendet wird, muss nur einmal verwendet werden, und sie über keine weiteren Microsoft Help\-Tags eingefügt werden muss. Wenn dieses Tag nicht verwendet wird, wird der Textkörper des Themas indiziert, mithilfe von wörtertrennung, die das Produktgebietsschema zugeordnet ist, wenn es angegeben wird. andernfalls die En\-us Worttrennmodul verwendet wird. Dieses Tag entspricht dem Standard RFC 4646 ISOC. Um sicherzustellen, dass Microsoft Help ordnungsgemäß funktioniert, verwenden Sie diese Eigenschaft anstelle der allgemeinen Language\-Attribut.|  
|\< Meta name\="Microsoft.Help.TopicLocale" Content \= "\[Sprachcode\]" \/ \>|Legt ein Gebietsschema für dieses Thema, wenn auch andere Gebietsschemas verwendet werden. Wenn dieses Tag in einem Thema verwendet wird, muss sie nur einmal verwendet werden. Verwenden Sie dieses Tag, wenn der Katalog Inhalt in mehreren Sprachen enthält. Mehrere Themen in einem Katalog können dieselbe ID haben, jedoch muss jede einen eindeutigen TopicLocale angeben. Das Thema, das eine TopicLocale angibt, die dem Gebietsschema des Katalogs entspricht, ist das Thema, das im Inhaltsverzeichnis angezeigt wird. Allerdings werden alle Sprachversionen des Themas in den Suchergebnissen angezeigt.|  
|\< Title \> \[Title\] \< \/ title \>|Gibt den Titel dieses Themas. Dieses Tag ist erforderlich und muss nur einmal in einem Thema verwendet werden. Enthält den Text des Themas keinen \< Div \>\-Titelabschnitt, wird dieser Titel in diesem Thema und im Inhaltsverzeichnis angezeigt.|  
|\< Meta Name \= "Microsoft.Help.Keywords" Content \= "\[aKeywordPhrase\]" \/ \>|Gibt den Text einer Verknüpfung, die im Bereich "Index" der Help Viewer angezeigt wird. Wenn auf der Link geklickt wird, wird das Thema angezeigt. Sie können mehrere Indexschlüsselwörter für ein Thema festlegen, oder Sie können dieses Tag weglassen, wenn Sie nicht, dass Links zu diesem Thema im Index angezeigt werden möchten. "K" Schlüsselwörter aus früheren Versionen der Hilfe können dieser Eigenschaft konvertiert werden.|  
|\< Meta name\="Microsoft.Help.Id" Content \= "\[TopicID\]" \/ \>|Wird den Bezeichner für die in diesem Thema. Dieses Tag ist erforderlich und muss nur einmal in einem Thema verwendet werden. Die ID muss für Themen im Katalog eindeutig sein, die das gleiche Gebietsschema festgelegt wurde. In einem anderen Thema können Sie eine Verknüpfung zu diesem Thema erstellen, mit dieser ID an.|  
|\< Meta\-name\="Microsoft.Help.F1" content\="\[System.Windows.Controls.Primitives.IRecyclingItemContainerGenerator\]"\/ \>|Gibt das F1\-Schlüsselwort für die in diesem Thema. Sie können mehrere F1\-Schlüsselwörter für ein Thema angeben, oder Sie können dieses Tag weglassen, wenn Sie nicht in diesem Thema angezeigt, wenn ein Anwendungsbenutzer F1 drückt. In der Regel ist nur ein F1\-Schlüsselwort für ein Thema angegeben. "F" Schlüsselwörter aus früheren Versionen der Hilfe können dieser Eigenschaft konvertiert werden.|  
|\< Meta Name \= "Description" Content \= "\[themabeschreibung\]" \/ \>|Enthält eine kurze Zusammenfassung des Inhalts in diesem Thema. Wenn dieses Tag in einem Thema verwendet wird, muss sie nur einmal verwendet werden. Diese Eigenschaft wird direkt von der Abfrage\-Bibliothek zugegriffen. in der Indexdatei nicht gespeichert.|  
|\< Meta name\="Microsoft.Help.TocParent" Content \= "\[Parent\_Id\]" \/ \>|Gibt die übergeordneten Thema dieses Themas im Inhaltsverzeichnis an. Dieses Tag ist erforderlich und muss nur einmal in einem Thema verwendet werden. Der Wert ist die Microsoft.Help.Id des übergeordneten Elements. Ein Thema kann nur ein Speicherort in der Tabelle des Inhalts erforderlich. Themen\-ID für den Stamm des Inhaltsverzeichnisses gilt als "\-1". In [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)], diese Seite ist die Hilfe\-Viewer\-Startseite. Dies ist aus demselben Grund, insbesondere hinzugefügt TocParent \=\-1 einige Themen, um sicherzustellen, dass sie auf der obersten Ebene werden angezeigt. Die Startseite der Hilfe\-Viewer ist eine System\-Seite und daher nicht ersetzbare. Wenn VSP versucht, eine Seite mit der ID 1 hinzufügen, wird es kann Inhalt hinzugefügt, aber Help Viewer immer der Seite – Startseite der Hilfe\-Viewer|  
|\< Meta name\="Microsoft.Help.TocOrder" Content \= "\[positive ganze Zahl\]" \/ \>|Gibt an, in dem in der Tabelle der Inhalt in diesem Thema relativ zu dessen Peer\-Themen angezeigt wird. Dieses Tag ist erforderlich und muss nur einmal in einem Thema verwendet werden. Der Wert ist eine ganze Zahl. Ein Thema, das eine kleineren Wert ganze Zahl angibt, wird über ein Thema, das eine höheren Wert ganze Zahl angibt.|  
|\< Meta name\="Microsoft.Help.Product" Content \= "\[Produktcode\]" \/ \>|Gibt das Produkt an, dem in diesem Thema beschrieben. Wenn dieses Tag in einem Thema verwendet wird, muss sie nur einmal verwendet werden. Diese Informationen kann auch als Parameter bereitgestellt werden, der auf den Hilfe\-Indexer übergeben wird.|  
|\< Meta name\="Microsoft.Help.ProductVersion" Content \= "\[Versionsnummer\]" \/ \>|Gibt die Version des Produkts, das in diesem Thema beschrieben. Wenn dieses Tag in einem Thema verwendet wird, muss sie nur einmal verwendet werden. Diese Informationen kann auch als Parameter bereitgestellt werden, der auf den Hilfe\-Indexer übergeben wird.|  
|\< Meta name\="Microsoft.Help.Category" Content \= "\[String\]" \/ \>|Zum Identifizieren der Unterabschnitte des Inhalts verwendet von Produkten. Sie können mehrere Unterabschnitte für ein Thema identifizieren, oder Sie können dieses Tag weglassen, wenn Sie nicht, dass Links zu jedem Unterabschnitte identifizieren möchten. Dieses Tag wird verwendet, um die Attribute für TargetOS und TargetFrameworkMoniker speichern, wenn ein Thema aus einer früheren Version der Hilfe konvertiert wird. Das Format des Inhalts ist AttributeName:AttributeValue.|  
|\< Meta name\="Microsoft.Help.TopicVersion Content \="\[Thema Version Anzahl\]"\/ \>|Gibt diese Version des Themas, in einem Katalog mehrere Versionen vorhanden. Da Microsoft.Help.Id nicht eindeutig sein unbedingt, ist dieses Tag erforderlich, wenn mehr als eine Version eines Themas in einem Katalog, z. B. liegt vor, wenn ein Katalog ein Thema für .NET Framework 3.5 und ein Thema für .NET Framework 4 enthält, und beide verfügen über die gleichen Microsoft.Help.Id.|  
|\< Meta Name \= "SelfBranded" Content \= "\[TRUE oder FALSE\]" \/ \>|Gibt an, ob es sich bei diesem Thema wird der Hilfebibliotheks\-Manager Start branding oder branding\-Paket, das für das Thema gilt. Dieses Tag muss entweder "true" oder "false". Wenn es TRUE ist, und klicken Sie dann die branding\-Paket für das zugehörige Thema branding\-Paket, das festgelegt wird überschreibt, wenn der Hilfebibliotheks\-Manager startet, sodass das Thema gerendert wird, wie beabsichtigt, selbst wenn es das Rendering von anderen Inhalten unterscheidet. Ist er FALSE, wird das aktuelle Thema gemäß der branding\-Paket gerendert, die festgelegt wird, wenn der Hilfebibliotheks\-Manager gestartet wird. Standardmäßig nimmt Hilfebibliotheks\-Manager Self\-branding auf false festgelegt ist, es sei denn, die SelfBranded\-Variable als TRUE deklariert wird. Sie müssen daher keine deklarieren \< Meta Name \= "SelfBranded" Content \= "FALSE" \/ \>.|  
  
### Erstellen eines Pakets branding  
 Die Visual Studio\-Version umfasst eine Anzahl von anderen Visual Studio\-Produkten, einschließlich der isoliert und integrierte Shells für Visual Studio\-Partner.  Jedes dieser Produkte erfordert ein gewisses Maß an themenbasierte Hilfeinhalt branding\-Unterstützung für das Produkt eindeutig.  Beispielsweise benötigen Visual Studio\-Themen eine Markenpräsentation konsistent SQL Studio, das ISO\-Shell umbrochen wird, erfordert eine eigene eindeutige Hilfe Content branding für jedes Thema.  Eine integrierte Shell Partner sollten ihre innerhalb des übergeordneten Elements Hilfeinhalt für Visual Studio\-Produkt werden, während ihre eigenen Thema branding\-Hilfethemen.  
  
 Branding\-Pakete werden vom Produkt mit der Help Viewer installiert.  Für Visual Studio\-Produkte:  
  
-   Eine alternative branding\-Paket \(Branding\_ \< Gebietsschema \> mshc\) im Stammverzeichnis app Help Viewer 2.1 installiert ist \(Beispiel: C:\\Program Files \(X 86\) \\Microsoft Help Viewer\\v2.1\) vom Help Viewer Language Pack.  Dieser Wert wird für Fälle, in denen entweder das Produkt branding\-Paket ist nicht installiert \(kein Inhalt installiert wurde\) oder, in dem die installierten branding\-Paket ist beschädigt.  Beachten Sie, dass die Visual Studio\-Elemente \(Logo und Feedback\) ignoriert werden, wenn die app Root Fallback branding\-Paket verwendet wird.  
  
-   Wenn Visual Studio\-Inhalte aus dem Content\-Paket\-Dienst installiert ist, wird ein branding\-Paket auch \(für das erste Mal Inhaltsinstallation\-Szenario\) installiert.  Wenn ein Update für das branding Paket vorhanden ist, ist das Update installiert, bei der nächsten Aktualisierung oder ein zusätzliches Paket installieren\-Aktion geschieht.  
  
 Microsoft Help Viewer unterstützt das branding von Themen, die auf der Grundlage Thema Metadaten.  
  
-   Wobei Thema Metadaten selbst die Marke definiert \= true, rendern das Thema ist, keine \(soweit es das branding\).  
  
-   Wobei Thema Metadaten selbst die Marke definiert \= False, verwenden Sie das branding Paket TopicVendor Metadatenwert zugeordnet.  
  
-   Thema Metadaten definiert, in denen name\="Microsoft.Help.TopicVendor" Content \= \< branding Paketnamen in Hersteller diese MSHA \> Verwenden Sie das branding\-Paket in den Wert Inhalt definiert.  
  
-   Beachten Sie, dass innerhalb der Visual Studio\-Katalog, eine Anwendung mit Priorität der Branding\-Pakete.  Erste Visual Studio Standard\-branding angewendet wird, und klicken Sie dann in den Metadaten Thema definiert und unterstützt das zugeordnete branding\-Paket \(im Sinne der Installation Msha\), die Hersteller branding definiert als eine Außerkraftsetzung angewendet wird.  
  
 Brandingelemente fallen normalerweise in drei Hauptkategorien unterteilt:  
  
-   Header\-Elemente \(z. B. Link "Feedback", bedingte Erläuterungstext, Logo\)  
  
-   Content\-Verhalten \(Beispiele für erweitern\/reduzieren\-Steuerelement Textelemente enthalten und Codeelemente Ausschnitt\)  
  
-   Footer\-Element \(z. B. Copyright\)  
  
 Elemente, die als Brandingelementen enthalten \(Siehe diese Spezifikation\):  
  
-   Katalog\-Produkt\-Logo \(z. B. Visual Studio\)  
  
-   Feedback\-Link und e\-Mail\-Elemente  
  
-   Verzichtserklärung  
  
-   Copyright text  
  
 Unterstützende Dateien in Visual Studio Help Viewer\-branding\-Paket:  
  
-   Grafiken \(Logos, Symbole usw.\).  
  
-   Branding.js – Dateien Skript unterstützende Content\-Verhalten  
  
-   Branding.XML – Zeichenfolgen, die konsistent in Kataloginhalt verwendet werden.  Hinweis: für Visual Studio Lokalisierung Textelemente in der branding.xml enthält \_locID \= "\< eindeutiger Wert \>"  
  
-   Branding.CSS – Stildefinitionen Presentation\-Konsistenz  
  
-   Printing.CSS – Stildefinitionen konsistent Ausdruck der Präsentation  
  
 Wie bereits erwähnt, sind Pakete Branding Thema zugeordnet:  
  
-   Wenn SelfBranded \= False in den Metadaten definiert ist, das Thema erbt den Katalog branding\-Paket  
  
-   Oder wenn SelfBranded \= false, und es wird eine eindeutige Branding\-Paket definiert in der MSHA und verfügbar, wenn der Inhalt installiert ist  
  
 Für das Implementieren von benutzerdefinierter branding Paketen VSPs \(VSP\-Inhalt, SelfBranded \= True\), eine Möglichkeit, um den Vorgang fortzusetzen, beginnen Sie mit der fallback branding\-Paket \(mit der Help Viewer installiert\), und ändern Sie den Namen der Datei nach Bedarf ist.  Die Branding\_ \< Gebietsschema \> mshc\-Datei ist eine Zip\-Datei mit der Erweiterung in mshc geändert, also einfach ändern Sie die Erweiterung von mshc in .zip, und extrahieren Sie den Inhalt.  Siehe unten für das branding Paketelemente und nach Bedarf ändern \(z. B. Ändern des Logos für das VSP\-Logo und den Verweis auf das Logo in der Datei Branding.xml, aktualisieren Sie Branding.xml pro VSP Besonderheiten usw.\).  
  
 Wenn alle Änderungen abgeschlossen haben, erstellen Sie eine Zip\-Datei, die mit der gewünschten Brandingelemente, und ändern Sie die Erweiterung in mshc.  
  
 Erstellen Sie, um das benutzerdefinierte Paket für branding zu verknüpfen, die MSHA enthält den Verweis auf das branding Mshc\-Datei zusammen mit dem Inhalt Mshc \(mit den Themen\).  Diese "MSHA" zum Erstellen einer grundlegenden diese MSHA unten Sie aufgeführt.  
  
 Die Branding.xml\-Datei enthält eine Listenelemente für bestimmte Elemente in einem Thema konsistent zu rendern, wenn das Thema enthält \< Meta name\="Microsoft.Help.SelfBranded" Content \= "false" \/ \>.  Die Visual Studio\-Liste der Elemente in der Datei Branding.xml sind unten aufgeführt.  Beachten Sie, dass diese Liste vorgesehen ist, werden als Vorlage für die ISO\-Shell\-Anwender, ändern sie diese Elemente \(z. B. Logos, Feedback und Copyright\) ihre eigenen Bedürfnisse branding Produkt erfüllen.  
  
 Hinweis: Variablen "{n}" vermerkt haben Abhängigkeiten – entfernen oder Ändern dieser Werte führt dazu, dass Fehler und möglicherweise zum Absturz der Anwendung. Lokalisierung Bezeichner \(Beispiel \_locID\="codesnippet.n"\) sind in der Visual Studio\-Branding\-Paket enthalten.  
  
 **Branding.Xml**  
  
|||  
|-|-|  
|Feature:|**CollapsibleArea**|  
|Verwendung:|Erweitern Sie Text\-Inhaltssteuerelement reduziert|  
|**Element**|**Wert**|  
|ExpandText|Erweitern|  
|CollapseText|Reduzieren|  
|Feature:|**CodeSnippet**|  
|Verwendung:|Code\-Ausschnitt Steuerelementtext.  Hinweis: Code Snippet Inhalte mit "Nicht unterbrechend" Speicherplatz wird zum Bereich geändert.|  
|**Element**|**Wert**|  
|CopyToClipboard|In Zwischenablage kopieren|  
|ViewColorizedText|Koloriert anzeigen|  
|CombinedVBTabDisplayLanguage|Visual Basic \(Beispiel\)|  
|VBDeclaration|Deklaration|  
|VBUsage|Verwendung|  
|Feature:|**Feedback, Fußzeile und \-Logo**|  
|Verwendung:|Geben Sie eine Feedback\-Steuerelement für Kunden Feedback des aktuellen Themas per E\-mail bereitstellen.  Copyright Text für den Inhalt.  Logo\-Definition.|  
|**Element**|**Wert \(diese Zeichenfolgen können Content Anwender müssen entsprechend geändert werden.\)**|  
|CopyRight|© 2013 Microsoft Corporation. Alle Rechte vorbehalten.|  
|SendFeedback|\< ein Href \= "{0}" \\{1\\} \> Feedback \<\/a \> zu diesem Thema an Microsoft senden.|  
|FeedbackLink||  
|LogoTitle|[!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)]|  
|LogoFileName|vs\_logo\_bk.gif|  
|LogoFileNameHC|vs\_logo\_wh.gif|  
|Feature:|**Haftungsausschluss**|  
|Verwendung:|Eine Gruppe von Case bestimmte Haftungsausschlüsse für Computer übersetzten Inhalten.|  
|**Element**|**Wert**|  
|MT\_Editable|Dieser Artikel wurde maschinell übersetzt. Wenn Sie über einen Internetzugang verfügen, wählen Sie "In diesem Thema online anzeigen", um diese Seite im bearbeitbaren Modus und den ursprünglichen englischen Inhalt gleichzeitig anzuzeigen.|  
|MT\_NonEditable|Dieser Artikel wurde maschinell übersetzt. Wenn Sie über einen Internetzugang verfügen, wählen Sie "In diesem Thema online anzeigen", um diese Seite im bearbeitbaren Modus und den ursprünglichen englischen Inhalt gleichzeitig anzuzeigen.|  
|MT\_QualityEditable|Dieser Artikel wurde maschinell übersetzt. Wenn Sie über einen Internetzugang verfügen, wählen Sie "In diesem Thema online anzeigen", um diese Seite im bearbeitbaren Modus und den ursprünglichen englischen Inhalt gleichzeitig anzuzeigen.|  
|MT\_QualityNonEditable|Dieser Artikel wurde maschinell übersetzt. Wenn Sie über einen Internetzugang verfügen, wählen Sie "In diesem Thema online anzeigen", um diese Seite im bearbeitbaren Modus und den ursprünglichen englischen Inhalt gleichzeitig anzuzeigen.|  
|MT\_BetaContents|Dieser Artikel wurde maschinell übersetzten für eine vorläufige Version. Wenn Sie über einen Internetzugang verfügen, wählen Sie "In diesem Thema online anzeigen", um diese Seite im bearbeitbaren Modus und den ursprünglichen englischen Inhalt gleichzeitig anzuzeigen.|  
|MT\_BetaRecycledContents|Dieser Artikel wurde für eine vorläufige Version manuell übersetzt. Wenn Sie über einen Internetzugang verfügen, wählen Sie "In diesem Thema online anzeigen", um diese Seite im bearbeitbaren Modus und den ursprünglichen englischen Inhalt gleichzeitig anzuzeigen.|  
|Feature:|**LinkTable**|  
|Verwendung:|Unterstützung für online\-Thema links|  
|**Element**|**Wert**|  
|LinkTableTitle|Linktabelle|  
|TopicEnuLinkText|Zeigen Sie die englische Version \<\/a \> in diesem Thema, das auf dem Computer verfügbar ist.|  
|TopicOnlineLinkText|In diesem Thema anzeigen \< ein Href \= "{0}" \\{1\\} \> online \<\/a \>|  
|OnlineText|Online|  
|Feature:|**Audio\-Videosteuerelement**|  
|Verwendung:|Anzeigen von Elementen und Text für Videoinhalte|  
|**Element**|**Wert**|  
|MultiMediaNotSupported|InternetExplorer 9 oder höher muss installiert werden, um {0} Inhalt zu unterstützen.|  
|VideoText|Video anzeigen|  
|AudioText|Streaming audio|  
|OnlineVideoLinkText|\< p \> zum Anzeigen des Videos in diesem Thema zugeordnet, klicken Sie auf {0} \< ein Href \= "\\\\ {1\\\\}" \> \\{2\\}here \<\/a \>. \<\/p \>|  
|OnlineAudioLinkText|\< p \>, um die in diesem Thema zugeordneten hören, klicken Sie auf {0} \< ein Href \= "\\\\ {1\\\\}" \> \\{2\\}here \<\/a \>. \<\/p \>|  
|Feature:|**Inhaltssteuerelement nicht installiert.**|  
|Verwendung:|Text\-Elemente \(Zeichenfolgen\) für die Darstellung von contentnotinstalled.htm verwendet|  
|**Element**|**Wert**|  
|ContentNotInstalledTitle|Auf dem Computer ist kein Inhalt gefunden.|  
|ContentNotInstalledDownloadContentText|\< p \>, um Inhalt auf Ihren Computer herunterladen \< ein Href \= "{0}" \\{1\\} \> Klicken Sie auf der Registerkarte verwalten \<\/a \>. \<\/p \>|  
|ContentNotInstalledText|\< p \> No Content wird auf Ihrem Computer installiert. Informieren Sie den Administrator für die lokale Hilfe Content Installation. \<\/p \>|  
|Feature:|**Thema nicht gefunden\-Steuerelement**|  
|Verwendung:|Text\-Elemente \(Zeichenfolgen\) für die Darstellung von topicnotfound.htm verwendet|  
|**Element**|**Wert**|  
|TopicNotFoundTitle|Angeforderte Thema auf Ihrem Computer wurde nicht gefunden.|  
|TopicNotFoundViewOnlineText|\< p \> das gewünschte Thema wurde auf dem Computer nicht gefunden, aber Sie können \< ein Href \= "{0}" \\{1\\} \> Zeigen Sie das Thema online \<\/a \>. \<\/p \>|  
|TopicNotFoundDownloadContentText|\< p \> finden Sie im Navigationsbereich links zu ähnlichen Themen oder \< ein Href \= "{0}" \\{1\\} \> Klicken Sie auf der Registerkarte verwalten \<\/a \> zum Herunterladen von Inhalt auf Ihrem Computer. \<\/p \>|  
|TopicNotFoundText|\< p \> das gewünschte Thema nicht auf Ihrem Computer. \<\/p \> gefunden|  
|Feature:|**Thema beschädigt Steuerelement**|  
|Verwendung:|Text\-Elemente \(Zeichenfolgen\) für die Darstellung von topiccorrupted.htm verwendet|  
|**Element**|**Wert**|  
|TopicCorruptedTitle|Kann nicht das gewünschte Thema angezeigt.|  
|TopicCorruptedViewOnlineText|\< p \> Help Viewer kann nicht auf das gewünschte Thema anzuzeigen. Möglicherweise liegt ein Fehler in das Thema Inhalt oder eine zugrunde liegende System Abhängigkeit. \<\/p \>|  
|Feature:|**Startseite\-Steuerelement**|  
|Verwendung:|Text, die Unterstützung der Anzeige der Inhalt der Hilfe\-Viewer\-Knoten der obersten Ebene.|  
|**Element**|**Wert**|  
|HomePageTitle|Startseite der Hilfe\-Viewer|  
|HomePageIntroduction|\< p \> Willkommen bei Microsoft Help Viewer eine wesentliche Informationsquelle für alle Benutzer, die Microsoft\-Tools, Produkte, Technologien und Dienste verwendet. Der Help Viewer erhalten Sie Zugriff auf die Gewusst\-wie\-und Referenzinformationen, Beispielcode, technischen Artikeln und mehr. Um den Inhalt zu suchen, den Sie das Inhaltsverzeichnis durchsuchen müssen, verwenden Sie den Volltextsuche, oder navigieren Sie durch die Inhalte, die mithilfe des Schlüsselworts Index. \<\/p \>|  
|HomePageContentInstallText|\< p \>\< Br \/ \> mit der \< ein Href \= "{0}" \\{1\\} \> Inhalt verwalten \<\/a \> Registerkarte die folgenden Schritte ausführen: \< Ul \>\< li \> Hinzufügen von Inhalt auf Ihrem Computer. \<\/li \>\< li \> Überprüfen auf Updates auf Ihrem lokalen Inhalt. \<\/li \>\< li \> Entfernen Sie Inhalt aus dem Computer. \<\/li \>\< \/ UL \>\< \/ p \>|  
|HomePageInstalledBooks|Installierte Bücher|  
|HomePageNoBooksInstalled|Auf dem Computer ist kein Inhalt gefunden.|  
|HomePageHelpSettings|Hilfe\-Inhalt\-Einstellungen|  
|HomePageHelpSettingsText|\< p \> die aktuelle Einstellung lokale Hilfe umfasst. Der Help Viewer zeigt Inhalte, die Sie auf Ihrem Computer installiert haben \< Br \/ \> Wählen Sie zum Ändern der Quelle Hilfeinhalt, der Visual Studio\-Menüleiste \< span Style \= "{0}" \> Hilfe Hilfeeinstellungen festlegen \< \/ span \>. \< Br \/ \>\< \/ p \>|  
|MB|MB|  
  
 **Branding.js**  
  
 Die branding.js\-Datei enthält JavaScript, die von Visual Studio Help Viewer Brandingelemente verwendet.  Im folgenden finden Sie eine Liste der branding\-Elemente und die unterstützenden JavaScript\-Funktion.  Im Abschnitt "Lokalisierbare Zeichenfolgen" am oberen Rand dieser Datei werden alle Zeichenfolgen lokalisiert werden, für diese Datei definiert.  Beachten Sie, dass für Loc\-Zeichenfolgen in der Datei branding.js ICL\-Datei erstellt wurde.  
  
||||  
|-|-|-|  
|**Branding\-Funktion**|**JavaScript\-Funktion**|**Beschreibung**|  
|Var...||Definieren Sie Variablen|  
|Die Sprache der Code abrufen|setUserPreferenceLang|Ordnet einen Index um Codesprache|  
|Festlegen und Abrufen von Werten für Cookies|GetCookie setCookie||  
|Geerbte Member|changeMembersLabel|Geerbten Member erweitern\/reduzieren|  
|Wenn SelfBranded \= False|onLoad|Lesen Sie die Abfragezeichenfolge prüfen, ob es sich um einen Druckauftrag ist.  Legen Sie alle Codesnippets die bevorzugte Registerkarte Benutzer konzentrieren.  Ist dies eine Anforderung IsPrinterFriendly klicken Sie dann auf True festgelegt. Überprüfen Sie den Modus für hohe Kontraste.|  
|Codeausschnitt|addSpecificTextLanguageTagSet||  
||getIndexFromDevLang||  
||Änderungsobjekte||  
||setCodesnippetLang||  
||setCurrentLang||  
||CopyToClipboard||  
|CollapsibleArea|addToCollapsibleControlSet|Schreiben Sie alle das reduzierbare Steuerelement\-Objekt in der Liste aus.|  
||CA\_Click|basierend auf den Zustand des reduzierbaren Bereichs, der definiert, welcher Bild\- und Texttyp an|  
|Kontrast\-Unterstützung für das Logo|isBlackBackground\(\)|Wird aufgerufen, um festzustellen, ob der Hintergrund Schwarz ist.  Nur korrekt, wenn im Modus für hohe Kontraste.|  
||isHighContrast\(\)|Verwenden Sie eine farbige Spanne Modus für hohe Kontraste erkennen|  
||onHighContrast\(black\)|Wird aufgerufen, wenn der hohe Kontrast erkannt wird|  
|LST\-Funktion|||  
||addToLanSpecTextIdSet\(id\)||  
||updateLST\(currentLang\)||  
||getDevLangFromCodeSnippet\(lang\)||  
|MultiMedia\-Funktionalität|Beschriftung \(beginnen, Ende, Text, Stil\)||  
||findAllMediaControls\(normalizedId\)||  
||getActivePlayer\(normalizedId\)||  
||captionsOnOff\(id\)||  
||toSeconds\(t\)||  
||getAllComments\(node\)||  
||StyleRectify \(Formatvorlage, StyleValue\)||  
||showCC\(id\)||  
||Subtitle\(ID\)||  
  
 **HTM\-DATEIEN**  
  
 Die branding\-Paket enthält eine Reihe von HTM\-Dateien, die für die Kommunikation der Schlüsselinformationen in Content helfen den Benutzern, z. B. eine Homepage, die einen Abschnitt beschreiben, welche Inhalte Sätze installiert sind und Seiten, die dem Benutzer mitteilt, wenn Themen nicht, in der lokalen Gruppe von Themen gefunden wird enthält unterstützen. Beachten Sie, dass diese HTM\-Dateien pro Produkt geändert werden können.  ISO\-Shell\-Anbieter können die Standard\-branding\-Paket erstellen und ändern das Verhalten und die Inhalte dieser Seiten Suite muss.  Diese Dateien finden Sie in ihren jeweiligen branding\-Paket in der Reihenfolge für die branding\-Tags den entsprechenden Inhalt aus der Datei branding.xml abrufen.  
  
||||  
|-|-|-|  
|**Datei**|**Verwendung**|**Inhaltsquelle angezeigt**|  
|Homepage.htm|Dies ist eine Seite, die derzeit installierten Inhalt und eine andere Meldung angezeigt, die der Benutzer über deren Inhalt angezeigt.  Diese Datei enthält zusätzliche Meta Data\-Attribut "Microsoft.Help.Id" Content \= "\-1" der dies am Anfang der lokalen Inhalte Inhaltsverzeichnis Inhalt platziert.||  
||\< META\_HOME\_PAGE\_TITLE\_ADD \/ \>|Branding.XML Tag \< HomePageTitle \>|  
||\< HOME\_PAGE\_INTRODUCTION\_SECTION\_ADD \/ \>|Branding.XML Tag \< HomePageIntroduction \>|  
||\< HOME\_PAGE\_CONTENT\_INSTALL\_SECTION\_ADD \/ \>|Branding.XML Tag \< HomePageContentInstallText \>|  
||\< HOME\_PAGE\_BOOKS\_INSTALLED\_SECTION\_ADD \/ \>|Überschrift Abschnitt Branding.xml Tag \< HomePageInstalledBooks \>, \< HomePageNoBooksInstalled \> bei der Installation keine Bücher\-Anwendung generierten Daten.|  
||\< HOME\_PAGE\_SETTINGS\_SECTION\_ADD \/ \>|Überschrift Abschnitt Branding.xml Tag \< HomePageHelpSettings \>, Abschnittstext \< HomePageHelpSettingsText \>.|  
|topiccorrupted.htm|Wenn ein Thema in der lokalen Gruppe vorhanden ist, aber für aus irgendeinem Grund nicht angezeigt werden kann \(Inhalte beschädigt\).||  
||\< META\_TOPIC\_CORRUPTED\_TITLE\_ADD \/ \>|Branding.XML Tag \< TopicCorruptedTitle \>|  
||\< TOPIC\_CORRUPTED\_SECTION\_ADD \/ \>|Branding.XML Tag \< TopicCorruptedViewOnlineText \>|  
|topicnotfound.htm|Wenn ein Thema nicht im lokalen Inhalt festgelegt, noch verfügbar online gefunden wird||  
||\< META\_TOPIC\_NOT\_FOUND\_TITLE\_ADD \/ \>|Branding.XML Tag \< TopicNotFoundTitle \>|  
||\< META\_TOPIC\_NOT\_FOUND\_ID\_ADD \/ \>|Branding.XML, Tag \< TopicNotFoundViewOnlineText \> \+ \< TopicNotFoundDownloadContentText \>|  
||\< TOPIC\_NOT\_FOUND\_SECTION\_ADD \/ \>|Branding.XML Tag \< TopicNotFoundText \>|  
|contentnotinstalled.htm|Wenn Sie keinen lokalen Inhalt für das Produkt installiert.||  
||\< META\_CONTENT\_NOT\_INSTALLED\_TITLE\_ADD \/ \>|Branding.XML Tag \< ContentNotInstalledTitle \>|  
||\< META\_CONTENT\_NOT\_INSTALLED\_ID\_ADD \/ \>|Branding.XML Tag \< ContentNotInstalledDownloadContentText \>|  
||\< CONTENT\_NOT\_INSTALLED\_SECTION\_ADD \/ \>|Branding.XML Tag \< ContentNotInstalledText \>|  
  
 **CSS\-Dateien**  
  
 Der Visual Studio\-Hilfe\-Viewer Branding\-Paket enthält zwei Css\-Dateien, um konsistente Hilfe von Visual Studio Darstellung Inhalts zu unterstützen:  
  
-   Branding.CSS – enthält Css\-Elemente für das Rendern von Where SelfBranded \= False  
  
-   Printer.CSS – enthält Css\-Elemente für das Rendern von Where SelfBranded \= False  
  
 Branding.CSS Dateien enthält Definitionen für Visual Studio Thema Präsentation \(Nachteil ist, dass die branding.css in der mshc Branding\_ \< Gebietsschema \> aus dem Paketdienst enthaltenen ändern können\).  
  
 **Grafikdateien**  
  
 Inhalte für Visual Studio zeigt eine Visual Studio\-Logo sowie andere Grafik.  Die vollständige Liste der Grafikdateien in Visual Studio Help Viewer\-branding\-Paket ist unten dargestellt.  
  
||||  
|-|-|-|  
|**Datei**|**Verwendung**|**Beispiele**|  
|Clear.gif|Zum Rendern von reduzierbaren Bereich||  
|footer\_slice.gif|Fußzeile\-Präsentation||  
|info\_icon.gif|Zum Anzeigen von Informationen|Haftungsausschluss|  
|online\_icon.gif|Dieses Symbol ist online Links zugeordnet werden||  
|tabLeftBD.gif|Zum Rendern des Code Snippet\-Containers||  
|tabRightBD.gif|Zum Rendern des Code Snippet\-Containers||  
|vs\_logo\_bk.gif|Für normale Kontrast Logo Verweise verwendet, wie im Branding.xml\-Tag \< LogoFileName \> definiert.  Visual Studio\-Produkten heißt Logo vs\_logo\_bk.gif.||  
|vs\_logo\_wh.gif|Für normale hohe Logo Verweise verwendet, wie im Branding.xml\-Tag \< LogoFileNameHC \> definiert.  Visual Studio\-Produkten heißt Logo vs\_logo\_wh.gif.||  
|ccOff.png|Untertitel\-Grafik||  
|ccOn.png|Untertitel\-Grafik||  
|ImageSprite.png|Zum Rendern von reduzierbaren Bereich|erweitert oder reduziert Grafik|  
  
### Bereitstellen von einer Reihe von Themen  
 Dies ist sehr einfach und schnell Lernprogramm zur Erstellung einer Bereitstellung der Help Viewer Content betroffenes diese MSHA\-Datei und den Satz von CAB\-Dateien festgelegt oder MSHC, die in den Themen enthält. Die MSHA ist eine XML\-Datei, einen Satz von CAB\-Dateien oder MSHC\-Dateien. Der Help Viewer erhalten die MSHA zum Abrufen einer Liste von Inhalten \(die. CAB\-Datei oder. MSHC\-Dateien\) für die lokale Installation verfügbar.  
  
 Dies ist nur eine Einführung in das einfache XML\-Schema für die Hilfe\-Viewer diese MSHA beschrieben.  Beachten Sie, dass eine beispielhafte unterhalb dieser kurzen Übersicht und Beispiel "HelpContentSetup.msha".  
  
 Der Name des dem MSHA im Rahmen dieser Einführung ist "HelpContentSetup.msha" \(der Name der Datei kann nichts mit der Erweiterung sein. DIESE MSHA\). "HelpContentSetup.msha" \(nachfolgendes Beispiel\) sollte eine Liste der CAB\-Dateien oder MSHCs verfügbaren enthalten.  Beachten Sie, dass der Dateityp innerhalb der MSHA konsistent sein muss \(bietet keine Unterstützung für eine Kombination von diese MSHA und CAB\-Datei\). Für jeden CAB oder MSHC, es muss ein \< Div\-Klasse "package" \= \>... \< \/ Div \> \(siehe Beispiel unten\).  
  
 Hinweis: in der folgenden Implementierungsbeispiel haben wir die branding\-Paket enthalten. Dies ist wichtig, enthalten, damit Sie um die erforderlichen Visual Studio Inhalt Rendern von Elementen und Content Verhalten zu erhalten.  
  
 Beispieldatei "HelpContentSetup.msha": \(ersetzen Sie "Content Set name 1" und "Set name 2" usw. mit Ihren Dateinamen Inhalt.\)  
  
```  
<html> <head /> <body class="vendor-book"> <div class="details"> <span class="vendor">Your Company</span> <span class="locale">en-us</span> <span class="product">Your Company Help Content</span> <span class="name">Your Company Help Content</span> </div> <div class="package-list"> <div class="package"> <span class="name">Your_Company _Content_Set_1</span> <span class="deployed">True</span> <a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a> </div> <div class="package"> <span class="name">Your_Company _Content_Set_2</span> <span class="deployed">True</span> <a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a> </div>.  
  
```  
  
1.  Erstellen von lokalen Ordner, z. B. "C:\\SampleContent"  
  
2.  In diesem Beispiel verwenden wir MSHC\-Dateien in den Themen enthalten.  Ein MSHC ist eine ZIP\-Datei mit der Erweiterung ZIP, geändert. MSHC.  
  
3.  Erstellen Sie die unter "HelpContentSetup.msha" als Textdatei \(Editor zum Erstellen der Datei verwendet wurde\) und speichern Sie sie in den oben genannten Ordner \(siehe Schritt 1\).  
  
 Beachten Sie, dass die Klasse "Branding" vorhanden und eindeutig ist. Die Branding\-Mshc ist in dieser Einführung aufgenommen, sodass installierte Inhalt wird branding und Content Verhaltensweisen, die in der MSHCs enthaltenen werden in der branding\-Paket enthaltenen Elemente unterstützt. Ohne diese Fehler ausgegeben, wenn das System nach Support\-Artikel, die nicht Teil der kopierten sucht \(installiert\) sind Inhalte.  
  
 Kopieren Sie zum Abrufen der Visual Studio\-Paket branding Branding\_en US.mshc Datei C:\\Program Files \(X 86\) \\Microsoft Help Viewer\\v2.1\\, an den Arbeitsordner.  
  
```html  
<html> <head /> <body class="vendor-book"> <div class="details"> <span class="vendor">Your Company</span> <span class="locale">en-us</span> <span class="product">Your Company Help Content</span> <span class="name">Your Company Help Content</span> </div> <div class="package-list"> <div class="package"> <span class="name">Your_Company _Content_Set_1</span> <span class="deployed">True</span> <a class="current-link" href="Your_Company _Content_Set_1.mshc">Your_Company _Content_Set_1.mshc </a> </div> <div class="package"> <span class="name">Your_Company _Content_Set_2</span> <span class="deployed">True</span> <a class="current-link"href=" Your_Company _Content_Set_2.mshc "> Your_Company _Content_Set_2.mshc </a> </div> <div class="package"> <span class="packageType">branding</span> <span class="name">Branding_en-US</span> <span class="deployed">True</span> <a class="current-link" href="Branding_en-US.mshc">Branding_en-US.mshc</a> </div> </div> </body> </html>  
  
```  
  
 **Zusammenfassung**  
  
 Verwenden und erweitern die oben genannten Schritte können VSPs, deren Inhalt Sätze für die Visual Studio Help Viewer bereitstellen.  
  
### Hinzufügen von Hilfe zu Visual Studio Shell \(integriert und isoliert\)  
 **Einführung**  
  
 In dieser exemplarischen Vorgehensweise veranschaulicht die Hilfeinhalte in einer Visual Studio\-Shell\-Anwendung integrieren und bereitstellen.  
  
 **Anforderungen**  
  
1.  [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)]  
  
2.  [Visual Studio 2013 isolierte Shell Redist](http://www.microsoft.com/visualstudio/11/downloads#vs-shell)  
  
 **Übersicht**  
  
 Die [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] Shell ist eine Version der [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] IDE auf dem eine Anwendung basieren können. Der Antrag enthalten die isolierte Shell zusammen mit den Erweiterungen, die Sie erstellen. Isolierte Shell Projektvorlagen verwenden, die in enthalten sind die [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] SDK, um Erweiterungen zu erstellen.  
  
 Die grundlegenden Schritte zum Erstellen eine isolierte Shell\-basierte Anwendung und die dazugehörige Hilfe:  
  
1.  Abrufen der [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] ISO Shell redistributable \(ein Microsoft\-Download\).  
  
2.  Erstellen Sie in Visual Studio eine Erweiterung der Hilfe, die z. B. auf die isolierte Shell basiert, die Contoso\-Hilfe\-Erweiterung, die weiter unten in dieser exemplarischen Vorgehensweise beschrieben wird.  
  
3.  Umschließen Sie die Erweiterung und die ISO\-Shell redistributable in eine MSI\-Datei \(eine Anwendungssetup\)\-Bereitstellung. Diese exemplarische Vorgehensweise umfasst einen Schritt während der Einrichtung nicht.  
  
 Erstellen Sie einen Visual Studio\-Inhaltsspeicher. Ändern Sie für das Szenario integrierte Shell von Visual Studio12 auf den Produktnamen für den Katalog wie folgt:  
  
-   Erstellen Sie Ordner C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12.  
  
-   Erstellen Sie eine Datei mit dem Namen "catalogtype.xml", und fügen Sie es in den Ordner. Die Datei sollte die folgenden Codezeilen enthalten:  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?> <catalogType>UserManaged</catalogType>  
    ```  
  
 Definieren Sie die Inhaltsspeicher in der Registrierung. Ändern Sie für die integrierte Shell VisualStudio12 auf den Katalog Produktnamen:  
  
-   HKLM\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12  
  
     Schlüssel: LocationPath Zeichenfolgenwert: C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\  
  
-   HKLM\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12\\en\-US  
  
     Schlüssel: Katalogname Zeichenfolgenwert: [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] Dokumentation  
  
 **Erstellen des Projekts**  
  
 So erstellen Sie eine isolierte Shell\-Erweiterung:  
  
1.  In Visual Studio unter **Datei**, wählen Sie **Neues Projekt**, unter **Andere Projekttypen** auswählen **Erweiterbarkeit**, und wählen Sie dann  **Visual Studio Shell Isolated**. Nennen Sie das Projekt `ContosoHelpShell`\) ein Erweiterungsprojekt, basierend auf der Visual Studio Isolated Shell\-Vorlage zu erstellen.  
  
2.  Öffnen Sie im Projektmappen\-Explorer im Projekt ContosoHelpShellUI im Ordner Ressourcendateien ApplicationCommands.vsct. Stellen Sie sicher, dass diese Zeile \(Suchen Sie nach "No\_Help"\) auskommentiert ist: `<!-- <define name=“No_HelpMenuCommands”/> -->`  
  
3.  Drücken Sie F5 kompilieren und ausführen **Debuggen**. Wählen Sie in der experimentellen Instanz der IDE isolierte Shell, die **Hilfe** Menü. Stellen Sie sicher, dass die **Hilfe anzeigen**, **Hinzufügen und Entfernen von Hilfeinhalt**, und **Hilfeeinstellungen festlegen** Befehle angezeigt.  
  
4.  Öffnen Sie im Projektmappen\-Explorer im Projekt ContosHelpShell im Ordner Shell Anpassung ContosoHelpShell.pkgdef. Um den Katalog Contoso Hilfe zu definieren, fügen Sie die folgenden Zeilen ein:  
  
    ```  
    [$RootKey$\Help] "Product"="Contoso" "Catalog"="Contoso" “Version"="100" "BrandingPackage"="ContosoBrandingPackage.mshc"  
    ```  
  
5.  Öffnen Sie im Projektmappen\-Explorer im Projekt ContosHelpShell im Ordner Shell Anpassung ContosoHelpShell.Application.pkgdef. Um die F1\-Hilfe zu aktivieren, fügen Sie die folgenden Zeilen ein:  
  
    ```  
    // F1 Help Provider [$RootKey$\HelpProviders\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}] "Name"="13407" "Package"="{DA9FB551-C724-11d0-AE1F-00A0C90FFFC3}" @="Help3 Provider" [$RootKey$\HelpProviders] @="{C99BDC23-FF29-46bf-9658-ADD634CCAED8}" [$RootKey$\Services\{C99BDC23-FF29-46bf-9658-ADD634CCAED8}] "Name"="Help3 Provider" @="{4A791146-19E4-11D3-B86B-00C04F79F802}"  
    ```  
  
6.  Wählen Sie im Projektmappen\-Explorer im Kontextmenü der Projektmappe ContosoHelpShell der **Eigenschaften** Menüelement. Klicken Sie unter **Konfigurationseigenschaften**, auf **Configuration Manager**. In der **Konfiguration** Spalte jeder Wert "Debug", "Release" ändern.  
  
7.  Erstellen Sie die Projektmappe. Dadurch werden eine Reihe von Dateien in einem Ordner Version, die im nächsten Abschnitt verwendet wird.  
  
 Um dies zu testen, als ob bereitgestellt:  
  
1.  Auf dem Computer sind Sie Contoso ein, um das heruntergeladene \(von oberhalb\) ISO\-Verwaltungsshell installieren bereit.  
  
2.  Erstellen eines Ordners in \\\\Program Files \(X 86\) \\, und nennen Sie es `Contoso`.  
  
3.  Kopieren Sie den Inhalt aus dem Ordner der ContosoHelpShell Version \\\\Program Files \(X 86\) \\Contoso\\ Ordner.  
  
4.  Starten des Registrierungs\-Editor durch Auswahl  **Ausführen** in die **Starten** Menü und Eingeben von `Regedit`. Wählen Sie in den Registrierungs\-Editor **Datei**, und klicken Sie dann **Import**. Navigieren Sie zum Projektordner ContosoHelpShell. Wählen Sie in den Unterordner ContosoHelpShell ContosoHelpShell.reg.  
  
5.  Erstellen Sie einen Inhaltsspeicher:  
  
     Erstellen Sie einen Contoso Inhaltsspeicher C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\ContosoDev12 für ISO\-Shell\-  
  
     Für [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] Integrated Shell erstellen Sie Ordner C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12  
  
6.  "Catalogtype.xml" erstellen und zu der Inhaltsspeicher \(vorherigen Schritt\), hinzufügen:  
  
    ```  
    <?xml version="1.0" encoding="UTF-8"?> <catalogType>UserManaged</catalogType>  
    ```  
  
7.  Fügen Sie die folgenden Registrierungsschlüssel hinzu:  
  
     HKLM\\SOFTWARE\\Wow6432Node\\Microsoft\\Help\\v2.1\\Catalogs\\VisualStudio12Key: LocationPath String\-Wert:  
  
     Für ISO\-Shell:  
  
     C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\  
  
     [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] Integrierte Shell:  
  
     C:\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\\\en\-US  
  
     Schlüssel: Katalogname Zeichenfolgenwert: [!INCLUDE[vs_dev12](../../data-tools/includes/vs_dev12_md.md)] Dokumentation. Für ISO\-Shell ist dies der Name des Katalogs.  
  
8.  Kopieren Sie den Inhalt \(CAB\-Dateien oder MSHC und diese MSHA\) in einen lokalen Ordner.  
  
9. Integrierte Shell Beispielbefehlszeile für Testzwecke Inhaltsspeicher. Für ISO\-Shell ändern Sie den Katalog und LaunchingApp Werte, um das Produkt überein.  
  
     "C:\\Program Files \(X 86\) \\Microsoft Help Viewer\\v2.1\\HlpViewer.exe" \/catalogName VisualStudio12 \/helpQuery Methode \= "Seite & Id \= ContosoTopic0" \/launchingApp Microsoft VisualStudio, 12.0  
  
10. Starten Sie die Contoso\-Anwendung \(ausgehend vom Stamm des Contoso\-app\). ISO\-Shell, wählen Sie die **Hilfe** Menüelement, und ändern Sie die **Hilfeeinstellungen festlegen** auf **verwenden lokale Hilfe**.  
  
11. Innerhalb der Shell, wählen Sie die **Hilfe** Menüelement, dann **Hilfe anzeigen**. Die lokale Hilfe\-Viewer starten sollte. Wählen Sie die Registerkarte **Inhalt verwalten** aus. Klicken Sie unter **Installationsquelle**, wählen Sie die **Datenträger** Optionsfeld. Wählen Sie die **...** Schaltfläche, und navigieren Sie zu den lokalen Ordner mit Contoso\-Inhalt \(in den lokalen Ordner im vorherigen Schritt kopiert\). Wählen Sie die Datei "HelpContentSetup.msha". Contoso wird jetzt als ein Buch in der Auswahl der Buch angezeigt. Wählen Sie **Hinzufügen**, und wählen Sie dann die **Update** Schaltfläche \(unten rechts\).  
  
12. Wählen Sie in der IDE Contoso die F1\-Taste F1 Funktionalität testen.  
  
### Zusätzliche Ressourcen  
 Die Laufzeit\-API finden Sie unter [Windows\-Hilfe\-API\-](http://msdn.microsoft.com/library/windows/desktop/hh447318\(v=vs.85\).aspx).  
  
 Weitere Informationen zum Nutzen der Hilfe\-API finden Sie unter [Hilfe\-Viewer\-Codebeispiele](http://visualstudiogallery.msdn.microsoft.com/f08f296f-7076-4aec-8da3-8f0fbe04461e)  
  
 Verwenden Sie zum Bereitstellen von Feedback zu diesen Komponenten [Microsoft Connect](http://connect.microsoft.com/).  
  
 Senden Sie Vorschläge für neue Funktionen zu [Microsoft User Voice](http://visualstudio.uservoice.com/forums/121579-visual-studio)  
  
 Um zusätzliche Hilfe erhalten, versuchen Sie die [Foren von MSDN Developer Documentation and Help System](http://social.msdn.microsoft.com/Forums/devdocs/threads)  
  
 Updates auf das aktuelle Problem, finden Sie unter der [Hilfe\-Viewer\-Infodatei](http://go.microsoft.com/fwlink/?LinkID=231397&clcid=0x409)  
  
 Um die Hilfe\-Viewer\-Uhr\-Team direkt erreichen, Senden einer E\-mail an hlpfdbk@microsoft.com