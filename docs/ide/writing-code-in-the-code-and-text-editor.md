---
title: "Schreiben von Code im Code- und Text-Editor | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.texteditor"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Zugehörige Klammer"
  - "Code"
  - "Code-Editor"
  - "Code-Editor [Visual Studio]"
  - "Code-Editor, Zugehörige Klammer"
  - "Code-Editor, Änderungen nachverfolgen"
  - "Code-Editor, Kommentarauswahl"
  - "Code-Editor, Vergleichen von Dateien"
  - "Code-Editor, Anpassen"
  - "Code-Editor, diff"
  - "Code-Editor, Error- und Warning-Marker"
  - "Code-Editor, Funktionen"
  - "Code-Editor, Gehe zu-Definition"
  - "Code-Editor, Gehe zu Zeile"
  - "Code-Editor, Zeilenumbruchzeichen"
  - "Code-Editor, Zeilennummern"
  - "Code-Editor, Navigieren zu"
  - "Code-Editor, Navigationsleiste"
  - "Code-Editor, Gliedern"
  - "Code-Editor, Drucken"
  - "Code-Editor, Wellenlinien"
  - "Code-Editor, Syntaxfarben"
  - "Code-Editor, Mit Tabstopps versehen"
  - "Code-Editor, Virtueller Bereich"
  - "Code-Editor, Zeilenumbruch"
  - "Code-Editor, Zoom"
  - "Codedateien"
  - "Code, Bearbeiten"
  - "Kommentarauswahl"
  - "diff"
  - "Error- und Warning-Marker"
  - "Gehe zu-Definition"
  - "Gehe zu Zeile"
  - "Zeilenumbruchzeichen"
  - "Zeilennummern"
  - "Navigieren zu"
  - "Gliedern"
  - "Drucken"
  - "Wellenlinien"
  - "Syntaxfarben"
  - "Mit Tabstopps versehen"
  - "Virtueller Bereich"
  - "Zeilenumbruch"
  - "Zoom"
ms.assetid: cb53ab9a-5b76-4759-b9e8-7bf32298ecbe
caps.latest.revision: 44
caps.handback.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Schreiben von Code im Code- und Text-Editor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der Visual Studio\-Editor bietet viele Funktionen, die Ihnen das Schreiben und die Verwaltung von Code erleichtern. Sie können mithilfe der Gliederung verschiedene Codeblöcke reduzieren und erweitern. Wenn Sie IntelliSense, den **Objektkatalog** und die Aufrufhierarchie verwenden, können Sie mehr über Ihren Code erfahren. Sie können im Code navigieren, indem Sie Funktionen wie **Navigieren zu**, **Gehe zu Definition** und **Alle Verweise suchen** verwenden. Mit Codeausschnitten können Sie Codeblöcke einfügen und Code mithilfe von Funktionen wie **Generate From Usage** generieren. Wenn Sie noch nie mit dem Visual Studio 2015\-Editor gearbeitet haben, finden Sie eine schnelle Übersicht unter [Codebearbeitung](https://www.visualstudio.com/features/ide-vs).  
  
 Code kann auf unterschiedliche Weise angezeigt werden. Öffnen Sie zum Anzeigen einer Projektmappe der Klassenansicht das Fenster **Klassenansicht**, oder erweitern Sie die Knoten im **Projektmappen\-Explorer** unter den Klassendateien.  
  
 Sie können Text in einzelnen oder mehreren Dateien suchen und ersetzen. Weitere Informationen finden Sie unter [Suchen und Ersetzen von Text](../ide/finding-and-replacing-text.md). Beachten Sie bei der Verwendung von regulären Ausdrücken, dass "Suchen und Ersetzen" jetzt reguläre .NET\-Ausdrücke verwendet. Weitere Informationen finden Sie unter [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
 Für die verschiedenen Visual Studio\-Sprachen werden unterschiedliche Funktionssätze angeboten, und in einigen Fällen verhalten sich die Funktionen in verschiedenen Sprachen unterschiedlich. Viele dieser Unterschiede werden in den Beschreibungen der Funktionen erläutert. Weitere Informationen können Sie den Abschnitten über einzelne Visual Studio\-Sprachen entnehmen.  
  
> [!IMPORTANT]
>  Die Visual Studio\-Edition und die verwendeten Einstellungen können sich auf die Funktionen der IDE auswirken. Sie können sich daher von den in diesem Thema beschriebenen Funktionen unterscheiden.  
  
## Editor\-Funktionen  
  
|||  
|-|-|  
|Farben für Syntax|Einige Syntaxelemente in den Code\- und Markupdateien sind unterschiedlich gefärbt, damit sie unterschieden werden können. Beispielsweise sind Schlüsselwörter \(wie `using` in C\# und `Imports` in Visual Basic\) in einer Farbe gehalten, jedoch Typen \(wie `Console` und `Uri`\) haben eine andere Farbe. Andere Syntaxelemente werden auch farbig hervorgehoben, wie zum Beispiel Zeichenfolgenliterale und Kommentare. In C\+\+ werden Farben verwendet, um Typen, Enumerationen und Makros von anderen Token zu unterscheiden.<br /><br /> Sie können die Standardfarbe für jeden Typ sehen, und Sie können die Farbe für spezifische Syntaxelemente im [Schriftarten und Farben, Umgebung, Dialogfeld "Optionen"](../ide/reference/fonts-and-colors-environment-options-dialog-box.md) ändern, auf das Sie über das Menü **Extras** zugreifen.|  
|Markierungen für Fehler und Warnungen|Wenn Sie Code hinzufügen und Ihre Projektmappe erstellen, werden möglicherweise \(a\) verschiedenfarbige Unterstreichungen \(sogenannte Wellenlinien\) oder \(b\) Glühbirnen in Ihrem Code angezeigt. Rote Wellenlinien kennzeichnen Syntaxfehler, blaue kennzeichnen Compilerfehler, grüne kennzeichnen Warnungen und lila Wellenlinien kennzeichnen alle anderen Arten von Fehlern.[Glühbirnen](../ide/perform-quick-actions-with-light-bulbs.md) schlagen Fehlerbehebungen für Probleme vor und vereinfachen das Anwenden der jeweiligen Fehlerbehebung.<br /><br /> Sie können die Standardfarben für alle Wellenlinien, die Fehler und Warnungen anzeigen, im Dialogfeld **Extras \> Optionen \> Umgebung \> Schriftarten und Farben** aufrufen. Suchen Sie nach **Syntaxfehler**, **Compilerfehler**, **Warnung** und **Anderer Fehler**.|  
|Überprüfung des Klammergleichgewichts|Bei Platzierung der Einfügemarke auf eine öffnende geschweifte Klammer in einer Codedatei werden die öffnende und die schließende Klammer hervorgehoben. Durch diese Funktion erhalten Sie unmittelbar Feedback zu falsch platzierten oder fehlenden geschweiften Klammern. Sie können die Zuordnung von geschweiften Klammern mit der Einstellung **Trennzeichen automatisch hervorheben** \(**Extras \> Optionen \> Text\-Editor**\) aktivieren bzw. deaktivieren. Sie können die in der Einstellung **Schriftarten und Farben** festgelegte Hervorhebungsfarbe ändern \(**Extras \> Optionen \> Umgebung**\). Suchen Sie nach **Zugehörige Klammer \(Hervorhebung\)** oder **Zugehörige Klammer \(Rechteck\)**.|  
|Zeilennummern|Zeilennummern können im linken Rand des Codefensters angezeigt werden. Standardmäßig werden sie nicht angezeigt. Sie können diese Option in den Einstellungen **Text\-Editor \> Alle Sprachen** \(**Extras \> Optionen \> Text\-Editor \> Alle Sprachen**\) deaktivieren. Sie können die Zeilennummern für einzelne Programmiersprachen anzeigen, indem Sie die Einstellungen für diese Sprachen ändern \(**Extras \> Optionen \> Text\-Editor \<Sprache\>**\). Damit die Zeilennummern ausgedruckt werden, müssen Sie im Dialogfeld **Drucken** die Option "Zeilennummern einschließen" auswählen.|  
|Änderungsnachverfolgung|Durch die Farbe am linken Rand können Sie die Änderungen verfolgen, die Sie an einer Datei vorgenommen haben. Änderungen, die Sie seit dem Öffnen der Datei vorgenommen, jedoch nicht gespeichert haben, werden durch eine gelbe Leiste am linken Rand gekennzeichnet \(auch als "Auswahlrand" bezeichnet\). Nach dem Speichern der Änderungen \(jedoch vor dem Schließen der Datei\), wird die Statusleiste grün. Wenn Sie eine Änderung rückgängig machen, nachdem Sie die Datei gespeichert haben, wird die Leiste orange. Wenn Sie diese Funktion aktivieren oder deaktivieren möchten, ändern Sie die Option **Änderungen nachverfolgen** in den Einstellungen des **Text\-Editors** \(**Extras \> Optionen \> Text\-Editor**\).|  
|Auswählen von Text und Code|Sie können Text entweder im standardmäßigen fortlaufenden Streammodus oder im Feldmodus auswählen, indem Sie einen rechteckigen Bereich des Texts anstelle eines Zeilensatzes auswählen. Um eine Auswahl im Feldmodus zu vorzunehmen, drücken Sie auf ALT, während Sie die Maus über die Auswahl ziehen \(oder drücken Sie UMSCHALT\+ALT\+\<Pfeiltaste\>\). Die Auswahl umfasst alle Zeichen innerhalb des Rechtecks, das durch das erste und das letzte Zeichen in der Auswahl definiert wird. Eingaben oder Einfügungen im ausgewählten Bereich werden in jeder Zeile am gleichen Punkt eingefügt.|  
|Zoom|Sie können die Anzeige in jedem Codefenster vergrößern oder verkleinern, indem Sie die STRG\-TASTE gedrückt halten und das Mausrad drehen \(oder zum Vergrößern STRG\+UMSCHALT\+. und zum Verkleinern STRG\+UMSCHALT\+, drücken\). Sie können auch mithilfe des Zoomfelds links unten im Codefenster einen bestimmten Zoomprozentsatz festlegen. Die Zoomfunktion funktioniert nicht in Toolfenstern.|  
|Virtueller Bereich|Standardmäßig enden Zeilen in Visual Studio\-Editoren nach dem letzten Zeichen, sodass der Cursor am Ende einer Zeile mit der NACH RECHTS\-TASTE an den Anfang der nächsten Zeile verschoben werden kann. In einigen Editoren endet eine Zeile nicht nach dem letzten Zeichen, und Sie können den Cursor an einer beliebigen Stelle in der Zeile platzieren. Der virtuelle Bereich kann im Editor über die Einstellungen **Extras \> Optionen \> Text\-Editor \> Alle Sprachen** aktiviert werden. Beachten Sie, dass Sie entweder **Virtueller Bereich** oder **Zeilenumbruch** aktivieren können, jedoch nicht beide Optionen gleichzeitig.|  
|Drucken|Beim Drucken einer Datei können Sie über die Optionen im Dialogfeld **Drucken** Zeilennummern einschließen oder reduzierte Bereiche des Codes ausblenden. Im Dialogfeld **Seite einrichten** können Sie auch festlegen, dass der vollständige Pfad und der Dateiname gedruckt werden, indem Sie **Kopfzeile** auswählen.<br /><br /> Im Dialogfeld **Extras \> Optionen \> Umgebung \> Schriftarten und Farben** können Sie Farbdruckoptionen festlegen. Wählen Sie **Drucker** in der Liste **Einstellungen anzeigen für** aus, um den Farbdruck anzupassen. Sie können zum Drucken einer Datei andere Farben als beim Bearbeiten der Datei angeben.|  
|Globales Rückgängigmachen und Wiederholen|Mithilfe der Befehle **Letzte globale Aktion rückgängig machen** und **Letzte globale Aktion wiederholen** im Menü **Bearbeiten** werden globale Aktionen, die sich auf mehrere Dateien auswirken, rückgängig gemacht oder wiederholt. Globale Aktionen beinhalten das Umbenennen einer Klasse oder eines Namespaces, das Durchführen eines Such\- und Ersetzungsvorgangs in einer Projektmappe, die Umgestaltung einer Datenbank oder eine beliebige andere Aktion, die mehrere Dateien ändert. Sie können die Befehle zum globalen Rückgängigmachen und Wiederholen auf Aktionen in der aktuellen Visual Studio\-Sitzung anwenden, sogar nachdem Sie die Projektmappe geschlossen haben, in der eine Aktion angewendet wurde.|  
  
## Erweiterte Bearbeitungsfunktionen  
 Einige erweiterte Funktionen befinden sich im Untermenü **Bearbeiten \> Erweitert**. Nicht alle diese Funktionen sind für alle Typen von Codedateien verfügbar.  
  
|||  
|-|-|  
|Dokument formatieren|Legt den richtigen Einzug von Codezeilen fest und verschiebt geschweifte Klammern in separate Zeilen im Dokument.|  
|Auswahl formatieren|Legt den richtigen Einzug von Codezeilen fest und verschiebt geschweifte Klammern in separate Zeilen in der Auswahl.|  
|Ausgewählte Zeilen mit Tabstopps versehen|Ändert führende Leerzeichen ggf. in Tabstopps.|  
|Tabstopps aus ausgewählten Zeilen entfernen|Ändert führende Tabstopps in Leerzeichen. Wenn Sie in einer Datei alle Leerzeichen in Tabstopps \(oder alle Tabstopps in Leerzeichen\) konvertieren möchten, können Sie dazu die Befehle `Edit.ConvertSpacesToTabs` und `Edit.ConvertTabsToSpaces` verwenden. Diese Befehle werden nicht in Visual Studio\-Menüs angezeigt. Sie können sie jedoch über das Schnellzugriffs\- oder Befehlsfenster aufrufen.|  
|In Großbuchstaben umwandeln|Wandelt alle Zeichen in der Auswahl in Großbuchstaben um. Wenn keine Auswahl vorhanden ist, wird das Zeichen an der Einfügemarke in Großbuchstaben dargestellt.|  
|In Kleinbuchstaben umwandeln|Wandelt alle Zeichen in der Auswahl in Kleinbuchstaben um. Wenn keine Auswahl vorhanden ist, wird das Zeichen an der Einfügemarke in Kleinbuchstaben dargestellt.|  
|Dokument prüfen|Überprüft JScript\-Codedateien.|  
|Horizontale Leerstelle löschen|Löscht Tabstopps oder Leerzeichen am Ende der aktuellen Zeile.|  
|Leerstelle anzeigen|Zeigt Leerzeichen als Hochpunkte und Tabstopps als Pfeile an. Das Ende einer Datei wird als rechteckiges Symbol angezeigt. Wenn **Extras \> Optionen \> Text\-Editor \> Alle Sprachen \> Zeilenumbruch \> Visuelle Symbole für Zeilenumbruch anzeigen** ausgewählt ist, wird dieses Symbol ebenfalls angezeigt.|  
|Zeilenumbruch|Bewirkt, dass alle Zeilen in einem Dokument im Codefenster sichtbar sind. In der Einstellung "Alle Sprachen" im Text\-Editor können Sie den Zeilenumbruch deaktivieren und aktivieren \(**Extras \> Optionen \> Text\-Editor \> Alle Sprachen**\).|  
|Kommentar aus Auswahl entfernen|Fügt Kommentarzeichen zur Auswahl oder aktuellen Zeile hinzu.|  
|Auswahl kommentieren|Entfernt Kommentarzeichen aus der Auswahl oder der aktuellen Zeile.|  
|Zeileneinzug vergrößern|Fügt eine Registerkarte \(oder die entsprechenden Leerzeichen\) zu den ausgewählten Zeilen oder zur aktuellen Zeile hinzu.|  
|Zeileneinzug verkleinern|Entfernt eine Registerkarte \(oder die entsprechenden Leerzeichen\) aus den ausgewählten Zeilen oder der aktuellen Zeile.|  
|Tag auswählen|Wählt das Tag in einem Dokument aus, das Tags enthält \(zum Beispiel XML oder HTML\).|  
|Tag\-Inhalt auswählen|Wählt den Tag\-Inhalt in einem Dokument aus, das Tags enthält \(zum Beispiel XML oder HTML\).|  
  
## Navigieren im Codefenster  
 Sie können sich auf verschiedene Arten in einem Dokument bewegen. Zusätzlich zu den Standardvorgängen können Sie die Schaltflächen **Rückwärts navigieren** \(oder STRG\+MINUSZEICHEN\) und **Vorwärts navigieren** \(oder STRG\+UMSCHALT\+MINUSZEICHEN\) auf der Symbolleiste verwenden, um die Einfügemarke im aktiven Dokument auf vorherige Positionen oder auf Positionen zu verschieben, die Sie gerade erst besucht haben. Diese Schaltflächen speichern die letzten 20 Positionen der Einfügemarke.  
  
 ![Navigationsschaltflächen "Vor" und "Zurück"](../ide/media/vs2015_nav_buttons.png "VS2015\_Nav\_buttons")  
  
 Sie können ebenfalls die erweiterte Bildlaufleiste im Codefenster verwenden, um den Code aus der Vogelperspektive zu betrachten. Im Zuordnungsmodus können Sie eine Codevorschau sehen, wenn Sie den Cursor auf der Bildlaufleiste nach oben und unten bewegen. Weitere Informationen hierzu finden Sie unter [Gewusst wie: Nachverfolgen von Code durch Anpassen der Schiebeleiste](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md).  
  
 Die folgenden Befehle stehen für codespezifische Navigationsmethoden:  
  
|||  
|-|-|  
|Gehe zu \<Zeilennummer\>|\(**Bearbeiten \> Gehe zu** oder STRG\+G\): zu einer bestimmten Zeilennummer im aktiven Dokument wechseln.|  
|Navigieren zu|\(**Bearbeiten\/Navigieren zu** oder STRG\+,\): sucht ein Symbol oder eine Datei in der aktiven Projektmappe. Hiermit können Sie einen geeigneten Satz von übereinstimmenden Ergebnissen für eine Abfrage auswählen. Sie können nach Schlüsselwörtern in einem Symbol suchen, indem Sie die Kamel\-Schreibweise und Unterstriche verwenden, um das Symbol in Schlüsselwörter aufzuteilen.|  
|Alle Verweise suchen|\(Kontextmenü\): sucht alle Verweise auf das ausgewählte Element in der Projektmappe.|  
|Gehe zu Definition|\(Kontextmenü oder F12\): sucht die Definition des ausgewählten Elements.|  
|Peek\-Definition|\(Kontextmenü oder ALT\+F12\): sucht die Definition des ausgewählten Elements und zeigt sie in einem Popupfenster an. Weitere Informationen finden Sie unter [Gewusst wie: Anzeigen und Bearbeiten von Code mithilfe von "Definition einsehen" \(Alt\+F12\)](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).|  
|Nächste Methode, Vorherige Methode|\(**Bearbeiten \> Nächste Methode, Vorherige Methode**\): Verwenden Sie diese Befehle in Visual Basic\-Codedateien, um die Einfügemarke zu den verschiedenen Methoden zu verschieben.|  
|Markieren von Verweisen|Wenn Sie auf ein Symbol im Quellcode klicken, werden alle Instanzen dieses Symbols im Dokument hervorgehoben. Die markierten Symbole können Deklarationen und Verweise sowie weitere Symbole umfassen, die von **Alle Verweise suchen** zurückgegeben werden können. Dazu zählen die Namen von Klassen, Objekten, Variablen, Methoden und Eigenschaften. In Visual Basic\-Code werden auch Schlüsselwörter für viele Steuerungsstrukturen hervorgehoben. Um zum nächsten oder vorherigen hervorgehobenen Symbol zu springen, drücken Sie STRG\+UMSCHALTTASTE\+NACH\-UNTEN\-TASTE bzw. STRG\+UMSCHALTTASTE\+NACH\-OBEN\-TASTE. Sie können die Hervorhebungsfarbe in **Extras \> Optionen \> Umgebung \> Schriftarten und Farben \> Hervorgehobener Verweis** ändern.|  
|Suchen von codebezogenen Informationen|Sie können Informationen über bestimmten Code, wie Änderungen und wer diese Änderungen vorgenommen hat, Verweise, Fehler, Arbeitsaufgaben und Codeüberprüfungen sowie Komponententeststatus anzeigen, wenn Sie CodeLens im Code\-Editor verwenden. CodeLens funktioniert wie ein Heads\-up\-Display, wenn Sie Visual Studio Enterprise mit Team Foundation Server verwenden. Siehe [Änderungen am Code und andere Verläufe ermitteln](../ide/find-code-changes-and-other-history-with-codelens.md).|  
  
 Sie können zum Navigieren in einer Codedatei ebenfalls die **Navigationsleiste** verwenden, d. h. die beiden Dropdownfelder, die im oberen Bereich des Codefensters angezeigt werden. Mit dieser Leiste können Sie direkt zu einem bestimmten Typ oder zu einem der Member innerhalb eines Typs navigieren. Die Navigationsleiste wird mit Codedateien von Visual Basic, C\# und C\+\+ angezeigt.  
  
 Ändern Sie zum Ausblenden der Navigationsleiste die Option **Navigationsleiste** im Text\-Editor in der Einstellung "Alle Sprachen" \(**Extras \> Optionen \> Text\-Editor \> Alle Sprachen**, oder ändern Sie die Einstellungen für einzelne Sprachen\). Sie können in den Dropdownfeldern wie folgt navigieren:  
  
-   Um den Fokus im Codefenster der Navigationsleiste zu verschieben, drücken Sie die Tastenkombination STRG\+F2.  
  
-   Um den Fokus von der Navigationsleiste wieder in das Codefenster zu verschieben, drücken Sie ESC.  
  
-   Um den Fokus auf der Navigationsleiste von Element zu Element zu verschieben, drücken Sie die TAB\-TASTE.  
  
-   Um das Element mit dem Fokus auf der Navigationsleiste auszuwählen und zur IDE zurückzukehren, drücken Sie die EINGABETASTE.  
  
-   Um zu einer Klasse bzw. einem Typ zu navigieren, klicken Sie auf den entsprechenden Namen in der linken Dropdownliste.  
  
-   Um direkt zu einer Prozedur in einer Klasse zu navigieren, klicken Sie auf die Prozedur in der rechten Dropdownliste.  
  
 In einer partiellen Klasse sind Member, die außerhalb der aktuellen Codedatei definiert wurden, ggf. abgeblendet.  
  
## Anpassen des Editors  
 **Einstellungen importieren und exportieren**: Sie können im Menü **Extras** unter **Assistent zum Importieren und Exportieren von Einstellungen** Einstellungen für einen anderen Entwickler freigeben, die Einstellungen an einen Standard anpassen oder zu den Visual Studio\-Standardeinstellungen zurückkehren. Sie können allgemeine Einstellungen, Spracheinstellungen und projektspezifische Einstellungen ändern.  
  
 **Tastaturzuordnung**: Sie können neue Hotkeys definieren oder bestehende Hotkeys in den Einstellungen "Extras \> Optionen \> Umgebung \> Tastatur" neu definieren. Weitere Informationen über Hotkeys finden Sie unter [Standardtastenkombinationen](../ide/default-keyboard-shortcuts-in-visual-studio.md).  
  
 Informationen über sprachspezifische Editoroptionen finden Sie unter:  
  
-   [Visual Basic Settings](/dotnet/visual-basic/developing-apps/using-ide/settings)  
  
-   [Using the Visual C\# Development Environment](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)  
  
-   [Optionen, Text\-Editor, JavaScript, Formatierung](../ide/reference/options-text-editor-javascript-formatting.md)  
  
## In diesem Abschnitt  
  
-   [Suchen und Ersetzen von Text](../ide/finding-and-replacing-text.md)  
  
-   [Codierungen und Zeilenumbrüche](../ide/encodings-and-line-breaks.md)  
  
-   [Gliedern](../ide/outlining.md)  
  
-   [Umgestaltung](../ide/refactoring-in-visual-studio.md)  
  
-   [Produktivitätstipp](../ide/productivity-tips-for-visual-studio.md)  
  
-   [Verwenden von IntelliSense](../ide/using-intellisense.md)  
  
-   [Anpassen des Editors](../ide/customizing-the-editor.md)  
  
-   [Gewusst wie: Nachverfolgen von Code durch Anpassen der Schiebeleiste](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)  
  
-   [Gewusst wie: Anzeigen und Bearbeiten von Code mithilfe von "Definition einsehen" \(Alt\+F12\)](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)  
  
-   [Ausführen von schnellen Aktionen mit Glühbirnen](../ide/perform-quick-actions-with-light-bulbs.md)  
  
-   [Codeausschnitte](../ide/code-snippets.md)  
  
-   [Verwenden der Toolbox](../ide/using-the-toolbox.md)  
  
-   [Anzeigen der Codestruktur](../ide/viewing-the-structure-of-code.md)  
  
-   [Festlegen von Lesezeichen im Code](../ide/setting-bookmarks-in-code.md)  
  
-   [Verwenden der Aufgabenliste](../ide/using-the-task-list.md)  
  
-   [Änderungen am Code und andere Verläufe ermitteln](../ide/find-code-changes-and-other-history-with-codelens.md)  
  
## Siehe auch  
 [Visual Studio\-IDE](../ide/visual-studio-ide.md)