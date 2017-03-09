---
title: "Analysieren der Speicherauslastung von Store-Apps (VB, C#, C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: 24238fc0-40b8-4079-8579-698211db9a26
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Analysieren der Speicherauslastung von Store-Apps (VB, C#, C++)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In Visual Studio 2013 Update 2 können Sie das Speicherauslastungstool im Leistungs\- und Diagnosehub verwenden, um die Speicherauslastung von in C\#, Visual Basic oder C\+\+ und XAML geschriebenen Windows\-Runtime\-Apps zu analysieren.  Insbesondere können Sie:  
  
-   Die Speicherauslastung Ihrer App direkt in Visual Studio überwachen, während Sie ein Szenario entwickeln.  Sie brauchen dazu keine System\- oder Drittanbietertools zu verwenden.  
  
-   Mit einem einzigen Klick detaillierte Momentaufnahmen des Zustands Ihres App\-Speichers erstellen.  
  
-   Momentaufnahmen vergleichen, um die Ursache subtiler oder komplexer Speicherprobleme zu finden.  
  
> [!NOTE]
>  In diesem Thema wird beschrieben, wie Sie das Speicherauslastungstool verwenden, um C\#\- und Visual Basic\-Apps zu analysieren.  
>   
>  Der Leistungs\- und Diagnosehub bietet Ihnen viele Optionen zum Ausführen und Verwalten von Diagnosesitzungen.  Beispielsweise können Sie das CPU\-Auslastungstool auf Windows Phone\- oder Windows Store\-Apps ausführen oder die Diagnosesitzung auf dem Visual Studio\-Computer, einem Windows Phone, einem Windows Store\-Gerät oder in einem der Visual Studio\-Emulatoren oder \-Simulatoren ausführen.  Weitere Informationen finden Sie unter [Ausführen von Leistungs\- und Diagnosetools](../Topic/Run%20analysis%20tools%20from%20the%20Performance%20and%20Diagnostic%20page.md).  
>   
>  Wie Sie die Speicherauslastung in Windows Store\-Apps analysieren, die JavaScript und HTML verwenden, erfahren Sie unter [Speicherauslastung analysieren \(JavaScript\)](http://msdn.microsoft.com/en-us/library/windows/apps/jj819176.aspx).  
>   
>  Weitere Informationen über das Speicherauslastungstool, darunter über das Analysieren von C\+\+\- und C\+\+\/Cx\-Apps, finden Sie unter [Diagnose von Speicherproblemen mit dem neuen Speicherauslastungstool in Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=394706) im Microsoft Application Lifecycle Management Blog.  
  
##  <a name="BKMK_Start_a_Memory_Usage_diagnostic_session"></a> Starten einer Diagnosesitzung zur Speicherauslastung  
  
1.  Öffnen Sie Ihr Projekt in Visual Studio.  
  
2.  Wählen Sie im Menü **Debuggen**, **Leistung und Diagnose** aus.  
  
3.  Wählen Sie auf der Seite des Leistungs\- und Diagnosehub **Speicherauslastung**  aus und danach die Schaltfläche **Starten**.  
  
     ![Diagnosesitzung zur Speicherauslastung starten](../profiling/media/memuse_start_diagnosticssession.png "MEMUSE\_Start\_DiagnosticsSession")  
  
###  <a name="BKMK_Choose_the_programming_languages_to_include"></a> Auswahl des Profilerstellungsmodus  
 Möglicherweise testen Sie eine systemeigene Komponente zusammen mit der verwalteten App, die Ihr Startprojekt ist.  Oder die verwaltete App ist nur eine Testumgebung und Sie interessiert nur der systemeigene Speicher.  Vielleicht möchten Sie auch erfahren, welche Beziehung zwischen Ihrer verwalteten App und Windows\-Runtime besteht.  Wählen Sie in solchen Situationen **Einstellungen** und dann die gewünschte Sprache oder die gewünschten Sprachen.  
  
 ![Programmiersprachen wählen](../profiling/media/memuse_start_chooselanguages.png "MEMUSE\_Start\_ChooseLanguages")  
  
##  <a name="BKMK_Monitor_memory_use"></a> Speicherverwendung überwachen  
 Sie können das **Speicherauslastungstool** verwenden, um detaillierte Berichte zu erstellen, mit denen Sie Probleme finden und beheben, aber Sie können dieses Tool auch verwenden, um die Echtzeit\-Speicherauswirkungen eines Szenarios zu untersuchen, das Sie gerade entwickeln.  
  
 Wenn Sie eine Diagnosesitzung starten, startet Ihre App und die Seite "Leistung und Diagnose" zeigt eine Zeitachse der Speicherverwendung Ihrer App an.  
  
 ![Speichernutzung überwachen](../profiling/media/memuse_beforefirstsnapshot.png "MEMUSE\_BeforeFirstSnapshot")  
  
 Während Ihre App ausgeführt wird, können Sie neue Funktionen ausprobieren oder Szenarios untersuchen, bei denen eventuell Probleme auftreten.  Die Zeitachse der Speicherauslastung zeigt Schwankungen im Speicher Ihrer App an, während diese ausgeführt wird.  
  
 Spitzen in der Zeitachse weisen normalerweise darauf hin, dass eine Routine in der App Daten erfasst oder erstellt und diese dann verwirft, wenn die Verarbeitung abgeschlossen ist.  Hohe Spitzen weisen auf Methoden hin, die Sie ggf. optimieren können.  Problematischer ist ein Anstieg in der Auslastung von Speicher, der nicht zurückgegeben wird, denn dies kann auf ineffiziente Speicherverwendung oder sogar einen Speicherverlust hindeuten.  
  
###  <a name="BKMK_Close_a_monitoring_session"></a> Schließen der Überwachungssitzung  
 ![Auflistung anhalten](../profiling/media/memuse__stopcollection.png "MEMUSE\_\_StopCollection")  
  
 Um eine Überwachungssitzung zu schließen, ohne einen Bericht zu erstellen, schließen Sie das Diagnosefenster einfach.  Um einen Bericht zu generieren, wenn Sie Momentaufnahmen erstellt haben, wählen Sie **Beenden**.  
  
##  <a name="BKMK_Take_snapshots_to_analyze_the_memory_state_of_your_app"></a> Momentaufnahmen erstellen, um den Speicherzustand Ihrer App zu analysieren  
 Wenn Sie auf ein Speicherproblem stoßen und es untersuchen möchten, können Sie während der Diagnosesitzung Momentaufnahmen erstellen, um Speicherobjekte zu bestimmten Zeitpunkten zu erfassen.  Da eine App eine Vielzahl verschiedener Arten von Objekten verwendet, sollten Sie Ihre Analyse auf ein Szenario ausrichten.  Empfehlenswert ist es auch, vor dem Auftreten eines Speicherproblems eine Baselinemomentaufnahme der App zu erstellen, nach dem ersten Auftreten des Problems eine weitere Momentaufnahme zu erstellen und eine oder mehrere zusätzliche, wenn Sie das Szenario wiederholen.  
  
 Um Momentaufnahmen zu erstellen, starten Sie eine neue Diagnosesitzung.  Wählen Sie **Momentaufnahme erstellen**, wenn Sie mit dem Erfassen der Speicherdaten beginnen möchten.  Um einen Bericht zu erstellen, wählen Sie **Beenden**.  
  
##  <a name="BKMK_Memory_Usage_overview_page"></a> Übersichtsseite Speicherauslastung  
 Wenn Sie die Datenerfassung beenden, hält das Speicherauslastungstool die App an und zeigt die Übersicht an.  
  
 ![Übersichtsseite "Speicherauslastung"](../profiling/media/memuse__reportoverview.png "MEMUSE\_\_ReportOverview")  
  
###  <a name="BKMK_Memory_Usage_snapshot_views"></a> Ansichten der Momentaufnahmen zur Speicherauslastung  
 Die Ansichten der Momentaufnahmen dienen dazu, detaillierte Berichte in neuen Visual Studio\-Fenstern zu öffnen.  Es gibt zwei zwei Arten von Ansichten:  
  
-   Ein [Berichte über Momentaufnahmendetails](../profiling/memory-usage-without-debugging2.md#BKMK_Snapshot_details_reports) zeigt die Arten und Instanzen in einer Momentaufnahme.  
  
-   Ein [Bericht über Momentaufnahmenunterschiede](../profiling/memory-usage-without-debugging2.md#BKMK_Snapshot_difference__diff__reports) vergleicht die Arten und Instanzen in zwei Momentaufnahmen.  
  
 ![Links Snapshot&#45;Ansicht](../profiling/media/memuse__snapshotview_numbered.png "MEMUSE\_\_SnapshotView\_Numbered")  
  
 Die nummerierten Objekte im Bild sind Links, die Momentaufnahmenberichte öffnen.  
  
|||  
|-|-|  
|![Schritt 1](../profiling/media/procguid_1.png "ProcGuid\_1")|Der Text des Links zeigt die Gesamtzahl der Bytes im Speicher zum Zeitpunkt der Momentaufnahme.<br /><br /> Wählen Sie diesen Link, um einen Bericht über Momentaufnahmendetails anzuzeigen, der nach der Gesamtgröße der Typinstanzen geordnet ist.|  
|![Schritt 2](../profiling/media/procguid_2.png "ProcGuid\_2")|Der Text des Links zeigt die Gesamtzahl der Objekte im Speicher zum Zeitpunkt der Momentaufnahme.<br /><br /> Wählen Sie diesen Link, um einen Bericht über Momentaufnahmendetails anzuzeigen, der nach der Anzahl der Typinstanzen geordnet ist.|  
|![Schritt 3](../profiling/media/procguid_3.png "ProcGuid\_3")|Der Text des Links zeigt den Unterschied zwischen der Gesamtgröße der Objekte im Speicher zum Zeitpunkt dieser Momentaufnahme und der Gesamtgröße der vorhergehenden Momentaufnahme.<br /><br /> Er zeigt eine positive Zahl, wenn die Speichergröße dieser Momentaufnahme größer ist als die der vorhergehenden, und eine negative Zahl, wenn die Speichergröße kleiner ist.  Der Linktext **Baseline** weist darauf hin, dass diese Momentaufnahme die erste in dieser Diagnosesitzung ist, **No Difference** bedeutet, dass die Differenz null ist.<br /><br /> Wählen Sie diesen Link, um einen Bericht über Momentaufnahmenunterschiede anzuzeigen, der nach den Unterschieden in der Gesamtgröße der Typinstanzen geordnet ist.|  
|![Schritt 4](../profiling/media/procguid_4.png "ProcGuid\_4")|Der Text des Links zeigt den Unterschied zwischen der Gesamtzahl an Speicherobjekten in dieser Momentaufnahme und der Zahl der Objekte in der vorhergehenden Momentaufnahme.<br /><br /> Wählen Sie diesen Link, um einen Bericht über Momentaufnahmenunterschiede anzuzeigen, der nach den Unterschieden in der Gesamtzahl der Typinstanzen geordnet ist.|  
  
##  <a name="BKMK_Snapshot_reports"></a> Momentaufnahmenberichte  
 ![Speicherauslastung Snapshot&#45;Bericht](../profiling/media/memuse_snapshotreport_all.png "MEMUSE\_SnapshotReport\_All")  
  
###  <a name="BKMK_Snapshot_report_trees"></a> Strukturen der Momentaufnahmenberichte  
  
####  <a name="BKMK_Managed_Heap"></a> Verwalteter Heap  
 Die Struktur des verwalteten Heaps [Struktur des verwalteten Heaps (Momentaufnahmendetails)](../profiling/memory-usage-without-debugging2.md#BKMK_Managed_Heap_tree__Snapshot_details_) und die [Struktur des verwalteten Heaps (Momentaufnahmenunterschiede)](../profiling/memory-usage-without-debugging2.md#BKMK_Managed_Heap_tree__Snapshot_diff_) zeigen die Typen und Instanzen im Bericht.  Wenn Sie einen Typ oder eine Instanz auswählen, werden die **Pfade zum Stamm** und die Strukturen der **referenzierten Objekte** für das gewählte Element angezeigt.  
  
####  <a name="BKMK_Paths_to_Root"></a> Pfade zum Stamm  
 Die [Struktur der Pfade zum Stamm (Momentaufnahmendetails)](../profiling/memory-usage-without-debugging2.md#BKMK_Paths_to_Root_tree__Snapshot_details_) und die [Struktur der Pfade zum Stamm (Momentaufnahmenunterschiede)](../profiling/memory-usage-without-debugging2.md#BKMK_Paths_to_Root_tree__Snapshot_diff_) zeigen die Kette der Objekte, die den Typ oder die Instanz referenzieren.  Der Garbage Collector von .NET Framework bereinigt den Speicher für ein Objekt nur dann, wenn alle Verweise darauf freigegeben wurden.  
  
####  <a name="BKMK_Referenced_Objects"></a> Referenzierte Objekte  
 Die [Struktur der referenzierten Objekte (Momentaufnahmendetails)](../profiling/memory-usage-without-debugging2.md#BKMK_Referenced_Objects_tree__Snapshot_details_) und die [Struktur der referenzierten Objekte (Momentaufnahmenunterschiede)](../profiling/memory-usage-without-debugging2.md#BKMK_Referenced_Objects_tree__Snapshot_diff_) zeigen die Objekte, die der gewählte Typ oder die gewählte Instanz referenziert.  
  
###  <a name="BKMK_Object_Type_and_Instance_fields"></a> Objekttyp und Instanzenfelder  
 Wenn ein **Objekttyp**\-Eintrag über untergeordnete Einträge verfügt, können Sie diese über das Pfeilsymbol anzeigen.  Ist die Farbe des **Objekttyp**\-Textes blau, können Sie es auswählen, um zu dem Objekt in dessen Quellcodedatei zu navigieren.  Die Datei wird in einem separaten Fenster geöffnet.  
  
 Instanzennamen sind eindeutige IDs, die durch das Speicherauslastungstool generiert werden.  
  
> [!TIP]
>  Wenn Sie einen Typ bemerken, den Sie nicht einfach identifizieren können, oder wenn Sie nicht wissen, wie er mit Ihrem Code zusammenhängt, machen Sie sich darüber keine Gedanken.  Wahrscheinlich handelt es sich um ein Objekt aus dem Framework, dem Betriebssystem oder dem Compiler, das das Speicherauslastungstool anzeigt, weil es mit den Besitzketten Ihrer Objekte zusammenhängt.  
  
###  <a name="BKMK_Report_tree_filters_"></a> Berichtsstrukturenfilter  
 Die meisten Apps enthalten überraschend viele Typen, von denen die meisten für den App\-Entwickler nicht von Interesse sind.  Das Speicherauslastungstool definiert zwei Filter, mit denen Sie die meisten dieser Typen in den Strukturen des **verwalteten Heaps** und der **Pfade zum Stamm** verbergen können.  Sie können eine Struktur auch nach dem Typennamen filtern.  
  
 ![Sortier&#45; und Filteroptionen](../profiling/media/memuse_sortandfilter.png "MEMUSE\_SortAndFilter")  
  
####  <a name="BKMK_Filter"></a> Filter  
 Geben Sie in das Feld **Filter** eine Zeichenfolge ein, um die Strukturanzeigen auf Typen zu beschränken, die diese Zeichenfolge enthalten.  Der Filter berücksichtigt die Groß\-\/Kleinschreibung nicht und erkennt die angegebene Zeichenfolge in jedem Teil des Typennamens.  
  
####  <a name="BKMK_Collapse_Small_Objects"></a> Kleine Objekte reduzieren  
 Wird dieser Filter angewendet, dann werden Typen mit einer **Größe \(Bytes\)** von weniger als 0,5 Prozent der Gesamtgröße des Speichers bei Momentaufnahme in der Liste des **verwalteten Heaps** verborgen.  
  
####  <a name="BKMK_Just_My_Code"></a> Nur mein Code  
 Der Filter **Nur mein Code** verbirgt die meisten Instanzen, die durch externen Code generiert werden.  Externe Typen gehören zum Betriebssystem oder zu Framework\-Komponenten oder werden durch den Compiler generiert.  
  
##  <a name="BKMK_Snapshot_details_reports"></a> Berichte über Momentaufnahmendetails  
 Berichte über Momentaufnahmendetails werden verwendet, um sich auf eine Momentaufnahme aus einer Diagnosesitzung zu konzentrieren.  Um einen Detailbericht zu öffnen, wählen Sie einen der Links aus der Ansicht der Momentaufnahme, wie im Bild unten gezeigt.  Beide Links öffnen denselben Bericht; der Unterschied besteht lediglich in der Sortierreihenfolge der Struktur des **Managed Heap**.  In beiden Fällen können Sie die Sortierreihenfolge ändern, nachdem der Bericht geöffnet wurde.  
  
 ![Links zum Snapshot&#45;Bericht in einer Snapshot&#45;Ansicht](../profiling/media/memuse_snapshotview_snapshotdetailslinks.png "MEMUSE\_SnapshotView\_SnapshotDetailsLinks")  
  
-   Der Link **MB** ordnet den Bericht nach der Spalte **Inklusive Größe \(Bytes\)**.  
  
-   Der Link **Objekte** ordnet den Bericht nach der Spalte **Anzahl**.  
  
###  <a name="BKMK_Managed_Heap_tree__Snapshot_details_"></a> Struktur des verwalteten Heaps \(Momentaufnahmendetails\)  
 Die Struktur des **verwalteten Heaps** führt die Objekttypen auf, die im Speicher gehalten werden.  Sie können den Typennamen erweitern, um die zehn größten Instanzen des Typs nach Größe geordnet anzuzeigen.  Wenn Sie einen Typ oder eine Instanz auswählen, werden die **Pfade zum Stamm** und die Strukturen der **referenzierten Objekte** für das gewählte Element angezeigt.  
  
 ![Verwalteter Heap&#45;Baum](../profiling/media/memuse__snapshotdetails_managedheaptree.png "MEMUSE\_\_SnapshotDetails\_ManagedHeapTree")  
  
|||  
|-|-|  
|**Objekttyp**|Der Name des Typs oder der Objektinstanz.|  
|**Anzahl**|Die Anzahl der Objektinstanzen des Typs.  Für eine Instanz ist die Anzahl stets 1.|  
|**Größe \(Bytes\)**|Für Typen: Die Größe aller Instanzen des Typs in der Momentaufnahme des Speichers, ohne die Größe der in den Instanzen enthaltenen Objekte.<br /><br /> Für Instanzen: Die Größe des Objekts ohne die Größe der in den Instanzen enthaltenen Objekte.|  
|**Inklusive Größe \(Bytes\)**|Die Größe der Instanzen des Typs oder einer einzelnen Instanz, einschließlich der Größe der enthaltenen Objekte.|  
  
###  <a name="BKMK_Paths_to_Root_tree__Snapshot_details_"></a> Struktur der Pfade zum Stamm \(Momentaufnahmendetails\)  
 Die **Struktur der Pfade zum Stamm** zeigt die Kette der Objekte, die den Typ oder die Instanz referenzieren.  Der Garbage Collector von .NET Framework bereinigt den Speicher für ein Objekt nur dann, wenn alle Verweise darauf freigegeben wurden.  
  
 ![Pfade zum Stammbaum für Typen](../profiling/media/memuse_snapshotdetails_type_pathstoroottree.png "MEMUSE\_SnapshotDetails\_Type\_PathsToRootTree")  
  
 Wenn Sie einen Typ in der Struktur der **Pfade zum Stamm** anzeigen, wird die Zahl der Objekte der Typen mit Verweisen auf diesen Typ in der Spalte **Verweiszähler** angezeigt.  Wenn Sie eine Instanz analysieren, wird die Spalte nicht angezeigt.  
  
###  <a name="BKMK_Referenced_Objects_tree__Snapshot_details_"></a> Struktur der referenzierten Objekte \(Momentaufnahmendetails\)  
 Die Struktur der **referenzierten Objekte**  zeigt die Objekte, die der gewählte Typ oder die gewählte Instanz referenziert.  
  
 ![Referenzierter Objektbaum für Instanzen](../profiling/media/memuse_snapshotdetails_referencedobjects_instance.png "MEMUSE\_SnapshotDetails\_ReferencedObjects\_Instance")  
  
|||  
|-|-|  
|**Objekttyp \/ \-instanz**|Der Name des Typs oder der Objektinstanz.|  
|**Größe \(Bytes\)**|Für Typen: Die Größe aller Instanzen des Typs ohne die Größe der in dem Typ enthaltenen Objekte.<br /><br /> Für Instanzen: Die Größe des Objekts ohne die Größe der in dem Objekt enthaltenen Objekte.|  
|**Inklusive Größe \(Bytes\)**|Die Gesamtgröße der Instanzen des Typs oder die Größe der Instanz, einschließlich der Größe der enthaltenen Objekte.|  
  
##  <a name="BKMK_Snapshot_difference__diff__reports"></a> Bericht über Momentaufnahmenunterschiede  
 Ein Bericht über Momentaufnahmenunterschiede zeigt die Unterschiede zwischen der primären Momentaufnahme und der direkt davor erstellten Momentaufnahme.  Um einen solchen Bericht zu öffnen, wählen Sie einen der Links in der Momentaufnahmenansicht, wie im Bild unten gezeigt.  Beide Links öffnen denselben Bericht; der Unterschied besteht lediglich in der Sortierreihenfolge der Struktur des **Managed Heap**.  Sie können die Sortierreihenfolge ändern, nachdem der Bericht geöffnet wurde.  
  
 ![Links zum Unterschiedebericht in einer Snapshot&#45;Ansicht](../profiling/media/memuse_snapshotview_snapshotdifflinks.png "MEMUSE\_SnapshotView\_SnapshotDiffLinks")  
  
-   Der Link **MB** ordnet den Bericht nach der Spalte **Inklusive Größe \(Bytes\)**.  
  
-   Der Link **Objekte** ordnet den Bericht nach der Spalte **Anzahl**.  
  
###  <a name="BKMK_Managed_Heap_tree__Snapshot_diff_"></a> Struktur des verwalteten Heaps \(Momentaufnahmenunterschiede\)  
 Die Struktur des **verwalteten Heaps** führt die Objekttypen auf, die im Speicher gehalten werden.  Sie können den Typennamen erweitern, um die zehn größten Instanzen des Typs nach Größe geordnet anzuzeigen.  Wenn Sie einen Typ oder eine Instanz auswählen, werden die **Pfade zum Stamm** und die Strukturen der **referenzierten Objekte** für das gewählte Element angezeigt.  
  
 ![Verwalteter Heap&#45;Baum für einen Typ im Unterschiedebericht](../profiling/media/memuse_snapshotdiff_type_heap.png "MEMUSE\_SnapshotDiff\_Type\_Heap")  
  
 Im Bild sind die Spalten **Anzahl**, **Größe \(Bytes\)** und **Inklusive Größe \(Bytes\)** reduziert.  
  
|||  
|-|-|  
|**Objekttyp**|Der Name des Typs oder der Objektinstanz.|  
|**Anzahl**|Die Zahl der Instanzen eines Typs in der primären Momentaufnahme.  **Für eine Instanz ist die Anzahl**  stets 1.|  
|**Anzahlunterschied**|Für Typen: Der Unterschied zwischen der Anzahl der Instanzen des Typs in der primären Momentaufnahme und der vorhergehenden Momentaufnahme.  Für Instanzen ist das Feld leer.|  
|**Größe \(Bytes\)**|Die Größe der Objekte in der primären Momentaufnahme ohne die Größe der in den Objekten enthaltenen Objekte.  Für Typen sind **Größe \(Bytes\)** und **Inklusive Größe \(Bytes\)** die Gesamtgrößen der Typinstanzen.|  
|**Unterschied der Gesamtgrößen \(Bytes\)**|Für Typen: Der Unterschied in der Gesamtgröße der Typinstanzen zwischen der primären Momentaufnahme und der vorhergehenden Momentaufnahme, ohne die Größe der in den Instanzen enthaltenen Objekte.  Für Instanzen ist das Feld leer.|  
|**Inklusive Größe \(Bytes\)**|Die Größe der Objekte in der primären Momentaufnahme einschließlich der Größe der in den Objekten enthaltenen Objekte.|  
|**Unterschied der inklusiven Größen \(Bytes\)**|Für Typen: Der Unterschied in der Größe aller Typinstanzen zwischen der primären Momentaufnahme und der vorhergehenden Momentaufnahme, einschließlich der Größe der in den Objekten enthaltenen Objekte.  Für Instanzen ist das Feld leer.|  
  
###  <a name="BKMK_Paths_to_Root_tree__Snapshot_diff_"></a> Struktur der Pfade zum Stamm \(Momentaufnahmenunterschiede\)  
 Die **Struktur der Pfade zum Stamm** zeigt die Kette der Objekte, die den Typ oder die Instanz referenzieren.  Der Garbage Collector von .NET Framework bereinigt den Speicher für ein Objekt nur dann, wenn alle Verweise darauf freigegeben wurden.  
  
 ![Pfade zum Stammbaum für Instanzen in anderer Ansicht](../profiling/media/memuse_snapshotdiff_pathstoroot_instance_all.png "MEMUSE\_SnapshotDiff\_PathsToRoot\_Instance\_All")  
  
###  <a name="BKMK_Referenced_Objects_tree__Snapshot_diff_"></a> Struktur der referenzierten Objekte \(Momentaufnahmenunterschiede\)  
 Die Struktur der **referenzierten Objekte** zeigt die Objekte, die der primäre Typ oder die Instanz referenziert.  
  
 ![Referenzierter Objektbaum für Instanzen](../profiling/media/memuse_snapshotdetails_referencedobjects_instance.png "MEMUSE\_SnapshotDetails\_ReferencedObjects\_Instance")  
  
|||  
|-|-|  
|**Objekttyp \/ \-instanz**|Der Name des Typs oder der Objektinstanz.|  
|**Größe \(Bytes\)**|Für Instanzen: Die Größe des Objekts in der primären Momentaufnahme ohne die Größe der in der Instanz enthaltenen Objekte.<br /><br /> Für Typen: Die Gesamtgröße der Instanzen des Typs in der primären Momentaufnahme ohne die Größe der in der Instanz enthaltenen Objekte.|  
|**Inklusive Größe \(Bytes\)**|Die Größe der Objekte in der primären Momentaufnahme einschließlich der Größe der in den Objekten enthaltenen Objekte.|  
  
## Siehe auch  
 [JavaScript\-Speicher](../profiling/javascript-memory.md)   
 [Analysieren der App\-Leistung](../Topic/Analyze%20the%20performance%20of%20Windows%20Store%20apps%20using%20Visual%20Studio%20diagnostic%20tools.md)   
 [Ausführen von Leistungs\- und Diagnosetools](../Topic/Run%20analysis%20tools%20from%20the%20Performance%20and%20Diagnostic%20page.md)   
 [Bewährte Vorgehensweisen für die Leistungsverbesserung in Windows Store\-Apps mit C\+\+, C\# und Visual Basic](http://msdn.microsoft.com/library/windows/apps/hh750313.aspx)