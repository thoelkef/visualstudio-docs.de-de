---
title: Der Code-Editor in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 09/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JScript
- VB
- CSharp
helpviewer_keywords:
- code, editing [Visual Studio]
- code editor [Visual Studio]
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: abde071bd67ab3f6a65891d347b9214f6dd5257b
ms.sourcegitcommit: 94162a6b0440312cd71bc0c512daef9f122550f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/18/2018
---
# <a name="write-code-in-the-code-editor"></a>Schreiben von Code in den Code-Editor

Der Visual Studio-Editor bietet viele Funktionen, die Ihnen das Schreiben und die Verwaltung von Code und Text erleichtern. Sie können mithilfe der Gliederung verschiedene Codeblöcke reduzieren und erweitern. Wenn Sie IntelliSense, den **Objektkatalog** und die Aufrufhierarchie verwenden, können Sie mehr über Ihren Code erfahren. Sie können Code finden, indem Sie Funktionen wie **Gehe zu**, **Gehe zu Definition**und **Alle Verweise suchen** verwenden. Mit Codeausschnitten können Sie Codeblöcke einfügen und Code mithilfe von Funktionen wie **Generate From Usage**generieren. Wenn Sie noch nie mit dem Visual Studio-Editor gearbeitet haben, finden Sie eine schnelle Übersicht unter [Codebearbeitung](https://www.visualstudio.com/features/ide-vs) .

 Code kann auf unterschiedliche Weise angezeigt werden. Standardmäßig wird Ihr Code im **Projektmappen-Explorer** nach Dateien geordnet angezeigt. Sie können auf die Registerkarte **Klassenansicht** im unteren Bereich des Fensters klicken, damit Ihr Code nach Klassen geordnet angezeigt wird.

 Sie können Text in einzelnen oder mehreren Dateien suchen und ersetzen. Weitere Informationen finden Sie unter [Finding and Replacing Text](../ide/finding-and-replacing-text.md). Sie können reguläre Ausdrücke zum Suchen und Ersetzen von Text verwenden. Weitere Informationen finden Sie unter [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

 Für die verschiedenen Visual Studio-Sprachen werden unterschiedliche Funktionssätze angeboten, und in einigen Fällen verhalten sich die Funktionen in verschiedenen Sprachen unterschiedlich. Viele dieser Unterschiede werden in den Beschreibungen der Funktionen erläutert. Weitere Informationen können Sie den Abschnitten über einzelne Visual Studio-Sprachen entnehmen.

> [!IMPORTANT]
> Die Visual Studio-Edition und die verwendeten Einstellungen können sich auf die Funktionen der IDE auswirken. Sie können sich daher von den in diesem Thema beschriebenen Funktionen unterscheiden.

## <a name="editor-features"></a>Editor-Funktionen

|||
|-|-|
|Farben für Syntax|Einige Syntaxelemente in den Code- und Markupdateien sind unterschiedlich gefärbt, damit sie unterschieden werden können. Beispielsweise sind Schlüsselwörter (wie `using` in C# und `Imports` in Visual Basic) in einer Farbe gehalten, jedoch Typen (wie `Console` und `Uri`) haben eine andere Farbe. Andere Syntaxelemente werden auch farbig hervorgehoben, wie zum Beispiel Zeichenfolgenliterale und Kommentare. In C++ werden Farben verwendet, um Typen, Enumerationen und Makros von anderen Token zu unterscheiden.<br /><br /> Sie können die Standardfarbe für jeden Typ sehen, und Sie können die Farbe für spezifische Syntaxelemente im [Fonts and Colors, Environment, Options Dialog Box](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)ändern, auf das Sie über das Menü **Extras** zugreifen.|
|Markierungen für Fehler und Warnungen|Wenn Sie Code hinzufügen und Ihre Projektmappe erstellen, werden möglicherweise (a) verschiedenfarbige Unterstreichungen (sogenannte Wellenlinien) oder (b) Glühbirnen in Ihrem Code angezeigt. Rote Wellenlinien kennzeichnen Syntaxfehler, blaue kennzeichnen Compilerfehler, grüne kennzeichnen Warnungen und lila Wellenlinien kennzeichnen alle anderen Arten von Fehlern. [Glühbirnen](../ide/perform-quick-actions-with-light-bulbs.md) schlagen Fehlerbehebungen für Probleme vor und vereinfachen das Anwenden der jeweiligen Fehlerbehebung.<br /><br /> Sie können die Standardfarben für alle Wellenlinien, die Fehler und Warnungen anzeigen, im Dialogfeld **Extras > Optionen > Umgebung > Schriftarten und Farben** aufrufen. Suchen Sie nach **Syntaxfehler**, **Compilerfehler**, **Warnung**und **Anderer Fehler**.|
|Überprüfung des Klammergleichgewichts|Bei Platzierung der Einfügemarke auf eine öffnende geschweifte Klammer in einer Codedatei werden die öffnende und die schließende Klammer hervorgehoben. Durch diese Funktion erhalten Sie unmittelbar Feedback zu falsch platzierten oder fehlenden geschweiften Klammern. Sie können die Zuordnung von geschweiften Klammern mit der Einstellung **Trennzeichen automatisch hervorheben** (**Extras > Optionen > Text-Editor**) aktivieren bzw. deaktivieren. Sie können die in der Einstellung **Schriftarten und Farben** festgelegte Hervorhebungsfarbe ändern (**Extras > Optionen > Umgebung**). Suchen Sie nach **Zugehörige Klammer (Hervorhebung)** oder **Zugehörige Klammer (Rechteck)**.|
|Strukturschnellansicht|Gepunktete Linien verbinden passende Klammern in Codedateien, wodurch sich öffnende und schließende Klammerpaare leichter erkennen lassen. Das hilft Ihnen bei der schnelleren Suchen von Code in Ihrer Codebasis. Sie können diese Zeilen mithilfe von **Show structure guidelines** (Strukturrichtlinien anzeigen) im Abschnitt **Display** (Anzeige) auf der Seite **Tools/Options/Text Editor/General** (Extras/Optionen/Text-Editor/Allgemein) aktivieren und deaktivieren.|
|Zeilennummern|Zeilennummern können im linken Rand des Codefensters angezeigt werden. Standardmäßig werden sie nicht angezeigt. Sie können diese Option in den Einstellungen **Text-Editor &gt; Alle Sprachen** (**Extras &gt; Optionen &gt; Text-Editor &gt; Alle Sprachen**) deaktivieren. Sie können die Zeilennummern für einzelne Programmiersprachen anzeigen, indem Sie die Einstellungen für diese Sprachen ändern (**Extras/Optionen/Text-Editor/\<Sprache>**). Damit die Zeilennummern ausgedruckt werden, müssen Sie im Dialogfeld **Drucken** die Option **Zeilennummern einschließen** auswählen.|
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
|Auswahl kommentieren|Fügt Kommentarzeichen zur Auswahl oder aktuellen Zeile hinzu.|
|Kommentar aus Auswahl entfernen|Entfernt Kommentarzeichen aus der Auswahl oder der aktuellen Zeile.|
|Zeileneinzug vergrößern|Fügt eine Registerkarte (oder die entsprechenden Leerzeichen) zu den ausgewählten Zeilen oder zur aktuellen Zeile hinzu.|
|Zeileneinzug verkleinern|Entfernt eine Registerkarte (oder die entsprechenden Leerzeichen) aus den ausgewählten Zeilen oder der aktuellen Zeile.|
|Tag auswählen|Wählt das Tag in einem Dokument aus, das Tags enthält (zum Beispiel XML oder HTML).|
|Tag-Inhalt auswählen|Wählt den Tag-Inhalt in einem Dokument aus, das Tags enthält (zum Beispiel XML oder HTML).|

## <a name="navigate-and-find-code"></a>Navigieren und Suchen von Code

Es gibt verschiedene Möglichkeiten, um im Code-Editor zu navigieren: Sie können zwischen den Einfügepunkten vor- und zurückgehen, die Definition eines Typs oder Members abrufen und über die Navigationsleiste auf eine bestimmte Methode springen. Weitere Informationen finden Sie unter Verwenden von [Navigating code (Navigieren von Code)](navigating-code.md).

## <a name="finding-references-in-your-code-base"></a>Suchen von Verweisen in Ihrer Codebasis

Um den Ort zu finden, zu dem bestimmte Codeelemente in Ihrer gesamten Codebasis verwiesen werden, können Sie den Befehl **Alle Verweise suchen** verwenden. Wenn Sie außerdem auf einen Typ oder Member klicken, hebt die Funktion **Reference Highlighting** („Hervorheben von Verweisen“) automatisch alle Verweise auf diesen Typ oder Member hervor. Weitere Informationen finden Sie unter [Finding references in your code (Suchen von Verweisen in Ihrem Code)](finding-references.md).

## <a name="customize-the-editor"></a>Anpassen des Editors

Sie können im Menü **Extras** unter **Assistent zum Importieren und Exportieren von Einstellungen** Ihre Visual Studio-Einstellungen für einen anderen Entwickler freigeben, die Einstellungen an einen Standard anpassen oder zu den Visual Studio-Standardeinstellungen zurückkehren. Im **Assistent zum Importieren und Exportieren von Einstellungen** können Sie ausgewählte allgemeine Einstellungen oder Sprachen sowie projektspezifische Einstellungen ändern.

Um neue Hotkeys zu definieren oder bestehende Hotkeys neu zu definieren, navigieren Sie zu **Extras**, **Optionen**, **Umgebung**, **Tastatur**. Weitere Informationen zu Hotkeys finden Sie unter [Standardtastenkombinationen](../ide/default-keyboard-shortcuts-in-visual-studio.md).

Weitere Informationen zum Anpassen des Editors finden Sie unter [Anpassen des Editors](../ide/customizing-the-editor.md). Informationen zu JavaScript-spezifischen Editor-Optionen finden Sie unter [Optionen, Text-Editor, JavaScript, Formatierung](../ide/reference/options-text-editor-javascript-formatting.md).

## <a name="see-also"></a>Siehe auch

[Visual Studio-IDE](../ide/visual-studio-ide.md)
