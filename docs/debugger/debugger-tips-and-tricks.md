---
title: Tipps und Tricks im Debugger
description: Erfahren Sie mehr über einige der weniger bekannten Features, die vom Visual Studio-Debugger unterstützt werden
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
ms.openlocfilehash: bf8d6df020694bb10fe4f3f051551056549d5673
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301176"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Erfahren Sie produktivitätstipps und -tricks für den Debugger in Visual Studio

Lesen Sie dieses Thema, um einige Produktivitätstipps und -tricks für den Visual Studio-Debugger zu erfahren. Einen Blick auf die grundlegenden Features des Debuggers finden Sie unter [Erster Blick auf den Debugger](../debugger/debugger-feature-tour.md). In diesem Thema behandeln wir einige Bereiche, die nicht in der Feature-Tour enthalten sind.

## <a name="pin-data-tips"></a>Pin-Daten-Tipps

Wenn Sie häufig beim Debuggen mit dem Mauszeiger auf Datentipps zeigen, können Sie den Datentipp für die Variable anheften, um sich schnell zugreifen zu können. Die Variable bleibt auch nach dem Neustart angeheftet. Um die Datenspitze anzuheften, klicken Sie auf das Pin-Symbol, während Sie mit der Maus darauf bewegen. Sie können mehrere Variablen anheften.

![Anheften eines Datentipps](../debugger/media/dbg-tips-data-tips-pinned.png "PinningDataTip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Bearbeiten Sie Den Code, und fahren Sie mit dem Debuggen fort (C-, VB-, C++-)

In den meisten Sprachen, die von Visual Studio unterstützt werden, können Sie den Code während einer Debugsitzung bearbeiten und das Debuggen fortsetzen. Wenn Sie dieses Feature verwenden möchten, klicken Sie mit dem Cursor auf den Code, während dieser im Debugger angehalten wurde, und bearbeiten Sie diesen. Drücken Sie **F5**, **F10** oder **F11**, um das Debuggen fortzusetzen.

![Bearbeiten und Fortsetzen des Debuggens](../debugger/media/dbg-tips-edit-and-continue.gif "EditAndContinue")

Weitere Informationen zur Verwendung des Features finden Sie unter [Bearbeiten und Fortsetzen](../debugger/edit-and-continue.md).

## <a name="edit-xaml-code-and-continue-debugging"></a>Bearbeiten von XAML-Code und Fortsetzen des Debuggens

Weitere Informationen zum Ändern von XAML-Code während einer Debugsitzung finden Sie unter [Schreiben und Debuggen von ausgeführtem XAML-Code durch Neuladen von XAML im laufenden Betrieb](../xaml-tools/xaml-hot-reload.md).

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Debugprobleme, die schwer reproduziert werden können

Wenn es schwierig oder zeitaufwändig ist, einen bestimmten Status in Ihrer App neu zu erstellen, sollten Sie überlegen, ob die Verwendung eines bedingten Haltepunkts hilfreich sein kann. Sie können [bedingte Haltepunkte](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) und Filterhaltepunkte verwenden, um zu vermeiden, dass in Ihren App-Code überbrolungen wird, bis die App in einen gewünschten Zustand wechselt (z. B. einen Zustand, in dem eine Variable fehlerhafte Daten speichert). Sie können Bedingungen mithilfe von Ausdrücken, Filtern, Trefferzahlen usw. festlegen.

#### <a name="to-create-a-conditional-breakpoint"></a>So erstellen Sie einen bedingten Haltepunkt

1. Klicken Sie mit der rechten Maustaste auf ein Haltepunktsymbol (die rote Kugel) und wählen Sie **Bedingungen**.

2. Geben Sie im Fenster **Haltepunkteinstellungen** einen Ausdruck ein.

    ![Bedingter Haltepunkt](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "ConditionalBreakpoint")

3. Wenn Sie an einem anderen Zustandstyp interessiert sind, wählen Sie im Dialogfeld **Haltepunkteinstellungen** **filter** statt **bedingter Ausdruck** aus, und folgen Sie dann den Filtertipps.

## <a name="configure-the-data-to-show-in-the-debugger"></a>Konfigurieren der Daten, die im Debugger angezeigt werden sollen

Sie können dem Debugger mitteilen, welche Informationen mithilfe des [DebuggerDisplay-Attributs](../debugger/using-the-debuggerdisplay-attribute.md) angezeigt werden sollen. Für C++-Code können Sie dasselbe mit [Natvis-Visualisierungen](create-custom-views-of-native-objects.md)tun.

## <a name="change-the-execution-flow"></a>Ändern des Ausführungsablaufs

Wenn der Debugger in einer Codezeile angehalten wird, verwenden Sie die Maus, um den gelben Pfeilzeiger auf der linken Seite zu greifen. Bewegen Sie den gelben Pfeilzeiger an einen anderen Punkt im Codeausführungspfad. Anschließend verwenden Sie F5 oder einen Schrittbefehl, um die App weiter auszuführen.

![Verschieben des Ausführungszeigers](../debugger/media/dbg-tour-move-the-execution-pointer.gif "Verschieben des Ausführungszeigers")

Durch Ändern des Ausführungsablaufs können Sie Aktionen ausführen wie das Testen verschiedener Pfade für die Codeausführung oder das erneute Ausführen von Code ohne Neustarten des Debuggers.

> [!WARNING]
> Bei dieser Funktion müssen Sie häufig vorsichtig vorgehen. Sie werden durch eine Warnung in der QuickInfo auf Probleme aufmerksam gemacht. Möglicherweise werden Ihnen auch andere Warnungen angezeigt. Durch Verschieben des Zeigers kann die App nicht in einen früheren Anwendungsstatus zurückgesetzt werden.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Nachverfolgen eines Objekts anicht im Gültigkeitsbereich (C-, Visual Basic)

Es ist einfach, Variablen mithilfe von Debuggerfenstern wie dem **Überwachungsfenster** anzuzeigen. Wenn jedoch eine Variable im **Überwachungsfenster** aus dem Gültigkeitsbereich verschwindet, stellen Sie möglicherweise fest, dass sie ausgegraut ist. In einigen App-Szenarien kann sich der Wert einer Variablen ändern, auch wenn die Variable anicht mehr zum Gültigkeitsbereich gehört, und Sie möchten sie möglicherweise genau beobachten (z. B. kann eine Variable Garbage Collection erhalten). Sie können die Variable nachverfolgen, indem Sie im **Überwachungsfenster** eine Objekt-ID dafür erstellen.

#### <a name="to-create-an-object-id"></a>So erstellen Sie eine Objekt-ID

1. Legen Sie einen Haltepunkt in der Nähe einer Variablen fest, die Sie nachverfolgen möchten.

2. Starten Sie den Debugger (**F5**) und stoppen Sie den Haltepunkt.

3. Suchen Sie die Variable im Fenster **"Lokals"** (**Debug> Windows > Locals**), klicken Sie mit der rechten Maustaste auf die Variable, und wählen Sie **Objekt-ID erstellen**aus.

    ![Erstellen einer Objekt-ID](../debugger/media/dbg-tips-watch-create-object-id.png "CreateObjectID")

4. Im Fenster **$** **"Locals"** sollte eine Pluszahl angezeigt werden. Diese Variable ist die Objekt-ID.

5. Klicken Sie mit der rechten Maustaste auf die Objekt-ID-Variable, und wählen Sie **Watch hinzufügen**aus.

Weitere Informationen finden Sie unter [Erstellen einer Objekt-ID](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds).

## <a name="view-return-values-for-functions"></a>Rückgabewerte für Funktionen anzeigen

Um Rückgabewerte für Ihre Funktionen anzuzeigen, sehen Sie sich die Funktionen an, die im **Fenster Autos** angezeigt werden, während Sie den Code durchlaufen. Um den Rückgabewert für eine Funktion anzuzeigen, stellen Sie sicher, dass die Funktion, an der Sie interessiert sind, bereits ausgeführt wurde (drücken Sie **F10** einmal, wenn Sie derzeit beim Funktionsaufruf angehalten sind). Wenn das Fenster geschlossen ist, verwenden Sie **Debug-> Windows > Autos,** um das **Fenster "Autos"** zu öffnen.

![Fenster „Auto“](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

Darüber hinaus können Sie Funktionen im **Direktfenster** eingeben, um Rückgabewerte anzuzeigen. (Öffnen Sie es mit **Debug > Windows > Immediate**.)

![Direktfenster](../debugger/media/dbg-tips-immediate-window.png "ImmediateWindow")

Sie können auch [Pseudovariablen](../debugger/pseudovariables.md) im Fenster **Uhr** `$ReturnValue`und **Sofort** verwenden, z. B. .

## <a name="inspect-strings-in-a-visualizer"></a><a name="string_visualizer"></a>Überprüfen von Zeichenfolgen in einer Visualisierung

Wenn Sie mit Zeichenfolgen arbeiten, kann es hilfreich sein, die gesamte formatierte Zeichenfolge anzuzeigen. Um eine Nur-Text-, XML-, HTML- oder JSON-Zeichenfolge anzuzeigen, klicken Sie auf das Lupensymbol ![VisualizerIcon,](../debugger/media/dbg-tips-visualizer-icon.png "Visualizer-Symbol") während Sie den Mauszeiger über eine Variable bewegen, die einen Zeichenfolgenwert enthält.

![Öffnen eines String Visualizers](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

Eine Zeichenfolgenvisualisierung kann Ihnen helfen, je nach Zeichenfolgentyp herauszufinden, ob eine Zeichenfolge falsch formatiert ist. Ein leeres **Wertfeld** gibt beispielsweise an, dass die Zeichenfolge vom Visualisierungstyp nicht erkannt wird. Weitere Informationen finden Sie im [Dialogfeld String Visualizer](../debugger/string-visualizer-dialog-box.md).

![JSON String Visualizer](../debugger/media/dbg-tips-string-visualizer-json.png "JSONStringVisualizer")

Für einige andere Typen wie DataSet- und DataTable-Objekte, die in den Debuggerfenstern angezeigt werden, können Sie auch eine integrierte Visualisierung öffnen.

## <a name="break-into-code-on-handled-exceptions"></a>Auf Schlüsselcode für behandelte Ausnahmen einbrechen

Der Debugger wird bei nicht behandelten Ausnahmen in ihren Code eingefügt. Behandelte Ausnahmen (z. B. Ausnahmen, `try/catch` die innerhalb eines Blocks auftreten) können jedoch auch eine Quelle von Fehlern sein, und Sie sollten untersuchen, wann sie auftreten. Sie können den Debugger so konfigurieren, dass er auch in Code für behandelte Ausnahmen aufbricht, indem Sie Optionen im Dialogfeld **Ausnahmeeinstellungen** konfigurieren. Öffnen Sie dieses Dialogfeld, indem Sie **> Windows > Ausnahmeeinstellungen debuggen**auswählen.

Im Dialogfeld **Ausnahmeeinstellungen** können Sie den Debugger anweisen, für bestimmte Ausnahmen in Code einzubrechen. In der folgenden Abbildung wird der Debugger `System.NullReferenceException` bei auftretender Zeit in den Code eingebrochen. Weitere Informationen finden Sie unter [Verwalten von Ausnahmen](../debugger/managing-exceptions-with-the-debugger.md).

![Dialogfeld "Ausnahmeeinstellungen"](../debugger/media/dbg-tips-exception-settings.png "ExceptionSettingsDialogBox")

## <a name="debug-deadlocks-and-race-conditions"></a>Debug-Deadlocks und Race-Bedingungen

Wenn Sie die Arten von Problemen debuggen müssen, die bei Multithread-Apps auftreten, hilft es häufig, den Speicherort von Threads während des Debuggens anzuzeigen. Sie können dies ganz einfach mit der Schaltfläche **Threads in Quelle anzeigen** tun.

#### <a name="to-show-threads-in-your-source-code"></a>So zeigen Sie Threads im Quellcode an

1. Klicken Sie beim Debuggen in der **Symbolleiste Debuggen** auf die Schaltfläche **Threads in Quelle** anzeigen auf Threads anzeigen in ![Quelle](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") anzeigen.

2. Betrachten Sie den Bundsteg auf der linken Seite des Fensters. In dieser Zeile wird ein *Threadmarker-Symbol* ![Thread Marker](../debugger/media/dbg-thread-marker.png "ThreadMarker") angezeigt, das zwei Stofffäden ähnelt. Der Threadmarker gibt an, dass ein Thread an dieser Position angehalten wurde.

    Beachten Sie, dass eine Threadmarkierung möglicherweise teilweise durch einen Haltepunkt verdeckt wird.

3. Zeigen Sie mit dem Mauszeiger auf den Threadmarker. Ein DataTip wird angezeigt. Anhand des DataTips erfahren Sie den Namen und die Thread-ID jedes angehaltenen Threads.

    Sie können auch die Position von Threads im [Fenster Parallel Stacks](../debugger/get-started-debugging-multithreaded-apps.md)anzeigen.

::: moniker range="vs-2017"
## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Überprüfen der Nutzlasten für Webdienste und Netzwerkressourcen (UWP)

In UWP-Apps können Sie Netzwerkvorgänge `Windows.Web.Http` analysieren, die mit der API ausgeführt werden. Mit diesem Tool können Sie Webdienste und Netzwerkressourcen debuggen. Um das Tool zu verwenden, wählen Sie **Debug> Performance Profiler**. Wählen Sie **Netzwerk**aus, und wählen Sie dann **Start**aus. Durchlaufen Sie in Ihrer Anwendung das Szenario, das `Windows.Web.Http` verwendet, und wählen Sie anschließend **Auflistung beenden** aus, um einen Bericht zu generieren.

![Profilerstellungstool „Netzwerkauslastung“](../profiling/media/prof-tour-network-usage.png "NetworkUsageProfTool")

Wählen Sie einen Vorgang in der Ansicht „Zusammenfassung“ aus, um mehr Details anzuzeigen.

![Ausführliche Informationen im Tool „Netzwerkauslastung“](../profiling/media/prof-tour-network-usage-details.png "DetailedViewNetworkUsage")

Weitere Informationen finden Sie unter [Netzwerkverwendung](../profiling/network-usage.md).
::: moniker-end

## <a name="get-more-familiar-with-how-the-debugger-attaches-to-your-app-c-c-visual-basic-f"></a><a name="modules_window"></a>Machen Sie sich besser mit der Anfübeung des Debuggers an Ihre App (C, C++, Visual Basic, F) vertraut.

Um an Ihre ausgeführte App anzufügen, lädt der Debugger Symboldateien (.pdb), die für genau den gleichen Build der App generiert wurden, die Sie debuggen möchten. In einigen Szenarien kann ein wenig Wissen über Symboldateien hilfreich sein. Sie können anhand des **Fensters Modules** untersuchen, wie Visual Studio Symboldateien lädt.

Öffnen Sie das Fenster Module während des **Debuggens,** indem Sie **Debuggen > Windows > Modules**auswählen. Im Fenster **Module** können Sie erkennen, welche Module der Debugger als Benutzercode behandelt, oder [*Mein Code*](../debugger/just-my-code.md)und der Status des Symbolladestatus für das Modul. In den meisten Szenarien findet der Debugger automatisch Symboldateien für Benutzercode, aber wenn Sie in .NET-Code, Systemcode oder Bibliothekscode von Drittanbietern eindringen (oder debuggen) möchten, sind zusätzliche Schritte erforderlich, um die richtigen Symboldateien zu erhalten.

![Symbolinformationen im Fenster Module anzeigen](../debugger/media/dbg-tips-modules-window.png "ViewSymbolInformation")

Sie können Symbolinformationen direkt aus dem **Fenster Module laden,** indem Sie mit der rechten Maustaste klicken und **Symbole laden**auswählen.

Manchmal versenden App-Entwickler Apps ohne die passenden Symboldateien (um den Platzbedarf zu reduzieren), behalten jedoch eine Kopie der übereinstimmenden Symboldateien für den Build bei, damit sie später eine freigegebene Version debuggen können.

Informationen dazu, wie der Debugger Code als Benutzercode klassifiziert, finden Sie unter [Nur mein Code](../debugger/just-my-code.md). Weitere Informationen zu Symboldateien finden Sie unter [Symbol (.pdb) und Quelldateien im Visual Studio-Debugger](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)angeben .

## <a name="learn-more"></a>Weitere Informationen

Weitere Tipps und Tricks und detailliertere Informationen finden Sie in diesen Blogbeiträgen:

- [7 weniger bekannte Hacks für das Debuggen in Visual Studio](https://devblogs.microsoft.com/visualstudio/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [7 versteckte Edelsteine in Visual Studio](https://devblogs.microsoft.com/visualstudio/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Weitere Informationen

[Tastaturbefehle](../ide/productivity-shortcuts.md)
