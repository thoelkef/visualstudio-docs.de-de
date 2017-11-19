---
title: Tipps und Tricks in Visual Studio-Debugger | Microsoft Docs
ms.custom: 
ms.date: 06/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stepping
- debugging [Visual Studio], execution control
- execution, controlling in debugger
ms.assetid: 5262d8b1-2648-429e-85d5-90fcaadfb362
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26993da79249d1706dc8609cfcd5b0ceb66e1ec4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Erfahren Sie Produktivitätstipps und Tricks für den Debugger in Visual Studio

Lesen Sie dieses Thema, um einige produktivitätstipps und Tricks für Visual Studio-Debugger finden. Um einen Überblick über die grundlegenden Funktionen des Debuggers werden soll, finden Sie unter [Debugger Feature Tour](../debugger/debugger-feature-tour.md). In diesem Thema behandelt wir einige Bereiche, die nicht in der Featuretour enthalten sind.

## <a name="pin-data-tips"></a>PIN-Datentipps

Wenn Sie häufig auf Datentipps während des Debuggens zeigen, können Sie Datentipp für die Variable auf sich selbst schnellen Zugriff erteilen anheften möchten. Die Variable bleibt auch nach dem Neustart angeheftete. Um den DataTip anzuheften, klicken Sie auf das Symbol zum Anheften während der Mauszeiger darauf. Sie können mehrere Variablen anheften.

![Anheften eines Datentipps](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Bearbeiten Sie den Code und fortfahren Sie, Debuggen (c#, VB, C++)

In den meisten Sprachen, die von Visual Studio unterstützt werden können Sie bearbeiten Sie Code in der Mitte einer Debugsitzung und mit dem Debuggen fortfahren. Um dieses Feature verwenden zu können, klicken Sie in Ihren Code mit dem Mauszeiger in den Debugger, stellen bearbeitet, und drücken Sie nach angehaltenen **F5**, **F10**, oder **F11** um das Debuggen fortzusetzen.

![Bearbeiten und fortfahren, Debuggen](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Weitere Informationen zur Verwendung der Features und funktionseinschränkungen finden Sie unter [bearbeiten und Fortfahren](../debugger/edit-and-continue.md).

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Debuggen von Problemen, die schwer zu reproduzieren sind

Ist es schwierig und zeitaufwändig einen bestimmten Status in der app erneut erstellen, erwägen Sie, ob für die Verwendung eines bedingten Haltepunkts Erklärungen. Sie können [bedingter Haltepunkte](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) und Filtern von Haltepunkten, um zu vermeiden, dass in Ihrem app-Code, bis die app wechselt in den gewünschten Zustand (z. B. in einem Zustand, in dem eine Variable fehlerhafte Daten gespeichert ist). Sie können Bedingungen mit Ausdrücken, filtern, Trefferanzahlen usw. festlegen.

#### <a name="to-create-a-conditional-breakpoint"></a>So erstellen einen bedingten Haltepunkt

1. Mit der rechten Maustaste ein Haltepunktsymbol (das rote Kugel), und wählen Sie **Bedingungen**.

2. In der **Haltepunkteinstellungen** Fenster einen Ausdruck.

    ![Bedingter Haltepunkt](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. Wenn Sie einen anderen Typ von Bedingung interessiert sind, wählen Sie **Filter** anstelle von **Bedingungsausdruck** in der **Haltepunkteinstellungen** (Dialogfeld), und klicken Sie dann führen Sie die Filter-Tipps.

## <a name="change-the-execution-flow"></a>Ändern des Ausführungsflusses

Mit dem Debugger auf eine Codezeile angehalten wird, verwenden Sie die Maus auf den gelben Pfeilzeiger auf der linken Seite. Bewegen Sie den gelben Pfeil-Zeiger zu einem anderen Zeitpunkt im Ausführungspfad Code ein. Verwenden Sie dann F5, oder einen Schrittbefehl weiter ausgeführt wird, die app aus.

![Verschieben der Ausführungszeiger](../debugger/media/dbg-tour-move-the-execution-pointer.gif "der Ausführungszeiger verschieben")

Durch eine Änderung der Ausführungsfluss, können Sie Aktionen wie Ausführungspfade für anderen Code zu testen, oder führen Sie Code erneut aus, ohne den Debugger neu gestartet.

> [!WARNING]
> Häufig müssen Sie mit dieser Funktion vorsichtig sein, und Sie eine Warnung in der QuickInfo angezeigt. Andere Warnungen, möglicherweise zu angezeigt werden. Verschieben den Zeiger kann nicht Ihre app in einem früheren Anwendungszustand wiederhergestellt werden.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Überwachen eines Objekts außerhalb des gültigen Bereichs liegt (c#, Visual Basic)

Es ist einfach, Variablen, die mithilfe der Debuggerfenster, z. B. Anzeigen der **Überwachen** Fenster. Jedoch, wenn eine Variable den Gültigkeitsbereich verlässt in der **Überwachen** Fenster können Sie feststellen, dass es abgeblendet ist. Der Wert einer Variablen kann in einigen app-Szenarien ändern, sogar, wenn sich die Variable außerhalb des gültigen Bereichs und möglicherweise sie beobachten möchten (z. B. eine Variable kann Garbage collection erhalten). Sie können die Variable verfolgen, indem eine Objekt-ID erstellen, er sich in der **Überwachen** Fenster.

#### <a name="to-create-an-object-id"></a>Um eine Objekt-ID zu erstellen.

1.  Legen Sie einen Haltepunkt in der Nähe eine Variable, die Sie nachverfolgen möchten.

2.  Starten Sie den Debugger (**F5**) und am Haltepunkt beendet.

3. Suchen Sie die Variable in der **"lokal"** Fenster (**Debuggen > Windows > "lokal"**) mit der rechten Maustaste auf die Variable, und wählen Sie **Objekt-ID**.

    ![Erstellen Sie eine Objekt-ID](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")
  
4.  Sie sollten ein **$** und eine Zahl im **Lokalfenster** einen Haltepunkt festlegen. Diese Variable ist die Objekt-ID.
  
5.  Die Objekt-ID-Variable Maustaste und wählen Sie **Überwachung hinzufügen**.

Weitere Informationen finden Sie unter [erstellen Sie eine Objekt-ID](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds).

## <a name="view-return-values-for-functions"></a>Anzeigen der Rückgabewerte für Funktionen

Betrachten Sie zum Anzeigen der Rückgabewerte für Funktionen die Funktionen, die in der **"Auto"** Fenster, während Sie über den Code schrittweise ausführen. Um den Rückgabewert einer Funktion anzuzeigen, stellen Sie sicher, dass die Funktion, die Sie von Interesse sind bereits ausgeführt wurde (drücken Sie **F10** einmal, wenn Sie auf den Funktionsaufruf derzeit beendet sind). Wenn das Fenster geschlossen wird, verwenden Sie **Debuggen > Windows > "Auto"** So öffnen die **"Auto"** Fenster.

![Fenster Fenster Auto](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

Darüber hinaus können Sie Funktionen in eingeben der **Direktfenster** Fenster zum Anzeigen der Rückgabewerte. (Öffnen Sie ihn mit **Debuggen > Windows > Direktfenster**.)

!["Direktfenster"](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

Können Sie auch [Pseudovariablen](../debugger/pseudovariables.md) in der **Überwachen** und **Direktfenster** Fenster, z. B. `$ReturnValue`.

## <a name="string_visualizer"></a>Überprüfen von Zeichenfolgen in einer Schnellansicht

Wenn Sie mit Zeichenfolgen arbeiten, kann es hilfreich, um die gesamte formatierte Zeichenfolge anzuzeigen sein. Klicken Sie zum Anzeigen einer nur-Text, XML, HTML oder JSON-Zeichenfolge auf das Lupensymbol ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Schnellansicht Symbol") beim mit dem Mauszeiger auf eine Variable, die einen Zeichenfolgenwert enthält.

![Öffnen Sie eine Zeichenfolgen-Schnellansicht](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

Eine Zeichenfolgen-Schnellansicht können Sie die herauszufinden, ob eine Zeichenfolge fehlerhaft ist, abhängig von der String-Datentyp ist. Angenommen, ein leerer **Wert** Feld zeigt die Zeichenfolge wird nicht erkannt, durch den Schnellansichttyp. Weitere Informationen finden Sie unter [Zeichenfolge Schnellansicht (Dialogfeld)](../debugger/string-visualizer-dialog-box.md).

![JSON-Zeichenfolgen-Schnellansicht](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

Für einigen andere Typen wie z. B. WPF-Objekte, die in den Debuggerfenstern angezeigt werden, können Sie auch Schnellansichten öffnen.

## <a name="break-into-code-on-handled-exceptions"></a>Unterbrechen Sie im Code auf behandelte Ausnahmen

Der Debugger unterbricht in Ihren Code auf nicht behandelte Ausnahmen. Allerdings behandelt Ausnahmen (z. B. Ausnahmen, die innerhalb von einer `try/catch` Block) kann auch eine Quelle von Fehlern, und Sie möchten untersuchen, wenn sie auftreten. Sie können konfigurieren, dass den Debugger zu unterbrechen Code für behandelte Ausnahmen als auch durch Konfigurieren von Optionen in der **Ausnahmeeinstellungen** (Dialogfeld). Öffnen Sie das Dialogfeld zu öffnen, indem auswählen **Debuggen > Windows > Ausnahmeeinstellungen**.

Die **Ausnahmeeinstellungen** Dialogfeld können Sie den Debugger zu unterbrechen von Code für bestimmte Ausnahmen zu informieren. In der Abbildung unten ist, unterbricht der Debugger in den Code immer eine `System.NullReferenceException` auftritt. Weitere Informationen finden Sie unter [Verwalten von Ausnahmen](../debugger/managing-exceptions-with-the-debugger.md).

![Das Dialogfeld "Einstellungen" Ausnahme](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Debuggen von Deadlocks und Racebedingungen

Wenn Sie die Arten von Problemen zu debuggen, Multithread-apps gemein befinden, müssen, ist es oft an den Speicherort des Threads während des Debuggens hilfreich. Hierzu können Sie einfach mit der **Threads in Quelle anzeigen** Schaltfläche.

#### <a name="to-show-threads-in-your-source-code"></a>Um Threads in Ihrem Quellcode anzuzeigen

1.  Während des Debuggens, klicken Sie auf die **Threads in Quelle anzeigen** Schaltfläche ![Threads in Quelle anzeigen](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") in der **Debuggen** Symbolleiste.
  
2.  Betrachten Sie den Bundsteg auf der linken Seite des Fensters. In dieser Zeile, die Sie sehen eine *Threadmarker* Symbol ![Threadmarker](../debugger/media/dbg-thread-marker.png "ThreadMarker") , das zwei Fäden ähnelt. Der Threadmarker gibt an, dass ein Thread an dieser Position angehalten wurde.

    Beachten Sie, dass ein Threadmarker teilweise durch einen Haltepunkt ausgeblendet werden kann.
  
3.  Zeigen Sie mit dem Mauszeiger auf den Threadmarker. Ein DataTip wird angezeigt. Anhand des DataTips erfahren Sie den Namen und die Thread-ID jedes angehaltenen Threads.

    Sie können auch den Speicherort der Threads im Anzeigen der [Fenster "Parallele Stapel"](../debugger/get-started-debugging-multithreaded-apps.md).

## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Untersuchen von Nutzlasten für Webdienste und Netzwerkressourcen (UWP)

UWP-apps können Sie analysieren, Netzwerkvorgängen mithilfe der `Windows.Web.Http` API. Sie können dieses Tool verwenden, um zum Debuggen von Webdiensten und Netzwerkressourcen. Wählen Sie zum Verwenden des Tools **Debuggen > Leistungsanalyse**. Wählen Sie **Netzwerk**, und wählen Sie dann **starten**. Durchlaufen Sie in Ihrer Anwendung das Szenario, das `Windows.Web.Http` verwendet, und wählen Sie anschließend **Auflistung beenden** aus, um einen Bericht zu generieren.

![Netzwerkauslastung-Profilerstellungstools](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

Wählen Sie einen Vorgang in der Ansicht „Zusammenfassung“ aus, um mehr Details anzuzeigen.

![Ausführliche Informationen in das Netzwerk-auslastungstool](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

Weitere Informationen finden Sie unter [Netzwerkverwendung](../profiling/network-usage.md).

## <a name="get-more-familiar-with-how-the-debugger-attaches-to-your-app"></a>Machen Sie mit wie verbindet sich der Debugger auf Ihre app mehr vertraut

Um an der ausgeführten app anfügen, lädt der Debugger Symboldateien (PDB) generierte Dateien für die exakt demselben Build der app, die Sie debuggen möchten. In einigen Szenarien kann ein wenig wissen Symboldateien hilfreich sein. Sie können überprüfen, wie Symboldateien, die mithilfe von Visual Studio lädt die **Module** Fenster.

Öffnen der **Module** Fenster während des Debuggens dazu **Debuggen > Windows > Module**. Die **Module** Fenster können Sie ermitteln, welche Module, die der Debugger wird als Benutzercode behandelt oder [ *mein Code*](../debugger/just-my-code.md), und das Symbol Status für das Modul geladen. In den meisten Szenarien der Debugger automatisch Symboldateien für Benutzercode findet, aber wenn Sie in Schritt (Debuggen) .NET Framework-Code, oder Systemcode Drittanbieter-Bibliothekscode möchten, sind zusätzliche Schritte erforderlich, um die richtigen Symboldateien abzurufen.

![Anzeigen von symbolischen Informationen im Fenster "Module"](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

Können Sie direkte Symbolinformationen laden die **Module** Fenster, indem Sie mit der rechten Maustaste und **Symbole laden**.

In manchen Fällen liefern app-Entwickler apps, ohne den übereinstimmenden Symboldateien (um den Speicherbedarf zu reduzieren), aber beibehalten, die eine Kopie des das entsprechende Symbol für den Build-Dateien, damit sie eine veröffentlichte Version später debuggen können.

Um herauszufinden, wie der Debugger Code als Benutzercode klassifiziert, finden Sie unter [nur mein Code](../debugger/just-my-code.md). Weitere Informationen zu Symboldateien finden Sie unter [angeben von Symbol(PDB)- und Quelldateien im Visual Studio-Debugger](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="learn-more"></a>Weitere Informationen

Zusätzliche Tipps und Tricks und ausführlichere Informationen finden Sie in folgenden Blogbeiträgen:

- [7 weniger bekannten Hackerangriffe für das Debuggen in Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2017/06/26/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [7 verborgenen Funktionen in Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2017/10/05/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Siehe auch
[Tastenkombinationen](../ide/tips-and-tricks-for-visual-studio.md)
