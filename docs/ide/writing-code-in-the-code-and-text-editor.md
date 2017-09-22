---
title: Schreiben von Code in den Code-Editor | Microsoft-Dokumentation
ms.custom: 
ms.date: 03/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.texteditor
dev_langs:
- JScript
- VB
- CSharp
helpviewer_keywords:
- code editor, word wrap
- outlining
- code, editing
- squiggles
- code editor, outlining
- code editor, error and warning markers
- word wrap
- code editor, syntax coloring
- code editor, go to definition
- diff
- code editor [Visual Studio]
- code editor, diff
- error and warning markers
- code editor, navigation bar
- code editor, customizing
- comment selection
- code editor, tabify
- brace matching
- code editor, line numbers
- printing
- code editor, brace matching
- code editor, squiggles
- code editor, features
- line numbers
- go to definition
- syntax coloring
- code editor, go to
- code editor, comparing files
- code editor, zoom
- code editor
- code files
- go to line
- tabify
- zoom
- go to
- line break characters
- code editor, virtual space
- code editor, change tracking
- code editor, comment selection
- code editor, printing
- virtual space
- code editor, line break characters
- code editor, go to line
- code
ms.assetid: cb53ab9a-5b76-4759-b9e8-7bf32298ecbe
caps.latest.revision: 44
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 7b3cc733a1a808f60a27332024bcfff1dd9e670b
ms.contentlocale: de-de
ms.lasthandoff: 05/13/2017

---
# <a name="write-code-in-the-code-editor"></a>Schreiben von Code in den Code-Editor
Der Visual Studio-Editor bietet viele Funktionen, die Ihnen das Schreiben und die Verwaltung von Code und Text erleichtern. Sie können mithilfe der Gliederung verschiedene Codeblöcke reduzieren und erweitern. Wenn Sie IntelliSense, den **Objektkatalog**und die Aufrufhierarchie verwenden, können Sie mehr über Ihren Code erfahren. Sie können Code finden, indem Sie Funktionen wie **Gehe zu**, **Gehe zu Definition**und **Alle Verweise suchen** verwenden. Mit Codeausschnitten können Sie Codeblöcke einfügen und Code mithilfe von Funktionen wie **Generate From Usage**generieren. Wenn Sie noch nie mit dem Visual Studio-Editor gearbeitet haben, finden Sie eine schnelle Übersicht unter [Codebearbeitung](https://www.visualstudio.com/features/ide-vs) .  

 Code kann auf unterschiedliche Weise angezeigt werden. Öffnen Sie zum Anzeigen einer Projektmappe der Klassenansicht das Fenster **Klassenansicht** , oder erweitern Sie Knoten im **Projektmappen-Explorer** unter den Klassendateien.

 Sie können Text in einzelnen oder mehreren Dateien suchen und ersetzen. Weitere Informationen finden Sie unter [Suchen und Ersetzen von Text](../ide/finding-and-replacing-text.md). Sie können reguläre Ausdrücke zum Suchen und Ersetzen von Text verwenden. Weitere Informationen finden Sie unter [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  

 Für die verschiedenen Visual Studio-Sprachen werden unterschiedliche Funktionssätze angeboten, und in einigen Fällen verhalten sich die Funktionen in verschiedenen Sprachen unterschiedlich. Viele dieser Unterschiede werden in den Beschreibungen der Funktionen erläutert. Weitere Informationen können Sie den Abschnitten über einzelne Visual Studio-Sprachen entnehmen.  

> [!IMPORTANT]
>  Die Visual Studio-Edition und die verwendeten Einstellungen können sich auf die Funktionen der IDE auswirken. Sie können sich daher von den in diesem Thema beschriebenen Funktionen unterscheiden.  

## <a name="editor-features"></a>Editor-Funktionen  

|||  
|-|-|  
|Farben für Syntax|Einige Syntaxelemente in den Code- und Markupdateien sind unterschiedlich gefärbt, damit sie unterschieden werden können. Beispielsweise sind Schlüsselwörter (wie `using` in C# und `Imports` in Visual Basic) in einer Farbe gehalten, jedoch Typen (wie `Console` und `Uri`) haben eine andere Farbe. Andere Syntaxelemente werden auch farbig hervorgehoben, wie zum Beispiel Zeichenfolgenliterale und Kommentare. In C++ werden Farben verwendet, um Typen, Enumerationen und Makros von anderen Token zu unterscheiden.<br /><br /> Sie können die Standardfarbe für jeden Typ sehen, und Sie können die Farbe für spezifische Syntaxelemente im [Fonts and Colors, Environment, Options Dialog Box](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)ändern, auf das Sie über das Menü **Extras** zugreifen.|  
|Markierungen für Fehler und Warnungen|Wenn Sie Code hinzufügen und Ihre Projektmappe erstellen, werden möglicherweise (a) verschiedenfarbige Unterstreichungen (sogenannte Wellenlinien) oder (b) Glühbirnen in Ihrem Code angezeigt. Rote Wellenlinien kennzeichnen Syntaxfehler, blaue kennzeichnen Compilerfehler, grüne kennzeichnen Warnungen und lila Wellenlinien kennzeichnen alle anderen Arten von Fehlern. [Glühbirnen](../ide/perform-quick-actions-with-light-bulbs.md) schlagen Fehlerbehebungen für Probleme vor und vereinfachen das Anwenden der jeweiligen Fehlerbehebung.<br /><br /> Sie können die Standardfarben für alle Wellenlinien, die Fehler und Warnungen anzeigen, im Dialogfeld **Extras > Optionen > Umgebung > Schriftarten und Farben** aufrufen. Suchen Sie nach **Syntaxfehler**, **Compilerfehler**, **Warnung**und **Anderer Fehler**.|  
|Überprüfung des Klammergleichgewichts|Bei Platzierung der Einfügemarke auf eine öffnende geschweifte Klammer in einer Codedatei werden die öffnende und die schließende Klammer hervorgehoben. Durch diese Funktion erhalten Sie unmittelbar Feedback zu falsch platzierten oder fehlenden geschweiften Klammern. Sie können die Zuordnung von geschweiften Klammern mit der Einstellung **Trennzeichen automatisch hervorheben** (**Extras > Optionen > Text-Editor**) aktivieren bzw. deaktivieren. Sie können die in der Einstellung **Schriftarten und Farben** festgelegte Hervorhebungsfarbe ändern (**Extras > Optionen > Umgebung**). Suchen Sie nach **Zugehörige Klammer (Hervorhebung)** oder **Zugehörige Klammer (Rechteck)**.|  
|Strukturschnellansicht|Gepunktete Linien verbinden passende Klammern in Codedateien, wodurch sich öffnende und schließende Klammerpaare leichter erkennen lassen. Das hilft Ihnen bei der schnelleren Suchen von Code in Ihrer Codebasis. Sie können diese Zeilen mithilfe von **Show structure guidelines** (Strukturrichtlinien anzeigen) im Abschnitt **Display** (Anzeige) auf der Seite **Tools/Options/Text Editor/General** (Extras/Optionen/Text-Editor/Allgemein) aktivieren und deaktivieren.|
|Zeilennummern|Zeilennummern können im linken Rand des Codefensters angezeigt werden. Standardmäßig werden sie nicht angezeigt. Sie können diese Option in den Einstellungen **Text-Editor &gt; Alle Sprachen** (**Extras &gt; Optionen &gt; Text-Editor &gt; Alle Sprachen**) deaktivieren. Sie können die Zeilennummern für einzelne Programmiersprachen anzeigen, indem Sie die Einstellungen für diese Sprachen ändern (**Extras/Optionen/Text-Editor/\<Sprache>**). Damit die Zeilennummern ausgedruckt werden, müssen Sie im Dialogfeld **Drucken** die Option "Zeilennummern einschließen" auswählen.|  
|Änderungsnachverfolgung|Durch die Farbe am linken Rand können Sie die Änderungen verfolgen, die Sie an einer Datei vorgenommen haben. Änderungen, die Sie seit dem Öffnen der Datei vorgenommen, jedoch nicht gespeichert haben, werden durch eine gelbe Leiste am linken Rand gekennzeichnet (auch als "Auswahlrand" bezeichnet). Nach dem Speichern der Änderungen (jedoch vor dem Schließen der Datei), wird die Statusleiste grün. Wenn Sie eine Änderung rückgängig machen, nachdem Sie die Datei gespeichert haben, wird die Leiste orange. Wenn Sie diese Funktion aktivieren oder deaktivieren möchten, ändern Sie die Option **Änderungen nachverfolgen** in den Einstellungen des **Text-Editors** (**Extras > Optionen > Text-Editor**).|  
|Auswählen von Text und Code|Sie können Text entweder im standardmäßigen fortlaufenden Streammodus oder im Feldmodus auswählen, indem Sie einen rechteckigen Bereich des Texts anstelle eines Zeilensatzes auswählen. Um eine Auswahl im Feldmodus zu vorzunehmen, drücken Sie ALT, während Sie die Maus über die Auswahl ziehen (oder drücken Sie UMSCHALT+ALT+\<Pfeiltaste>). Die Auswahl umfasst alle Zeichen innerhalb des Rechtecks, das durch das erste und das letzte Zeichen in der Auswahl definiert wird. Eingaben oder Einfügungen im ausgewählten Bereich werden in jeder Zeile am gleichen Punkt eingefügt.|  
|Zoom|Sie können die Anzeige in jedem Codefenster vergrößern oder verkleinern, indem Sie die STRG-TASTE gedrückt halten und das Mausrad drehen (oder zum Vergrößern STRG+UMSCHALT+. und zum Verkleinern STRG+UMSCHALT+, drücken). Sie können auch mithilfe des Zoomfelds links unten im Codefenster einen bestimmten Zoomprozentsatz festlegen. Die Zoomfunktion funktioniert nicht in Toolfenstern.|  
|Virtueller Bereich|Standardmäßig enden Zeilen in Visual Studio-Editoren nach dem letzten Zeichen, sodass der Cursor am Ende einer Zeile mit der NACH RECHTS-TASTE an den Anfang der nächsten Zeile verschoben werden kann. In einigen Editoren endet eine Zeile nicht nach dem letzten Zeichen, und Sie können den Cursor an einer beliebigen Stelle in der Zeile platzieren. Der virtuelle Bereich kann im Editor über die Einstellungen **Extras > Optionen > Text-Editor > Alle Sprachen** aktiviert werden. Beachten Sie, dass Sie entweder **Virtueller Bereich** oder **Zeilenumbruch**aktivieren können, jedoch nicht beide Optionen gleichzeitig.|  
|Drucken|Beim Drucken einer Datei können Sie über die Optionen im Dialogfeld **Drucken** Zeilennummern einschließen oder reduzierte Bereiche des Codes ausblenden. Im Dialogfeld **Seite einrichten** können Sie auch festlegen, dass der vollständige Pfad und der Dateiname gedruckt werden, indem Sie **Kopfzeile**auswählen.<br /><br /> Im Dialogfeld **Extras > Optionen > Umgebung > Schriftarten und Farben** können Sie Farbdruckoptionen festlegen. Wählen Sie **Drucker** in der Liste **Einstellungen anzeigen für** aus, um den Farbdruck anzupassen. Sie können zum Drucken einer Datei andere Farben als beim Bearbeiten der Datei angeben.|  
|Globales Rückgängigmachen und Wiederholen|Mithilfe der Befehle **Letzte globale Aktion rückgängig machen** und **Letzte globale Aktion wiederholen** im Menü **Bearbeiten** werden globale Aktionen, die sich auf mehrere Dateien auswirken, rückgängig gemacht oder wiederholt. Globale Aktionen beinhalten das Umbenennen einer Klasse oder eines Namespaces, das Durchführen eines Such- und Ersetzungsvorgangs in einer Projektmappe, die Umgestaltung einer Datenbank oder eine beliebige andere Aktion, die mehrere Dateien ändert. Sie können die Befehle zum globalen Rückgängigmachen und Wiederholen auf Aktionen in der aktuellen Visual Studio-Sitzung anwenden, sogar nachdem Sie die Projektmappe geschlossen haben, in der eine Aktion angewendet wurde.|  

## <a name="advanced-editing-features"></a>Erweiterte Bearbeitungsfunktionen  
 Einige erweiterte Funktionen befinden sich im Untermenü **Bearbeiten > Erweitert** . Nicht alle diese Funktionen sind für alle Typen von Codedateien verfügbar.  

|||  
|-|-|  
|Dokument formatieren|Legt den richtigen Einzug von Codezeilen fest und verschiebt geschweifte Klammern in separate Zeilen im Dokument.|  
|Auswahl formatieren|Legt den richtigen Einzug von Codezeilen fest und verschiebt geschweifte Klammern in separate Zeilen in der Auswahl.|  
|Ausgewählte Zeilen mit Tabstopps versehen|Ändert führende Leerzeichen ggf. in Tabstopps.|  
|Tabstopps aus ausgewählten Zeilen entfernen|Ändert führende Tabstopps in Leerzeichen. Wenn Sie in einer Datei alle Leerzeichen in Tabstopps (oder alle Tabstopps in Leerzeichen) konvertieren möchten, können Sie dazu die Befehle `Edit.ConvertSpacesToTabs` und `Edit.ConvertTabsToSpaces` verwenden. Diese Befehle werden nicht in Visual Studio-Menüs angezeigt. Sie können sie jedoch über das Schnellzugriffs- oder Befehlsfenster aufrufen.|  
|In Großbuchstaben umwandeln|Wandelt alle Zeichen in der Auswahl in Großbuchstaben um. Wenn keine Auswahl vorhanden ist, wird das Zeichen an der Einfügemarke in Großbuchstaben dargestellt.|  
|In Kleinbuchstaben umwandeln|Wandelt alle Zeichen in der Auswahl in Kleinbuchstaben um. Wenn keine Auswahl vorhanden ist, wird das Zeichen an der Einfügemarke in Kleinbuchstaben dargestellt.|  
|Ausgewählte Zeilen nach oben verschieben|Verschiebt die ausgewählte Zeilen um eine Zeile nach oben Tastenkombination: ALT + NACH-OBEN-TASTE.|
|Ausgewählte Zeilen nach unten verschieben|Verschiebt die ausgewählte Zeile um eine Zeile nach unten. Tastenkombination: ALT + NACH-UNTEN-TASTE.|
|Dokument prüfen|Überprüft JScript-Codedateien.|  
|Horizontale Leerstelle löschen|Löscht Tabstopps oder Leerzeichen am Ende der aktuellen Zeile.|  
|Leerstelle anzeigen|Zeigt Leerzeichen als Hochpunkte und Tabstopps als Pfeile an. Das Ende einer Datei wird als rechteckiges Symbol angezeigt. Wenn **Extras > Optionen > Text-Editor > Alle Sprachen > Zeilenumbruch > Visuelle Symbole für Zeilenumbruch anzeigen** ausgewählt ist, wird dieses Symbol ebenfalls angezeigt.|  
|Zeilenumbruch|Bewirkt, dass alle Zeilen in einem Dokument im Codefenster sichtbar sind. In der Einstellung "Alle Sprachen" im Text-Editor können Sie den Zeilenumbruch deaktivieren und aktivieren (**Extras > Optionen > Text-Editor > Alle Sprachen**).|  
|Kommentar aus Auswahl entfernen|Fügt Kommentarzeichen zur Auswahl oder aktuellen Zeile hinzu.|  
|Auswahl kommentieren|Entfernt Kommentarzeichen aus der Auswahl oder der aktuellen Zeile.|  
|Zeileneinzug vergrößern|Fügt eine Registerkarte (oder die entsprechenden Leerzeichen) zu den ausgewählten Zeilen oder zur aktuellen Zeile hinzu.|  
|Zeileneinzug verkleinern|Entfernt eine Registerkarte (oder die entsprechenden Leerzeichen) aus den ausgewählten Zeilen oder der aktuellen Zeile.|  
|Tag auswählen|Wählt das Tag in einem Dokument aus, das Tags enthält (zum Beispiel XML oder HTML).|  
|Tag-Inhalt auswählen|Wählt den Tag-Inhalt in einem Dokument aus, das Tags enthält (zum Beispiel XML oder HTML).|  

## <a name="navigate-and-find-code"></a>Navigieren und Suchen von Code  
Sie können sich auf verschiedene Arten in einem Dokument bewegen. Zusätzlich zu den Standardvorgängen können Sie die Schaltflächen **Rückwärts navigieren** (STRG+MINUSZEICHEN) und **Vorwärts navigieren** (oder STRG+UMSCHALT+MINUSZEICHEN) auf der Symbolleiste verwenden, um die Einfügemarke im aktiven Dokument auf vorherige Positionen oder auf Positionen zu verschieben, die Sie gerade erst besucht haben. Diese Schaltflächen speichern die letzten 20 Positionen der Einfügemarke.

![Navigationsschaltflächen "Vor" und "Zurück"](../ide/media/vs2017_nav_buttons.png)

Die Funktion „Strukturschnellansicht“ im Code-Editor zeigt *Strukturführungslinien*: vertikal gestrichelte Linien, die passende geschweifte Klammern in Ihrer Codebasis indizieren. Dadurch können Sie leichter erkennen, wo logische Blöcke anfangen und aufhören.

![Strukturschnellansicht](../ide/media/vside_structure_visualizer.png)

Um die Struktur von Hilfslinien zu deaktivieren, wechseln Sie zu **Extras**, **Optionen**, **Text-Editor**, **Allgemein** , und deaktivieren Sie das Feld **Strukturführungslinien anzeigen**.

Sie können ebenfalls die erweiterte Bildlaufleiste im Codefenster verwenden, um den Code aus der Vogelperspektive zu betrachten. Im Zuordnungsmodus können Sie eine Codevorschau sehen, wenn Sie den Cursor auf der Bildlaufleiste nach oben und unten bewegen. Weitere Informationen hierzu finden Sie unter [How to: Track Your Code by Customizing the Scrollbar](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md).  

Die folgenden Befehle stehen für codespezifische Navigationsmethoden:  

|||  
|-|-|  
|Alle Verweise suchen|(Kontextmenü oder SHIFT + F12): sucht alle Verweise auf das ausgewählte Element in der Projektmappe.|  
|Gehe zu|Enthält die folgenden Befehle: **Gehe zu Zeile** (STRG + G): zur angegebenen Zeilennummer im aktiven Dokument wechseln. **Gehe zu allen** (STRG + T): zur angegebenen Zeile oder Datei bzw. zum angegebenen Typ, Member oder Symbol wechseln. **Zu Datei wechseln** (STRG + 1, STRG + F): Zur angegebenen Datei in der Projektmappe wechseln. **Gehe zu Typ...** (STRG + 1, STRG + T): zum angegebenen Typ in der Projektmappe wechseln. **Zu Member navigieren...** (STRG + 1, STRG + M): zum angegebenen Member in der Projektmappe wechseln. **Gehe zu Symbol...** (STRG + 1, STRG + S): zum angegebenen Symbol in der Projektmappe wechseln. Weitere Informationen zu diesen Befehlen im Abschnitt „Code mithilfe von „Gehe zu“-Befehlen finden“ werden später in diesem Thema aufgeführt.|  
|Gehe zu Definition|(Kontextmenü oder F12): sucht die Definition des ausgewählten Elements.|  
|Gehe zu Implementierung|(Kontextmenü oder STRG + F12): sucht die Stelle im Code, wo das ausgewählte Element implementiert wird.|
|Peek-Definition|(Kontextmenü oder ALT+F12): sucht die Definition des ausgewählten Elements und zeigt sie in einem Fenster im Code-Editor an. Weitere Informationen finden Sie unter [Gewusst wie: Anzeigen und Bearbeiten von Code mithilfe von „Definition einsehen“ (Alt+F12)](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).|  
|Nächste Methode, Vorherige Methode|(**Bearbeiten > Nächste Methode, Vorherige Methode**): Verwenden Sie diese Befehle in Visual Basic-Codedateien, um die Einfügemarke zu den verschiedenen Methoden zu verschieben.|  
|Markieren von Verweisen|Wenn Sie auf ein Symbol im Quellcode klicken, werden alle Instanzen dieses Symbols im Dokument hervorgehoben. Die markierten Symbole können Deklarationen und Verweise sowie weitere Symbole umfassen, die von **Alle Verweise suchen** zurückgegeben werden können. Dazu zählen die Namen von Klassen, Objekten, Variablen, Methoden und Eigenschaften. In Visual Basic-Code werden auch Schlüsselwörter für viele Steuerungsstrukturen hervorgehoben. Um zum nächsten oder vorherigen hervorgehobenen Symbol zu springen, drücken Sie STRG+UMSCHALTTASTE+NACH-UNTEN-TASTE bzw. STRG+UMSCHALTTASTE+NACH-OBEN-TASTE. Sie können die Hervorhebungsfarbe in **Extras > Optionen > Umgebung > Schriftarten und Farben > Hervorgehobener Verweis**ändern.|  
|Suchen von codebezogenen Informationen|Sie können Informationen über bestimmten Code, wie Änderungen und wer diese Änderungen vorgenommen hat, Verweise, Fehler, Arbeitsaufgaben und Codeüberprüfungen sowie Komponententeststatus anzeigen, wenn Sie CodeLens im Code-Editor verwenden. CodeLens funktioniert wie ein Heads-up-Display, wenn Sie Visual Studio Enterprise mit Team Foundation Server verwenden. Weitere Informationen finden Sie unter [Ermitteln von Änderungen am Code und anderer Verläufe](../ide/find-code-changes-and-other-history-with-codelens.md).|
|Aufrufhierarchie anzeigen|(Kontextmenü oder STRG + K, STRG + T).|  

 Sie können auch die **Navigationsleiste** (Dropdownfeldern am Anfang des Codefensters) verwenden, um Code in einer Codebasis zu suchen. Sie können einen Typ oder Member auswählen und direkt zu diesem wechseln. Die Navigationsleiste wird angezeigt, wenn Sie Code in der Visual Basic-, C#- oder C++-Code-Basis bearbeiten.

 ![Codenavigationsleiste](../ide/media/vside_navigation_bar.png)

 Ändern Sie zum Ausblenden der Navigationsleiste die Option **Navigationsleiste** im Text-Editor in der Einstellung „Alle Sprachen“ (**Extras**, **Optionen**, **Text-Editor**, **Alle Sprachen**, oder ändern Sie die Einstellungen für einzelne Sprachen). Sie können in den Dropdownfeldern wie folgt navigieren:  

-   Um den Fokus im Codefenster der Navigationsleiste zu verschieben, drücken Sie die Tastenkombination STRG+F2.  

-   Um den Fokus von der Navigationsleiste wieder in das Codefenster zu verschieben, drücken Sie ESC.  

-   Um den Fokus auf der Navigationsleiste von Element zu Element zu verschieben, drücken Sie die TAB-TASTE.  

-   Um das Element mit dem Fokus auf der Navigationsleiste auszuwählen und zur IDE zurückzukehren, drücken Sie die EINGABETASTE.  

-   Um zu einer Klasse bzw. einem Typ zu navigieren, wählen Sie den entsprechenden Namen in der linken Dropdownliste aus.  

-   Um direkt zu einer Prozedur in einer Klasse zu navigieren, wählen Sie die Prozedur in der rechten Dropdownliste aus.  

 In einer partiellen Klasse sind Member, die außerhalb der aktuellen Codedatei definiert wurden, ggf. deaktiviert (werden in grau angezeigt).  

## <a name="find-code-using-go-to-commands"></a>Suchen von Code mithilfe von Gehe zu-Befehlen
Die Visual Studio-Befehle **Gehe zu** führen eine zielgerichtete Suche in Ihrem Code aus, um Ihnen das schnelle Auffinden der angegebenen Elemente in Codedateien, Dateipfaden und Codesymbolen zu erleichtern. Anders als andere Textsuchverfahren, wie etwa „Suchen“ oder „In Dateien suchen“, beschränkt „Gehe zu“ seine Suche auf Bereiche, in denen echter Code vorhanden ist, wie etwa Dateien, Formulare und Codemodule. Angenommen, Sie möchten in einer ASP.NET-Webanwendung mithilfe von Suchen oder In Dateien suchen in der gesamten Projektmappe eine Zeichenfolge suchen, erhalten Sie vermutlich Treffer, einschließlich Instanzen der Zeichenfolge in Codeanmerkungen. Mit einem „Gehe zu“-Befehl kann Ihre Suche möglicherweise die Funktion ermitteln, die Sie suchen, und Instanzen der Zeichenfolge in Codehinweisen ignorieren.

### <a name="find-code-using-go-to"></a>Suchen von Code mithilfe von Gehe zu

1. Öffnen Sie eine Projektmappe oder einen Ordner in Visual Studio.
1. Wählen Sie im Hauptmenü **Bearbeiten**, **Gehe zu** aus. Ein kleines Textfeld wird in der oberen Ecke des Code-Editors angezeigt.
1. Geben Sie im Textfeld den Namen des Codeelements ein, das Sie suchen.

    ![Fenster „Navigieren zu“](../ide/media/vside_navigatetowindow.png "Fenster „Navigieren zu“")

    Während der Eingabe werden die Ergebnisse in einer Dropdownliste unterhalb des Textfelds angezeigt.
1. Um zu einem Element zu wechseln, wählen Sie es in der Liste aus.


### <a name="filter-your-search"></a>Filtern der Suche

Standardmäßig wird das angegebene Element in allen Projektmappenelementen gesucht. Sie können jedoch die Codesuche auf bestimmte Elementtypen einschränken, indem Sie den Suchbegriffen bestimmte Zeichen voranstellen. Die einfachste Möglichkeit, das Dialogfeld „Gehe zu“ zu öffnen, ist, STRG + T zu drücken und anschließend das vorangestellte Zeichen mit einem aus der folgenden Liste zu ersetzen. (Alternativ können Sie die folgenden Tastenkombinationen drücken, damit das Zeichen automatisch für Sie hinzugefügt wird.)

|Symbol|Beschreibung|  
|-|-|
|Keine|Kein vorangestelltes Zeichen. Der angegebene Begriff wird in allen Zeilen, Dateien, Typen, Membern und Symbolen gesucht. Tastenkombination: STRG + T|
|:|Wechselt zur angegebenen Zeilennummer. Tastenkombination: STRG + G|
|f|Wechselt zum angegebenen Dateinamen. Tastenkombination: STRG + 1, STRG + F|
|t|Wechselt zum angegebenen Typ. Tastenkombination: STRG + 1, STRG + T|
|m|Wechselt zum angegebenen Member. Tastenkombination: STRG + 1, STRG + M|
|#|Wechseln zum angegebenen Symbol. Tastenkombination: STRG + 1, STRG + S|

Um Ihre Suche beispielsweise nur auf Codezeichen zu beschränken, öffnen Sie das „Gehe zu“-Dialogfeld mit der Tastenkombination STRG + T (oder STRG + ,), und stellen Sie Ihrer „Gehe zu“-Abfrage das Zeichen „#“ voran. Wählen Sie alternativ **Bearbeiten**, **Gehe zu**, **Gehe zu Symbol** im Menü aus. Die Suche nach `# application` zeigt z.B. nur Codesymbole an, die das Wort „application“ (Anwendung) enthalten.

Sie können auch schnell Suchfilter ändern, indem Sie Schaltflächen auf der Symbolleiste des Dialogfelds „Gehe zu“ auswählen. Schaltflächen, die die Filter ändern, befinden sich auf der linken Seite, Schaltflächen, die den Bereich der Suche ändern, befinden sich auf der rechten Seite.

![](../ide/media/vside_navigation_toolbar.png)

Wenn Sie die [Pascal-Schreibweise](https://en.wikipedia.org/wiki/Camel_case) (Kamel-Schreibweise) in Ihrem Code verwenden, können Sie Codeelemente schneller finden, indem Sie nur die Großbuchstaben des Codeelementnamens eingeben. Wenn Ihr Code beispielsweise über einen Typ namens `CredentialViewModel` verfügt, können Sie die Suche eingrenzen, indem Sie den Typfilter („t“) auswählen und anschließend nur die Großbuchstaben des Namens (`CVM`) in das „Gehe zu“-Dialogfeld eingeben.

![Fenster „Navigieren zu“ - Suchvorgänge mit Großbuchstaben](../ide/media/vside_capitalsearch.png)

Diese Funktion ist nützlich, wenn der Code lange Namen aufweist.

## <a name="finding-references-in-your-codebase"></a>Suchen von Verweisen in der Codebasis
Um den Ort zu finden, zu dem bestimmte Codeelemente in Ihrer gesamten Codebasis verwiesen werden, können Sie den Befehl **Alle Verweise suchen** verwenden. Wählen Sie zum Verwenden von **Alle Verweise suchen** diesen Befehl im Kontextmenü (Rechtsklick) des Elements, für das Sie die Verweise suchen möchten, oder klicken Sie SHIFT + F12.

Die Ergebnisse werden in einem Toolfenster mit der Bezeichnung **'*{lement}*'-Verweise** angezeigt, wobei *{element}* der Name des gesuchten Elements ist. Mit einer Symbolleiste in diesem Fenster können Sie folgendes tun:
- Den Bereich der Suche in einem Dropdown-Listenfeld ändern. Sie können auswählen, nur in geänderten Dokumenten bis hin zur gesamten Projektmappe zu suchen.
- Das ausgewählte Verweiselement durch Auswählen der Schaltfläche **Kopieren** kopieren.
- Schaltflächen auswählen, um zum nächsten oder vorherigen Platz in der Liste zu wechseln. Drücken Sie alternativ die Tasten F8 und SHIFT + F8.
- Alle Filter auf den zurückgegebenen Ergebnissen durch Auswählen der Schaltflächen **Alle Filter löschen** entfernen.
- Ändern, wie zurückgegebene Elemente gruppiert werden, indem Sie eine Einstellung im Dropdown-Listenfeld **Gruppieren nach:** auswählen.
- Das Fenster der aktuellen Suchergebnisse beibehalten, indem Sie auf die Schaltfläche **Ergebnisse beibehalten** drücken.
- Zeichenfolgen innerhalb der Suchergebnisse suchen, indem Sie Text in das Textfeld **Suche: Alle Verweise suchen** eingeben.

Sie können auch mit dem Mauszeiger auf jedes Suchergebnis zeigen, um eine Vorschau des zurückgegebenen Elements anzuzeigen.

![Toolfenster „Alle Verweise suchen“](../ide/media/vside_findallreferences.png)

Um die Ergebnisse der Suche beizubehalten, wählen Sie die **Ergebnisse beibehalten**-Schaltfläche aus. Wenn Sie diese Schaltfläche auswählen, verbleiben die aktuellen Suchergebnisse in diesem Fenster und neue Suchergebnisse erscheinen in einem neuen Toolfenster.

### <a name="navigate-to-references"></a>„Navigieren zu“-Verweise
Sie können im Dialogfeld „Alle Verweise suchen“ die folgenden Methode verwenden, um zu Verweisen zu wechseln.

- Drücken Sie F8, um zum nächsten Verweis zu springen, oder drücken Sie SHIFT + F8, um zum vorherigen Verweis zu wechseln.
- Drücken Sie die EINGABETASTE auf einem Verweis, oder führen Sie einen Doppelklick aus, um zu ihn im Code zu wechseln.
- Wählen Sie im Kontextmenü eines Verweises die Befehle **Gehe zu vorheriger Position** / **Gehe zu nächster Position**.
- Wählen Sie die NACH-OBEN- und NACH-UNTEN-TASTEN (falls sie im Dialogfeld „Optionen“ aktiviert sind). Wählen Sie zum Aktivieren dieser Funktionalität können Sie im Menü **Extras**, **Optionen**, **Umgebung**, **Registerkarten und Fenster**, **Vorschauregisterkarte**, und wählen Sie dann die **können neue Dateien geöffnet werden, in der Vorschau** und **eine Vorschau der ausgewählte Dateien in die Suchergebnisse** Felder.

### <a name="change-reference-groupings"></a>Änderung von Verweisgruppierungen
Standardmäßig werden Verweise vom Projekt dann per Definition gruppiert. Sie können jedoch diese Gruppierungsreihenfolge ändern, indem Sie die Einstellung im **Gruppieren nach:**-Dropdown-Listenfeld auf der Symbolleiste ändern. Sie können sie beispielsweise von der Standardeinstellung **Definition dann Projekt** zu **Projekt dann Definition** sowie zu anderen Einstellungen ändern.

**Definition** und **Projekt** sind die beiden verwendeten Standardgruppierungen, aber Sie können andere hinzufügen, indem Sie den Befehl **Gruppierung** im Kontextmenü des ausgewählten Elements auswählen. Das Hinzufügen weiterer Gruppen kann hilfreich sein, wenn Ihre Projektmappe viele Dateien und Pfade enthält.

## <a name="customize-the-editor"></a>Anpassen des Editors  
Sie können im Menü **Extras** unter **Assistent zum Importieren und Exportieren von Einstellungen** Ihre Visual Studio-Einstellungen für einen anderen Entwickler freigeben, die Einstellungen an einen Standard anpassen oder zu den Visual Studio-Standardeinstellungen zurückkehren. Im **Assistent zum Importieren und Exportieren von Einstellungen** können Sie ausgewählte allgemeine Einstellungen oder Sprachen sowie projektspezifische Einstellungen ändern.

Um neue Hotkeys zu definieren oder bestehende Hotkeys neu zu definieren, navigieren Sie zu **Extras**, **Optionen**, **Umgebung**, **Tastatur**. Weitere Informationen zu Hotkeys finden Sie unter [Standardtastenkombinationen](../ide/default-keyboard-shortcuts-in-visual-studio.md).  

Weitere Informationen zum Anpassen des Editors finden Sie unter [Anpassen des Editors](../ide/customizing-the-editor.md). Informationen über sprachspezifische Editoroptionen finden Sie unter [Verwenden der Visual Studio-Entwicklungsumgebung für C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md) und [Options, Text Editor, JavaScript, Formatting](../ide/reference/options-text-editor-javascript-formatting.md).

## <a name="see-also"></a>Siehe auch  
 [Visual Studio-IDE](../ide/visual-studio-ide.md)

