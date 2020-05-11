---
title: Debuggen einer Multithread-App
description: Debuggen mithilfe des Fensters Threads und der Symbolleiste Debugspeicherort in Visual Studio
ms.date: 02/14/2020
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multithreaded debugging, tutorial
- tutorials, multithreaded debugging
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb7b7850d8d7582110152d248683f89981933215
ms.sourcegitcommit: 6ef52c2030b37ea7a64fddb32f050ecfb77dd918
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416372"
---
# <a name="walkthrough-debug-a-multithreaded-app-using-the-threads-window-c-visual-basic-c"></a>Exemplarische Vorgehensweise: Debuggen einer multithreadapp mithilfeC#des Fensters " C++Threads" (, Visual Basic,)

Mehrere Visual Studio-Benutzeroberflächen Elemente helfen Ihnen beim Debuggen von Multithread-apps. In diesem Artikel werden multithreaddebuggingfunktionen im Fenster "Code-Editor", " **Debugspeicherort** " und " **Thread** " Weitere Informationen zu anderen Tools zum Debuggen von Multithread-apps finden [Sie unter Get Started Debugging Multithread apps](../debugger/get-started-debugging-multithreaded-apps.md).

Das Abschließen dieses Lernprogramms dauert nur einige Minuten und vermittelt Ihnen die Grundlagen des Debuggens von Multithread-apps.

## <a name="create-a-multithreaded-app-project"></a>Erstellen eines Multithread-App-Projekts

Erstellen Sie das folgende Multithread-App-Projekt für die Verwendung in diesem Tutorial:

1. Öffnen Sie Visual Studio, und erstellen Sie ein neues Projekt.

   ::: moniker range=">=vs-2019"

   Wenn das Startfenster nicht geöffnet ist, klicken Sie auf **Datei** > **Startfenster**.

   Wählen Sie im Startfenster **Neues Projekt erstellen** aus.

   Geben Sie im Fenster **Neues Projekt erstellen** im Suchfeld *Konsole* ein. Wählen Sie **C#** als nächstes **C++** oder in der Liste Sprache aus, und wählen Sie dann in der Liste Plattform die Option **Windows** aus. 

   Nachdem Sie die Sprach-und Platt Form Filter angewendet haben, wählen Sie die **Konsolen-app (.net Core)** oder für Konsolen- C++ **App** -Vorlage aus, und klicken Sie dann auf **weiter**.

   > [!NOTE]
   > Wenn die richtige Vorlage nicht angezeigt **wird, navigieren Sie zu Extras** > **Tools und Features anzeigen...** , um die Visual Studio-Installer zu öffnen. Wählen Sie die Workload **.NET-Desktopentwicklung*** oder **Desktopentwicklung mit C++** und anschließend **Ändern** aus.

   Geben Sie im Fenster **Neues Projekt konfigurieren** im Feld **Projektname den Namen** " *mythleswalkyghapp* " ein, oder geben Sie ihn ein. Wählen Sie anschließend **Erstellen** aus.

   ::: moniker-end
   ::: moniker range="vs-2017"
   Klicken Sie in der Menüleiste im oberen Bereich auf **Datei** > **Neu** > **Projekt**. Wählen Sie im linken Bereich des Dialog Felds **Neues Projekt** die folgenden Optionen aus:

   - Wählen Sie C# für eine-APP unter **Visual C#** den **Windows-Desktop**aus, und wählen Sie dann im mittleren Bereich die Option **Konsolen-app (.NET Framework)** aus.
   - Wählen Sie C++ für eine-APP unter **Visual C++** den **Windows-Desktop**aus, und wählen Sie dann **Windows-Konsolenanwendung**aus.

   Wenn Sie die Konsolen- **app (.net Core)** oder C++für die **Konsolen-App** -Projektvorlage nicht sehen, wechseln **Sie zu Extras** > **Tools und Features anzeigen...** , um die Visual Studio-Installer zu öffnen. Wählen Sie die Workload **.NET-Desktopentwicklung*** oder **Desktopentwicklung mit C++** und anschließend **Ändern** aus.

   Geben Sie dann einen Namen wie " *mythleswalkyghapp* " ein, und klicken Sie auf **OK**.

   Wählen Sie **OK**.
   ::: moniker-end

   Ein neues Konsolenprojekt wird angezeigt. Nachdem das Projekt erstellt wurde, wird eine Quelldatei angezeigt. Abhängig von der Sprache, die Sie ausgewählt haben, kann die Quelldatei " *Program.cs*", " *mythleswalkyghapp. cpp*" oder " *Module1. vb*" genannt werden.

1. Ersetzen Sie den Code in der Quelldatei durch C# den C++ -oder-Beispielcode aus " [Get Started Debugging Multithread apps](../debugger/get-started-debugging-multithreaded-apps.md)".

1. Wählen Sie **Datei** > **Alle speichern** aus.

## <a name="start-debugging"></a>Starten des Debugvorgangs

1. Suchen Sie im Quellcode nach den folgenden Zeilen:

   ```csharp
   Thread.Sleep(3000);
   Console.WriteLine();
   ```

   ```C++
   Thread::Sleep(3000);
   Console.WriteLine();
   ```

1. Legen Sie einen Haltepunkt in der `Console.WriteLine();` Zeile fest, indem Sie auf das linke bundbundfeld klicken, oder wählen Sie die Zeile aus, und drücken Sie **F9**.

   Der Haltepunkt wird als roter Kreis auf der linken Seite neben der Codezeile angezeigt.

1. Wählen Sie **Debuggen** > **Debugging starten**, oder drücken Sie **F5**.

   Die APP wird im Debugmodus gestartet und am Haltepunkt angehalten.

1. Öffnen Sie im Modus "unterbrechen" das Fenster **Threads** , indem Sie > **Fenster** > **Threads** **Debuggen** auswählen. Sie müssen sich in einer Debugsitzung befinden, um die **Threads** und andere Debuggingfenster zu öffnen oder anzuzeigen.

## <a name="examine-thread-markers"></a>Thread Marker überprüfen

1. Suchen Sie im Quellcode die `Console.WriteLine();` Zeile.

   1. Klicken Sie mit der rechten Maustaste in das Fenster **Threads** , und wählen Sie im Menü **Threads in Quelle** ![anzeigen Threads anzeigen](../debugger/media/dbg-multithreaded-show-threads.png "Threadmarker") aus.

   Der bundstein neben der Quell Code Zeile zeigt *nun ein Thread Marker-* Symbol ![Thread Marker](../debugger/media/dbg-thread-marker.png "Thread-Marker")an. Der Threadmarker gibt an, dass ein Thread an dieser Position angehalten wurde. Wenn am Speicherort mehr als ein angehaltener Thread vorhanden ist, wird das Symbol ![mehrere Threads](../debugger/media/dbg-multithreaded-show-threads.png "Mehrere Threads") angezeigt.

1. Zeigen Sie mit dem Mauszeiger auf den Threadmarker. Ein DataTip wird angezeigt, in dem der Name und die Thread-ID für den beendeten Thread oder die Threads angezeigt werden. Die Thread Namen können `<No Name>`werden.

   >[!TIP]
   >Um namenlose Threads zu identifizieren, können Sie Sie im Fenster **Threads** umbenennen. Klicken Sie mit der rechten Maustaste auf den Thread und wählen Sie **Umbenennen**

1. Klicken Sie mit der rechten Maustaste auf den Thread Marker im Quellcode, um die verfügbaren Optionen im Kontextmenü anzuzeigen.

## <a name="flag-and-unflag-threads"></a>Kennzeichnen von Threads und Aufheben der Kennzeichnung

Sie können Threads markieren, um die Threads nachzuverfolgen, auf die Sie besonders achten sollten.

Markieren Sie Threads im Quellcode-Editor oder im **Thread** Fenster, und deaktivieren Sie Sie. Wählen Sie aus der Symbolleiste **Debugspeicherort** oder **Thread** Fenster aus, ob nur gekennzeichnete Threads oder alle Threads angezeigt werden sollen. Die Auswahl von einem beliebigen Standort wirkt sich auf alle Standorte aus.

### <a name="flag-and-unflag-threads-in-source-code"></a>Flags im Quellcode markieren und deren Flag aufheben

1. Öffnen Sie die Symbolleiste **Debugspeicherort** , indem Sie > **Symbolleisten** > **Debugspeicherort** **anzeigen** auswählen Sie können auch mit der rechten Maustaste in den Symbolleisten Bereich klicken und **Debugspeicherort**auswählen.

1. Die Symbolleiste **Debugspeicherort** weist drei Felder auf: **verarbeiten**, **Thread**und **Stapel Rahmen**. Löschen Sie die **Thread** Liste, und notieren Sie sich, wie viele Threads vorhanden sind. In der **Thread** Liste wird der derzeit ausgeführte Thread durch ein **>** Symbol gekennzeichnet.

1. Zeigen Sie im Fenster "Quell Code" auf ein Thread Markersymbol im bundlover, und wählen Sie das Flag-Symbol (oder eines der leeren Flag-Symbole) im DataTip aus. Das Flag-Symbol wird rot angezeigt.

   Sie können auch mit der rechten Maustaste auf ein Thread Markersymbol, auf **Flag**zeigen und dann einen Thread auswählen, der aus dem Kontextmenü markiert werden soll.

1. Aktivieren Sie auf der Symbolleiste **Debugspeicherort** das Symbol nur gekennzeichnete **Threads anzeigen** , und klicken Sie rechts neben dem Feld **Thread** auf ![markierte Threads anzeigen](../debugger/media/dbg-threads-show-flagged.png "Gekennzeichnete Threads anzeigen"). Das Symbol ist ausgegraut, es sei denn, ein oder mehrere Threads werden gekennzeichnet.

   Nur der gekennzeichnete Thread wird jetzt in der Dropdown Liste **Thread** auf der Symbolleiste angezeigt. Wenn Sie alle Threads wieder anzeigen möchten, wählen Sie das Symbol **nur markierte Threads anzeigen** erneut aus.

   >[!TIP]
   >Nachdem Sie einige Threads gekennzeichnet haben, können Sie den Cursor im Code-Editor platzieren, mit der rechten Maustaste klicken und **markierte Threads zum Cursor ausführen**auswählen. Stellen Sie sicher, dass Sie Code auswählen, der von allen markierten Threads erreicht wird. **Ausführen von markierten Threads zum Cursor** Anhalten von Threads in der ausgewählten Codezeile, sodass die Ausführungsreihenfolge einfacher gesteuert werden kann, indem [Threads eingefroren und](#bkmk_freeze)aktiviert werden.

1. Um den markierten bzw. nicht markierten Status des aktuell ausgeführten Threads zu aktivieren, wählen Sie **die Symbolleisten** Schaltfläche "nur gekennzeichnete Threads anzeigen" auf der linken Seite der Schaltfläche nur gekennzeichnete **Threads anzeigen** aus. Das Kennzeichnen des aktuellen Threads ist hilfreich für die Suche nach dem aktuellen Thread, wenn nur gekennzeichnete Threads angezeigt werden.

1. Um das Flag für einen Thread zu entfernen, zeigen Sie auf die Thread Markierung im Quellcode, und wählen Sie das rote Flag-Symbol aus, um es zu löschen, oder **Klicken Sie mit**der rechten Maustaste auf den Thread Marker, und wählen Sie Markierung

### <a name="flag-and-unflag-threads-in-the-threads-window"></a>Markieren und Aufheben der Markierung von Threads im Thread Fenster

Im Fenster **Threads** haben gekennzeichnete Threads neben den roten Flag-Symbolen neben den markierten Threads leere Symbole.

![Fenster „Threads“](../debugger/media/dbg-threads-window.png "Fenster 'Threads'")

Wählen Sie ein Flag-Symbol aus, um den Thread Zustand je nach aktuellem Status in gekennzeichnet oder nicht gekennzeichnet zu ändern.

Sie können auch mit der rechten Maustaste auf eine Zeile klicken und **Markieren**, **Flag**aufheben oder **alle Threads** aus dem Kontextmenü aufheben.

Die Symbolleiste des **Thread** Fensters verfügt auch über die Schaltfläche gekennzeichnete **Threads anzeigen** . Dies ist das rechten eines der beiden Flag-Symbole. Sie funktioniert genauso wie die Schaltfläche auf der Symbolleiste **Debugspeicherort** , und beide Schaltflächen steuern die Anzeige an beiden Speicherorten.

### <a name="other-threads-window-features"></a>Weitere Thread Fenster Features

Wählen Sie im Fenster **Threads** den Header einer beliebigen Spalte aus, um die Threads nach dieser Spalte zu sortieren. Klicken Sie erneut, um die Sortierreihenfolge umzukehren. Wenn alle Threads angezeigt werden, werden die Threads durch Auswählen der Flag-Symbol Spalte nach dem Status "gekennzeichnet" oder "nicht gekennzeichnet" sortiert.

Die zweite Spalte des Thread **Fensters (** ohne Header) ist die **aktuelle Thread** Spalte. Ein gelber Pfeil in dieser Spalte markiert den aktuellen Ausführungs Punkt.

In der Spalte **Speicherort** wird angezeigt, wo die einzelnen Threads im Quellcode angezeigt werden. Wählen Sie den Erweiterungs Pfeil neben dem **Orts** Eintrag aus, oder zeigen Sie auf den Eintrag, um eine partielle aufrufsstapel für diesen Thread anzuzeigen.

>[!TIP]
>Verwenden Sie das Fenster [parallele Stapel](../debugger/using-the-parallel-stacks-window.md) , um eine grafische Ansicht der Aufruf Listen für Threads zu erhalten. Um das Fenster zu öffnen, wählen Sie beim Debuggen> **Fenster** > **parallele Stapel** **Debuggen** aus.

Neben dem **Flag**"Flag **", "Flag aufheben**" und " **Flag für alle Threads**aufheben" hat das Kontextmenü für **Thread** Fensterelemente folgendes Kontextmenü:

- Die Schaltfläche **Threads in Quelle anzeigen** .
- **Hexadezimale Anzeige**, bei der die **Thread-ID**s im Fenster **Threads** von Decimal in Hexadezimal Format geändert wird.
- [Wechseln Sie zu Thread](#switch-to-another-thread), der die Ausführung sofort an diesen Thread schaltet.
- **Umbenennen**: Hiermit können Sie den Thread Namen ändern.
- [Freeze-und Thaw-](#bkmk_freeze) Befehle.

## <a name="bkmk_freeze"></a>Einfrieren der Thread Ausführung

Sie können Threads fixieren und durch ein-und wieder aufnehmen, um die Reihenfolge zu steuern, in der die Threads Arbeit ausführen. Das Einfrieren und Reaktivieren von Threads kann Ihnen helfen, Parallelitäts Probleme zu beheben, z. b. Deadlocks und Racebedingungen.

> [!TIP]
> [Wenn Sie](../debugger/get-started-debugging-multithreaded-apps.md#bkmk_follow_a_thread)einem einzelnen Thread folgen möchten, ohne andere Threads zu sperren, bei denen es sich um ein häufiges Debugszenario handelt

**So fixieren Sie Threads und heben die Fixierung auf:**

1. Klicken Sie im Fenster **Threads** mit der rechten Maustaste auf einen beliebigen Thread, und wählen Sie dann **Einfrieren**aus. Ein **Pausen** Symbol in der Spalte **aktueller Thread** gibt an, dass der Thread eingefroren ist.

1. Wählen Sie in der Symbolleiste des **Thread** Fensters **Spalten** aus, und wählen Sie dann angehaltene **Anzahl** aus, **um die Spalte** angehaltene Der Wert für die angehaltene Anzahl für den fixierten Thread beträgt **1**.

1. Klicken Sie mit der rechten Maustaste auf den fixierten Thread, **und wählen Sie**dann

   Das **Pausen** Symbol wird nicht mehr angezeigt, und der Wert der angehaltenen **Anzahl wird** in **0**geändert

## <a name="switch-to-another-thread"></a>Zu einem anderen Thread wechseln

Wenn Sie versuchen, zu einem anderen Thread zu wechseln, sehen Sie möglicherweise, dass sich **die Anwendung im Fenster Umbruch Modus befindet** . In diesem Fenster wird Ihnen mitgeteilt, dass der Thread keinen Code hat, den der aktuelle Debugger anzeigen kann. Beispielsweise können Sie verwalteten Code Debuggen, aber der Thread ist nativer Code. Das Fenster enthält Vorschläge zur Behebung des Problems.

**So wechseln Sie zu einem anderen Thread:**

1. Notieren Sie **sich die aktuelle** Thread-ID im Thread Fenster, bei der es sich um den Thread mit einem gelben Pfeil in der **aktuellen Thread** Spalte handelt. Sie möchten zu diesem Thread zurück wechseln, um Ihre APP fortzusetzen.

1. Klicken Sie mit der rechten Maustaste auf einen anderen Thread, und wählen Sie im Kontextmenü **zu Thread wechseln** aus.

1. Beachten Sie, dass sich die gelbe Pfeil Position im **Thread** Fenster geändert hat. Der ursprüngliche aktuelle Thread Marker verbleibt auch als Kontur.

   Sehen Sie sich die QuickInfo auf dem Thread Marker im Quellcode-Editor an, und klicken Sie auf der Symbolleiste **Debugspeicherort** auf die Liste in der Dropdown Liste **Thread** . Beachten Sie, dass sich der aktuelle Thread auch dort geändert hat.

1. Wählen Sie auf der Symbolleiste **Debugspeicherort** einen anderen Thread aus der **Thread** Liste aus. Beachten Sie, dass sich der aktuelle Thread auch an den anderen beiden Speicherorten ändert.

1. Klicken Sie im Quellcode-Editor mit der rechten Maustaste auf einen Thread Marker, zeigen Sie auf **zu Thread wechseln**, und wählen Sie einen anderen Thread aus der Liste aus. Beachten Sie, dass sich der aktuelle Thread an allen dreispeicher Orten ändert.

Mit dem Thread Marker im Quellcode können Sie nur zu Threads wechseln, die an diesem Speicherort angehalten wurden. Über das **Threadfenster** und die Symbolleiste **Debugspeicherort** können Sie zu jedem beliebigen Thread wechseln.

Sie haben nun die Grundlagen des Debuggens von Multithread-apps kennengelernt. Sie können Threads mithilfe des Fensters **Threads** , der **Thread** Liste in der Symbolleiste **Debugspeicherort** oder von Thread Markierungen im Quellcode-Editor überwachen, kennzeichnen und aufheben.

## <a name="see-also"></a>Siehe auch
- [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Gewusst wie: Wechseln zu einem anderen Thread während des Debuggings](../debugger/how-to-switch-to-another-thread-while-debugging.md)
