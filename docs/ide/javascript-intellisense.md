---
title: "JavaScript IntelliSense | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "<reference>-JavaScript-XML-Tag"
  - "Codekommentare, JavaScript IntelliSense"
  - "IntelliSense [JavaScript]"
  - "IntelliSense [JavaScript], Informationen über"
  - "IntelliSense-Erweiterungen [JavaScript]"
  - "JavaScript-Code-Editor"
  - "JavaScript-Editor"
  - "JavaScript, IntelliSense"
  - "JavaScript, Verweisdirektive"
  - "JavaScript, Verweisgruppen"
  - "JavaScript, XML-Dokumentationskommentare"
  - "Verweisdirektiven [JavaScript]"
  - "Verweisgruppen [JavaScript]"
  - "reference-JavaScript-XML-Tag"
  - "XML-Codekommentare, JavaScript IntelliSense"
  - "XML-Dokumentationskommentare [JavaScript]"
ms.assetid: af1a3171-c9d8-45a3-9c96-a763e3b163ef
caps.latest.revision: 63
caps.handback.revision: 63
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# JavaScript IntelliSense
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

IntelliSense hilft Ihnen dabei, Code schneller und mit weniger Fehlern zu schreiben, indem Sie relevante Informationen direkt bei der Eingabe von Code zur Hand haben.  Während Sie mit Clientskripts in JavaScript\-Editor arbeiten, listet IntelliSense die Objekte, Funktionen, Eigenschaften und Parameter, die im aktuellen Kontext für Sie verfügbar sind, direkt auf.  Sie können eine Codierungsoption aus der von IntelliSense bereitgestellten Popupliste auswählen, um den Code zu vervollständigen.  
  
 IntelliSense vereinfacht die Ausführung folgender Aufgaben:  
  
-   Suchen nach Memberinformationen  
  
-   Einfügen von Sprachelementen direkt in den Code  
  
-   Beibehalten des Kontexts, ohne den Code\-Editor verlassen zu müssen  
  
-   Unterstützen Sie benutzerdefinierte IntelliSense\-Elemente mit XML\-Dokumentationskommentaren und JavaScript\-IntelliSense\-Erweiterbarkeit.  
  
 Dieses Thema enthält folgende Abschnitte:  
  
-   [Bestimmen des IntelliSense\-Kontexts](#DeterminingIntelliSenseContext)  
  
-   [Verarbeiten von IntelliSense\-Informationen](#ProcessingIntelliSenseInformation)  
  
-   [JavaScript\-IntelliSense\-Funktionen](#Features)  
  
-   [JavaScript\-IntelliSense\-Erweiterbarkeit](#Extensibility)  
  
-   [JavaScript\-Validierung](#Validation)  
  
 Weitere Informationen zur IntelliSense\-Funktionalität von [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] finden Sie unter [Verwenden von IntelliSense](../ide/using-intellisense.md).  
  
##  <a name="DeterminingIntelliSenseContext"></a> Bestimmen des IntelliSense\-Kontexts  
 JavaScript\-IntelliSense bietet die Möglichkeit, Codeelemente auszuwählen, die für den gesamten Skriptcode in Ihrem aktuellen Skriptkontext geeignet sind.  Dies beinhaltet nicht nur Skriptelemente in der aktuellen Datei,  sondern auch den gesamten Code auf den direkt oder indirekt vom Skript verwiesen wird, also Verweise auf Skriptdateien, Assemblyskripts, Dienste sowie seitenbezogene Verweise.  
  
 Der aktuelle Skriptkontext wird auf Grundlage der folgenden Elemente erstellt:  
  
-   Funktionen, die in allen Skriptblöcken im aktiven Dokument definiert werden.  Inline\-Skriptblöcke werden in Dateien mit folgenden Dateinamenerweiterungen unterstützt: .aspx., .ascx, .master, .html und .htm.  
  
-   `script`\-Elemente mit `src`\-Attributen, die auf eine andere Skriptdatei zeigen.  Die Zielskriptdatei muss über die Dateinamenerweiterung .js verfügen.  
  
-   JavaScript\-Dateien, die über eine `reference`\-Direktive auf andere JavaScript\-Dateien verweisen.  
  
-   Verweisgruppen für globale Objekte, IntelliSense\-Erweiterungen oder verzögert geladene Skriptdateien.  
  
-   Verweise auf XML\-Webdienste.  
  
-   Das <xref:System.Web.UI.ScriptManager>\-Steuerelement und das <xref:System.Web.UI.ScriptManagerProxy>\-Steuerelement, wenn die Webanwendung eine AJAX\-fähige .NET\-ASP\-Anwendung ist.  
  
-   [!INCLUDE[atlaslib_current_ext](../ide/includes/atlaslib_current_ext_md.md)], wenn Sie in einer AJAX\-fähigen ASP.NET\-Webanwendung arbeiten.  
  
    > [!NOTE]
    >  Skripts in Ereignishandlerattributen für HTML\-Elemente oder in `href`\-Attributen definierte Skripts werden von IntelliSense nicht unterstützt.  
  
##  <a name="ProcessingIntelliSenseInformation"></a> Verarbeiten von IntelliSense\-Informationen  
 Um JavaScript\-IntelliSense bereitzustellen, führt der Sprachdienst die folgenden Vorgänge aus:  
  
-   Erstellen einer Liste abhängiger JavaScript\-Dateien, die auf Verweisen im aktiven Dokument sowie auf rekursiven Überprüfungen der Skriptverweise in den Dateien basieren, auf die verwiesen wird.  
  
-   Durchlaufen der Liste und Erfassen von Typinformationen sowie anderer relevanter Daten aus den einzelnen Dateien.  
  
-   Aggregieren und Übergeben der Daten an den JavaScript\-Sprachdienst, über den die Typinformationen und Daten für IntelliSense bereitgestellt werden.  
  
-   Überwachen der Dateien auf Änderungen, die sich auf die IntelliSense\-Liste auswirken könnten, und Aktualisieren der Liste nach Bedarf.  Skripts auf Remotespeichern \(z. B. Speicher, auf die mit HTTP verwiesen wird\) werden nicht überwacht.  
  
##  <a name="Features"></a> JavaScript\-IntelliSense\-Funktionen  
 JavaScript\-IntelliSense unterstützt die folgenden Objekte:  
  
-   [Elemente des Dokumentobjektmodells \(DOM\)](#HTMLDom)  
  
-   [Systeminterne Objekte](#IntrinsicObjects)  
  
-   [Benutzerdefinierte Variablen, Funktionen und Objekte](#UserDefined)  
  
-   Objekte, die in externen Dateien mit Verweisen wie [Skriptverweise](#Script), [References\-Direktive](#ReferenceDirectives) und [Verweisgruppen](#ReferenceGroups) definiert werden.  
  
-   Objekte, die in Remotedateien definiert werden, die von Visual Studio heruntergeladen werden.  
  
-   Objekte, die in [XML\-Dokumentationskommentaren](#XMLDocComments), wie Parametern und Feldern, angegeben werden.  
  
-   Objekte, die mit JavaScript\-Standardkommentartags \(\/\/\) beschrieben werden.  Weitere Informationen finden Sie unter [Erweitern von JavaScript IntelliSense](../ide/extending-javascript-intellisense.md).  
  
-   Objekte, die mithilfe des [JavaScript-IntelliSense-Erweiterbarkeit](#Extensibility)\-Mechanismus unterstützt werden.  Weitere Informationen finden Sie unter [Erweitern von JavaScript IntelliSense](../ide/extending-javascript-intellisense.md).  
  
-   [ASP.NET\-AJAX\-Objekte](#ASPNet)  
  
 Wenn IntelliSense den Typ eines Objekts nicht bestimmen kann, stellt es Optionen für die Anweisungsvervollständigung mithilfe der Bezeichner im aktiven Dokument bereit.  Weitere Informationen finden Sie unter [Anweisungsvervollständigung für Bezeichner](../ide/statement-completion-for-identifiers.md).  
  
###  <a name="HTMLDom"></a> HTML\-DOM\-Elemente  
 JavaScript\-IntelliSense umfasst Programmierreferenzen für Dynamic HTML \(DHTML\)\-DOM\-Elemente, z. B. `body`, `form` und `div`.  Nur die Elemente, die im aktuellen Dokument enthalten sind, und die Masterseite werden von IntelliSense angezeigt.  JavaScript\-IntelliSense unterstützt außerdem das `window`\-Objekt und das `document`\-Objekt sowie zugehörige Member.  
  
###  <a name="IntrinsicObjects"></a> Systeminterne Objekte  
 JavaScript\-IntelliSense umfasst Programmierreferenzen für systeminterne Objekte wie `Array`, `String`, `Math`, `Date` und `Number`.  Weitere Informationen zu systeminternen Objekten finden Sie unter [Systeminterne Objekte](../Topic/Intrinsic%20Objects%20\(JavaScript\).md).  
  
###  <a name="UserDefined"></a> Benutzerdefinierte Variablen, Funktionen und Objekte  
 Wenn Sie eine JavaScript\-Datei ändern, werden Dokumente, die geöffnet sind und auf die verwiesen wird, von [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] überprüft, um alle verfügbaren Coderessourcen zu ermitteln.  Dies schließt auch die von Ihnen erstellten Variablen, Funktionen und Objekte ein.  Diese Ressourcen stehen dann für JavaScript\-IntelliSense zur Verfügung.  
  
 Weitere Informationen zu benutzerdefinierten Variablen, Funktionen und Objekten finden Sie unter [Erstellen von Objekten](http://go.microsoft.com/fwlink/?LinkId=108671) auf der MSDN\-Website.  
  
###  <a name="External"></a> Externe Dateiverweise  
 Sie können verschiedene externe Dateiverweise einschließen, um IntelliSense\-Unterstützung im Code zu erreichen.  Externe Dateiverweise können Skriptverweise oder Reference\-Direktiven sein oder sie können mit Verweisgruppen angegeben werden.  
  
####  <a name="Script"></a> Skriptverweise  
 Anstatt das gesamte Clientskript auf einer Seite zu schreiben, können Sie auf externe Dateien verweisen, die Skriptcode enthalten.  Auf diese Weise können Sie Code einfach seitenübergreifend wiederverwenden, und das Clientskript kann vom Browser zwischengespeichert werden.  
  
 Wenn Sie keine ASP.NET\-AJAX\-fähige Webseite verwenden, können Sie mit dem `src`\-Attribut im Starttag eines `script`\-Elements auf externe Skriptdateien verweisen.  Das `src`\-Attribut gibt die URL zu einer externen Datei an, die den Quellcode oder die Daten enthält.  
  
 Das folgende Beispiel enthält Markup, das das `src`\-Attribut in einem \<`script`\>\-Tag zum Verweisen auf eine Skriptdatei verwendet.  
  
```html  
<script type="text/javascript" src="~/Scripts/JavaScript.js">  
  
</script>  
```  
  
 Bei Verwendung einer ASP.NET\-AJAX\-fähigen Webseite können Sie mithilfe des <xref:System.Web.UI.ScriptReference>\-Objekts des <xref:System.Web.UI.ScriptManager>\-Steuerelements auf Skriptdateien verweisen.  
  
 Das folgende Beispiel enthält Markup, das ein <xref:System.Web.UI.ScriptReference>\-Objekt in einem <xref:System.Web.UI.ScriptManager>\-Steuerelement zum Verweisen auf eine Skriptdatei verwendet.  
  
```html  
<asp:ScriptManager ID="ScriptManager1" runat="server">  
  <Scripts>  
    <asp:ScriptReference Path="~/Scripts/JavaScript.js" />  
  </Scripts>  
</asp:ScriptManager>  
```  
  
 IntelliSense bietet zusätzlich Unterstützung für Skriptdateien, die als Ressourcen in einer Assembly in ASP.NET\-AJAX\-Webanwendungen eingebettet sind.  Weitere Informationen zu eingebetteten Skriptressourcen finden Sie unter [Walkthrough: Embedding a JavaScript File as a Resource in an Assembly](../Topic/Walkthrough:%20Embedding%20a%20JavaScript%20File%20as%20a%20Resource%20in%20an%20Assembly.md).  
  
####  <a name="ReferenceDirectives"></a> Reference\-Direktiven  
 Mithilfe einer `reference`\-Direktive kann [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] eine Beziehung zwischen dem gerade von Ihnen bearbeiteten und anderen Skripts herstellen.  Die `reference`\-Direktive bietet Ihnen die Möglichkeit, eine Skriptdatei in den Skriptkontext der aktuellen Skriptdatei einzubeziehen.  Dadurch kann IntelliSense auf extern definierte Funktionen, Typen und Felder verweisen, während Sie den Code erstellen.  
  
 Sie erstellen eine `reference`\-Direktive in Form eines XML\-Kommentars.  Die Direktive muss in der Datei vor allen möglichen Skripts deklariert werden.  Eine `reference`\-Direktive kann Skriptverweise enthalten, die auf Datenträgern, Assemblys, Diensten oder Seiten basieren.  
  
 Im Folgenden wird anhand verschiedener Beispiele die Verwendung datenträgerbasierter Reference\-Direktiven veranschaulicht.  Im ersten Beispiel sucht der Sprachdienst nach der Datei in dem Ordner, der die Projektdatei enthält \(z. B. JSPROJ\).  
  
 `/// <reference path="ScriptFile1.js" />`  
  
 `/// <reference path="Scripts/ScriptFile2.js" />`  
  
 `/// <reference path="../ScriptFile3.js" />`  
  
 `/// <reference path="~/Scripts/ScriptFile4.js" />`  
  
 Das folgende Beispiel zeigt, wie ein Verweis auf ein assemblybasiertes Skript erstellt wird.  
  
 `/// <reference name "Ajax.js" assembly="System.Web.Extensions, ..." />`  
  
 Das folgende Beispiel zeigt, wie auf ein dienstbasiertes Skript verwiesen wird:  
  
 `/// <reference path="MyService.asmx" />`  
  
 `/// <reference path="Services/MyService.asmx" />`  
  
 `/// <reference path="../MyService.asmx" />`  
  
 `/// <reference path="~/Services/MyService.asmx" />`  
  
> [!NOTE]
>  Bei Skripts innerhalb von Webdienstdateien \(.asmx\) in Webanwendungsprojekten \(WAP\) wird JavaScript\-IntelliSense nicht unterstützt.  
  
 Das folgende Beispiel zeigt, wie auf ein seitenbasiertes Skript verwiesen wird.  
  
 `/// <reference path="Default.aspx" />`  
  
 `/// <reference path="Admin/Default.aspx" />`  
  
 `/// <reference path="../Default.aspx" />`  
  
 `/// <reference path="~/Admin/Default.aspx" />`  
  
 Die folgenden Regeln beziehen sich auf eine `reference`\-Direktive.  
  
-   Der `reference`\-XML\-Kommentar muss vor allen möglichen Skripts deklariert werden.  
  
-   Es muss XML\-Kommentarsyntax mit drei Schrägstrichen verwendet werden.  Verweise, die unter Verwendung der standardmäßigen Kommentarsyntax \(zwei Schrägstriche\) erstellt wurden, werden ignoriert.  
  
-   Pro Direktive kann nur eine Datei oder Ressource angegeben werden.  
  
-   Mehrere Verweise auf seitenbasierte Skripts sind nicht zulässig.  
  
-   Wenn ein Seitenverweis angegeben wird, ist kein anderer Reference\-Direktiventyp zulässig.  
  
-   Dateinamen verwenden relative Pfade.  Sie können den Tildeoperator \(`~`\) verwenden, um Pfade relativ zum Stammverzeichnis der Anwendung anzugeben.  
  
-   Absolute Pfade werden ignoriert.  
  
-   Reference\-Direktiven in Seiten, auf die verwiesen wird, werden nicht verarbeitet. Dies bedeutet, dass Reference\-Direktiven für Seiten nicht rekursiv aufgelöst werden.  Es wird nur Skriptcode berücksichtigt, auf den direkt von der Seite verwiesen wird.  
  
####  <a name="ReferenceGroups"></a> Verweisgruppen  
 Sie können vordefinierte Verweisgruppen verwenden, um anzugeben, dass bestimmte IntelliSense\-JS\-Dateien für verschiedene JavaScript\-Projekte verfügbar sind.  Die folgenden Verweisgruppentypen sind verfügbar:  
  
-   Implizit \(Windows\) für [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]\-Apps, die JavaScript verwenden.  Die Dateien, die in dieser Gruppe enthalten sind, sind für jede JS\-Datei verfügbar, die im Code\-Editor für das Projekt des angegebenen Typs geöffnet ist.  
  
-   Implizit \(Internet\), für HTML5\-Projekte.  Die Dateien, die in dieser Gruppe enthalten sind, sind im Bereich für jede JS\-Datei, die im Code\-Editor für die Projekttypen geöffnet ist.  
  
-   Dedizierte Workerverweisgruppen, für HTML5\-Web\-Worker.  Die Dateien, die in dieser Gruppe angegeben werden, sind für JS\-Dateien verfügbar, die einen expliziten Verweis auf eine dedizierte Workerverweisgruppe haben.  
  
-   Generisch, für andere JavaScript\-Projekttypen.  
  
 In den meisten Szenarien müssen Sie Verweisgruppen nicht ändern.  Wenn Sie Änderungen vornehmen möchten, können Sie Konfigurationseinstellungen für JavaScript\-Code\-Editor verwenden, um die in den Verweisgruppen enthaltenen Dateien anzugeben.  Anleitungen zur Verwendung dieser Funktion finden Sie unter [Optionen, Text\-Editor, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).  
  
> [!TIP]
>  Die IntelliSense\-Verweise werden normalerweise verwendet, um die IntelliSense\-Unterstützung für globale Objekte und für IntelliSense\-[Erweiterungen](#Extensibility) bereitzustellen.  Sie können diese Funktion auch für Skripts verwenden, die mithilfe des Skriptladeprogramms zur Laufzeit geladen werden müssen.  
  
### Remotedateiverweise  
 Sie können Visual Studio anweisen, die JavaScript\-Remotedateien herunterzuladen, auf die in einer JavaScript\-Datei verwiesen wird, um IntelliSense\-Unterstützung für die Remotedatei oder die Bibliothek bereitzustellen.  Wenn Sie diese Funktion verwenden, werden die Dateien herunterladen, wenn Sie sie als Verweis in die JavaScript\-Datei einschließen.  
  
> [!NOTE]
>  Außer für Webprojekte ist diese Funktion nur für JavaScript\-Dateien verfügbar, die außerhalb des Kontexts eines Projekts geöffnet sind.  Für Webprojekte werden die Remotedateien, auf die im Projekt verwiesen wird, standardmäßig heruntergeladen.  
  
 Anleitungen zur Verwendung dieser Funktion finden Sie unter [Optionen, Text\-Editor, JavaScript, IntelliSense](../ide/reference/options-text-editor-javascript-intellisense.md).  
  
> [!WARNING]
>  Wenn Sie diese Funktion aktivieren und einen Rückgang der Leistung im Code\-Editor feststellen, wird empfohlen, sie zu deaktivieren.  
  
###  <a name="XMLDocComments"></a> XML\-Dokumentationskommentare  
 XML\-Dokumentationskommentare sind Textbeschreibungen von Codeelementen, die Sie dem Skript hinzufügen.  Diese Textbeschreibungen werden in IntelliSense angezeigt, wenn Sie auf das kommentierte Skript verweisen.  Sie können beispielsweise Informationen zu den Parametern und dem Rückgabewert einer Funktion bereitzustellen.  XML\-Dokumentationskommentare sind nur in den Dateien, Assemblys und Diensten verfügbar, auf die verwiesen wurde.  Weitere Informationen finden Sie unter [XML\-Dokumentationskommentare](../ide/xml-documentation-comments-javascript.md) und [Gewusst wie: Erstellen von JavaScript\-XML\-Dokumentationskommentaren](../ide/create-xml-documentation-comments-for-javascript-intellisense.md).  
  
 IntelliSense kann XML\-Dokumentationskommentare in den folgenden Szenarien anzeigen:  
  
-   JS\-Datei, die auf eine andere JS\-Datei verweist.  
  
-   JS\-Datei, die auf eine ASPX\-Datei verweist.  
  
-   ASPX\-Datei, die auf eine JS\-Datei verweist.  
  
 IntelliSense ist nicht verfügbar, wenn eine ASPX\-Datei auf eine andere ASPX\-Datei verweist.  
  
###  <a name="ASPNet"></a> ASP.NET\-AJAX\-Objekte  
 JavaScript\-IntelliSense wird außerdem von ASP.NET AJAX unterstützt.  ASP.NET AJAX umfasst ein Clientframework, durch das die in ECMAScript \(JavaScript\) verfügbaren Standardtypen erweitert werden.  Damit JavaScript\-IntelliSense Einzelheiten zu ASP.NET AJAX\-Objekten bereitstellen kann, müssen XML\-Dokumentationskommentare über [!INCLUDE[atlaslib_current_ext](../ide/includes/atlaslib_current_ext_md.md)] hinzugefügt werden.  Diese XML\-Dokumentationskommentare werden angezeigt, wenn Sie Typen und Member aus der ASP.NET AJAX\-Bibliothek verwenden.  
  
> [!NOTE]
>  Private Member werden nicht von JavaScript\-IntelliSense angezeigt.  Private Member werden in ASP.NET\-AJAX als Member gekennzeichnet, die mit einem Unterstrich \(\_\) beginnen.  
  
##  <a name="Extensibility"></a> JavaScript\-IntelliSense\-Erweiterbarkeit  
 Der JavaScript\-Sprachdienst stellt Objekte und Funktionen bereit, die es Ihnen ermöglichen, die IntelliSense\-Erfahrung für Entwickler zu verändern, die Bibliotheken von Drittanbietern verwenden.  Diese Funktionen sind besonders nützlich, wenn der Standardsprachdienst nicht alle Informationen liefern kann, die Sie für Kunden bereitstellen möchten.  Weitere Informationen finden Sie unter [Erweitern von JavaScript IntelliSense](../ide/extending-javascript-intellisense.md).  
  
##  <a name="Validation"></a> JavaScript\-Validierung  
 Die JavaScript\-Skriptvalidierung wird ständig im Hintergrund ausgeführt.  Wenn [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] Syntaxfehler im JavaScript\-Code erkennt, wird wie folgt Feedback bereitgestellt:  
  
-   Unterstrichene Elemente im Editor.  Wellenförmige rote Unterstreichungen weisen auf Fehler hin.  Wenn Sie den Mauszeiger über den Fehler bewegen, wird die Fehlerbeschreibung in einer QuickInfo angezeigt.  
  
-   Fenster **Fehlerliste**.  Im Fenster **Fehlerliste** werden die Fehlerbeschreibung, die Datei, in der der Fehler aufgetreten ist, Zeilen\- und Spaltennummer und das Projekt angezeigt.  Klicken Sie im Menü **Ansicht** auf die Option **Fehlerliste**, um das Fenster **Fehlerliste** anzuzeigen.  
  
-   Das Ausgabefenster zeigt Verweise an, die nicht geladen wurden.  
  
## Siehe auch  
 [Verwenden von IntelliSense](../ide/using-intellisense.md)   
 [Gewusst wie: Erstellen von JavaScript\-XML\-Dokumentationskommentaren](../ide/create-xml-documentation-comments-for-javascript-intellisense.md)   
 [Erweitern von JavaScript IntelliSense](../ide/extending-javascript-intellisense.md)   
 [Anweisungsvervollständigung für Bezeichner](../ide/statement-completion-for-identifiers.md)   
 [XML\-Dokumentationskommentare](../ide/xml-documentation-comments-javascript.md)   
 [Info zum DHTML\-Objektmodell](http://go.microsoft.com/fwlink/?LinkID=92344)   
 [List Members](http://msdn.microsoft.com/de-de/1b9cc469-9cd4-4d42-9999-1f9479635ff8)   
 [SRC\-Attribut &#124; src\-Eigenschaft](http://go.microsoft.com/fwlink/?LinkId=92345)