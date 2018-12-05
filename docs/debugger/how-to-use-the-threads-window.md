---
title: Debuggen einer Multithread-app
description: Debuggen Sie mithilfe des Fensters Threads und die Symbolleiste Debuggen in Visual Studio
ms.custom: ''
ms.date: 11/21/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cd66d7f9d8f214e8e7166a77162553b694e20cc5
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389402"
---
# <a name="walkthrough-debug-a-multithreaded-app-using-the-threads-window"></a>Exemplarische Vorgehensweise: Debuggen einer Multithread-app mithilfe des Fensters Threads

Einige Benutzeroberflächenelemente von Visual Studio helfen Ihnen beim Debuggen von Multithreadanwendungen. In diesem Artikel wird die Multithread-debugging-Funktionen im Code-Editor-Fenster, **Debugspeicherort** Symbolleiste und **Threads** Fenster. Weitere Informationen zu anderen Tools zum Debuggen von Multithreadanwendungen, finden Sie unter [erste Schritte zum Debuggen von Multithreadanwendungen](../debugger/get-started-debugging-multithreaded-apps.md). 
  
Abschluss dieses Tutorials dauert nur wenige Minuten, und erfahren Sie, wie mit den Grundlagen des Debuggens von Multithreadanwendungen.

## <a name="create-a-multithreaded-app-project"></a>Erstellen Sie ein Multithread-app-Projekt  

Erstellen Sie das folgende Multithread-app-Projekt in diesem Tutorial verwenden: 
  
1. Klicken Sie in Visual Studio auf **Datei** > **Neu** > **Projekt**.  
   
1. In der **neues Projekt** Dialogfeld:
   - Für eine C# app, und wählen **Visual C#**    >  **Konsolen-App ((.NET Framework)**.  
   - Wählen Sie für eine C++-app **Visual C++** > **Windows-Konsolenanwendung**.
   
1. Benennen Sie die app MyThreadWalkthroughApp ein, und wählen Sie dann **OK**.  
   
   Das neue Projekt wird im **Projektmappen-Explorer**, und eine Quelldatei namens *"Program.cs"* oder *MyThreadWalkthroughApp.cpp* wird im Quellcodefenster geöffnet.  
   
1. Ersetzen Sie den Code in der Quelldatei mit der C# oder C++-Beispielcode von [erste Schritte zum Debuggen von Multithreadanwendungen](../debugger/get-started-debugging-multithreaded-apps.md).  
   
1. Wählen Sie **Datei** > **alle speichern**.  
  
## <a name="start-debugging"></a>Debugging starten 

1. Suchen Sie die folgenden Zeilen im Quellcode:  
   
   ```csharp  
   Thread.Sleep(3000); 
   Console.WriteLine();
   ```  
   
   ```C++ 
   Thread::Sleep(3000); 
   Console.WriteLine(); 
   ```
   
1. Legen Sie einen Haltepunkt auf der `Console.WriteLine();` Zeile, indem Sie auf im linken Bundsteg, oder Sie die Zeile auswählen und **F9**.  
   
   Der Haltepunkt wird als ein roter Kreis im linken Bundsteg neben der Codezeile angezeigt.  
   
1. Wählen Sie **Debuggen** > **Debuggen starten**, oder drücken Sie **F5**.  
   
   Die app wird im Debugmodus gestartet und die Ausführung am Haltepunkt angehalten wird.  
   
1. Öffnen Sie im Unterbrechungsmodus, der **Threads** Fenster durch Auswahl **Debuggen** > **Windows** > **Threads**. Sie muss in einer Debugsitzung zu öffnen, oder finden Sie unter den **Threads** und andere debugging-Fenster. 
   
## <a name="examine-thread-markers"></a>Überprüfen Sie die Threadmarker

1. Suchen Sie im Quellcode an, die `Console.WriteLine();` Zeile. 
   
   1. Mit der rechten Maustaste den **Threads** , und wählen **Threads in Quelle anzeigen** ![Threads in Quelle anzeigen](../debugger/media/dbg-multithreaded-show-threads.png "ThreadMarker") aus dem Menü.
   
   Im Bundsteg neben den Quellcode Zeile zeigt nun eine *Threadmarker* Symbol ![Threadmarker](../debugger/media/dbg-thread-marker.png "Threadmarker"). Der Threadmarker gibt an, dass ein Thread an dieser Position angehalten wurde. Wenn mehr als einen angehaltenen Thread vorhanden, an der Position ist der ![mehrere Threads](../debugger/media/dbg-multithreaded-show-threads.png "mehrere Threads") Symbol angezeigt wird.
   
1. Zeigen Sie mit dem Mauszeiger auf den Threadmarker. Ein DataTip wird angezeigt, die die Namen und die Thread-ID-Nummer für die angehaltenen Threads oder Threads angezeigt. Die Threadnamen möglicherweise `<No Name>`.  

   >[!TIP]
   >Um namenlosen Threads zu ermitteln, können Sie umbenennen, in der **Threads** Fenster. Mit der rechten Maustaste im Threads aus, und wählen Sie **umbenennen**.
  
1. Mit der rechten Maustaste in des Threadmarker im Quellcode und die verfügbaren Optionen im Kontextmenü anzuzeigen. 

## <a name="flag-and-unflag-threads"></a>Kennzeichnen von Threads und Aufheben der Kennzeichnung 

Sie können Threads kennzeichnen zum Nachverfolgen Threads besondere Aufmerksamkeit werden sollen. 

Kennzeichnen und Kennzeichnung von Threads aus dem Quellcode-Editor oder die **Threads** Fenster. Wählen Sie, ob angezeigt wird, nur gekennzeichnete von Threads oder alle Threads aus dem **Debugspeicherort** oder **Threads** Symbolleisten des Toolfensters. Auswahl von einem beliebigen Standort wirken sich auf alle Speicherorte. 

### <a name="flag-and-unflag-threads-in-source-code"></a>Kennzeichnen und Kennzeichnung von Threads im Quellcode 

1. Öffnen der **Debugspeicherort** Symbolleiste dazu **Ansicht** > **Symbolleisten** > **Debugspeicherort**. Sie können auch mit der rechten Maustaste auf der Symbolleiste angezeigt, und wählen Sie **Debugspeicherort**. 
   
1. Die **Debugspeicherort** Symbolleiste verfügt über drei Felder: **Prozess**, **Thread**, und **Stapelrahmen**. Öffnen Sie die Dropdownliste der **Thread** aus, und beachten Sie, wie viele Threads vorhanden sind. In der **Thread** Liste der aktuell ausgeführte Thread ist gekennzeichnet durch einen **>** Symbol. 
   
1. Klicken Sie im Quellcodefenster zeigen Sie auf eine Thread-Marker-Symbol im Bundsteg angezeigt, und wählen Sie das Flaggensymbol klicken (oder eines der Symbole leere Flag) in einem DataTip. Das Flaggensymbol klicken, wird rot angezeigt. 
   
   Sie können auch mit der rechten Maustaste ein Thread-Marker-Symbol, zeigen Sie auf **Flag**, und wählen Sie dann einen Thread so kennzeichnen Sie aus dem Kontextmenü.  
   
1. Auf der **Debugspeicherort** -Symbolleiste auf die **nur gekennzeichnete Threads anzeigen** Symbol ![gekennzeichnete Threads anzeigen](../debugger/media/dbg-threads-show-flagged.png "gekennzeichnete Threads anzeigen"), in der rechts von der **Thread** Feld. Das Symbol ist ausgegraut, es sei denn, ein oder mehrere Threads gekennzeichnet sind.  
   
   Nur der gekennzeichnete Thread wird jetzt in der **Thread** Dropdownfeld in der Symbolleiste. Um wieder alle Threads anzuzeigen, wählen Sie die **nur gekennzeichnete Threads anzeigen** Symbol erneut aus.
   
   >[!TIP]
   >Nachdem Sie einige Threads gekennzeichnet haben, können Sie den Cursor in die Code-Editor, mit der rechten Maustaste und wählen Sie platzieren **gekennzeichnete Threads bis zum Cursor ausführen**. Stellen Sie sicher, um auszuwählen, dass Code, der alle gekennzeichnete Threads erreicht wird. **Ausführen von gekennzeichnete Threads bis Cursor** hält Threads in der ausgewählten Zeile des Codes, erleichtert Ihnen die Steuerung die Reihenfolge der Ausführung von [sperren und Entsperren von Threads](#bkmk_freeze).
   
1. Um den markierten oder nicht gekennzeichnet Status des aktuell ausgeführten Thread zu wechseln, wählen Sie den einzigen Flag **aktuellen Thread gekennzeichnete Umschaltstatus** Symbolleisten-Schaltfläche, auf der linken Seite von der **nur gekennzeichnete Threads anzeigen** Schaltfläche ". Kennzeichnen den aktuellen Thread eignet sich für die Suche nach den aktuellen Thread, wenn nur gekennzeichnete Threads angezeigt werden. 
   
1. Klicken Sie zum Aufheben der Kennzeichnung eines Threads, zeigen Sie auf den Threadmarker im Quellcode, und wählen Sie das rote Kennzeichnungssymbol deaktivieren, oder mit der rechten Maustaste des Threadmarker aus, und wählen Sie **Flag**.  

### <a name="flag-and-unflag-threads-in-the-threads-window"></a>Kennzeichnen und Kennzeichnung von Threads im Fenster Threads 

In der **Threads** Fenster gekennzeichneten Threads haben Red Symbole neben dem Namen, bei der nicht gekennzeichnete Threads kennzeichnen, ob angezeigt, die leere Symbole haben.

![Fenster "Threads"](../debugger/media/dbg-threads-window.png "Fenster \"Threads\"")  
  
Wählen Sie ein Flaggensymbol der Threadzustand gekennzeichnet oder nicht gekennzeichnet, abhängig von ihrem aktuellen Zustand zu ändern. 

Sie können auch mit der rechten Maustaste einer Zeile, und wählen Sie **Flag**, **Flag**, oder **Kennzeichnung aller Threads** aus dem Kontextmenü. 

Die **Threads** Symbolleiste des Fensters verfügt auch über eine **nur gekennzeichnete Threads anzeigen Threads** Schaltfläche, die der eines der zwei Kennzeichnungsymbole-Link ist. Es funktioniert genauso wie die Schaltfläche auf der **Debugspeicherort** Symbolleiste, und eine der Schaltflächen steuert die Anzeige der an beiden Standorten. 

### <a name="other-threads-window-features"></a>Andere Funktionen des Fensters Threads

In der **Threads** Fenster, wählen Sie die Überschrift einer beliebigen Spalte sortiert Threads nach dieser Spalte. Wählen Sie erneut, um die Sortierreihenfolge umzukehren. Wenn alle Threads angezeigt werden, sortiert die Spalte zur Kennzeichnung Symbol auswählen der Threads ein, nach Status gekennzeichnet oder nicht gekennzeichnet. 

Die zweite Spalte von der **Threads** Fenster (mit keinen Header) ist die **aktuellen Thread** Spalte. In dieser Spalte ein gelber Pfeil kennzeichnet den aktuellen Ausführungspunkt an. 

Die **Speicherort** Spalte wird angezeigt, wobei jeder Thread im Quellcode angezeigt wird. Aktivieren Sie den Erweiterungspfeil neben der **Speicherort** Eintrag oder zeigen Sie auf den Eintrag, um eine teilweise Aufrufliste für diesen Thread anzuzeigen. 

>[!TIP]
>Verwenden Sie für eine grafische Darstellung der Aufruflisten für Threads, die [parallele Stapel](../debugger/using-the-parallel-stacks-window.md) Fenster. Wählen Sie zum Öffnen im Fensters während des Debuggens **Debuggen**> **Windows** > **parallele Stapel**.  

Zusätzlich zu **Flag**, **Flag**, und **Kennzeichnung aller Threads**, das Rechtsklick-Kontextmenü für **Thread** Fenster Elemente enthält:

- Die **Threads in Quelle anzeigen** Schaltfläche.
- **Hexadezimale Anzeige**, welche Änderungen an der **Thread-ID**s in der **Threads** Fenster von Dezimal in hexadezimal-Format. 
- [Zu Thread wechseln](#switch-to-another-thread), die sofort die Ausführung zu diesem Thread wechselt. 
- **Benennen Sie**, sodass Sie den Threadnamen zu ändern. 
- [Einfrieren und reaktivieren](#bkmk_freeze) Befehle.

## <a name="bkmk_freeze"></a> Einfrieren Sie und reaktivieren Sie die Ausführung des Threads 

Sie Einfrieren und reaktivieren, oder anhalten und fortsetzen, Threads zu steuern, die Reihenfolge, in dem die Threads Arbeit ausführen. Sperren und Entsperren von Threads können Sie beheben von Parallelitätsproblemen wie Deadlocks und Racebedingungen.

> [!TIP]
> Um folgen zu einen einzelnen Thread ohne andere Threads Einfrieren ist ein häufiges Szenario für Debuggen, finden Sie unter [erste Schritte zum Debuggen von Multithreadanwendungen](../debugger/get-started-debugging-multithreaded-apps.md#bkmk_follow_a_thread).
  
**So fixieren Sie Threads und heben die Fixierung auf:**  
  
1. In der **Threads** mit der rechten Maustaste auf einen beliebigen Thread, und wählen Sie dann **fixieren**. Ein **anhalten** Symbol in der **aktuellen Thread** Spalte gibt an, dass der Thread gesperrt ist.  
   
1. Wählen Sie **Spalten** in die **Threads** Symbolleiste des Fensters, und wählen Sie dann **angehaltene Anzahl** zum Anzeigen der **angehaltene Anzahl** Spalte. Der Unterbrechungszähler-Wert für den gesperrten Thread ist **1**.  
   
1. Mit der rechten Maustaste in des gesperrten Threads, und wählen Sie **reaktivieren**.  
  
   Die **anhalten** Symbol wird ausgeblendet, und die **angehaltene Anzahl** Wert ändert sich in **0**. 
  
## <a name="switch-to-another-thread"></a>Wechseln Sie zu einem anderen thread 

Möglicherweise eine **der Anwendung befindet sich im Unterbrechungsmodus** Fenster, wenn Sie versuchen, wechseln Sie zu einem anderen Thread. In diesem Fenster Aufschluss darüber, dass der Thread keiner Code, der der aktuelle Debugger angezeigt werden kann. Angenommen, Sie verwalteten Code Debuggen, aber der Thread ist systemeigener Code. Das Fenster bietet Vorschläge zur Behebung des Problems. 
  
**Wechseln Sie zu einem anderen Thread:**

1. In der **Threads** Fenster, notieren Sie die aktuellen Thread-ID, dies ist der Thread mit einem gelben Pfeil in der **aktuellen Thread** Spalte. Sie sollten so wechseln Sie an diesen Thread aus, um Ihre app den Vorgang fortzusetzen. 
   
1. Mit der rechten Maustaste in eines anderen Threads aus, und wählen Sie **Switch zum Thread** aus dem Kontextmenü.  
   
1. Beachten Sie, dass der gelbe Pfeil-Speicherort im geändert hat die **Threads** Fenster. Der ursprünglichen und aktuellen Threadmarker hat, auch als Gliederung bleibt. 
   
   Sehen Sie sich die QuickInfo auf den Threadmarker im Quellen-Editor für Code und die Liste in der **Thread** Dropdownliste auf der **Debugspeicherort** Symbolleiste. Beachten Sie, dass der aktuelle Thread auch es geändert wurde. 
   
1. Auf der **Debugspeicherort** Symbolleiste wählen Sie einen anderen Thread aus dem **Thread** Liste. Beachten Sie, dass der aktuelle Thread auch in den anderen beiden Speicherorten geändert wird. 
   
1. Der Quellcode-Editor, mit der Maustaste eines Threadmarker, zeigen Sie auf **Switch zum Thread**, und wählen Sie einen anderen Thread aus der Liste. Beachten Sie, dass der aktuelle Thread in allen drei Speicherorten geändert.  
   
Mit den Threadmarker in den Quellcode einfügen können Sie nur zu Threads wechseln, die an dieser Stelle beendet wurden. Über das **Threadfenster** und die Symbolleiste **Debugspeicherort** können Sie zu jedem beliebigen Thread wechseln.   

Sie haben nun die Grundlagen des Debuggens von Multithreadanwendungen kennengelernt. Sie können beobachten, flag und Aufheben der Kennzeichnung, und Einfrieren und Threads reaktivieren, mit der **Threads** Fenster die **Thread** Liste der **Debugspeicherort** Symbolleiste oder Threadmarker in der Quellcode-Editor.
  
## <a name="see-also"></a>Siehe auch  
 [Debug multithreaded applications (Debuggen von Multithreadanwendungen)](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Gewusst wie: Wechseln zu einem anderen Thread während des Debuggings](../debugger/how-to-switch-to-another-thread-while-debugging.md)
