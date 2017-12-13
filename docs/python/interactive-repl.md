---
title: Python Interactive REPL in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 07/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 642dc47e-c265-44ea-a77d-3db14170a36f
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 0e524208684afa38916af858e6ec3a8adb1f5932
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="working-with-the-python-interactive-window"></a>Arbeiten mit dem interaktiven Python-Fenster

Visual Studio bietet ein interaktives „Lesen-Auswerten-Ausgeben-Schleife“-Fenster (Read Eval Print Loop, REPL) für Ihre Python-Umgebungen, das eine Verbesserung ist gegenüber dem REPL, das Sie mit der Eingabe von `python.exe` in der Befehlszeile erhalten. Im interaktiven Fenster (geöffnet mit den Befehlen **Ansicht > Weitere Fenster > &lt;Umgebung&gt; interaktive** Menübefehle) können Sie beliebigen Python-Code eingeben und sofortige Ergebnisse anzeigen lassen. Diese Art der Codierung unterstützt Sie beim Lernen und Experimentieren mit APIs und Bibliotheken und beim interaktiven Entwickeln von funktionierendem Code, den Sie in Ihre Projekte einfügen können.

![Interaktives Python-Fenster](media/interactive-window.png)

Visual Studio stellt eine Reihe von Python-REPL-Modi zur Auswahl:

| REPL | Beschreibung | Bearbeiten | Debuggen | Bilder |
| --- | --- | --- | --- | --- |
| Standard | Standard-REPL, kommuniziert direkt mit Python | Standardbearbeitung (mehrzeilig usw.) | Ja, über `$attach` | Nein |
| Debuggen | Standard-REPL, kommuniziert mit gedebuggtem Python-Prozess | Standardbearbeitung | Nur Debuggen | Nein |
| IPython | REPL kommuniziert mit IPython-Back-End | IPython-Befehle, Pylab-Vorteile | Nein | Ja, inline in REPL |
| IPython ohne Pylab | REPL kommuniziert mit IPython-Back-End | Standardmäßiges IPython | Nein | Ja, separates Fenster | 

Dieses Thema beschreibt den **Standard**- und **Debug**-REPL-Modus. Ausführliche Informationen zu den IPython-Modi finden Sie unter [Using Python in the Interactive Window](interactive-repl-ipython.md) (Verwenden von Python im interaktiven Fenster).

Eine detaillierte exemplarische Vorgehensweise mit Beispielen, einschließlich der Interaktionen mit dem Editor wie z.B. STRG+EINGABETASTE, finden Sie unter [Tutorial Step 3: Using the interactive REPL window (Tutorial Schritt 3: Verwenden des interaktiven REPL-Fensters)](vs-tutorial-01-03.md). Eine Video-Einführung finden Sie unter [Python Interactive Window (Interaktives Python-Fenster)](https://mva.microsoft.com/en-US/training-courses/python-tools-for-visual-studio-2017-18121?l=gJYKY5LWE_4605918567) (Microsoft Virtual Academy, 2 Min. 22 Sek.).

> [!VIDEO https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Python-Interactive-Window-gJYKY5LWE_4605918567]

## <a name="opening-an-interactive-window"></a>Öffnen eines interaktiven Fensters

Es gibt mehrere Methoden zum Öffnen des interaktiven Fensters für eine Umgebung.

Erstens: Wechseln Sie zum Python-Umgebungenfenster (**Ansicht > Weitere Fenster > Python-Umgebungen** oder STRG+K,STRG+'), und wählen Sie den Befehl oder die Schaltfläche **Interaktives Fenster öffnen** für eine ausgewählte Umgebung.

![Link zu interaktivem Fenster in Python-Umgebungen](media/interactive-window-opening.png)

Zweitens: Am unteren Rand des Menüs **Anzeige > Weitere Fenster** finden Sie den Befehl „Interaktives Phyton-Fenster“ für Ihre Standardumgebung und einen Befehl, um zum Fenster „Umgebungen“ zu wechseln:

![Menüelemente für interaktives Fenster in „Ansicht > Weitere Fenster“](media/interactive-window-menu.png)

Drittens: Sie können in der Startdatei Ihres Projekts – oder für eine eigenständige Datei – durch Auswahl des Menübefehls **Debuggen > [Projekt | Datei] in interaktivem Python ausführen** (UMSCHALT+Alt+5) ein interaktives Fenster öffnen:

![Ausführen des Projekts im interaktiven Python-Menü](media/interactive-execute-project.png)

Schließlich können Sie Code in der Datei auswählen und den unten beschriebenen Befehl [An Interactive senden](#send-code-to-interactive-command) verwenden.

## <a name="interactive-window-options"></a>Optionen für das interaktive Fenster

Sie können verschiedene Aspekte des interaktiven Fensters über **Tools > Optionen > Python-Tools > Interaktive Fenster** (siehe [Optionen](options.md)) steuern:

![Optionen für interaktives Python-Fenster](media/options-interactive-windows.png)

## <a name="using-the-interactive-window"></a>Verwenden des interaktiven Fensters

Sobald das interaktive Fenster geöffnet ist, können Sie beginnen, Zeile für Zeile Code an der `>>>`-Eingabeaufforderung einzugeben. Das interaktive Fenster führt jede Zeile nach der Eingabe aus, Importieren von Modulen, Definieren von Variablen usw. eingeschlossen:

![Interaktives Python-Fenster](media/interactive-window.png)

Eine Ausnahme besteht, wenn zusätzliche Codezeilen benötigt werden, um eine vollständige Anweisung zu erstellen, beispielsweise wenn eine `for`-Anweisung wie oben gezeigt mit einem Doppelpunkt endet. In diesen Fällen ändert sich die Eingabeaufforderungszeile in `...`, um anzugeben, dass Sie zusätzliche Zeilen für den Block eingeben müssen, wie in der obigen Grafik in der vierten und fünften Zeile dargestellt. Wenn Sie in einer leeren Zeile die EINGABETASTE drücken, schließt das interaktive Fenster den Block und führt ihn im Interpreter aus.

> [!Tip]
> Eine Verbesserung im Vergleich zum üblichen Befehlszeilen-REPL von Python ist im interaktiven Fenster das automatische Einrücken von Anweisungen, die zum gleichen Bereich gehören. Sein Verlauf (abgerufen mit der NACH-OBEN-TASTE) bietet auch mehrzeilige Elemente, während im Befehlszeilen-REPL nur einzelne Zeilen möglich sind.

<a name="meta-commands"></a> Das interaktive Fenster unterstützt auch mehrere Metabefehle. Alle Metabefehle beginnen mit `$`, und Sie können `$help` eingeben, um eine Liste der Metabefehle abzurufen, und `$help <command>`, um nähere Informationen zur Verwendung eines bestimmten Befehls zu erhalten.

| Metabefehl | Beschreibung |
| --- | --- |
| `$$` | Fügt einen Kommentar ein, was das Kommentieren von Code während der gesamten Sitzung erleichtert. |
| `$attach` | Fügt den Visual Studio-Debugger dem REPL-Fensterprozess an, um das Debuggen zu aktivieren. |
| `$cls`, `$clear` | Löscht den Inhalt des Editorfensters, Verlauf und Ausführungskontext bleiben erhalten. |
| `$help` | Zeigt eine Liste von Befehlen an, oder Hilfe zu einem bestimmten Befehl. |
| `$load` | Lädt Befehle aus einer Datei und führt sie aus. |
| `$mod` | Legt das angegebene Modul als aktuellen Bereich fest. |
| `$reset` | Setzt die Ausführungsumgebung auf den ursprünglichen Zustand zurück, behält jedoch den Verlauf bei. |
| `$wait` | Wartet mindestens die angegebene Zahl von Millisekunden. |

Befehle sind auch über Visual Studio-Erweiterungen durch Implementieren und Exportieren von `IInteractiveWindowCommand` ([Beispiel](https://github.com/Microsoft/PTVS/blob/master/Python/Product/PythonTools/PythonTools/Repl/InteractiveWindowCommands.cs#L85)) erweiterbar.

## <a name="switching-scopes"></a>Wechseln von Bereichen

Standardmäßig wird der Bereich des interaktiven Fensters für ein Projekt auf die Startdatei des Projekts beschränkt, als ob Sie es von der Befehlszeile aus ausführen würden. Für eine eigenständige Datei ist der Bereich auf diese Datei beschränkt. Sie können jedoch während der REPL-Sitzung jederzeit im Dropdownmenü am oberen Rand des interaktiven Fensters den Bereich wechseln:

![Bereiche des interaktiven Fensters](media/interactive-scopes.png)

Sobald Sie ein Modul importieren, z.B. durch Eingabe von `import importlib`, werden in der Dropdownliste Optionen zum Wechsel in einen beliebigen Bereich dieses Moduls angezeigt. Eine Meldung im interaktiven Fenster gibt den neuen Bereich an, damit Sie verfolgen können, wie ein bestimmter Zustand während einer Sitzung zustande gekommen ist.

Bei Eingabe von `dir()` in einem Bereich werden gültige Bezeichner in diesem Bereich einschließlich Funktionsnamen, Klassen und Variablen angezeigt. Bei Verwendung von `import importlib` gefolgt von `dir()` wird z.B. Folgendes angezeigt:

![Interaktives Fenster im Bereich „importlib“](media/interactive-importlib-scope.png)

<a name="sending-code-to-interactive"</a>

## <a name="send-code-to-interactive-command"></a>Befehl „An Interactive senden“

Außer direkt im interaktiven Fenster zu arbeiten, können Sie im Editor Code auswählen, mit der rechten Maustaste klicken und **An Interactive senden** wählen oder STRG+EINGABETASTE drücken.

![Menübefehl „An Interactive senden“](media/interactive-send-to.png)

Dieser Befehl ist auch zur iterativen oder evolutionären Codeentwicklung inklusive des Testens Ihres Codes während der Entwicklung nützlich. Sobald Sie einen Codeausschnitt an das interaktive Fenster gesendet und seine Ausgabe gesehen haben, können Sie z.B. die NACH-OBEN-TASTE drücken, um den Code erneut anzuzeigen, ihn ändern und schnell testen, indem Sie STRG+EINGABETASTE drücken. (Durch Drücken der EINGABETASTE am Ende der Eingabe wird diese ausgeführt. Wenn Sie aber die EINGABETASTE in der Mitte der Eingabe drücken, wird eine neue Zeile eingefügt.) Sobald Sie den gewünschten Code haben, können Sie ihn problemlos wieder in die Projektdatei kopieren.

> [!Tip]
> Visual Studio entfernt standardmäßig >>> und ... Die REPL erzeugt eine Eingabeaufforderung, wenn Code von einem interaktiven Fenster in den Editor eingefügt wird. Sie können dieses Verhalten in der Registerkarte **Tools > Optionen > Text-Editor > Python > Erweitert** mithilfe der Option **Paste removes REPL prompts** (Einfügen entfernt REPL-Eingabeaufforderungen) ändern. Siehe [Options - Miscellaneous options (Optionen: Sonstige Optionen)](options.md#miscellaneous-options).

<!-- After 15.3 is released, you can also press "Undo" after pasting to restore prompts. Press "Undo" a second time to remove the pasted code entirely. -->

Wenn Sie eine Codedatei als Zwischenablage verwenden, haben Sie häufiger kleine Codeblöcke, die Sie auf einmal senden möchten. Um Code zu gruppieren, markieren Sie den Code als *code cell* (Codezelle), indem Sie einen Kommentar mit `#%%` zum Anfang der Zelle hinzufügen, der die vorherige beendet. Codezellen können reduziert und erweitert werden. Das Drücken von STRG+EINGABETASTE innerhalb einer Codezelle sendet die gesamte Zelle an das interaktive Fenster und wechselt zur nächsten.

Visual Studio erkennt auch Codezellen, die mit Kommentaren wie `# In[1]:` beginnen, was dem Format entspricht, das Sie beim Exportieren eines Jupyter-Notebooks als Python-Datei erhalten. Durch diese Erkennung kann ein Notebook von [Azure Notebooks (Azure-Notebooks)](https://notebooks.azure.com/) einfach ausgeführt werden, indem es als Python-Datei heruntergeladen,in Visual Studio geöffnet und anschließend STRG+EINGABETASTE gedrückt wird, um jede Zelle auszuführen.

![Interaktive Codezellen](media/interactive-code-cells.png)

## <a name="intellisense-behavior"></a>IntelliSense-Verhalten

Das interaktive Fenster enthält IntelliSense auf der Basis von Liveobjekten, im Gegensatz zum Code-Editor, in dem IntelliSense nur auf der Quellcodeanalyse basiert. Diese Vorschläge im interaktiven Fenster sind korrekter, insbesondere bei dynamisch generiertem Code. Der Nachteil besteht darin, dass Funktionen mit Nebenwirkungen (z.B. Protokollierungsmeldungen) Ihre Entwicklungserfahrung beeinträchtigen können.

Wenn dieses Verhalten ein Problem darstellt, ändern Sie die Einstellungen unter **Tools > Optionen > Python-Tools > Interaktive Fenster** in der Gruppe **Vervollständigungsmodus**, wie unter [Options - Interactive Windows options (Optionen: Optionen zu interaktiven Fenstern)](options.md#interactive-windows-options) beschrieben.
