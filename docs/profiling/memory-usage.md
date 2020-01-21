---
title: Messen des Speicherverbrauchs in Ihren Apps
description: Suchen Sie nach Speicherverlusten und ineffizienter Arbeitsspeichernutzung beim Debuggen mit dem im Debugger integrierten Diagnosetool.
ms.custom: seodec18
ms.date: 04/25/2018
ms.topic: tutorial
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2876e1b25380719a4424c5828c8b37fb5bb72b41
ms.sourcegitcommit: 9a5cf730d8e43eed6eba25369b7b44cae0b26b98
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2020
ms.locfileid: "75929233"
---
# <a name="measure-memory-usage-in-visual-studio"></a>Messen der Speicherauslastung in Visual Studio

Suchen Sie Speicherverluste und ineffiziente Arbeitsspeichernutzung während des Debuggens mit dem im Debugger integrierten **Speicherauslastungs**-Diagnosetool. Mit dem Speicherauslastungstool können Sie einen oder mehrere *Momentaufnahmen* des verwalteten und nativen Momentaufnahme-Heaps erstellen, um ein besseres Verständnis darüber zu erlangen, welchen Einfluss die Speicherauslastung von Objekttypen hat. Sie können Momentaufnahmen von .NET-Apps, systemeigenen Apps und Apps in gemischtem Modus (.Net und systemeigen) erfassen.

Das folgende Bild zeigt das Fenster **Diagnosetools** (verfügbar in Visual Studio 2015 Update 1 und höheren Versionen):

![Diagnosetools-Update1](../profiling/media/diagnostictools-update1.png "Diagnosetools-Update1")

Obwohl Sie Speichermomentaufnahmen des Arbeitsspeichers zu jedem beliebigen Zeitpunkt im **Speicherauslastungstool** erfassen können, können Sie mit dem Visual Studio-Debugger kontrollieren, wie Ihre Anwendung die Ausführung vornimmt, und dabei Leistungsprobleme untersuchen. Festlegen von Haltepunkten, schrittweises Ausführen, alles unterbrechen und andere Debugger-Aktionen können Ihnen helfen, Ihre Leistungsuntersuchungen auf die relevantesten Codepfade zu fokussieren. Durch die Ausführung dieser Aktionen, während Ihre App ausgeführt wird, kann das Rauschen, das Sie nicht interessiert, vom Code entfernt werden, wodurch sich der Zeitaufwand, den Sie zur Diagnose eines Problems benötigen, maßgeblich verringert.

Sie können das Speichertool auch außerhalb des Debuggers verwenden. Siehe [Analysieren der Arbeitsspeicherauslastung ohne Visual Studio-Debugger](../profiling/memory-usage-without-debugging2.md). Unter Windows 7 und höher können Sie die Profilerstellungstools ohne den Debugger verwenden. Windows 8 und höher ist erforderlich, um die Profilerstellungstools mit dem Debugger auszuführen (Fenster **Diagnosetools**).

> [!NOTE]
> **Unterstützung für benutzerdefinierte Speicherbelegungen** Der native Speicherprofiler sammelt auf die Speicherbelegung bezogene [ETW-](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-)-Ereignisdaten, die zur Laufzeit ausgegeben werden.  Zuweisungen im CRT und Windows SDK wurden auf Quellebene kommentiert, sodass ihre Speicherbelegungsdaten erfasst werden können. Wenn Sie Ihre eigenen Zuweisungen schreiben, kann jede Funktion, die einen Zeiger auf neu zugewiesenen Heapspeicher zurückgibt, mit [__declspec](/cpp/cpp/declspec)(allocator) ergänzt werden, wie in diesem Beispiel für myMalloc zu sehen ist:
>
> `__declspec(allocator) void* myMalloc(size_t size)`

In diesem Tutorial werden Sie Folgendes durchführen:

> [!div class="checklist"]
> * Erstellen von Momentaufnahmen des Speichers
> * Analysieren der Speicherauslastungsdaten

## <a name="collect-memory-usage-data"></a>Sammeln von Speicherauslastungsdaten

1. Öffnen Sie das Projekt, das Sie in Visual Studio debuggen möchten, und legen Sie in Ihrer App einen Haltepunkt an dem Punkt fest, an dem Sie die CPU-Auslastung untersuchen möchten.

    Wenn Sie über einen Bereich verfügen, bei dem Sie ein Speicherproblem vermuten, legen Sie den ersten Haltepunkt fest, bevor das Speicherproblem auftritt.

    > [!TIP]
    > Da es schwierig sein kann, das Speicherprofil eines Vorgangs zu erfassen, der für Sie von Interesse ist, wenn Ihre App häufig Speicher zuweist und dessen Speicherung wieder aufhebt, richten Sie zu Beginn und zum Ende des Vorgangs Haltepunkte ein (oder gehen Sie schrittweise durch den Vorgang), um so den genauen Punkt zu finden, an dem sich der Speicher geändert hat.

2. Legen Sie einen zweiten Haltepunkt am Ende der Funktion oder des Codebereichs an, den Sie analysieren möchten (oder nachdem ein vermutetes Speicherproblem aufgetreten ist).

3. Das Fenster **Diagnosetools** wird automatisch angezeigt, es sei denn, Sie haben es deaktiviert. Klicken Sie auf **Debuggen** > **Windows** > **Diagnosetools anzeigen**, um das Fenster erneut aufzurufen.

4. Wählen Sie **Speicherauslastung** mit der Einstellung **Auswahltools** auf der Symbolleiste aus.

     ![Fenster „Diagnosetools“](../profiling/media/diag-tools-select-tool-2.png "DiagToolsSelectTool")

5. Klicken Sie auf **Debuggen / Debugging starten** (oder auf **Start** auf der Symbolleiste oder auf **F5**).

     Wenn das Laden der Anwendung abgeschlossen ist, wird die Zusammenfassungsansicht der Diagnosetools angezeigt.

     ![Registerkarte „Zusammenfassung“ der Diagnosetools](../profiling/media/diag-tools-summary-tab-2.png "DiagToolsSummaryTab")

     > [!NOTE]
     > Da das Erfassen von Speicherdaten die Debugleistung Ihrer systemeigenen Apps oder Ihrer Apps mit gemischtem Modus beeinträchtigen kann, sind Speichermomentaufnahmen standardmäßig deaktiviert. Starten Sie eine Debugsitzung, um Momentaufnahmen in nativen Apps oder in Apps im gemischten Modus zu aktivieren. Nutzen Sie dazu die Tastenkombination **F5**. Wenn das Fenster **Diagnosetools** angezeigt wird, wählen Sie die Registerkarte **Speicherauslastung** und dann **Heapprofilerstellung** aus.
     >
     >  ![Momentaufnahmen aktivieren](../profiling/media/dbgdiag_mem_mixedtoolbar_enablesnapshot.png "DBGDIAG_MEM_MixedToolbar_EnableSnapshot")
     >
     >  Beenden Sie den Debugvorgang (Tastenkombination: **UMSCHALTTASTE**+**F5**), und starten Sie ihn neu.

6. Um eine Momentaufnahme zu Beginn der Debugsitzung zu erstellen, wählen Sie auf der Übersichtssymbolleiste **Speicherauslastung** die Option **Momentaufnahme erstellen** aus. (Es kann hilfreich sein, auch hier einen Haltepunkt festzulegen.)

    ![Schaltfläche „Momentaufnahme erstellen“](../profiling/media/dbgdiag_mem_mixedtoolbar_takesnapshot.png "DBGDIAG_MEM_MixedToolbar_TakeSnapshot")

     > [!TIP]
     > Um eine Basislinie für Speichervergleiche zu erstellen, sollten Sie zu Beginn Ihrer Debugsitzung eine Momentaufnahme erstellen.

6. Führen Sie das Szenario aus, bei dem Ihr erster Haltepunkt erreicht wird.

7. Wählen Sie **Momentaufnahme erstellen** auf der Übersichtssymbolleiste **Speicherauslastung** aus, während der Debugger am ersten Haltepunkt angehalten wird.

8. Drücken Sie **F5**, um die App bis zum zweiten Haltepunkt auszuführen.

9. Erstellen Sie nun eine andere Momentaufnahme.

     An diesem Punkt können Sie beginnen, die Daten zu analysieren.

## <a name="analyze-memory-usage-data"></a>Analysieren der Speicherauslastungsdaten
Die Zeilen der Speicherauslastungs-Übersichtstabelle führt die Momentaufnahmen auf, die Sie während der Debugsitzung erstellt haben, und bietet Links zu detaillierteren Ansichten.

![Tabelle mit zusammengefassten Informationen zum Speicher](../profiling/media/dbgdiag_mem_summarytable.png "DBGDIAG_MEM_SummaryTable")

 Der Name der Spalten ist abhängig von dem Debugmodus, den Sie in den Projekteigenschaften gewählt haben: .NET, nativ oder gemischt (sowohl .NET als auch nativ).

- Die Spalten **Objekte (Diff.)** und **Zuweisungen (Diff.)** zeigen die Anzahl der Objekte im .NET-Speicher und im nativen Speicher zum Zeitpunkt der Erstellung der Momentaufnahme an.

- Die Spalte **Heapgröße (Diff)** zeigt die Anzahl der Bytes in den .NET- und nativen Heaps

Wenn Sie mehrere Momentaufnahmen erstellt haben, beinhalten die Zellen der Übersichtstabelle die Wertänderung zwischen Zeilenmomentaufnahme und vorheriger Momentaufnahme.

Um die Speicherauslastung zu analysieren, klicken Sie auf einen der Links. Ein detaillierter Bericht der Speicherauslastung wird geöffnet:

- Wählen Sie die Änderungsverknüpfung links des Pfeils aus (![Zunahme der Speicherauslastung](../profiling/media/prof-tour-mem-usage-up-arrow.png "Zunahme der Speicherauslastung")), um sich die Details des Unterschiedes zwischen aktueller Momentaufnahme und vorheriger Momentaufnahme anzeigen zu lassen. Ein roter Pfeil zeigt eine Zunahme der Speicherauslastung und ein grüner Pfeil die Abnahme der Speicherauslastung.

> [!TIP]
> Um Speicherprobleme schnell auszumachen, werden die Unterschiedsberichte nach Objekttypen sortiert, deren Anzahl sich am stärksten erhöht hat (klicken Sie auf die Änderungsverknüpfung in der Spalte **Objekte (Diff.)** ) oder deren gesamte Heapgröße sich am signifikantesten erhöht hat (klicken Sie auf die Änderungsverknüpfung in der Spalte **Heapgröße (Diff.)** ).

- Um nur die Details der ausgewählten Momentaufnahme anzuzeigen, klicken Sie auf die Verknüpfung ohne Änderung.

   Der Bericht wird in einem separaten Fenster angezeigt.

### <a name="managed-types-reports"></a>Berichte zu den verwalteten Typen
 Wählen Sie die aktuelle Verknüpfung einer **Objekte (Diff.)** - oder **Zuweisungen (Diff.)** -Zelle in der Übersichtstabelle der Speicherauslastung aus.

 ![Debugger; Berichte zu den verwalteten Typen; Pfade zum Stamm](../profiling/media/dbgdiag_mem_managedtypesreport_pathstoroot.png "DBGDIAG_MEM_ManagedTypesReport_PathsToRoot")

 Im oberen Bereich werden Anzahl und Größe der Typen in der Momentaufnahme angezeigt, einschließlich der Größe aller Objekte, auf die der Typ verweist (**Umfassende Größe**).

 Die Baumstruktur **Pfade zum Stamm** im unteren Bereich zeigt die Objekte an, die auf den im oberen Bereich ausgewählten Typ verweisen. Der .NET Framework-Garbage Collector bereinigt den Speicher für ein Objekt nur, wenn der letzte Typ, der darauf verweist, freigegeben wurde.

 Die Baumstruktur **Referenzierte Objekte** enthält die Verweise, die vom im oberen Bereich ausgewählten Typ gehalten werden.

 ![Berichtsansicht für verwaltete referenzierte Objekte](../profiling/media/dbgdiag_mem_managedtypesreport_referencedtypes.png "DBGDIAG_MEM_ManagedTypesReport_ReferencedTypes")

 Klicken Sie auf das Symbol ![Instanzsymbol](../profiling/media/dbgdiag_mem_instanceicon.png "DBGDIAG_MEM_InstanceIcon"), um die Instanzen eines ausgewählten Typs im oberen Bereich anzuzeigen.

 ![Ansicht „Instanzen“](../profiling/media/dbgdiag_mem_managedtypesreport_instances.png "DBGDIAG_MEM_ManagedTypesReport_Instances")

 Die Ansicht **Instanzen** zeigt die Instanzen des ausgewählten Objekts in der Momentaufnahme des oberen Bereichs an. Die Bereiche **Pfade zum Stamm** und **Referenzierte Objekte** zeigen die Objekte an, die auf die ausgewählte Instanz verweisen, sowie die Typen, auf die die ausgewählte Instanz verweist. Wenn der Debugger zu dem Zeitpunkt beendet wird, an dem die Momentaufnahme erstellt wurde, können Sie auf die Zelle **Wert** zeigen, um die Werte des Objekts in einer QuickInfo anzuzeigen.

### <a name="native-type-reports"></a>Berichte zu den systemeigenen Typen
 Wählen Sie die aktuelle Verknüpfung einer Zelle **Zuordnungen (Diff.)** oder **Heapgröße (Diff.)** aus der Speicherauslastungs-Übersichtstabelle des Fensters **Diagnosetools** aus.

 ![Ansicht der nativen Typen](../profiling/media/dbgdiag_mem_native_typesview.png "DBGDIAG_MEM_Native_TypesView")

 Die **Typenansicht** zeigt die Anzahl und Größe der Typen in der Momentaufnahme an.

- Wählen Sie das Instanzensymbol (![Instanzensymbol in der Spalte „Objekttyp“](../profiling/media/dbg_mma_instancesicon.png "DBG_MMA_InstancesIcon")) eines ausgewählten Typs aus, um sich Informationen zu Objekten des ausgewählten Typs in der Momentaufnahme anzeigen zu lassen.

     Die Ansicht **Instanzen** zeigt jede Instanz des ausgewählten Typs an. Durch Auswahl einer Instanz wird die Aufrufliste angezeigt, welche die Erstellung der Instanz im Bereich **Belegungsaufrufliste** bewirkt hat.

     ![Ansicht „Instanzen“](../profiling/media/dbgdiag_mem_native_instances.png "DBGDIAG_MEM_Native_Instances")

- Wählen Sie **Stapelansicht** im **Ansichtsmodus** , um den Zuweisungsstapel für den ausgewählten Typ anzuzeigen.

     ![Stapelansicht](../profiling/media/dbgdiag_mem_native_stacksview.png "DBGDIAG_MEM_Native_StacksView")

### <a name="change-diff-reports"></a>(Diff) Änderungsberichte

- Wählen Sie die Änderungsverknüpfung in einer Zelle der Übersichtstabelle der Registerkarte **Speicherauslastung** im Fenster **Diagnosetools** aus.

   ![Änderungs bzw. Unterschiedsbericht auswählen](../profiling/media/dbgdiag_mem_choosediffreport.png "DBGDIAG_MEM_ChooseDiffReport")

- Wählen Sie eine Momentaufnahme aus der Liste **Vergleichen mit** Liste eines verwalteten oder systemeigenen Berichts aus.

   ![Auswählen einer Momentaufnahme aus der Liste „Vergleichen mit“](../profiling/media/dbgdiag_mem_choosecompareto.png "DBGDIAG_MEM_ChooseCompareTo")

Der Änderungsbericht fügt dem Basisbericht Spalten (durch **(Diff)** gekennzeichnet) hinzu, die den Unterschied zwischen der Basismomentaufnahme und der Vergleichsmomentaufnahme anzeigen. So könnte ein Unterschiedsbericht der Ansicht mit nativen Typen aussehen:

![Ansicht „Unterschiede bei nativen Typen“](../profiling/media/dbgdiag_mem_native_typesviewdiff.png "DBGDIAG_MEM_Native_TypesViewDiff")

## <a name="blogs-and-videos"></a>Blogs und Videos

[Analyze CPU and Memory While Debugging (Analysieren der CPU und des Arbeitsspeichers beim Debuggen)](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ Team Blog: Memory Profiling in Visual C++ 2015 (Visual C++-Teamblog: Speicherprofilerstellung in Visual C++ 2015)](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial haben Sie gelernt, wie Speicherauslastungsdaten gesammelt und analysiert werden. Wenn Sie die [tour of the profiler (Einführung zum Profilerstellungsfeature)](../profiling/profiling-feature-tour.md) bereits abgeschlossen haben, sollten Sie sich einen Überblick darüber verschaffen, wie die CPU-Nutzung in Ihren Apps analysiert werden kann.

> [!div class="nextstepaction"]
> [Analysieren der CPU-Auslastung](../profiling/beginners-guide-to-performance-profiling.md)
