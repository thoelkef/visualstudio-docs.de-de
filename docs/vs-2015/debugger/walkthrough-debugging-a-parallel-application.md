---
title: 'Exemplarische Vorgehensweise: Debuggen einer Parallelanwendung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks walkthrough
- parallel stacks toolwindow
- parallel tasks toolwindow
- parallel applications, debugging [C++]
- debugging, parallel applications
- parallel applications, debugging [Visual Basic]
- parallel applications, debugging [C#]
ms.assetid: 2820ac4c-c893-4d87-8c62-83981d561493
caps.latest.revision: 31
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 22a4d8ea3bfe98a034f485be8ceec1004f8fba75
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513867"
---
# <a name="walkthrough-debugging-a-parallel-application"></a>Exemplarische Vorgehensweise: Debuggen einer parallelen Anwendung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Exemplarische Vorgehensweise: Debuggen einer Parallelanwendung](https://docs.microsoft.com/visualstudio/debugger/walkthrough-debugging-a-parallel-application).  
  
In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie mit der **Parallele Aufgaben** und **parallele Stapel** Windows zum Debuggen einer parallelen Anwendung. Diese Fenster unterstützen Sie besser verstehen und prüfen das Laufzeitverhalten von Code, verwendet der [Task Parallel Library (TPL)](http://msdn.microsoft.com/library/b8f99f43-9104-45fd-9bff-385a20488a23) oder [Concurrency Runtime](http://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c). Diese exemplarische Vorgehensweise bietet Beispielcode mit integrierten Haltepunkte. Nachdem der Code unterbrochen wird, in der exemplarischen Vorgehensweise veranschaulicht, wie die **Parallele Aufgaben** und **parallele Stapel** Windows zu untersuchen.  
  
 In dieser exemplarischen Vorgehensweise werden die folgenden Aufgaben erklärt:  
  
-   Anzeigen der Aufruflisten aller Threads in einer Ansicht.  
  
-   Anzeigen der Liste der `System.Threading.Tasks.Task`-Instanzen, die in der Anwendung erstellt werden.  
  
-   Anzeigen der tatsächlichen Aufruflisten mit Aufgaben anstelle von Threads.  
  
-   Gewusst wie: Navigieren zu Code von der **Parallele Aufgaben** und **parallele Stapel** Windows.  
  
-   Skalieren der Fenster durch Gruppieren, Vergrößern/Verkleinern und sonstigen entsprechenden Funktionen.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 In dieser exemplarischen Vorgehensweise wird vorausgesetzt, dass **nur mein Code** aktiviert ist. Auf der **Tools** Menü klicken Sie auf **Optionen**, erweitern Sie die **Debuggen** Knoten **allgemeine**, und wählen Sie dann **aktivieren Nur mein Code (nur verwaltet)**. Wenn Sie diese Funktion nicht festlegen, können Sie die vorliegende exemplarische Vorgehensweise zwar verwenden, Ihre Ergebnisse weichen jedoch möglicherweise von den Abbildungen ab.  
  
## <a name="c-sample"></a>C#-Beispiel  
 Wenn Sie das C#-Beispiel verwenden, wird in dieser exemplarischen Vorgehensweise auch davon ausgegangen, dass externer Code ausgeblendet ist. Um die Anzeige von externem Code umzuschalten, Informationen zu diesem mit der rechten Maustaste die **Namen** Tabellenheader der **Aufrufliste** Fenster, und aktivieren oder deaktivieren **externen Code anzeigen**. Wenn Sie diese Funktion nicht festlegen, können Sie die vorliegende exemplarische Vorgehensweise zwar verwenden, Ihre Ergebnisse weichen jedoch möglicherweise von den Abbildungen ab.  
  
## <a name="c-sample"></a>C++-Beispiel  
 Wenn Sie das C++-Beispiel verwenden, können Sie Verweise auf externen Code in diesem Thema ignorieren. Externer Code bezieht sich ausschließlich auf das C#-Beispiel.  
  
## <a name="illustrations"></a>Abbildungen  
 Die Abbildungen in diesem Thema wurden auf einem Quad-Core-Computer aufgezeichnet, auf dem das C#-Beispiel ausgeführt wird. Sie können diese exemplarische Vorgehensweise auch mit anderen Konfigurationen durcharbeiten. Die Abbildungen unterscheiden sich jedoch möglicherweise von der Anzeige auf Ihrem Computer.  
  
## <a name="creating-the-sample-project"></a>Erstellen des Beispielprojekts  
 Der Beispielcode in dieser exemplarischen Vorgehensweise ist für eine Anwendung ohne konkrete Aufgaben. Das Ziel besteht lediglich darin zu erläutern, wie mit den Toolfenstern parallele Anwendungen gedebuggt werden.  
  
#### <a name="to-create-the-sample-project"></a>So erstellen Sie das Beispielprojekt  
  
1.  Zeigen Sie in Visual Studio im Menü **Datei** auf **Neu**, und klicken Sie auf **Projekt**.  
  
2.  In der **installierte Vorlagen** Bereich, wählen Sie entweder Visual c#, Visual Basic oder Visual C++. Stellen Sie für verwaltete Sprachen sicher, dass im Frameworkfeld [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] angezeigt wird.  
  
3.  Wählen Sie **Konsolenanwendung** , und klicken Sie dann auf **OK**. Behalten Sie die Debugkonfiguration bei (Standardeinstellung).  
  
4.  Öffnen Sie die CPP-, CS- oder VB-Codedatei im Projekt. Löschen Sie den Dateiinhalt, um eine leere Codedatei zu erstellen.  
  
5.  Fügen Sie den folgenden Code für die ausgewählte Sprache in die leere Codedatei ein.  
  
 [!code-cpp[Debugger#1](../snippets/cpp/VS_Snippets_Misc/debugger/cpp/beta2_native.cpp#1)]
 [!code-csharp[Debugger#1](../snippets/csharp/VS_Snippets_Misc/debugger/cs/s.cs#1)]
 [!code-vb[Debugger#1](../snippets/visualbasic/VS_Snippets_Misc/debugger/vb/module1.vb#1)]  
  
1.  Auf der **Datei** Menü klicken Sie auf **Alles speichern**.  
  
2.  Auf der **erstellen** Menü klicken Sie auf **Projektmappe neu erstellen**.  
  
     Beachten Sie, dass es vier Aufrufe zu `Debugger.Break` (`DebugBreak` im C++-Beispiel) gibt. Daher müssen keine Haltepunkte eingefügt werden; wenn nur die Anwendung ausgeführt wird, hat dies bis zu vier Unterbrechungen im Debugger zur Folge.  
  
## <a name="using-the-parallel-stacks-window-threads-view"></a>Verwenden des Fensters Parallele Stapel: Threadansicht  
 Klicken Sie im Menü **Debuggen** auf **Debuggen starten**. Warten Sie, bis der erste Haltepunkt erreicht wird.  
  
#### <a name="to-view-the-call-stack-of-a-single-thread"></a>So zeigen Sie die Aufrufliste eines einzelnen Threads an  
  
1.  Auf der **Debuggen** Startmenü **Windows** , und klicken Sie dann auf **Threads**. Andocken der **Threads** Fenster am unteren Rand der Visual Studio.  
  
2.  Auf der **Debuggen** Startmenü **Windows** , und klicken Sie dann auf **Aufrufliste**. Andocken der **Aufrufliste** -Fensters am unteren Rand von Visual Studio.  
  
3.  Doppelklicken Sie auf einen Thread in der **Threads** Fenster zum aktuellen werden soll. Aktuelle Threads sind durch einen gelben Pfeil gekennzeichnet. Wenn Sie den aktuellen Thread ändern, wird seine Aufrufliste angezeigt, der **Aufrufliste** Fenster.  
  
#### <a name="to-examine-the-parallel-stacks-window"></a>So untersuchen Sie das Fenster Parallele Stapel  
  
1.  Auf der **Debuggen** Startmenü **Windows** , und klicken Sie dann auf **parallele Stapel**. Stellen Sie sicher, dass **Threads** ausgewählt ist, in das Feld in der oberen linken Ecke.  
  
     Mithilfe der **parallele Stapel** Fenster können Sie mehrere Aufruflisten gleichzeitig in einer Ansicht anzeigen. Die folgende Abbildung zeigt die **parallele Stapel** oben im Fenster der **Aufrufliste** Fenster.  
  
     ![Threadansicht im Fenster "Parallele Stapel"](../debugger/media/pdb-walkthrough-1.png "PDB_Walkthrough_1")  
  
     Die Aufrufliste des Hauptthreads wird in einem Feld angezeigt, während die Aufruflisten für die anderen vier Threads als Gruppe in einem anderen Feld angezeigt werden. Vier Threads werden als Gruppe angezeigt, da für ihre Stapelrahmen dieselben Methodenkontexte verwendet werden; d. h., sie befinden sich in denselben Methoden: `A`, `B` und `C`. Zum Anzeigen, die die Thread-IDs und Namen der Threads, die gemeinsam das gleiche Feld, zeigen den Header (**4 Threads**). Der aktuelle Thread wird fett formatiert angezeigt, wie in der folgenden Abbildung veranschaulicht.  
  
     ![QuickInfo, die Thread-IDs-Namen und](../debugger/media/pdb-walkthrough-1a.png "PDB_Walkthrough_1A")  
  
     Der gelbe Pfeil gibt den aktiven Stapelrahmen des aktuellen Threads an. Zeigen Sie mit dem Mauszeiger darauf, um weitere Informationen anzuzeigen.  
  
     ![QuickInfo auf aktivem Stapelrahmen](../debugger/media/pdb-walkthrough-1b.png "PDB_Walkthrough_1B")  
  
     Sie können festlegen, wie viele Details, die für die Stapelrahmen angezeigt (**Modulnamen**, **Parametertypen**, **Parameternamen**, **Parameterwerte**, **Zeilennummern** und **Byte-Offsets**) mit der rechten Maustaste den **Aufrufliste** Fenster.  
  
     Durch eine blaue Hervorhebung um ein Feld wird angegeben, dass der aktuelle Thread zu diesem Feld gehört. Der aktuelle Thread wird auch durch den fett formatierten Stapelrahmen in der QuickInfo angegeben. Wenn Sie den Hauptthread im Fenster Threads doppelklicken, können Sie beobachten, die blaue Hervorhebung im der **parallele Stapel** Fenster entsprechend verschoben wird.  
  
     ![Hervorgehobener Hauptthread im Fenster "Parallele Stapel"](../debugger/media/pdb-walkthrough-1c.png "PDB_Walkthrough_1C")  
  
#### <a name="to-resume-execution-until-the-second-breakpoint"></a>So setzen Sie die Ausführung bis zum zweiten Haltepunkt fort  
  
1.  Um die Ausführung fortzusetzen, bis der zweite Breakpoint erreicht wird, auf die **Debuggen** Menü klicken Sie auf **Weiter**. In der folgenden Abbildung wird die Threadstruktur beim zweiten Haltepunkt dargestellt.  
  
     ![Fenster "Parallele Stapel", die vielen Branches](../debugger/media/pdb-walkthrough-2.png "PDB_Walkthrough_2")  
  
     Beim ersten Haltepunkt gingen alle vier Threads von den Methoden S.A zu S.B zu S.C über. Diese Informationen in immer noch sichtbar ist die **parallele Stapel** Fenster, aber die vier Threads weiter ausgeführt haben. Ein Thread ist zu S.D und dann zu S.E übergegangen. Ein anderer hat mit S.F, S.G und S.H fortgefahren. Zwei andere wechselten zu S.I und S.J. Von dort ging einer zu S.K über, während der andere zu nicht vom Benutzer stammendem externen Code wechselte.  
  
     Sie können auf zeigen den Header des Felds, z. B. **1 Thread** oder **2 Threads**, um die Thread-IDs der Threads anzuzeigen. Sie können mit dem Mauszeiger auf Stapelrahmen zeigen, um die Thread-IDs sowie andere Details zum Rahmen zu überprüfen. Die blaue Hervorhebung gibt den aktuellen Thread an, während mit dem gelben Pfeil der aktive Stapelrahmen des aktuellen Threads angegeben wird.  
  
     Mit dem Faden-Symbol (einander überlappenden blauen und roten Wellenlinien) werden die aktiven Stapelrahmen der nicht aktuellen Threads angegeben. In der **Aufrufliste** Fenster, doppelklicken Sie auf S.B, um Frames zu wechseln. Die **parallele Stapel** Fenster gibt den aktuellen Stapelrahmen des aktuellen Threads an, mit einem grünen gekrümmten Pfeilsymbol.  
  
     In der **Threads** Fenster, wechseln Sie zwischen Threads, und beachten Sie, dass die Ansicht in der **parallele Stapel** Fenster wird aktualisiert.  
  
     Sie können die zu einem anderen Thread oder einen anderen Frame eines anderen Threads wechseln, indem Sie über das Kontextmenü in der **parallele Stapel** Fenster. Z. B. mit der rechten Maustaste S.J, zeigen Sie auf **zu Rahmen wechseln**, und klicken Sie dann auf einen Befehl.  
  
     ![Parallele Stapel-Ausführungspfad](../debugger/media/pdb-walkthrough-2b.png "PDB_Walkthrough_2B")  
  
     Mit der rechten Maustaste S.C, und zeigen Sie auf **zu Rahmen wechseln**. Ein Befehl ist mit einem Häkchen versehen, das den Stapelrahmen des aktuellen Threads angibt. Sie können zu diesem Frame desselben Threads (nur der grüne Pfeil wird verschoben) wechseln, oder Sie können zum anderen Thread (die blaue Hervorhebung wird ebenfalls verschoben) wechseln. Die folgende Abbildung zeigt das Untermenü.  
  
     ![Menü "Stapel" mit 2 Optionen auf C, während J aktuell ist](../debugger/media/pdb-walkthrough-3.png "PDB_Walkthrough_3")  
  
     Wenn ein Methodenkontext nur einem Stapelrahmen zugeordnet ist, im Feldheader **1 Thread** und Sie können durch Doppelklicken zu diesem wechseln. Wenn Sie auf einen Methodenkontext doppelklicken, dem mehrere Frames zugeordnet sind, wird das Menü automatisch aufgerufen. Wie Sie mit dem Mauszeiger auf die Methodenkontexte zeigen, wird rechts ein schwarzes Dreieck angezeigt. Wenn Sie auf dieses Dreieck klicken, wird ebenfalls das Kontextmenü geöffnet.  
  
     Bei großen Anwendungen mit einer Vielzahl von Threads kann es sich empfehlen, sich nur auf eine Teilmenge von Threads zu konzentrieren. Die **parallele Stapel** Aufruflisten nur für gekennzeichnete Threads anzeigen. Klicken Sie auf der Symbolleiste auf die **nur gekennzeichnete Elemente anzeigen** Schaltfläche neben dem Listenfeld.  
  
     ![Leere Fenster "Parallele Stapel" und QuickInfo](../debugger/media/pdb-walkthrough-3a.png "PDB_Walkthrough_3A")  
  
     Als Nächstes wird in der **Threads** Fenster Flag einzelnen threads, um festzustellen, wie deren Aufruflisten in angezeigt werden die **parallele Stapel** Fenster. Verwenden Sie zum Kennzeichnen von Threads das Kontextmenü oder die erste Zelle eines Threads. Klicken Sie auf die **nur gekennzeichnete Elemente anzeigen** Symbolleisten-Schaltfläche erneut aus, um alle Threads anzuzeigen.  
  
#### <a name="to-resume-execution-until-the-third-breakpoint"></a>So setzen Sie die Ausführung bis zum dritten Haltepunkt fort  
  
1.  Um die Ausführung fortzusetzen, bis zum dritte Haltepunkt erreicht wird, auf die **Debuggen** Menü klicken Sie auf **Weiter**.  
  
     Wenn mehrere Threads in derselben Methode enthalten sind, diese sich jedoch nicht am Anfang der Aufrufliste befand, wird die Methode in verschiedenen Feldern angezeigt. Ein Beispiel am aktuellen Haltepunkt ist S.L. Hierin sind drei Threads enthalten, und die Methode wird in drei Feldern angezeigt. Doppelklicken Sie auf S.L.  
  
     ![Ausführungspfad im Fenster "Parallele Stapel"](../debugger/media/pdb-walkthrough-3b.png "PDB_Walkthrough_3B")  
  
     Beachten Sie, dass S.L in den anderen beiden Feldern fett formatiert ist, damit dort ersichtlich ist, an welcher Stelle die Methode außerdem angezeigt wird. Wenn Sie anzeigen möchten, welche frames s.l aufrufen, und welche frames es Aufrufe, klicken Sie auf die **Methodenansicht** auf der Symbolleiste. Die folgende Abbildung zeigt die Methodenansicht des der **parallele Stapel** Fenster.  
  
     ![Methodenansicht im Fenster "Parallele Stapel"](../debugger/media/pdw-walkthrough-4.png "PDW_Walkthrough_4")  
  
     Das Diagramm wurde für die ausgewählte Methode pivotiert, und diese wurde in einem eigenen Feld in der Mitte der Ansicht positioniert. Die Aufgerufenen und die Aufrufer werden am oberen und unteren Rand angezeigt. Klicken Sie auf die **Methodenansicht** Schaltfläche erneut aus, um diesen Modus zu verlassen.  
  
     Im Kontextmenü des der **parallele Stapel** Fenster verfügt auch über die folgenden anderen Elementen.  
  
    -   **Hexadezimale Anzeige** die Zahlen in den QuickInfos Dezimal-und hexadezimaldarstellung umgeschaltet.  
  
    -   **Symbolladeinformationen** und **Symboleinstellungen** die entsprechenden Dialogfelder zu öffnen.  
  
    -   **Gehe zu Quellcode** und **Gehe zu Disassembly** im Editor zur ausgewählten Methode navigiert.  
  
    -   **Externen Code anzeigen** werden alle Frames angezeigt, auch wenn sie nicht im Benutzercode sind. Das Diagramm wird erweitert, um die zusätzlichen Frames aufzunehmen (die möglicherweise abgeblendet dargestellt werden, da keine Symbole dafür vorhanden sind).  
  
     Wenn Sie bei großen Diagrammen zum nächsten Haltepunkt wechseln, können Sie einen automatischen Bildlauf der Anzeige zum aktiven Stapelrahmen des aktuellen Threads ausführen lassen (d. h. des Threads, der den Haltepunkt zuerst erreicht hat). In der **parallele Stapel** Fenster, stellen Sie sicher, dass die **automatischen Bildlauf zu aktuellem Stapelrahmen** befindet sich auf der Symbolleiste auf.  
  
     ![Automatischer Bildlauf in das Fenster "Parallele Stapel"](../debugger/media/pdb-walkthrough-4a.png "PDB_Walkthrough_4A")  
  
2.  Bevor Sie, in fortfahren der **parallele Stapel** Fenster, einen Bildlauf ganz nach links und ganz nach unten.  
  
#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>So setzen Sie die Ausführung bis zum vierten Haltepunkt fort  
  
1.  Um die Ausführung fortzusetzen, bis zum vierte Haltepunkt erreicht wird, auf die **Debuggen** Menü klicken Sie auf **Weiter**.  
  
     Beachten Sie, wie ein automatischer Bildlauf der Ansicht an die korrekte Position stattfindet. Schalten Sie zwischen Threads in der **Threads** Fenster oder Switch Stapelrahmen der **Aufrufliste** Fenster, und beachten Sie, dass wie die Ansicht Stapelrahmen zum richtigen Frame. Deaktivieren Sie **automatischen Bildlauf zu aktuellem Stapelrahmen** aus, und beobachten Sie den Unterschied.  
  
     Die **Vogelperspektive** auch hilfreich bei großen Diagrammen in der **parallele Stapel** Fenster. Sie sehen die **Vogelperspektive** mit der Schaltfläche zwischen den Bildlaufleisten in der unteren rechten Ecke des Fensters, wie in der folgenden Abbildung dargestellt.  
  
     ![Der Vogelperspektive&#45;-Augen-Ansicht im Fenster "Parallele Stapel"](../debugger/media/pdb-walkthrough-5.png "PDB_Walkthrough_5")  
  
     Sie können das Rechteck verschieben, um einen schnellen Schwenk um das Diagramm auszuführen.  
  
     Eine weitere Möglichkeit, das Diagramm in beliebiger Richtung zu verschieben, besteht darin, auf einen leeren Bereich des Diagramms zu klicken und das Diagramm an die gewünschte Stelle zu ziehen.  
  
     Zum Vergrößern und Verkleinern der Ansicht des Diagramms halten Sie STRG gedrückt, während Sie das Mausrad drehen. Sie können auch auf der Symbolleiste auf die Schaltfläche Zoom klicken und das Tool Zoom verwenden.  
  
     ![Vergrößerte Stapel im Fenster "Parallele Stapel"](../debugger/media/pdb-walkthrough-5a.png "PDB_Walkthrough_5A")  
  
     Sie können auch die Stapel in eine Richtung von oben nach unten anstatt von unten nach oben, anzeigen, indem Sie auf die **Tools** Menü auf **Optionen**, und klicken Sie dann aktivieren oder deaktivieren die Option unter dem **Debuggen** Knoten.  
  
2.  Bevor Sie fortfahren, auf die **Debuggen** Menü klicken Sie auf **Debuggen beenden** zu der die Ausführung.  
  
## <a name="using-the-parallel-tasks-window-and-the-tasks-view-of-the-parallel-stacks-window"></a>Verwenden des Fensters Parallele Aufgaben und der Aufgabenansicht des Fensters Parallele Stapel  
 Es empfiehlt sich, vor dem Fortfahren die früheren Prozeduren abzuschließen.  
  
#### <a name="to-restart-the-application-until-the-first-breakpoint-is-hit"></a>So starten Sie die Anwendung neu, bis der erste Haltepunkt erreicht wird  
  
1.  Auf der **Debuggen** Menü klicken Sie auf **Debuggen starten** und warten Sie, bis der erste Haltepunkt erreicht wird.  
  
2.  Auf der **Debuggen** Startmenü **Windows** , und klicken Sie dann auf **Threads**. Andocken der **Threads** Fenster am unteren Rand der Visual Studio.  
  
3.  Auf der **Debuggen** Startmenü **Windows** , und klicken Sie auf **Aufrufliste**. Andocken der **Aufrufliste** -Fensters am unteren Rand von Visual Studio.  
  
4.  Doppelklicken Sie auf einen Thread in der **Threads** Fenster können sie aktuelle. Aktuelle Threads sind durch einen gelben Pfeil gekennzeichnet. Wenn Sie den aktuellen Thread ändern, werden die anderen Fenster aktualisiert. Nun werden Aufgaben untersucht.  
  
5.  Auf der **Debuggen** Startmenü **Windows** , und klicken Sie dann auf **Parallele Aufgaben**. Die folgende Abbildung zeigt die **Parallele Aufgaben** Fenster.  
  
     ![Vier mit Aufgaben im Fenster "Parallele Aufgaben"](../debugger/media/pdw-walkthrough-6.png "PDW_Walkthrough_6")  
  
     Für jede ausgeführte Aufgabe können Sie die zugehörige ID lesen. Diese wird zusammen mit der gleichnamigen Eigenschaft, der ID und dem Namen des ausführenden Threads und ihrer Position zurückgegeben (wenn Sie mit dem Mauszeiger darauf zeigen, wird eine QuickInfo mit der gesamten Aufrufliste angezeigt). Darüber hinaus unter der **Aufgabe** Spalte sehen Sie die Methode, die an die Aufgabe übergeben wurde; das heißt, der Ausgangspunkt.  
  
     Alle Spalten können sortiert werden. Beachten Sie das Sortiersymbol, das Sortierspalte und -richtung angibt. Sie können auch die Anordnung der Spalten ändern, indem Sie sie nach links oder rechts ziehen.  
  
     Der gelbe Pfeil gibt die aktuelle Aufgabe an. Sie können zwischen Aufgaben wechseln, indem Sie auf eine Aufgabe doppelklicken oder indem Sie das Kontextmenü aufrufen. Beim Wechseln zwischen Aufgaben wird der zugrunde liegende Thread zum aktuellen Thread, und die übrigen Fenster werden aktualisiert.  
  
     Wenn Sie manuell von einer Aufgabe zu einer anderen wechseln, wird der gelbe Pfeil verschoben. Ein weißer Pfeil zeigt jedoch weiterhin die Aufgabe an, die die Unterbrechung des Debuggers verursacht hat.  
  
#### <a name="to-resume-execution-until-the-second-breakpoint"></a>So setzen Sie die Ausführung bis zum zweiten Haltepunkt fort  
  
1.  Um die Ausführung fortzusetzen, bis der zweite Breakpoint erreicht wird, auf die **Debuggen** Menü klicken Sie auf **Weiter**.  
  
     Zuvor die **Status** Artikel haben Sie alle Aufgaben ausgeführt, aber nun werden zwei Aufgaben wartet. Aufgaben können aus vielen anderen Gründen blockiert werden. In der **Status** Spalte, zeigen Sie auf eine wartende Aufgabe, um zu erfahren, warum er blockiert wird. In der folgenden Abbildung wartet beispielsweise Aufgabe 3 auf Aufgabe 4.  
  
     ![2 wartende Aufgaben im Fenster "Parallele Aufgaben"](../debugger/media/pdb-walkthrough-7.png "PDB_Walkthrough_7")  
  
     Aufgabe 4 wiederum wartet auf einen Monitor, der zu dem Thread gehört, der Aufgabe 2 zugewiesen ist.  
  
     ![Wartende Aufgabe und QuickInfo im Aufgabenfenster](../debugger/media/pdb-walkthrough-7a.png "PDB_Walkthrough_7A")  
  
     Sie können eine Aufgabe kennzeichnen, indem Sie auf das Flag in der ersten Spalte der **Parallele Aufgaben** Fenster.  
  
     Kennzeichnen können Sie Aufgaben zwischen den verschiedenen Haltepunkten einer Debugsitzung verfolgen oder Aufgaben filtern, deren Aufruflisten, in angezeigt werden, der **parallele Stapel** Fenster.  
  
     Sie bei Verwendung der **parallele Stapel** Fenster oben haben Sie die Anwendungsthreads angezeigt. Anzeigen der **parallele Stapel** Fenster erneut, aber dieses Mal anzeigen Aufgaben der Anwendung. Hierzu **Aufgaben** in das Feld auf der linken oberen Ecke. In der folgenden Abbildung wird die Aufgabenansicht dargestellt.  
  
     ![Threadansicht im Fenster "Parallele Stapel"](../debugger/media/pdb-walkthrough-8.png "PDB_Walkthrough_8")  
  
     Threads, die derzeit keine Aufgaben ausführen, werden werden nicht angezeigt, in der Aufgabenansicht des der **parallele Stapel** Fenster. Auch für Threads, die Aufgaben ausführen, werden einige der für Aufgaben irrelevanten Stapelrahmen im Stapel von oben und unten gefiltert.  
  
     Anzeigen der **Parallele Aufgaben** Fenster erneut. Klicken Sie mit der rechten Maustaste auf einen Spaltenheader, um das Kontextmenü für die betreffende Spalte aufzurufen.  
  
     ![Ansicht "Kontextmenü" im Fenster "Parallele Aufgaben"](../debugger/media/pdb-walkthrough-8a.png "PDB_Walkthrough_8A")  
  
     Über das Kontextmenü können Spalten hinzugefügt und entfernt werden. Die Spalte AppDomain ist z. B. nicht ausgewählt. Daher wird sie in der Liste nicht aufgeführt. Klicken Sie auf **übergeordneten**. Die **übergeordneten** Spalte wird ohne Werte für die vier Aufgaben angezeigt.  
  
#### <a name="to-resume-execution-until-the-third-breakpoint"></a>So setzen Sie die Ausführung bis zum dritten Haltepunkt fort  
  
1.  Um die Ausführung fortzusetzen, bis zum dritte Haltepunkt erreicht wird, auf die **Debuggen** Menü klicken Sie auf **Weiter**.  
  
     Eine neue Aufgabe, Aufgabe 5, wird nun ausgeführt, und Aufgabe 4 ist nun wartend. Sie sehen dies überprüfen, indem mit dem Mauszeiger auf die wartende Aufgabe in der **Status** Fenster. In der **übergeordneten** Spalte, beachten Sie, dass Aufgabe 4 ist das übergeordnete Element von Aufgabe 5.  
  
     Um die über-/ unterordnungsbeziehung besser zu visualisieren, Maustaste den **übergeordneten** Spaltenüberschrift, und klicken Sie dann auf **übergeordneten untergeordneten Ansicht**. Die Anzeige entspricht der folgenden Abbildung:  
  
     ![Übergeordnete&#45;untergeordnete Ansicht im Fenster "Parallele Aufgaben"](../debugger/media/pdb-walkthrough-9.png "PDB_Walkthrough_9")  
  
     Sie stellen fest, dass Aufgabe 4 und Aufgabe 5 im selben Thread ausgeführt werden. Diese Informationen werden nicht angezeigt, der **Threads** Fenster; sehen sie hier ein weiterer Vorteil ist die **Parallele Aufgaben** Fenster. Um dies zu bestätigen, zeigen Sie die **parallele Stapel** Fenster. Stellen Sie sicher, dass Ihnen eingesehene **Aufgaben**. Suchen Sie die Aufgaben 4 und 5 durch Doppelklicken in der **Parallele Aufgaben** Fenster. Wenn Sie so vorgehen, die blaue Hervorhebung der **parallele Stapel** Fenster wird aktualisiert. Sie können die Aufgaben 4 und 5 auch suchen, durch das Scannen von QuickInfos für die **parallele Stapel** Fenster.  
  
     ![Aufgabe der Ansicht im Fenster "Parallele Stapel"](../debugger/media/pdb-walkthrough-9a.png "PDB_Walkthrough_9A")  
  
     In der **parallele Stapel** rechten Maustaste auf S.P, und klicken Sie dann auf **zu Thread wechseln**. Das Fenster wechselt zur Threadansicht, und der entsprechende Frame wird angezeigt. Sie können beide Aufgaben im selben Thread sehen.  
  
     ![Hervorgehobener Thread in der Ansicht "Threads"](../debugger/media/pdb-walkthrough-9b.png "PDB_Walkthrough_9B")  
  
     Dies ist ein weiterer Vorteil der Aufgabenansicht im der **parallele Stapel** Fenster im Vergleich zu den **Threads** Fenster.  
  
#### <a name="to-resume-execution-until-the-fourth-breakpoint"></a>So setzen Sie die Ausführung bis zum vierten Haltepunkt fort  
  
1.  Um die Ausführung fortzusetzen, bis zum dritte Haltepunkt erreicht wird, auf die **Debuggen** Menü klicken Sie auf **Weiter**. Klicken Sie auf die **ID** Spaltenüberschrift sortiert nach ID auf. Die Anzeige entspricht der folgenden Abbildung:  
  
     ![Aufgaben in 4 Zuständen im Fenster "Parallele Stapel"](../debugger/media/pdb-walkthrough-10.png "PDB_Walkthrough_10")  
  
     Da Aufgabe 5 abgeschlossen wurde, wird sie nicht mehr angezeigt. Wenn dies auf Ihrem Computer nicht der Fall ist und der Deadlock nicht angezeigt wird, führen Sie einen Schritt aus, indem Sie F11 drücken.  
  
     Aufgabe 3 und Aufgabe 4 warten nun auf einander, und für sie ist ein Deadlock eingetreten. Es sind auch fünf neue Aufgaben vorhanden, die untergeordnete Elemente von Aufgabe 2 darstellen und nun geplant sind. Geplante Aufgaben sind Aufgaben, die im Code gestartet, jedoch noch nicht ausgeführt wurden. Aus diesem Grund die **Speicherort** und **Threadzuweisung** Spalten leer sind.  
  
     Anzeigen der **parallele Stapel** Fenster erneut. Der Header der einzelnen Felder weist jeweils eine QuickInfo auf, in der die Thread-IDs und -Namen angegeben werden. Wechseln Sie zur Ansicht der Aufgaben in der **parallele Stapel** Fenster. Zeigen Sie auf einen Header, um die Aufgaben-ID sowie den Namen und den Status der Aufgabe anzuzeigen, wie in der folgenden Abbildung veranschaulicht.  
  
     ![Header-QuickInfo im Fenster "Parallele Stapel"](../debugger/media/pdb-walkthrough-11.png "PDB_Walkthrough_11")  
  
     Sie können die Aufgaben nach Spalten gruppieren. In der **Parallele Aufgaben** Fenster mit der rechten Maustaste die **Status** Spaltenüberschrift, und klicken Sie dann auf **Gruppieren nach Status**. Die folgende Abbildung zeigt die **Parallele Aufgaben** nach Status gruppierte Fenster.  
  
     ![Gruppiert Aufgaben im Fenster "Parallele Aufgaben"](../debugger/media/pdb-walkthrough-12.png "PDB_Walkthrough_12")  
  
     Sie können auch nach einer beliebigen anderen Spalte gruppieren. Durch das Gruppieren von Aufgaben können sich auf eine Teilmenge von Aufgaben konzentrieren. Jede reduzierbare Gruppe weist eine Anzahl von Elementen auf, die zu einer Gruppe gehören. Sie können alle Elemente in der Gruppe auch schnell kennzeichnen, indem Sie auf die **Flag** Schaltfläche rechts neben der **reduzieren** Schaltfläche.  
  
     ![Gruppierte Stapel im Fenster "Parallele Stapel"](../debugger/media/pdb-walkthrough-12a.png "PDB_Walkthrough_12A")  
  
     Das letzte Feature von der **Parallele Aufgaben** Fenster, um zu überprüfen ist im Kontextmenü angezeigt wird, wenn Sie eine Aufgabe mit der rechten Maustaste.  
  
     ![Kontextmenü im Fenster "Parallele Aufgaben"](../debugger/media/pdb-walkthrough-12b.png "PDB_Walkthrough_12B")  
  
     Im Kontextmenü sind weitere Befehle enthalten, die vom Status der Aufgabe abhängen. Folgende Befehle zählen **Kopie**, **Alles markieren**, **Hexadezimale Anzeige**, **zu Aufgabe wechseln**, **fixieren zugewiesen Thread**, **Einfrieren aller Threads, aber dies**, und **zugewiesenen Thread reaktivieren**, und **Flag**.  
  
     Sie können den zugrunde liegenden Thread einer Aufgabe oder mehrerer Aufgaben einfrieren, oder Sie können alle Threads außer dem zugewiesenen Thread einfrieren. Ein eingefrorener Thread wird dargestellt, der **Parallele Aufgaben** Fenster befindet sich in der **Threads** Fenster durch ein blaues *anhalten* Symbol.  
  
## <a name="summary"></a>Zusammenfassung  
 Diese exemplarische Vorgehensweise veranschaulicht die **Parallele Aufgaben** und **parallele Stapel** Debuggerfenster. Verwenden Sie diese Fenster für tatsächliche Projekte, in denen Code mit mehreren Threads enthalten ist. Sie können parallelen Code in C++, C# oder Visual Basic untersuchen.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Multithreadanwendungen](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Debugger – Grundlagen](../debugger/debugger-basics.md)   
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)   
 [Parallele Programmierung](http://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)   
 [Concurrency Runtime](http://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)   
 [Verwenden das Fenster "Parallele Stapel"](../debugger/using-the-parallel-stacks-window.md)   
 [Verwenden des Fensters „Aufgaben“](../debugger/using-the-tasks-window.md)



