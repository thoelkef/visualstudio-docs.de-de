---
title: Debuggen von Python-Code
description: Eine exemplarische Vorgehensweise zu den spezifischen Debugfunktionen in Visual Studio für Python-Code, einschließlich dem Festlegen von Haltepunkten, der Einzelschrittausführung, der Untersuchung von Werten, des Überprüfens von Ausnahmen und des Debuggens im interaktiven Fenster.
ms.date: 03/05/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 576a8ffdd025667e811e96a712368de98bbe4cb4
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="debugging-your-python-code"></a>Debuggen von Python-Code

Visual Studio bietet umfangreiche Debugfunktionen für Python, u.a. Folgende: Anfügen an ausgeführte Prozesse, Auswerten von Ausdrücken in den Überwachungs- und Direktfenstern, Untersuchen lokaler Variablen, Haltepunkte, Anweisungsausführung in Einzelschritten, Prozedurschritten oder bis Rücksprung, Festlegen der nächsten Anweisung und viele weitere.

Weitere Informationen finden Sie auch in den folgenden szenariospezifischen Artikeln:

- [Linux-Remotedebuggen](debugging-python-code-on-remote-linux-machines.md)
- [Azure-Remotedebuggen](debugging-remote-python-code-on-azure.md)
- [Python/C++ – Debuggen im gemischten Modus](debugging-mixed-mode-c-cpp-python-in-visual-studio.md)
- [Symbole für das Debuggen im gemischten Modus](debugging-symbols-for-mixed-mode-c-cpp-python.md)

|   |   |
|---|---|
| ![Kamerasymbol für video](../install/media/video-icon.png "Video ansehen") | [Sehen Sie sich ein Video (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Debugging-Python-Ep5dp5LWE_3805918567) mit einer Demonstration zum Python-Debugging an (3 Minuten, 32 Sekunden).|

<a name="debugging-without-a-project"></a>

> [!Tip]
> Python in Visual Studio unterstützt das Debuggen ohne ein Projekt. Klicken Sie in einer geöffneten eigenständigen Python-Datei mit der rechten Maustaste in den Editor, und klicken Sie auf **Mit Debugging starten**. Visual Studio startet das Skript mit der globalen Standard-Umgebung (siehe [Python-Umgebungen](managing-python-environments-in-visual-studio.md)) und ohne Argumente. Danach verfügen Sie über vollständige Debuggingunterstützung.
>
> Erstellen Sie ein Projekt für den Code, um die Umgebung und die Argumente zu steuern. Mit der Projektvorlage [Aus vorhandenem Python-Code](managing-python-projects-in-visual-studio.md#creating-a-project-from-existing-files) ist dies ganz einfach erledigt.

<a name="debugging-with-a-project"></a>

## <a name="basic-debugging"></a>Debuggen – Grundlagen

Der grundlegende Debugworkflow umfasst das Festlegen von Haltepunkten, die Einzelschrittausführung des Codes, das Untersuchen von Code und das Behandeln von Ausnahmen, wie in den folgenden Abschnitten beschrieben.

Eine Debugsitzung wird mit dem Befehl **Debuggen > Debuggen starten**, der Schaltfläche **Start** auf der Symbolleiste oder der Taste F5 gestartet. Diese Aktionen öffnen die Startdatei Ihres Projekts (im Projektmappen-Explorer fett hervorgehoben) mit der aktiven Umgebung des Projekts und allen Befehlszeilenargumenten oder Suchpfaden, die in den Projekteigenschaften festgelegt wurden (siehe [Project debugging options (Projektbezogene Debugoptionen)](#project-debugging-options)). **Visual Studio 2017 Version 15.6** und höher warnt Sie, wenn Sie keine Startdatei festgelegt haben; frühere Versionen öffnen möglicherweise ein Ausgabefenster, in dem der Python-Interpreter ausgeführt wird, oder das Ausgabefenster wird nur kurz angezeigt und dann geschlossen. Klicken Sie in jedem Fall mit der rechten Maustaste auf die entsprechende Datei, und wählen Sie **Als Startdatei festlegen** aus.

> [!Note]
> Der Debugger startet immer mit der aktiven Python-Umgebung für das Projekt. Legen Sie, wie unter [Selecting a Python environment for a project](selecting-a-python-environment-for-a-project.md) (Auswählen einer Python-Umgebung für ein Projekt) beschrieben, eine andere Umgebung als aktiv fest, um die Umgebung zu ändern.

### <a name="breakpoints"></a>Haltepunkte

Haltepunkte halten die Ausführung des Codes an einem markierten Punkt an, sodass Sie den Programmzustand überprüfen können. Legen Sie Haltepunkte fest, indem Sie auf den linken Rand des Code-Editors klicken oder indem Sie mit der rechten Maustaste auf eine Codezeile klicken und **Haltepunkt > Haltepunkt einfügen** auswählen. In jeder Zeile mit einem Haltepunkt wird ein roter Punkt angezeigt.

![Haltepunkte in Visual Studio](media/debugging-breakpoints.png)

Durch Klicken auf den roten Punkt oder durch Klicken mit der rechten Maustaste auf die Codezeile und Auswählen von **Haltepunkt > Haltepunkt löschen** wird der Haltepunkt entfernt. Mit dem Befehl **Haltepunkt > Haltepunkt deaktivieren** können Sie den Haltepunkt auch deaktivieren, ohne ihn zu löschen.

> [!Note]
> Einige Haltepunkte in Python können für Entwickler überraschend sein, die mit anderen Programmiersprachen gearbeitet haben. In Python ist die gesamte Datei ausführbarer Code, daher führt Python die Datei beim Laden aus, um Klassen- oder Funktionsdefinitionen auf oberster Ebene zu verarbeiten. Wenn ein Haltepunkt festgelegt wurde, stellen Sie möglicherweise fest, dass der Debugger mitten in einer Klassendeklaration unterbricht. Dieses Verhalten ist korrekt, obwohl es manchmal überraschend ist.

Sie können die Bedingungen anpassen, unter denen ein Haltepunkt ausgelöst wird, sodass z.B. nur dann unterbrochen wird, wenn eine Variable auf einen bestimmten Wert oder Wertebereich festgelegt ist. Um Bedingungen festzulegen, klicken Sie mit der rechten Maustaste auf den roten Punkt des Haltepunkts, wählen **Bedingungen** aus und erstellen dann mithilfe von Python-Code Ausdrücke. Ausführliche Informationen zu dieser Funktion in Visual Studio finden Sie unter [Haltepunktbedingungen](../debugger/using-breakpoints.md#breakpoint-conditions),

Beim Festlegen von Bedingungen können Sie auch **Aktion** auswählen und eine Meldung zum Protokollieren im Ausgabefenster erstellen. Die Ausführung kann dabei optional automatisch fortgesetzt werden. Durch das Protokollieren einer Meldung wird ein sogenannter *Ablaufverfolgungspunkt* erstellt, ohne dass der Anwendung direkt ein Protokollierungscode hinzugefügt werden muss:

![Erstellen eines Ablaufverfolgungspunkts mit einem Haltepunkt](media/debugging-tracepoint.png)

### <a name="stepping-through-code"></a>Einzelschrittausführung von Code

Nachdem der Code an einem Haltepunkt angehalten wurde, haben Sie verschiedene Möglichkeiten, den Code schrittweise auszuführen oder Codeblöcke auszuführen, bevor wieder unterbrochen wird. Diese Befehle sind an verschiedenen Stellen verfügbar, z.B. in der oberen Symbolleiste zum Debuggen, im **Debuggen**-Menü, im Kontextmenü im Code-Editor sowie über Tastaturkurzbefehle (nicht alle Befehle sind an all diesen Stellen verfügbar):

| Feature | Tastatureingabe | description |
| --- | --- | --- |
| Weiter | F5 | Führt den Code aus, bis der nächste Haltepunkt erreicht ist. |
| Einzelschritt | F11 | Führt die nächste Anweisung aus und hält an. Wenn die nächste Anweisung ein Funktionsaufruf ist, hält der Debugger in der ersten Zeile der aufgerufenen Funktion an. |
| Prozedurschritt | F10 | Führt die nächste Anweisung aus, einschließlich des Aufrufs einer Funktion (sämtlicher Code wird ausgeführt) und der Anwendung von möglichen Rückgabewerten. Mit Prozedurschritten können Sie problemlos Funktionen überspringen, die Sie nicht debuggen müssen. |
| Ausführen bis Rücksprung | UMSCHALTTASTE+F11 | Führt Code bis zum Ende der aktuellen Funktion aus und springt dann zur aufrufenden Anweisung.  Dieser Befehl ist hilfreich, wenn Sie den Rest der aktuellen Funktion nicht debuggen müssen. |
| Ausführen bis Cursor | Strg+F10 | Führt Code bis zur Position des Textcursors im Editor aus. Mit diesem Befehl können Sie ganz einfach ein Codesegment überspringen, das Sie nicht debuggen müssen. |
| Festlegen der nächsten Anweisung | Ctrl+Shift+F10 | Ändert den aktuellen Ausführungspunkt im Code in die Position des Textcursors. Mit diesem Befehl können Sie die Ausführung eines Codesegments verhindern, wenn Sie z.B. wissen, dass der Code fehlerhaft ist oder zu unerwünschten Nebeneffekten führt. |
| Nächste Anweisung anzeigen | ALT+Num * | Bringt Sie zur nächsten Anweisung zurück, die ausgeführt wird. Dieser Befehl ist sehr hilfreich, wenn Sie Ihren Code untersucht haben und nicht mehr wissen, wo der Debugger angehalten hat. |

### <a name="inspecting-and-modifying-values"></a>Untersuchen und Ändern von Werten

Wenn der Debugger angehalten hat, können Sie die Werte von Variablen überprüfen und ändern. Sie können auch das Überwachungsfenster verwenden, um einzelne Variablen sowie benutzerdefinierte Ausdrücke zu überwachen. (Allgemeine Informationen dazu finden Sie unter [Überprüfen von Variablen](../debugger/getting-started-with-the-debugger.md#inspect-variables-with-the-autos-and-locals-windows).)

Um einen Wert mithilfe von DataTips anzuzeigen, zeigen Sie einfach mit dem Mauszeiger auf eine beliebige Variable im Editor. Klicken Sie auf den Wert, um ihn zu ändern:

![DataTips im Debugger](media/debugging-quick-tips.png)

Das Auto-Fenster (**Debuggen > Fenster > Auto**) enthält Variablen und Ausdrücke für die aktuelle Anweisung. Sie können auf die Wertspalte doppelklicken oder einen Wert auswählen und F2 drücken, um den Wert zu bearbeiten:

![Auto-Fenster im Debugger](media/debugging-autos-window.png)

Das Fenster für lokale Variablen (**Debuggen > Fenster > Lokale Variablen**) zeigt alle Variablen, die sich im aktuellen Geltungsbereich befinden und bearbeitet werden können:

![Fenster für lokale Variablen im Debugger](media/debugging-locals-window.png)

Weitere Informationen zum Auto-Fenster und zum Fenster für lokale Variablen finden Sie unter [Überprüfen von Variablen im Auto-Fenster und im Fenster für lokale Variablen](../debugger/autos-and-locals-windows.md).

Das Überwachungsfenster (**Debuggen > Fenster > Überwachen > Überwachen 1-4**) ermöglicht es Ihnen, beliebige Python-Ausdrücke einzugeben und die Ergebnisse anzuzeigen. Ausdrücke werden für jeden Schritt erneut ausgewertet:

![Überwachungsfenster im Debugger](media/debugging-watch-window.png)

Weitere Informationen zum Verwenden der Überwachung finden Sie unter [Festlegen einer Überwachung von Variablen in den Fenstern „Überwachung“ und „Schnellüberwachung“](../debugger/watch-and-quickwatch-windows.md).

Beim Überprüfen eines Zeichenfolgenwerts (`str`, `unicode`, `bytes` und `bytearray` gelten für diesen Zweck als Zeichenfolgen) wird rechts neben dem Wert ein Lupensymbol angezeigt. Wenn Sie auf das Symbol klicken, wird der nicht in Anführungszeichen eingeschlossene Zeichenfolgenwert in einem Popup-Dialogfeld angezeigt. Es werden Zeilenumbrüche angezeigt und Sie können im Fenster scrollen: eine hilfreiche Funktion für lange Zeichenfolgen. Wenn Sie auf den nach unten weisenden Pfeil auf dem Symbol klicken, können Sie zudem Nur-Text-, HTML-, XML- und JSON-Schnellansichten auswählen:

![Schnellansichten für Zeichenfolgen](media/debugging-string-visualizers.png)

HTML-, XML- und JSON-Schnellansichten werden in separaten Popupfenstern mit Syntaxhervorhebung und Strukturansichten angezeigt.

### <a name="exceptions"></a>Ausnahmen

Wenn während des Debuggens ein Fehler in Ihrem Programm auftritt, aber kein Ausnahmehandler dafür vorhanden ist, hält der Debugger am Punkt der Ausnahme an:

![Popupfenster für Ausnahmen](media/debugging-exception-popup.png)

An diesem Punkt können Sie den Programmzustand überprüfen, einschließlich der Aufrufliste. Wenn Sie jedoch den Code in Einzelschritten ausführen, wird die Ausnahme weiterhin ausgelöst, bis sie behandelt oder das Programm beendet wird.

Der Menübefehl **Debuggen > Fenster > Ausnahmeeinstellungen** öffnet ein Fenster, in dem Sie **Python-Ausnahmen** erweitern können:

![Fenster für Ausnahmen](media/debugging-exception-settings.png)

Das Kontrollkästchen für jede Ausnahme steuert, ob der Debugger *immer* unterbricht, wenn die Ausnahme ausgelöst wird. Aktivieren Sie dieses Kontrollkästchen, wenn Sie bei einer bestimmten Ausnahme häufiger unterbrechen möchten.

Standardmäßig wird bei den meisten Ausnahmen unterbrochen, wenn im Quellcode kein Ausnahmehandler gefunden werden kann. Um dieses Verhalten zu ändern, klicken Sie mit der rechten Maustaste auf eine Ausnahme, und aktivieren bzw. deaktivieren Sie die Option **Continue When Unhandled in User Code** (Fortfahren, wenn in Benutzercode nicht behandelt). Deaktivieren Sie das Kontrollkästchen, wenn bei einer Ausnahme seltener unterbrochen werden soll.

Wenn Sie eine Ausnahme konfigurieren möchten, die in dieser Liste nicht angezeigt wird, klicken Sie auf die Schaltfläche **Hinzufügen**, um sie hinzuzufügen. Der Name muss mit dem vollständigen Namen der Ausnahme übereinstimmen.

## <a name="project-debugging-options"></a>Projektbezogene Debugoptionen

Standardmäßig startet der Debugger Ihr Programm mit dem Python-Standardstartprogramm, ohne Befehlszeilenargumente und ohne andere spezielle Pfade oder Bedingungen. Die Startoptionen können in den Debugeigenschaften des Projekts geändert werden. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf Ihr Projekt, und wählen Sie **Eigenschaften** und die Registerkarte **Debuggen** aus.

![Debugeigenschaften des Projekts](media/debugging-project-properties.png)

### <a name="launch-mode-options"></a>Optionen für den Startmodus

| Option | description |
| --- | --- |
| Python-Standardstartprogram | Verwendet in portierbarem Python geschriebenen Debugcode, der mit CPython, IronPython und Varianten wie Stackless Python kompatibel ist. Diese Option bietet die beste Leistung für das Debuggen von reinem Python-Code. Beim Anfügen an einen ausgeführten `python.exe`-Prozess wird dieses Startprogramm verwendet. Dieses Startprogramm ermöglicht auch das [Debuggen im gemischten Modus](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) für CPython, mit dem Sie nahtlos zwischen C/C++-Code und Python-Code wechseln können. |
| Webstartprogramm | Startet Ihren Standardbrowser und ermöglicht das Debuggen von Vorlagen. Im Abschnitt [Debuggen von Webvorlagen](python-web-application-project-templates.md#debugging) finden Sie weitere Informationen. |
| Django-Webstartprogramm | Ist mit dem Webstartprogramm identisch und wird nur aus Gründen der Abwärtskompatibilität aufgeführt. |
| IronPython-Startprogramm (.NET) | Verwendet den .NET-Debugger, der nur mit IronPython funktioniert, aber das Wechseln zwischen Projekten in beliebigen .NET-Sprachen ermöglicht, einschließlich C# und VB. Dieses Startprogramm wird beim Anfügen an einen ausgeführten .NET-Prozess verwendet, der IronPython hostet. |

### <a name="run-options-search-paths-startup-arguments-and-environment-variables"></a>Ausführungsoptionen (Suchpfade, Startargumente und Umgebungsvariablen)

| Option | description |
| --- | --- |
| Suchpfade | Diese Werte entsprechen den im Knoten „Suchpfade“ des Projektmappen-Explorers angezeigten Pfaden. Sie können den Wert hier ändern, es ist aber einfacher, den Projektmappen-Explorer zu verwenden, der das Durchsuchen von Ordnern ermöglicht und Pfade automatisch in ihre relative Form konvertiert. |
| Skriptargumente | Diese Argumente werden dem Befehl hinzugefügt, der zum Starten Ihres Skripts verwendet wird, und werden nach dem Dateinamen des Skripts angezeigt. Das erste Element hier ist für das Skript als `sys.argv[1]` verfügbar, das zweite als `sys.argv[2]` usw. |
| Interpreterargumente | Diese Argumente werden vor dem Namen Ihres Skripts in die Befehlszeile des Startprogramms eingefügt. Allgemeine Argumente sind `-W ...` zum Steuern von Warnungen, `-O` zum Optimieren Ihres Programms und `-u` zum Verwenden von nicht gepufferter E/A. IronPython-Benutzer werden dieses Feld vermutlich zum Übergeben von `-X`-Optionen verwenden, z.B. `-X:Frames` oder `-X:MTA`. |
| Interpreterpfad | Überschreibt den Pfad, der der aktuellen Umgebung zugeordnet ist.  Dieser Wert kann hilfreich sein, wenn Sie Ihr Skript mit einem nicht standardmäßigen Interpreter starten. |
| Umgebungsvariablen | In diesem mehrzeiligen Textfeld fügen Sie Einträge in der Form `NAME=VALUE` hinzu. Diese Einstellung wird als letztes, zusätzlich zu allen vorhandenen globalen Umgebungsvariablen und nach dem Festlegen von `PYTHONPATH` gemäß der Einstellung für Suchpfade angewendet. Daher kann sie zum manuellen Überschreiben all dieser anderen Variablen verwendet werden. |

<a name="the-debug-interactive-window"></a>

## <a name="immediate-and-interactive-windows"></a>Direktfenster und interaktive Fenster

Es gibt zwei interaktive Fenster, die Sie während einer Debugsitzung verwenden können: das standardmäßige Visual Studio-Direktfenster und das interaktive Python-Debugfenster.

Das Direktfenster (**Debuggen > Fenster > Direkt**) wird zum schnellen Auswerten von Python-Ausdrücken und Überprüfen oder Zuweisen von Variablen im ausgeführten Programm verwendet. Ausführliche Informationen finden Sie im allgemeinen Artikel [Direktfenster](../ide/reference/immediate-window.md).

Das interaktive Python-Debugfenster (**Debuggen > Fenster > Interaktives Debuggen in Python**) bietet einen größeren Funktionsumfang, da es alle [interaktiven REPL](python-interactive-repl-in-visual-studio.md)-Funktionen für das Debuggen zur Verfügung stellt, einschließlich des Schreibens und Ausführens von Code. Das Fenster stellt automatisch eine Verbindung zu jedem Prozess her, der mit dem Python-Standardstartprogramm gestartet wird (einschließlich Prozessen, die über **Debuggen > An den Prozess anhängen*** angefügt werden). Beim Debuggen im gemischten C/C++-Modus ist es jedoch nicht verfügbar.

![Interaktives Python-Debugfenster](media/debugging-interactive.png)

Das Fenster zum interaktiven Debuggen unterstützt zusätzlich zu den [REPL-Standardbefehlen](python-interactive-repl-in-visual-studio.md#meta-commands) spezielle Metabefehle:

| Befehl | Argumente | description |
| --- | --- | --- |
| `$continue`, `$cont`, `$c` | Startet die Ausführung des Programms ab der aktuellen Anweisung. |
| `$down`, `$d` | Verschiebt den aktuellen Rahmen in der Stapelüberwachung eine Ebene nach unten. |
| `$frame` | | Zeigt die aktuelle Rahmen-ID an.
| `$frame` | frame id | Legt den aktuellen Rahmen auf die angegebene Rahmen-ID fest.
| `$load` | Lädt Befehle aus einer Datei und führt sie vollständig aus. |
| `$proc` |  | Zeigt die aktuelle Prozess-ID an. |
| `$proc` | process id | Legt den aktuellen Prozess auf die angegebene Prozess-ID fest. |
| `$procs` | | Führt die aktuell im Debugmodus befindlichen Prozesse auf. |
| `$stepin`, `$step`, `$s` | Springt in den nächsten Funktionsaufruf, wenn möglich. |
| `$stepout`, `$return`, `$r` | Springt aus der aktuellen Funktion heraus. |
| `$stepover`, `$until`, `$unt` | Springt über den nächsten Funktionsaufruf. |
| `$thread` | | Zeigt die aktuelle Thread-ID an. |
| `$thread` | thread id | Legt den aktuellen Thread auf die angegebene Thread-ID fest. |
| `$threads` | | Führt die aktuell im Debugmodus befindlichen Threads auf. |
| `$up`, `$u` | | Verschiebt den aktuellen Rahmen in der Stapelüberwachung eine Ebene nach oben. |
| `$where`, `$w`, `$bt` | Führt die Rahmen für den aktuellen Thread auf. |

Beachten Sie, dass die standardmäßigen Debuggerfenster wie „Prozesse“, „Threads“ und „Aufrufliste“ nicht mit dem Fenster zum interaktiven Debuggen synchronisiert werden. Das Ändern des aktiven Prozesses, Threads oder Frames im interaktiven Debugfenster wirkt sich nicht auf die anderen Debuggerfenster aus. Entsprechend gilt: Das Ändern des aktiven Prozesses, Threads oder Frames in anderen Debuggerfenster wirkt sich nicht auf das interaktive Debugfenster aus.

Das Fenster zum interaktiven Debuggen verfügt über einen eigenen Satz Optionen, auf die Sie über **Tools > Optionen > Python-Tools > Fenster zum interaktiven Debuggen** zugreifen können. Im Gegensatz zum regulären interaktiven Python-Fenster, das für jede Python-Umgebung über eine separate Instanz verfügt, gibt es nur ein Fenster zum interaktiven Debuggen, und dieses verwendet immer den Python-Interpreter für den Prozess, für den das Debugging ausgeführt wird. Siehe [Options - Debugging options (Optionen: Debugoptionen)](python-support-options-and-settings-in-visual-studio.md#debugging-options).

![Optionen für das Fenster zum interaktiven Debuggen](media/debugging-interactive-options.png)

## <a name="see-also"></a>Siehe auch

Vollständige Informationen zum Visual Studio-Debugger finden Sie unter [Debuggen in Visual Studio](../debugger/debugger-feature-tour.md).