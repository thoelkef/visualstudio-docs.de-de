---
title: Tipps und Tricks, die im debugger
description: Erfahren Sie mehr über einige der weniger bekannten Features von Visual Studio-Debugger unterstützt
ms.custom: seodec18
ms.date: 06/15/2018
ms.topic: conceptual
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 5262d8b1-2648-429e-85d5-90fcaadfb362
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fe676731170b0e643e00b1ab5e10aa768f256434
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 03/06/2019
ms.locfileid: "57526359"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Erfahren Sie mehr Produktivitätstipps und Tricks für den Debugger in Visual Studio

Lesen Sie dieses Thema, um ein paar produktivitätstipps und Tricks für Visual Studio-Debugger zu erfahren. Informationen zu den grundlegenden Funktionen des Debuggers, finden Sie unter [ein erster Blick auf der Debugger](../debugger/debugger-feature-tour.md). In diesem Thema werden einige Bereiche, die nicht in der Führung durch Features enthalten sind.

## <a name="pin-data-tips"></a>PIN-Datentipps

Wenn Sie häufig auf Datentipps während des Debuggens zeigen, können Sie den Datentipp für die Variable auf sich selbst den schnellen Zugriff erteilen anheften möchten. Die Variable bleibt auch nach dem Neustart angeheftete. Um den DataTip anzuheften, klicken Sie auf das Symbol zum Anheften und mit dem Mauszeiger auf ihn. Sie können mehrere Variablen anheften.

![Anheften eines Datentipps](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Ihren Code bearbeiten und Debuggen fortsetzen (C#, VB, C++)

In den meisten Sprachen, die von Visual Studio unterstützt werden können Sie bearbeiten den Code in der Mitte einer Debugsitzung und mit dem Debuggen fortfahren. Um dieses Feature verwenden zu können, klicken Sie in Ihrem Code mit dem Cursor während der Debugger, nehmen Änderungen, und drücken Sie angehalten **F5**, **F10**, oder **F11** um das Debuggen fortzusetzen.

![Bearbeiten und fortfahren, Debuggen](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Weitere Informationen zur Verwendung der Features und Einschränkungen für Funktionen, finden Sie unter [bearbeiten und Fortfahren](../debugger/edit-and-continue.md).

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Debuggen von Problemen, die schwer zu reproduzieren sind

Ist es schwierig oder zeitaufwändig ist, um einen bestimmten Status in Ihrer app neu zu erstellen, erwägen Sie, ob für die Verwendung eines bedingten Haltepunkts Erklärungen. Sie können [bedingte Haltepunkte](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) und Filtern Sie Haltepunkte, um zu vermeiden, dass in Ihrem app-Code, bis die app wechselt in einen gewünschten Status (z. B. einem Zustand, in dem eine Variable ist das Speichern von fehlerhaften Daten). Sie können Bedingungen mit Ausdrücken, filtern, Trefferzähler und usw. festlegen.

#### <a name="to-create-a-conditional-breakpoint"></a>Erstellen Sie einen bedingten Haltepunkt

1. Mit der rechten Maustaste ein Symbol "Haltepunkt" (die rote Kugel), und wählen Sie **Bedingungen**.

2. In der **Haltepunkteinstellungen** geben einen Ausdruck ein.

    ![Bedingter Haltepunkt](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. Wenn Sie einen anderen Typ der Bedingung interessiert sind, wählen Sie **Filter** anstelle von **Bedingungsausdruck** in die **Haltepunkteinstellungen** (Dialogfeld), und führen Sie dann die Filter-Tipps.

## <a name="change-the-execution-flow"></a>Ändern des Ausführungsablaufs

Mit dem Debugger auf eine einzige Zeile Code angehalten, verwenden Sie die Maus auf um den gelben Pfeilzeiger auf der linken Seite zu erfassen. Bewegen Sie den gelben Pfeil-Zeiger zu einem anderen Zeitpunkt im Code Ausführungspfad. Anschließend verwenden Sie F5, oder ein Befehl, der die app weiter auszuführen.

![Verschieben der Ausführungszeiger](../debugger/media/dbg-tour-move-the-execution-pointer.gif "der Ausführungszeiger verschieben")

Durch Ändern des Ausführungsablaufs können Sie Aktionen ausführen wie das Testen verschiedener Pfade für die Codeausführung oder das erneute Ausführen von Code ohne Neustarten des Debuggers.

> [!WARNING]
> Bei dieser Funktion müssen Sie häufig vorsichtig vorgehen. Sie werden durch eine Warnung in der QuickInfo auf Probleme aufmerksam gemacht. Möglicherweise werden Ihnen auch andere Warnungen angezeigt. Verschieben den Zeiger kann nicht rückgängig gemacht, Ihre app in einem früheren Anwendungszustand.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Überwachen eines Objekts außerhalb des Bereichs (C#, Visual Basic)

Es ist einfach, zeigen Sie die Variablen mithilfe der Debuggerfenster wie die **Watch** Fenster. Aber wenn eine Variable den Gültigkeitsbereich verlässt in der **Watch** Fenster werden Sie feststellen, dass er ausgegraut ist. Der Wert einer Variablen kann in einigen app-Szenarien ändern, selbst wenn die Variable ist außerhalb des gültigen Bereichs, und möglicherweise möchten es so beobachten (z. B. eine Variable kann Garbage collection erhalten). Sie können die Variable verfolgen, indem Sie dafür im Objekt-ID erstellen die **Watch** Fenster.

#### <a name="to-create-an-object-id"></a>Um eine Objekt-ID zu erstellen.

1.  Legen Sie einen Haltepunkt in der Nähe einer Variablen, die Sie nachverfolgen möchten.

2.  Starten Sie den Debugger (**F5**) und die Ausführung am Haltepunkt beendet.

3. Suchen Sie die Variable in der **"lokal"** Fenster (**Debuggen > Windows > "lokal"**) mit der rechten Maustaste auf die Variable, und wählen Sie **Objekt-ID**.

    ![Erstellen Sie eine ObjectID](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")

4.  Sie sollten ein **$** und eine Zahl im **Lokalfenster** einen Haltepunkt festlegen. Diese Variable ist die Objekt-ID.

5.  Mit der rechten Maustaste der Objekt-ID-Variable, und wählen Sie **Überwachung hinzufügen**.

Weitere Informationen finden Sie unter [erstellen Sie eine Objekt-ID](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds).

## <a name="view-return-values-for-functions"></a>Anzeigen der Rückgabewerte für Funktionen

Um die Rückgabe von Werten für Ihre Funktionen anzeigen, sehen Sie sich die Funktionen, die in angezeigt werden die **"Auto"** Fenster, während Sie durch den Code schrittweise ausführen. Um den Rückgabewert für eine Funktion anzuzeigen, stellen Sie sicher, dass die Funktion, die Sie interessiert sind, bereits ausgeführt wurde (drücken Sie die **F10** einmal, wenn Sie derzeit für den Funktionsaufruf beendet sind). Wenn das Fenster geschlossen wird, verwenden Sie **Debuggen > Windows > "Auto"** zum Öffnen der **"Auto"** Fenster.

![Autos Window](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

Darüber hinaus können Sie Funktionen in eingeben der **direkt** Fenster zum Anzeigen der Rückgabewerte. (Öffnen Sie sie in **Debuggen > Windows > direkt**.)

![Fenster "direkt"](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

Sie können auch [Pseudovariablen](../debugger/pseudovariables.md) in die **sehen Sie sich** und **direkt** Fenster z. B. `$ReturnValue`.

## <a name="string_visualizer"></a>Überprüfen von Zeichenfolgen in einer Schnellansicht

Bei der Arbeit mit Zeichenfolgen kann es hilfreich sein, zeigen Sie die gesamte formatierte Zeichenfolge sein. Klicken Sie zum Anzeigen einer nur-Text, XML, HTML oder JSON-Zeichenfolge auf das Lupensymbol ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Schnellansicht Symbol") beim Zeigen auf eine Variable, die einen Zeichenfolgenwert enthält.

![Öffnen Sie eine Zeichenfolgen-Schnellansicht](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

Eine Zeichenfolgen-Schnellansicht helfen Ihnen dabei herauszufinden, ob eine Zeichenfolge falsch formatiert, abhängig vom Zeichenfolgentyp ist. Angenommen, ein Leerzeichen **Wert** Feld gibt an, die Zeichenfolge wird vom Typ Schnellansicht nicht erkannt. Weitere Informationen finden Sie unter [Zeichenfolge Schnellansicht (Dialogfeld)](../debugger/string-visualizer-dialog-box.md).

![JSON-Zeichenfolgen-Schnellansicht](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

Für einigen andere Typen wie z. B. WPF-Objekte, die in den Debuggerfenstern angezeigt werden, können Sie auch Schnellansichten öffnen.

## <a name="break-into-code-on-handled-exceptions"></a>Unterbrechen Sie im Code auf behandelten Ausnahmen

Der Debugger unterbricht in Ihren Code auf nicht behandelte Ausnahmen. Wird jedoch behandelt Ausnahmen (z. B. Ausnahmen, die innerhalb einer `try/catch` Block) kann auch eine Quelle von Fehlern sein, und Sie sollten untersuchen, wenn die Zeitpunkte. Sie können konfigurieren, dass den Debugger für behandelten Ausnahmen sowie in Code unterbrochen, durch Konfigurieren von Optionen in der **Ausnahmeeinstellungen** Dialogfeld. Öffnen Sie das Dialogfeld durch auswählen **Debuggen > Windows > Ausnahmeeinstellungen**.

Die **Ausnahmeeinstellungen** Dialogfeld können Sie des Debuggers zum Unterbrechen im Code für bestimmte Ausnahmen informieren. In der Abbildung unten, unterbricht der Debugger in den Code immer ein `System.NullReferenceException` auftritt. Weitere Informationen finden Sie unter [Verwalten von Ausnahmen](../debugger/managing-exceptions-with-the-debugger.md).

![Das Dialogfeld "Einstellungen" Ausnahme](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Debuggen von Deadlocks und Racebedingungen

Wenn Sie die Arten von Problemen zu debuggen, die für Multithreadanwendungen befinden müssen, es ist häufig hilfreich, den Speicherort von Threads während des Debuggens anzeigen. Hierzu können Sie problemlos, indem Sie die **Threads in Quelle anzeigen** Schaltfläche.

#### <a name="to-show-threads-in-your-source-code"></a>Um Threads in Ihrem Quellcode anzuzeigen.

1.  Während des Debuggens, klicken Sie auf die **Threads in Quelle anzeigen** Schaltfläche ![Threads in Quelle anzeigen](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") in die **Debuggen** Symbolleiste.

2.  Betrachten Sie den Bundsteg auf der linken Seite des Fensters. In dieser Zeile, die Sie sehen eine *Threadmarker* Symbol ![Threadmarker](../debugger/media/dbg-thread-marker.png "ThreadMarker") , das zwei Fäden ähnelt. Der Threadmarker gibt an, dass ein Thread an dieser Position angehalten wurde.

    Beachten Sie, dass ein Threadmarker teilweise kann, können Sie durch einen Haltepunkt abgedeckt werden.

3.  Zeigen Sie mit dem Mauszeiger auf den Threadmarker. Ein DataTip wird angezeigt. Anhand des DataTips erfahren Sie den Namen und die Thread-ID jedes angehaltenen Threads.

    Sie können auch den Speicherort der Threads im Anzeigen der [Fenster "Parallele Stapel"](../debugger/get-started-debugging-multithreaded-apps.md).

## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Untersuchen von Nutzlasten für Webdienste und Netzwerkressourcen (UWP)

In UWP-apps können Sie Netzwerkoperationen mithilfe analysieren die `Windows.Web.Http` API. Sie können dieses Tool zum Debuggen von Webdiensten und Netzwerkressourcen verwenden. Wählen Sie zum Verwenden des Tools **Debuggen > Profiler für Leistung**. Wählen Sie **Netzwerk**, und wählen Sie dann **starten**. Durchlaufen Sie in Ihrer Anwendung das Szenario, das `Windows.Web.Http` verwendet, und wählen Sie anschließend **Auflistung beenden** aus, um einen Bericht zu generieren.

![Das Werkzeug zur profilerstellung Netzwerkverwendung](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

Wählen Sie einen Vorgang in der Ansicht „Zusammenfassung“ aus, um mehr Details anzuzeigen.

![Ausführliche Informationen in das Netzwerk-auslastungstool](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

Weitere Informationen finden Sie unter [Netzwerkverwendung](../profiling/network-usage.md).

## <a name="modules_window"></a> Erhalten Sie immer vertrauter mit, wie der Debugger an Ihre app angefügt (C#, C++, Visual Basic F#)

Zum Anfügen an der ausgeführten app lädt der Debugger Symboldateien (.pdb) generierte Dateien für die exakt demselben Build von der app, die Sie debuggen möchten. In einigen Fällen kann ein wenig wissen von Symboldateien hilfreich sein. Sie können überprüfen, wie Symboldateien, die mithilfe von Visual Studio lädt die **Module** Fenster.

Öffnen der **Module** Fenster beim Debuggen, indem Sie die Auswahl **Debuggen > Windows > Module**. Die **Module** Fenster können Sie ermitteln, welche Module, die der Debugger wird als Benutzercode behandeln oder [ *mein Code*](../debugger/just-my-code.md), und das Symbol Status für das Modul geladen. In den meisten Szenarien der Debugger sucht automatisch nach Symboldateien für Benutzercode, jedoch sollten Sie in Schritt (oder Debuggen) Sie .NET Framework-Code, Systemcode oder Drittanbieter-Bibliothek-Code, sind zusätzliche Schritte erforderlich, um die richtige Symboldateien zu erhalten.

![Anzeigen von Symbolinformationen in das Fenster "Module"](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

Sie Laden von symbolischen Informationen direkt aus der **Module** Fenster, indem Sie mit der rechten Maustaste, und wählen **Symbole laden**.

In einigen Fällen liefern app-Entwickler-apps, ohne die entsprechenden Symboldateien (um den Fußabdruck verringern möchten), aber beibehalten, die eine Kopie des entsprechenden Symbols für den Build-Dateien, damit sie eine veröffentlichte Version später debuggen können.

Um herauszufinden, wie der Debugger Code als Benutzercode klassifiziert, finden Sie unter [nur mein Code](../debugger/just-my-code.md). Weitere Informationen zu Symboldateien finden Sie unter [angeben von Symbol(PDB)- und Quelldateien im Visual Studio-Debugger](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="learn-more"></a>Weitere Informationen

Zusätzliche Tipps und Tricks und ausführlichere Informationen finden Sie in folgenden Blogbeiträgen:

- [7 weniger bekannte Hacks für das Debuggen in Visual Studio](https://devblogs.microsoft.com/visualstudio/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [7 verborgenen Funktionen in Visual Studio](https://devblogs.microsoft.com/visualstudio/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Siehe auch
[Tastenkombinationen](../ide/tips-and-tricks-for-visual-studio.md)
