---
title: Analysieren von .NET Framework Arbeitsspeicher Problemen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.diagnostics.managedmemoryanalysis
ms.assetid: 43341928-9930-48cf-a57f-ddcc3984b787
caps.latest.revision: 9
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e94edbeac381ac634171507766126ab954153eb1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295886"
---
# <a name="analyze-net-framework-memory-issues"></a>Analysieren von .NET Framework-Arbeitsspeicherproblemen
Ermitteln Sie mithilfe des Analyzers für verwalteten Speicher von Visual Studio Speicherverluste und ineffiziente Arbeitsspeichernutzung in .NET Framework-Code. Die mindestens erforderliche .NET Framework-Version für den Zielcode ist .NET Framework 4.5.  
  
 Das Speicher Analysetool analysiert Informationen in *Dumpdateien mit Heap Daten* , die eine Kopie der Objekte im Arbeitsspeicher einer APP sind. Sie können Dumpdateien (.dmp) von der Visual Studio IDE oder mit anderen Systemtools sammeln.  
  
- Sie können eine einzelne Momentaufnahme analysieren, um die relativen Auswirkungen der Objekttypen auf die Arbeitsspeichernutzung zu verstehen und Code in der App zu suchen, die Arbeitsspeicher auf ineffiziente Weise verwendet.  
  
- Sie können auch zwei Momentaufnahmen einer APP vergleichen (*diff*), um Bereiche im Code zu suchen, die bewirken, dass die Arbeitsspeicher Nutzung im Laufe der Zeit zunimmt.  
  
  Eine exemplarische Vorgehensweise zur Analyse des verwalteten Speichers finden [Sie unter Verwenden von Visual Studio 2013 zur Diagnose von .net-Speicherproblemen in der Produktion](https://devblogs.microsoft.com/devops/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production/) im Visual Studio Alm + Team Foundation Server Blog.  
  
## <a name="BKMK_Contents"></a> Inhalt  
 [Arbeitsspeicher Nutzung in .NET Framework-apps](#BKMK_Memory_use_in__NET_Framework_apps)  
  
 [Identifizieren eines Arbeitsspeicher Problems in einer APP](#BKMK_Identify_a_memory_issue_in_an_app)  
  
 [Sammeln von Speicher Momentaufnahmen](#BKMK_Collect_memory_snapshots)  
  
 [Analysieren der Arbeitsspeicher Nutzung](#BKMK_Analyze_memory_use)  
  
## <a name="BKMK_Memory_use_in__NET_Framework_apps"></a>Arbeitsspeicher Nutzung in .NET Framework-apps  
 .NET Framework ist eine speicherbereinigte Laufzeitumgebung, sodass die Speichernutzung in den meisten Apps kein Problem darstellt. In Anwendungen mit langer Laufzeit jedoch, wie z. B. Webdienste und Anwendungen, sowie auf Geräten, die einen begrenzten Arbeitsspeicher haben, kann die Ansammlung von Objekten im Arbeitsspeicher die Leistung der App und auch das Gerät, auf dem sie ausgeführt wird, beeinträchtigen. Übermäßige Arbeitsspeichernutzung kann die Anwendung und den Computer durch Ressourcen blockieren, wenn der Garbage Collector zu häufig ausgeführt wird oder wenn das Betriebssystem gezwungen wird, Arbeitsspeicher zwischen RAM und Datenträger zu verschieben. Im ungünstigsten Fall kann eine Anwendung bei einer Ausnahme aufgrund "nicht genügend Arbeitsspeicher" abstürzen.  
  
 Der verwaltete .net- *Heap* ist eine Region des virtuellen Arbeitsspeichers, in der die von einer APP erstellten Verweis Objekte gespeichert werden. Die Lebensdauer der Objekte wird vom Garbage Collector (GC) verwaltet. Der Garbage Collector verwendet Verweise, um Objekte zu verfolgen, die Speicherblöcke belegen. Ein Verweis wird erstellt, wenn ein Objekt erstellt und einer Variablen zugewiesen wird. Ein einzelnes Objekt kann mehrere Verweise haben. Beispielsweise können zusätzliche Verweise auf ein Objekt erstellt werden, indem das Objekt einer Klasse, Auflistung oder anderen Datenstruktur hinzufügt wird oder indem das Objekt einer zweiten Variable zugeordnet wird. Eine weniger offensichtliche Methode zum Erstellen eines Verweises besteht darin, dass ein Objekt einen Handler zum Ereignis eines anderen Objekts hinzufügt. In diesem Fall behält das zweite Objekt den Verweis zum ersten Objekt, bis der Handler explizit entfernt ist oder das zweite Objekt vernichtet wird.  
  
 Für jede Anwendung verwaltet das GC eine Verweisstruktur, die die Objekte verfolgt, auf die von der Anwendung verwiesen wird. Die *Referenz* Struktur verfügt über einen Satz von Stämme, der globale und statische Objekte sowie zugehörige Thread Stapel und dynamisch instanziierte Objekte umfasst. Ein Objekt verfügt über einen Stamm, wenn das Objekt mindestens ein übergeordnetes Objekt hat, das einen Verweis darauf enthält. Das GC kann den Arbeitsspeicher eines Objekts nur dann freigeben, wenn kein anderes Objekt oder keine andere Variable in der Anwendung über einen Verweis darauf verfügt.  
  
 ![Zurück zum obersten](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
## <a name="BKMK_Identify_a_memory_issue_in_an_app"></a>Identifizieren eines Arbeitsspeicher Problems in einer APP  
 Das sichtbarste Symptom von Arbeitsspeicherproblemen ist die Leistung der App, insbesondere dann, wenn die Leistung im Zeitverlauf abnimmt. Eine Verringerung der Leistung anderer Apps während der Ausführung Ihrer App kann ebenfalls auf ein Arbeitsspeicherproblem hinweisen. Wenn Sie ein Arbeitsspeicher Problem vermuten, verwenden Sie ein Tool wie Task-Manager oder Windows-System [Monitor](https://technet.microsoft.com/library/cc749249.aspx) , um weitere Informationen zu erhalten. Schauen Sie beispielsweise, ob die Gesamtgröße des Speichers angestiegen ist, was sich aber nicht als potenzielle Quelle von Arbeitsspeicherverlusten erklären lässt:  
  
 ![Konsistentes Speicher Wachstum in Ressourcenmonitor](../misc/media/mngdmem-resourcemanagerconsistentgrowth.png "MNGDMEM_ResourceManagerConsistentGrowth")  
  
 Sie können auch Arbeitsspeicherspitzen beobachten, die größer sind, als sie es Ihrer Kenntnis des Codes nach vermuten würden, was möglicherweise auf eine ineffiziente Arbeitsspeicherverwendung in einer Prozedur hinweist:  
  
 ![Arbeitsspeicher Spitzen in Ressourcen-Manager](../misc/media/mngdmem-resourcemanagerspikes.png "MNGDMEM_ResourceManagerSpikes")  
  
## <a name="BKMK_Collect_memory_snapshots"></a>Sammeln von Speicher Momentaufnahmen  
 Das Speicher Analysetool analysiert Informationen in *Dumpdateien* , die Heap Informationen enthalten. Sie können Dumpdateien in Visual Studio erstellen, oder Sie können ein Tool wie [procdump](https://technet.microsoft.com/sysinternals/dd996900.aspx) von [Windows Sysinternals](https://technet.microsoft.com/sysinternals)verwenden. Weitere Informationen finden Sie im Blog des Visual Studio Debugger-Teams unter [Was ist ein Dump und wie erstelle ich einen?](https://blogs.msdn.microsoft.com/debugger/2009/12/30/what-is-a-dump-and-how-do-i-create-one/)  
  
> [!NOTE]
> Die meisten Tools können Dumpinformationen mit oder ohne vollständige Heapspeicherdaten sammeln. Die Speicheranalyse von Visual Studio erfordert vollständige Heapinformationen.  
  
 **So erfassen Sie einen Dump aus Visual Studio**  
  
1. Sie können eine Dumpdatei für einen Prozess erstellen, der von einem Visual Studio-Projekt gestartet wurde, oder Sie fügen den Debugger an einen laufenden Prozess an. Siehe [Anfügen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
2. Beenden Sie die Ausführung. Der Debugger wird angehalten, wenn Sie im Menü **Debuggen** die Option **Alle unterbrechen** auswählen, oder bei einer Ausnahme oder an einem Breakpoint.  
  
3. Wählen Sie im Menü **Debuggen** die Option **Dump speichern**unter aus. Geben Sie im Dialogfeld **Dump speichern** unter einen Speicherort an, und stellen Sie sicher, dass **Minidump mit Heap** (Standard) in der Liste **Dateityp** ausgewählt ist.  
  
   **So vergleichen Sie zwei Speicher Momentaufnahmen**  
  
   Um die gestiegene Arbeitsspeichernutzung einer App zu analysieren, erfassen Sie zwei Dumpdateien aus einer einzelnen Instanz der App.  
  
   ![Zurück zum obersten](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
## <a name="BKMK_Analyze_memory_use"></a>Analysieren der Arbeitsspeicher Nutzung  
 [Filtern der Liste der Objekte](#BKMK_Filter_the_list_of_objects) **&#124;** [Analysieren der Arbeitsspeicher Daten aus einer einzelnen Momentaufnahme](#BKMK_Analyze_memory_data_in_from_a_single_snapshot) **&#124;** [Vergleichen von zwei Speicher Momentaufnahmen](#BKMK_Compare_two_memory_snapshots)  
  
 So analysieren Sie eine Dumpdatei bei Problemen mit der Arbeitsspeichernutzung  
  
1. Wählen Sie in Visual Studio **Datei**, **Öffnen** aus, und geben Sie die Dumpdatei an.  
  
2. Wählen Sie auf der Seite **minidumpdateizusammenfassung** die Option **verwalteten Speicher Debuggen**.  
  
    ![Zusammenfassungs Seite der Dumpdatei](../misc/media/mngdmem-dumpfilesummary.png "MNGDMEM_DumpFileSummary")  
  
   Die Speicheranalyse startet eine Debugsitzung, um die Datei zu analysieren, und zeigt die Ergebnisse auf der Seite "Heap-Ansicht" an:  
  
   ![Zurück zum obersten](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
### <a name="BKMK_Filter_the_list_of_objects"></a>Filtern der Liste der Objekte  
 Standardmäßig wird die Liste der Objekte in einer Speichermomentaufnahme von der Speicheranalyse gefiltert, um nur die Typen und die Instanzen anzuzeigen, die Benutzercode sind, und nur die Typen darzustellen, deren inklusive Gesamtgröße einen prozentualen Schwellenwert der gesamten Heapgröße überschreitet. Sie können diese Optionen in der Liste der **Ansichts Einstellungen** ändern:  
  
|||  
|-|-|  
|**Nur meinen Code aktivieren**|"Nur eigenen Code" blendet die häufigsten Systemobjekte aus, sodass nur die Typen, die Sie erstellen, in der Liste angezeigt werden.<br /><br /> Sie können auch die Option nur eigenen Code im Dialogfeld Visual Studio- **Optionen** festlegen. Klicken Sie im Menü **Debuggen** auf **Optionen und Einstellungen**. Wählen Sie auf der Registerkarte **Debuggen**/**Allgemein** **nur eigenen Code**aus.|  
|**Kleine Objekte reduzieren**|**Kleine Objekte** reduzieren blendet alle Typen aus, deren Gesamtgröße insgesamt kleiner als 0,5 Prozent der gesamten Heap Größe ist.|  
  
 Sie können die Typliste auch filtern, indem Sie eine Zeichenfolge in das **Suchfeld** eingeben. Die Liste enthält nur die Typen, deren Namen die Zeichenfolge enthalten.  
  
 ![Zurück zum obersten](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
### <a name="BKMK_Analyze_memory_data_in_from_a_single_snapshot"></a>Analysieren von Speicherdaten aus einer einzelnen Momentaufnahme  
 Visual Studio beginnt eine neue Debugsitzung zur Analyse der Datei und zeigt die Speicherdaten in einem Fenster Heap-Ansicht an.  
  
 ![Die Objekttyp Liste](../misc/media/dbg-mma-objecttypelist.png "DBG_MMA_ObjectTypeList")  
  
 ![Zurück zum obersten](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
#### <a name="object-type-table"></a>Objekttyptabelle  
 In der Tabelle ganz oben werden die Typen von Objekten aufgeführt, die im Arbeitsspeicher gespeichert werden.  
  
- **Count** zeigt die Anzahl der Instanzen des Typs in der Momentaufnahme an.  
  
- **Size (Bytes)** ist die Größe aller Instanzen des Typs, ausgenommen der Größe der Objekte, auf die verwiesen wird. Die  
  
- **Inklusive Größe (Bytes)** umfasst die Größe der Objekte, auf die verwiesen wird.  
  
  Sie können das Instanzen Symbol (![das Instanzsymbol in der Spalte Objekttyp](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon")) in der Spalte **Objekttyp** auswählen, um eine Liste der Instanzen des Typs anzuzeigen.  
  
#### <a name="instance-table"></a>Instanztabelle  
 ![Instanzen Tabelle](../misc/media/dbg-mma-instancestable.png "DBG_MMA_InstancesTable")  
  
- **Instance** ist der Speicherort des Objekts, das als Objekt Bezeichner des Objekts fungiert.  
  
- Der **Wert** zeigt den tatsächlichen Wert von Werttypen. Sie können den Mauszeiger über den Namen eines Referenztyps bewegen, sodass sein Datenwert in einem Datentipp angezeigt wird.  
  
   ![Instanzwerte in einem Datentipp](../misc/media/dbg-mma-instancevaluesindatatip.png "DBG_MMA_InstanceValuesInDataTip")  
  
- **Size (Bytes)** ist die Größe des Objekts, ohne die Größe der Objekte, auf die es verweist. Die  
  
- **Inklusive Größe (Bytes)** umfasst die Größe der Objekte, auf die verwiesen wird.  
  
  Standardmäßig werden Typen und Instanzen nach **inklusiver Größe (Bytes)** sortiert. Wählen Sie eine Spaltenüberschrift in der Liste aus, um die Sortierreihenfolge ändern.  
  
#### <a name="paths-to-root"></a>Pfade zum Stamm  
  
- Für einen aus der Tabelle **Objekttyp** ausgewählten Typ werden in der Tabelle **Pfade zum** Stamm die eindeutigen Typhierarchien angezeigt, die zu Stamm Objekten für alle Objekte des Typs führen, sowie die Anzahl der Verweise auf den Typ, der sich in der Hierarchie oberhalb des Typs befindet.  
  
- Für ein Objekt, das aus der Instanz eines Typs ausgewählt wurde, zeigen die **Pfade zum** Stamm ein Diagramm der tatsächlichen Objekte an, die einen Verweis auf die Instanz enthalten. Sie können den Mauszeiger über den Namen des Objekts bewegen, sodass sein Datenwert in einem Datentipp angezeigt wird.  
  
#### <a name="referenced-types--referenced-objects"></a>Referenzierte Typen / Referenzierte Objekte  
  
- Für einen aus der Tabelle **Objekttyp** ausgewählten Typ zeigt die Registerkarte **referenzierte Typen** die Größe und die Anzahl der referenzierten Typen an, die von allen Objekten des ausgewählten Typs gespeichert werden.  
  
- Für eine ausgewählte Instanz eines Typs zeigt **referenzierte Objekte** die Objekte an, die von der ausgewählten Instanz gehalten werden. Sie können den Mauszeiger über den Namen bewegen, sodass sein Datenwert in einem Datentipp angezeigt wird.  
  
  **Zirkuläre Verweise**  
  
  Ein Objekt kann auf ein zweites Objekt verweisen, das direkt oder indirekt einen Verweis auf das erste Objekt enthält. Wenn die Speicher Analyse auf diese Situation stößt, wird der Verweis Pfad nicht mehr erweitert, und es wird eine **[Cycle erkannt]** -Anmerkung zur Auflistung des ersten Objekts hinzugefügt und beendet.  
  
  **Stamm Typen**  
  
  Die Speicheranalyse fügt Stammobjekten Anmerkungen hinzu, die die Art des gespeicherten Verweises beschreiben:  
  
|Annotation|Beschreibung|  
|----------------|-----------------|  
|**Statische Variable** `VariableName`|Eine statische Variable. `VariableName` ist der Name der Variablen.|  
|**Finalisierungshandle**|Ein Verweis von der Finalizer-Warteschlange|  
|**Lokale Variable**|Eine lokale Variable.|  
|**Starkes handle**|Ein Handle für einen starken Verweis von der Objekthandletabelle.|  
|**Async. Fixierte Handles**|Ein asynchrones angeheftetes Objekt von der Objekthandletabelle.|  
|**Abhängiges handle**|Ein abhängiges Objekt von der Objekthandletabelle.|  
|**Fixierte Handles**|Ein angehefteter starker Verweis von der Objekthandletabelle.|  
|**Ref count-handle**|Ein Objekt mit Verweiszählung von der Objekthandletabelle.|  
|**Sizedref-handle**|Ein starkes Handle, das eine ungefähre Größe des kollektiven Abschlusses aller Objekte und Objektstämme zur Garbage Collection-Zeit enthält.|  
|**Angeheftete lokale Variable**|Eine angeheftete lokale Variable.|  
  
### <a name="BKMK_Compare_two_memory_snapshots"></a>Vergleichen von zwei Speicher Momentaufnahmen  
 Sie können zwei Dumpdateien eines Prozesses vergleichen, um nach Objekten zu suchen, die möglicherweise die Ursache von Speicherverlusten sind. Das Intervall zwischen der Auflistung aus der ersten (früheren) und zweiten (späteren) Datei sollte so groß sein, dass der Anstieg der Anzahl von Objekten, die Speicherverluste verursachen, leicht ersichtlich ist. So vergleichen Sie die beiden Dateien  
  
1. Öffnen Sie die zweite Dumpdatei, und wählen Sie dann auf der Seite **minidumpdateizusammenfassung** die Option **verwalteten Speicher Debuggen** .  
  
2. Öffnen Sie auf der Seite "Speicher Analysebericht" die Liste **Baseline auswählen** , und wählen Sie dann **Durchsuchen** aus, um die erste Dumpdatei anzugeben.  
  
   Das Analysetool fügt dem oberen Bereich des Berichts Spalten hinzu, die den Unterschied zwischen der **Anzahl**, der **Größe**und der **inklusiven Größe** der Typen auf die Werte in der früheren Momentaufnahme anzeigen.  
  
   ![Diff-Spalten in der Typliste](../misc/media/mngdmem-diffcolumns.png "MNGDMEM_DiffColumns")  
  
   Außerdem wird der Tabelle " **path to root** " eine diff-Spalte für **Verweis Zähler** hinzugefügt.  
  
   ![Zurück zum obersten](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
## <a name="see-also"></a>Siehe auch  
 [Vs Alm TFS-Blog: Verwenden von Visual Studio 2013 zur Diagnose von .net-Speicherproblemen in der Produktion](https://devblogs.microsoft.com/devops/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production/)   
 [Channel 9 &#124; -Analyse von &#124; Visual Studio TV-verwaltetem Arbeitsspeicher](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Managed-Memory-Analysis)   
 [Channel 9 &#124; -Analyse der &#124; verwalteten Speicher für Visual Studio-Toolbox in Visual Studio 2013](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Managed-Memory-Analysis-in-Visual-Studio-2013)