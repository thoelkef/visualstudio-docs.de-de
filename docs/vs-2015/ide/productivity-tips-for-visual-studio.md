---
title: Produktivitätstipps | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: ccc5e543-7dcf-465c-97dd-e133e869800c
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f43187faf1dd53cc9daf45da1191e1e944a43c8a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696292"
---
# <a name="productivity-tips-for-visual-studio"></a>Produktivitätstipps für Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie diese Tipps befolgen, können Sie den Code in Visual Studio schneller und effizienter schreiben und debuggen sowie in diesem navigieren. Weitere Informationen zu häufig verwendeten Tastenkombinationen finden Sie unter [Tipps und Tricks](../ide/tips-and-tricks-for-visual-studio.md). Eine detailliertere Liste finden Sie unter [Finden und Anpassen von Tastenkombinationen](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) und [Standardtastenkombinationen](../ide/default-keyboard-shortcuts-in-visual-studio.md).

 Dieses Thema enthält die folgenden Abschnitte:

 [Zugriff auf die Visual Studio-Tools](../ide/productivity-tips-for-visual-studio.md#BKMK_Access)

 [Schreiben von Code](../ide/productivity-tips-for-visual-studio.md#BKMK_Writing)

 [Navigieren innerhalb des Codes](../ide/productivity-tips-for-visual-studio.md#BKMK_Navigating)

 [Schnelleres Suchen von Elementen](../ide/productivity-tips-for-visual-studio.md#BKMK_Finding)

 [Debuggen von Code](../ide/productivity-tips-for-visual-studio.md#BKMK_Debugging)

 [Verwalten von Dateien, Symbolleisten und Fenstern](../ide/productivity-tips-for-visual-studio.md#BKMK_Managing)

## <a name="BKMK_Access"></a>Zugriff auf die Visual Studio-Tools
 Sie können einfacher auf die Developer-Eingabeaufforderung oder auf ein anderes Tool zugreifen, wenn Sie diese auf der Startseite oder in der Taskleiste fixieren.

1. Geben Sie auf der Startseite `Visual Studio Tools` ein, und drücken sie dann die EINGABETASTE.

2. Öffnen Sie im **Datei-Explorer** das Kontextmenü für das gewünschte Element.

    - Buildbenachrichtigungen

    - Manager für debugfähige Pakete

    - Developer-Eingabeaufforderung für VS2013

    - Microsoft Feedback Client 2013

    - VS2013 ARM Cross Tools-Eingabeaufforderung

    - VS2013 x64 Cross Tools-Eingabeaufforderung

    - VS2013 x64 Native Tools-Eingabeaufforderung

    - VS2013 x86 Native Tools-Eingabeaufforderung

3. Wählen Sie **An Taskleiste anheften** oder **An „Start“ anheften** aus.

## <a name="BKMK_Writing"></a>Schreiben von Code
 Schreiben Sie Code schneller, indem Sie die folgenden Funktionen verwenden.

- **Verwenden von Beispielanwendungen**. Sie können Anwendungsentwicklung beschleunigen, indem Sie Beispielanwendungen von der MSDN Code Gallery herunterladen und installieren. Sie können eine bestimmte Technologie oder ein Programmierkonzept auch kennenlernen, indem Sie ein Beispielpaket für diesen Bereich herunterladen und untersuchen.

- **Verwenden von IntelliSense**. Wie Sie Code im Editor eingeben, werden IntelliSense-Informationen, wie Listenmember, Parameterinformationen, QuickInfos, Signaturhilfe und Wortvervollständigung angezeigt. Diese Funktionen unterstützen Fuzzyübereinstimmung des Texts. So umfasst die Ergebnisliste für die Listenmember nicht nur Einträge, die mit dem Zeichen beginnen, das Sie eingegeben haben, sondern auch Einträge, die die Zeichenkombination an einer beliebigen Stelle im Namen enthalten. Weitere Informationen finden Sie unter [Verwenden von IntelliSense](../ide/using-intellisense.md).

- **Ändern der Optionen für Autoeinfügung von IntelliSense bei der Codeeingabe**. Wenn Sie den Vorschlagsmodus in IntelliSense umschalten, können Sie festlegen, dass IntelliSense-Optionen nur eingefügt werden, wenn Sie sie explizit auswählen.

     Um den Vorschlagsmodus zu aktivieren, wählen Sie die STRG+ALT+LEERTASTE-TASTEN aus, oder wählen Sie in der Menüleiste **Bearbeiten**, **IntelliSense**, **Vervollständigungsmodus umschalten** aus.

- **Verwenden von Codeausschnitten**. Sie können mithilfe der integrierten Ausschnitte eigene Ausschnitte erstellen.

     Zum Einfügen eines Ausschnittes wählen Sie in der Menüleiste **Bearbeiten**, **IntelliSense**, **Ausschnitt einfügen** aus, oder öffnen Sie das Kontextmenü in einer Datei, und wählen Sie **Ausschnitt einfügen** aus. Weitere Informationen finden Sie unter [Codeausschnitte](../ide/code-snippets.md).

- **Inline-Behebung von Codefehlern**. Smarttags werden als blaue oder rote Felder unter einer Codezeile angezeigt. Sie können Smarttag-Optionen anzeigen, indem Sie auf eines der Felder zeigen oder indem Sie den Cursor in der Codezeile platzieren und STRG+ auswählen. (Punkt)-Schlüssel.

     In blauen Feldern werden Möglichkeiten vorgeschlagen, Fehler im Code zu korrigieren.

     Abbildung 1: Fehler-Smarttags

     ![Fehler-Smarttag-Vorschläge](../ide/media/productivity-bluesmarttags.png "Productivity_BlueSmartTags")

     In roten Feldern werden Möglichkeiten vorgeschlagen, den Code umzugestalten.

     Abbildung 2: Umgestaltungs-Smarttags

     ![Refactoring-Smarttag-Vorschläge](../ide/media/productivity-redsmarttags.png "Productivity_RedSmartTags")

- **Anzeigen und Bearbeiten der Definition eines Codeelements**. Sie können das Modul schnell anzeigen und bearbeiten, in dem ein Codeelement, wie ein Member, eine Variable oder eine lokale Variable, definiert ist.

     Um eine Definition in einem Popupfenster zu öffnen, markieren Sie das Element und wählen Sie dann die Tasten ALT+F12 aus, oder öffnen Sie das Kontextmenü für das Element, und wählen Sie dann **Definition einsehen** aus. Um eine Definition in einem separaten Codefenster zu öffnen, öffnen Sie das Kontextmenü für das Codeelement, und wählen Sie dann **Gehe zu Definition** aus.

## <a name="BKMK_Navigating"></a>Navigieren innerhalb des Codes
 Sie können verschiedene Methoden verwenden, um bestimmte Positionen im Code schneller zu finden und dorthin zu wechseln.

- **Speichern von Codezeilen als Lesezeichen**. Sie können Lesezeichen verwenden, um schnell zu bestimmten Codezeilen in einer Datei zu navigieren.

     Wählen Sie zum Setzen eines Lesezeichens in der Menüleiste **Bearbeiten**, **Lesezeichen**, **Lesezeichen umschalten** aus. Sie können alle Lesezeichen für eine Projektmappe im Fenster **Lesezeichen** anzeigen. Weitere Informationen finden Sie unter [Festlegen von Lesezeichen im Code](../ide/setting-bookmarks-in-code.md).

- **Suchen nach Symboldefinitionen in einer Datei**. Sie können in einer Projektmappe nach Symboldefinitionen und Dateinamen suchen. Die Suchergebnisse enthalten jedoch keine Namespaces oder lokalen Variablen.

     Um auf diese Funktion zuzugreifen, wählen Sie in der Menüleiste **Bearbeiten**, **Navigieren zu** aus.

- **Durchsuchen der Gesamtstruktur des Codes**. Im **Projektmappen-Explorer** können Sie Klassen und ihre Typen und Member in den Projekten suchen. Sie können auch nach Symbolen suchen, die Aufrufhierarchie einer Methode anzeigen, Symbolverweise suchen und andere Aufgaben ausführen. Wenn Sie ein Codeelement im **Projektmappen-Explorer** auswählen, wird die dazugehörige Datei auf einer Registerkarte **Vorschau** angezeigt, und der Cursor wird auf das Element in der Datei verschoben. Weitere Informationen finden Sie unter [Anzeigen der Codestruktur](../ide/viewing-the-structure-of-code.md).

## <a name="BKMK_Finding"></a> Schnelleres Suchen von Elementen
 Sie können in der IDE nach Befehlen, Dateien und Optionen suchen und gleichzeitig die Inhalte der Toolfenster filtern, um relevante Informationen nur für die aktuelle Aufgabe anzuzeigen.

- **Filtern der Inhalte von Toolfenstern**. Sie können in den Inhalten vieler Toolfenster, z. B. der Fenster **Toolbox**, **Eigenschaften** und im **Projektmappen-Explorer** suchen. Es werden aber nur Elemente angezeigt, deren Namen die Zeichen enthalten, die Sie angeben.

- **Zeigen Sie nur die Fehler an, die berücksichtigt werden sollen**. Wenn Sie die Schaltfläche **Filter** auf der Symbolleiste **Fehlerliste** auswählen, können Sie die Anzahl der Fehler reduzieren, die im Fenster **Fehlerliste** angezeigt werden. Sie können nur die Fehler in den Dateien anzeigen, die im Editor geöffnet sind, nur die Fehler in der aktuellen Datei oder nur die Fehler im aktuellen Projekt. Sie können im Fenster Fehlerliste auch nach bestimmten Fehlern suchen.

- **Suchen von Dialogfeldern, Menübefehlen und Optionen**. Geben Sie im Feld [Schnellstart, Umgebung, Dialogfeld „Optionen“](../ide/reference/quick-launch-environment-options-dialog-box.md) Schlüsselwörter oder Ausdrücke für die Elemente ein, die Sie suchen. Beispielsweise werden die folgenden Optionen angezeigt, wenn Sie `new project` eingeben:

     Abbildung 3: Ergebnisliste für Schnellstart für `new project`

     ![Schnellstartergebnisse für „Neues Projekt“](../ide/media/productivity-quicklaunch.png "Productivity_QuickLaunch")

     **Schnellstart** zeigt unter anderem Links zum Dialogfeld **Neues Projekt**, zum Dialogfeld **Neues Element hinzufügen** und zur Projekt- und Projektmappenseite im Dialogfeld **Optionen** an. Ergebnisse des Schnellstarts können auch Projektdateien und Toolfenster enthalten.

## <a name="BKMK_Debugging"></a>Debuggen von Code
 Debuggen kann viel Zeit in Anspruch nehmen, aber die folgenden Tipps können Ihnen helfen, den Prozess zu beschleunigen.

- **Testen Sie die gleiche Seite, Anwendung oder Website in unterschiedlichen Browsern**. Wenn Sie den Code debuggen, können Sie zwischen den installierten Webbrowsern, einschließlich [Seitenprüfung (Visual Studio)](https://msdn.microsoft.com/library/65880969-1ad2-47be-85b9-bb12c81bf209), problemlos wechseln, ohne dass Sie das Dialogfeld **Browserauswahl** öffnen müssen. Sie können die Liste **Debugziel** verwenden, die auf der Symbolleiste **Standard** neben der Schaltfläche **Debuggen starten** zu finden ist, um beim Debuggen oder Anzeigen von Seiten schnell zu überprüfen, welchen Browser Sie verwenden.

     ![Debuggingoptionen für Webbrowser auswählen](../ide/media/webbrowserdropdowntoolbar.png "WebBrowserDropDownToolbar")

- **Legen Sie temporäre Haltepunkte fest**. Sie können einen temporären Haltepunkt in der aktuellen Zeile des Codes erstellen und gleichzeitig den Debugger starten. Wenn Sie diese Codezeile erreicht haben, gibt der Debugger Unterbrechungsmodus ein. Weitere Informationen finden Sie unter [Navigieren im Code mit dem Debugger](../debugger/navigating-through-code-with-the-debugger.md).

     Um diese Funktion zu verwenden, wählen Sie die STRG+F10-TASTEN, oder öffnen Sie das Kontextmenü für die Codezeile, bei der Sie unterbrechen möchten, und wählen Sie dann **Ausführen bis Cursor** aus.

- **Verschieben Sie den Ausführungspunkt während des Debuggens**. Sie können den aktuellen Ausführungspunkt zu einem anderen Codeabschnitt verschieben und Debuggen von diesem Punkt neu starten. Diese Methode ist hilfreich, wenn Sie einen Codeabschnitt debuggen möchten, ohne alle Schritte neu erstellen zu müssen, die erforderlich sind, um diesen Abschnitt zu erreichen. Weitere Informationen finden Sie unter [Navigieren im Code mit dem Debugger](../debugger/navigating-through-code-with-the-debugger.md).

     Um den Ausführungspunkt zu verschieben, ziehen Sie die gelbe Pfeilspitze zu einer Position, an der Sie die folgende Anweisung in derselben Quelldatei festlegen möchten, und wählen Sie dann die F5-TASTE, um das Debuggen fortzusetzen.

- **Erfassen Sie Wertinformationen für Variablen**. Sie können einer Variablen im Code einen DataTip hinzufügen und diesen fixieren, damit Sie auf den letzten bekannten Wert für die Variable zugreifen können, nachdem der Debugvorgang abgeschlossen hat. Weitere Informationen finden Sie unter [Anzeigen von Datenwerten als Datentipps](../debugger/view-data-values-in-data-tips-in-the-code-editor.md).

     Zum Hinzufügen eines DataTips muss sich der Debugger im Unterbrechungsmodus befinden. Platzieren Sie den Cursor in der Variablen, und wählen Sie dann die Anheftschaltfläche auf dem angezeigten DataTip aus. Wenn das Debuggen beendet wird, wird in der Quelldatei ein blaues Anheftsymbol neben der Codezeile angezeigt, die die Variable enthält. Wenn Sie auf den blauen Pin zeigen, wird der Wert der Variablen aus der letzten Debugsitzung angezeigt.

- **Löschen Sie das Direktfenster**. Sie können den Inhalt des [Direktfensters](../ide/reference/immediate-window.md) zur Entwurfszeit löschen, indem Sie `>cls` oder `>Edit.ClearAll` eingeben.

     Weitere Informationen zu weiteren Befehlen finden Sie unter [Visual Studio-Befehlsaliase](../ide/reference/visual-studio-command-aliases.md).

## <a name="BKMK_Managing"></a>Verwalten von Dateien, Symbolleisten und Fenstern
 Bei der Entwicklung einer Anwendung möchten Sie jederzeit in mehreren Codedateien arbeiten und sich in mehreren Toolfenstern bewegen können. Mit folgenden Tipps behalten Sie die Übersicht.

- **Halten Sie Dateien, die Sie häufig verwenden, im Editor sichtbar**. Sie können die Dateien, die Sie häufig verwenden, an der linken Seite der Registerkartenreihe anheften, damit Sie unabhängig davon, wie viele Dateien im Editor geöffnet sind, sichtbar bleiben.

     Um eine Datei anzuheften, wählen Sie die Registerkarte der Datei, und wählen Sie dann die Schaltfläche **Anheftstatus umschalten** aus.

- **Verschieben Sie Dokumente und Fenster auf andere Bildschirme**. Wenn Sie bei der Entwicklung einer Anwendung mehr als einen Bildschirm verwenden, können Sie leichter an Teilen der Anwendung arbeiten, wenn Sie Dateien, die im Editor geöffnet sind, auf einen anderen Bildschirm verschieben. Sie können Toolfenster, wie z. B. Debuggerfenster, auf einen anderen Bildschirm verschieben und Dokument- und -Toolfenster miteinander verbinden, um „Flösse“ zu erstellen. Weitere Informationen finden Sie unter [Gewusst wie: Anordnen und Andocken von Fenstern](../misc/how-to-arrange-and-dock-windows.md).

     Sie können Dateien auch einfacher verwalten, indem Sie eine weitere Instanz des **Projektmappen-Explorers** erstellen und sie auf einen anderen Bildschirm verschieben. Um eine andere Instanz des **Projektmappen-Explorers** zu erstellen, öffnen Sie ein Kontextmenü im **Projektmappen-Explorer**, und wählen Sie dann **Neue Projektmappen-Explorer-Ansicht** aus.

- **Passen Sie die Schriftarten an, die in Visual Studio angezeigt werden**. Sie können die Schriftart, Größe und Farbe ändern, die für Text in der IDE verwendet wird. Beispielsweise können Sie die Farbe von bestimmten Codeelementen im Editor und die Schriftart in Toolfenstern oder in der IDE anpassen. Weitere Informationen finden Sie unter [Gewusst wie: Ändern von Schriftarten und Farben](../ide/how-to-change-fonts-and-colors-in-visual-studio.md) und [Gewusst wie: Ändern der im Editor verwendeten Schriftarten und Farben](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Siehe auch
 [Standardtastenkombinationen für häufig verwendete Befehle in Visual Studio](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md) [Vorgehensweise: Anpassen von Menüs und Symbolleisten in Visual Studio](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md) [Exemplarische Vorgehensweise: Erstellen einer einfachen Anwendung mit Visual C# oder Visual Basic](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md) [Tipps und Tricks zur Barrierefreiheit für Visual Studio](../ide/reference/accessibility-tips-and-tricks.md)
