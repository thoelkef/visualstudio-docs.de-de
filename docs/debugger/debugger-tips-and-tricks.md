---
title: Tipps und Tricks im Debugger
description: Erfahren Sie mehr über einige der weniger bekannten Features, die vom Visual Studio-Debugger unterstützt werden.
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
ms.openlocfilehash: 61c1efea7340425090adbdd1c9bc865c4a056d42
ms.sourcegitcommit: 0e482cfc15f809b564c3de61646f29ecd7bfcba6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/14/2019
ms.locfileid: "70987764"
---
# <a name="learn-productivity-tips-and-tricks-for-the-debugger-in-visual-studio"></a>Erfahren Sie mehr über Produktivitäts Tipps und Tricks für den Debugger in Visual Studio

Lesen Sie dieses Thema, um einige Produktivitäts Tipps und Tricks für den Visual Studio-Debugger zu erlernen. Weitere Informationen zu den grundlegenden Funktionen des Debuggers finden Sie unter [der erste Einblick in den Debugger](../debugger/debugger-feature-tour.md). In diesem Thema werden einige Bereiche behandelt, die nicht in der Featuretour enthalten sind.

## <a name="pin-data-tips"></a>Tipps zur PIN-Daten

Wenn Sie während des Debuggens häufig auf Daten Tipps zeigen, sollten Sie den Datentipp für die Variable anheften, um Ihnen einen schnellen Zugriff zu verschaffen. Die Variable bleibt auch nach einem Neustart fixiert. Um den Datentipp anzuheften, klicken Sie auf das anheft Symbol, während Sie darauf zeigen. Sie können mehrere Variablen anheften.

Anheten ![eines Datentyps](../debugger/media/dbg-tips-data-tips-pinned.png "Pinningdatatip")

## <a name="edit-your-code-and-continue-debugging-c-vb-c"></a>Bearbeiten des Codes und Fortsetzen desC#Debuggens C++(, VB,)

In den meisten Sprachen, die von Visual Studio unterstützt werden, können Sie den Code in der Mitte einer Debugsitzung bearbeiten und das Debuggen fortsetzen. Wenn Sie dieses Feature verwenden möchten, klicken Sie auf den Code mit dem Cursor, während er im Debugger angehalten wurde, bearbeiten Sie die Bearbeitung, und drücken Sie **F5**, **F10**oder **F11** , um das Debuggen fortzusetzen.

![Debuggen bearbeiten und Fortfahren](../debugger/media/dbg-tips-edit-and-continue.gif "EDITANDCONTINUE")

Weitere Informationen zur Verwendung des Features und zu Funktions Beschränkungen finden Sie unter [Bearbeiten und Fortfahren](../debugger/edit-and-continue.md).

## <a name="edit-xaml-code-and-continue-debugging"></a>XAML-Code bearbeiten und Debuggen fortsetzen

Informationen zum Ändern von XAML-Code während einer Debugsitzung finden Sie unter [schreiben und Debuggen von XAML-Code mit XAML Hot Neuladen](xaml-hot-reload.md).

## <a name="debug-issues-that-are-hard-to-reproduce"></a>Debuggingprobleme, die schwer zu reproduzieren sind

Wenn es schwierig oder zeitaufwändig ist, einen bestimmten Zustand in der APP neu zu erstellen, sollten Sie Bedenken, ob die Verwendung eines bedingten halte Punkts hilfreich sein kann. Sie können [Bedingte Haltepunkte](../debugger/using-breakpoints.md#BKMK_Specify_a_breakpoint_condition_using_a_code_expression) verwenden und Breakpoints filtern, um das Unterbrechen des App-Codes zu vermeiden, bis die app in den gewünschten Zustand wechselt (z. b. ein Zustand, in dem eine Variable ungültige Daten speichert). Sie können Bedingungen mithilfe von Ausdrücken, Filtern, Treffer Zählungen usw. festlegen.

#### <a name="to-create-a-conditional-breakpoint"></a>So erstellen Sie einen bedingten Haltepunkt

1. Klicken Sie mit der rechten Maustaste auf ein Haltepunkt Symbol (die rote Kugel), und wählen Sie **Bedingungen**aus.

2. Geben Sie im Fenster halte **Punkt Einstellungen** einen Ausdruck ein.

    ![Bedingter Haltepunkt](../debugger/media/dbg-multithreaded-conditional-breakpoint.png "Conditionalbreakpoint")

3. Wenn Sie an einer anderen Art von Bedingung interessiert sind, wählen Sie im Dialogfeld halte **Punkt Einstellungen** die Option anstelle von **bedingtem Ausdruck** **Filtern** aus, und befolgen Sie dann die filtertipps.

## <a name="configure-the-data-to-show-in-the-debugger"></a>Konfigurieren der Daten, die im Debugger angezeigt werden sollen

Für C#, Visual Basic und ( C++ C++nur/CLI-Code) können Sie dem Debugger mitteilen, welche Informationen mit dem [DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md) -Attribut angezeigt werden sollen. Für C++ Code können Sie mit [natvis-Visualisierungen](create-custom-views-of-native-objects.md)identisch Vorgehen.

## <a name="change-the-execution-flow"></a>Ändern des Ausführungsablaufs

Wenn der Debugger in einer Codezeile angehalten wurde, verwenden Sie die Maus, um den gelben Pfeil Zeiger auf der linken Seite zu drücken. Bewegen Sie den gelben Pfeil Zeiger an einen anderen Punkt im Code Ausführungs Pfad. Anschließend verwenden Sie F5 oder einen Schritt Befehl, um die Ausführung der APP fortzusetzen.

![Verschieben des Ausführungs Zeigers](../debugger/media/dbg-tour-move-the-execution-pointer.gif "Verschieben des Ausführungs Zeigers")

Durch Ändern des Ausführungsablaufs können Sie Aktionen ausführen wie das Testen verschiedener Pfade für die Codeausführung oder das erneute Ausführen von Code ohne Neustarten des Debuggers.

> [!WARNING]
> Bei dieser Funktion müssen Sie häufig vorsichtig vorgehen. Sie werden durch eine Warnung in der QuickInfo auf Probleme aufmerksam gemacht. Möglicherweise werden Ihnen auch andere Warnungen angezeigt. Wenn Sie den Zeiger verschieben, kann Ihre APP nicht auf einen früheren Anwendungs Status zurückgesetzt werden.

## <a name="track-an-out-of-scope-object-c-visual-basic"></a>Nachverfolgen eines Objekts außerhalb des Gültigkeits BereichsC#(, Visual Basic)

Es ist einfach, Variablen mit Debuggerfenstern wie dem Fenster über **Wachen** anzuzeigen. Wenn jedoch eine Variable den Gültigkeitsbereich im **Überwachungs** Fenster verlässt, werden Sie möglicherweise bemerken, dass Sie ausgegraut ist. In einigen App-Szenarien kann sich der Wert einer Variablen ändern, auch wenn die Variable außerhalb des gültigen Bereichs liegt, und Sie möchten Sie möglicherweise genau ansehen (z. b. kann eine Variable in die Garbage Collection aufgenommen werden). Sie können die Variable nachverfolgen, indem Sie im **Überwachungs** Fenster eine Objekt-ID dafür erstellen.

#### <a name="to-create-an-object-id"></a>So erstellen Sie eine Objekt-ID

1. Legen Sie einen Haltepunkt in der Nähe einer Variablen fest, die Sie nachverfolgen möchten.

2. Starten Sie den Debugger (**F5**), und brechen Sie am Haltepunkt ab.

3. Suchen **Sie die Variable im Fenster Lokal** (**Debuggen > Fenster >** lokal), klicken Sie mit der rechten Maustaste auf die Variable, und wählen Sie **Objekt-ID erstellen**aus.

    ![Erstellen einer Objekt-ID] " (../debugger/media/dbg-tips-watch-create-object-id.png "Kreateobjectid") "

4. Sie sollten ein **$** und eine Zahl im **Lokalfenster** einen Haltepunkt festlegen. Diese Variable ist die Objekt-ID.

5. Klicken Sie mit der rechten Maustaste auf die Variable Objekt-ID und wählen Sie **Überwachung hinzufügen**

Weitere Informationen finden Sie unter [Erstellen einer Objekt-ID](../debugger/watch-and-quickwatch-windows.md#bkmk_objectIds).

## <a name="view-return-values-for-functions"></a>Anzeigen von Rückgabe Werten für Funktionen

Wenn Sie Rückgabewerte für ihre Funktionen anzeigen möchten, sehen Sie sich die Funktionen an **, die im Fenster Auto** angezeigt werden, während Sie den Code schrittweise durchlaufen. Wenn Sie den Rückgabewert für eine Funktion anzeigen möchten, stellen Sie sicher, dass die Funktion, an der Sie interessiert sind, bereits ausgeführt wurde (drücken Sie die **Taste F10** , wenn Sie den Funktionsbefehl gerade beendet haben). Wenn das Fenster geschlossen ist, verwenden Sie **Debuggen > Windows >** Auto, **um das Fenster** Auto zu öffnen.

![Autos Window](../debugger/media/dbg-tips-autos-window.png "AutosWindow")

Außerdem können Sie Funktionen im **direkt** Fenster eingeben, um Rückgabewerte anzuzeigen. (Öffnen Sie ihn mit **debug> Fenster > direkt**.)

![Direkt Fenster](../debugger/media/dbg-tips-immediate-window.png "Unmittelfenster")

Sie können auch [Pseudo Variablen](../debugger/pseudovariables.md) im Fenster "über **Wachen** " und " **direkt** " verwenden `$ReturnValue`, z. b.

## <a name="string_visualizer"></a>Überprüfen von Zeichen folgen in einer Schnellansicht

Beim Arbeiten mit Zeichen folgen kann es hilfreich sein, die gesamte formatierte Zeichenfolge anzuzeigen. Wenn Sie eine nur-Text-, XML-, HTML-oder JSON-Zeichenfolge anzeigen möchten, klicken Sie auf das Lupensymbol ![visualizericon](../debugger/media/dbg-tips-visualizer-icon.png "Visualizer Icon") , während Sie auf eine Variable mit einem Zeichen folgen Wert zeigen.

![Öffnen einer Zeichen] folgen Schnellansicht (../debugger/media/dbg-tips-string-visualizers.png "Openstringvisualizer")

Mithilfe einer Zeichen folgen Schnellansicht können Sie abhängig vom Typ der Zeichenfolge ermitteln, ob eine Zeichenfolge falsch formatiert ist. Ein leeres **Wertfeld** gibt beispielsweise an, dass die Zeichenfolge vom Typ der Schnellansicht nicht erkannt wird. Weitere Informationen finden Sie unter [Dialog Feld "Zeichen](../debugger/string-visualizer-dialog-box.md)folgen Schnellansicht".

![JSON-Zeichen] folgen Schnellansicht (../debugger/media/dbg-tips-string-visualizer-json.png "Jsonstringvisualizer")

Für einige andere Typen, wie z. b. DataSet-und Datentabelle-Objekte, die in den Debuggerfenstern angezeigt werden, können Sie auch eine integrierte Schnellansicht öffnen.

## <a name="break-into-code-on-handled-exceptions"></a>Unterbrechen von Code für behandelte Ausnahmen

Der Debugger unterbricht den Code bei nicht behandelten Ausnahmen. Behandelte Ausnahmen (z. b. Ausnahmen, die innerhalb eines `try/catch` -Blocks auftreten) können jedoch auch eine Fehlerquelle sein, und Sie können untersuchen, wann Sie auftreten. Sie können den Debugger so konfigurieren, dass der Code für behandelte Ausnahmen unterteilt wird, indem Sie Optionen im Dialogfeld **Ausnahme Einstellungen** konfigurieren. Öffnen Sie dieses Dialogfeld, indem Sie **Debuggen > Windows > Ausnahme Einstellungen**auswählen.

Im Dialogfeld **Ausnahme Einstellungen** können Sie den Debugger anweisen, den Code für bestimmte Ausnahmen zu unterbrechen. In der Abbildung unten unterbricht der Debugger den Code, wenn ein `System.NullReferenceException` auftritt. Weitere Informationen finden Sie unter [Verwalten von Ausnahmen](../debugger/managing-exceptions-with-the-debugger.md).

![Dialog Feld "Ausnahme Einstellungen] " (../debugger/media/dbg-tips-exception-settings.png "Exceptionsettingsdialogbox")

## <a name="debug-deadlocks-and-race-conditions"></a>Deadlocks und Racebedingungen Debuggen

Wenn Sie die Arten von Problemen Debuggen müssen, die bei Multithreadanwendungen häufig vorkommen, ist es häufig hilfreich, den Speicherort der Threads während des Debuggens anzuzeigen. Dies kann problemlos mithilfe der Schaltfläche **Threads in Quelle anzeigen** durchzuführen sein.

#### <a name="to-show-threads-in-your-source-code"></a>So zeigen Sie Threads in Ihrem Quellcode an

1. Klicken Sie beim Debuggen auf die Schaltfläche **Threads in Quelle anzeigen** , und klicken Sie auf der Symbolleiste **Debuggen** ![auf](../debugger/media/dbg-multithreaded-show-threads.png "Thread Marker") anzeigen

2. Betrachten Sie den Bundsteg auf der linken Seite des Fensters. In dieser Zeile sehen Sie ein *Thread* Marker-Symbol ![Thread]Marker(../debugger/media/dbg-thread-marker.png "Threadmarker") , der zwei tuchthreads ähnelt. Der Threadmarker gibt an, dass ein Thread an dieser Position angehalten wurde.

    Beachten Sie, dass ein Thread Marker möglicherweise teilweise durch einen Haltepunkt verborgen ist.

3. Zeigen Sie mit dem Mauszeiger auf den Threadmarker. Ein DataTip wird angezeigt. Anhand des DataTips erfahren Sie den Namen und die Thread-ID jedes angehaltenen Threads.

    Sie können auch den Speicherort der Threads im [Fenster parallele Stapel](../debugger/get-started-debugging-multithreaded-apps.md)anzeigen.

## <a name="examine-payloads-for-web-services-and-network-resources-uwp"></a>Überprüfen von Nutzlasten für Webdienste und Netzwerkressourcen (UWP)

In UWP-Apps können Sie mithilfe der `Windows.Web.Http` -API ausgeführte Netzwerk Vorgänge analysieren. Sie können dieses Tool verwenden, um Webdienste und Netzwerkressourcen zu debuggen. Wählen Sie **> leistungsprofiler Debuggen**, um das Tool zu verwenden. Wählen Sie **Netzwerk**aus, und klicken Sie dann auf **starten**. Durchlaufen Sie in Ihrer Anwendung das Szenario, das `Windows.Web.Http` verwendet, und wählen Sie anschließend **Auflistung beenden** aus, um einen Bericht zu generieren.

![Tool zur Netzwerk Verwendungs Profilerstellung](../profiling/media/prof-tour-network-usage.png "Networkusageproftool")

Wählen Sie einen Vorgang in der Ansicht „Zusammenfassung“ aus, um mehr Details anzuzeigen.

![Ausführliche Informationen im Netzwerk Verwendungs Tool](../profiling/media/prof-tour-network-usage-details.png "Detailedviewnetworkusage")

Weitere Informationen finden Sie unter [Netzwerkverwendung](../profiling/network-usage.md).

## <a name="modules_window"></a>Informieren Sie sich darüber, wie der Debugger an Ihre APP angefügt wird (C#, F# C++, Visual Basic,)

Zum Anfügen an die laufende App lädt der Debugger Symbol Dateien (. pdb), die für genau denselben Build der APP generiert werden, die Sie debuggen möchten. In einigen Szenarien kann es hilfreich sein, Symbol Dateien zu kennen. Sie können untersuchen, wie Visual Studio Symbol Dateien mit dem Fenster **Module** lädt.

Öffnen Sie das Fenster **Module** beim Debuggen, indem Sie **Debuggen > Windows > Module**auswählen Das Fenster " **Module** " kann Aufschluss darüber [*geben, welche*](../debugger/just-my-code.md)Module der Debugger als Benutzercode behandelt, und den Symbol Ladestatus für das Modul. In den meisten Szenarien findet der Debugger automatisch Symbol Dateien für Benutzercode, aber wenn Sie .NET Framework-Code, Systemcode oder Drittanbieter-Bibliotheks Code schrittweise ausführen (oder Debuggen) möchten, sind zusätzliche Schritte erforderlich, um die richtigen Symbol Dateien zu erhalten.

![Anzeigen von Symbol Informationen im Fenster "Module] " (../debugger/media/dbg-tips-modules-window.png "Viewsymbolinformation")

Sie können Symbol Informationen direkt aus dem Fenster **Module** laden, indem Sie mit der rechten Maustaste klicken und **Symbole laden**auswählen.

Manchmal liefern App-Entwickler apps ohne übereinstimmende Symbol Dateien (um den Speicherbedarf zu reduzieren), behalten jedoch eine Kopie der übereinstimmenden Symbol Dateien für den Build bei, damit Sie eine veröffentlichte Version später Debuggen können.

Informationen dazu, wie der Debugger Code als Benutzercode klassifiziert, finden Sie unter [nur eigenen Code](../debugger/just-my-code.md). Weitere Informationen zu Symbol Dateien finden Sie unter [Angeben von Symbol Dateien (PDB) und Quelldateien im Visual Studio-Debugger](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="learn-more"></a>Weitere Informationen

Weitere Tipps und Tricks sowie ausführlichere Informationen finden Sie in den folgenden Blogbeiträgen:

- [7 weniger bekannte Hacks für das Debuggen in Visual Studio](https://devblogs.microsoft.com/visualstudio/7-lesser-known-hacks-for-debugging-in-visual-studio/)
- [7 Verborgene Juwelen in Visual Studio](https://devblogs.microsoft.com/visualstudio/7-hidden-gems-in-visual-studio-2017/)

## <a name="see-also"></a>Siehe auch

[Tastenkombinationen](../ide/productivity-shortcuts.md)
