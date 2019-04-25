---
title: Analysieren von .NET Framework-Arbeitsspeicherproblemen | Microsoft-Dokumentation
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
ms.openlocfilehash: 75a51cbe851b6566ab210a3c8ae12a9b7c2e0d2b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60107657"
---
# <a name="analyze-net-framework-memory-issues"></a>Analysieren von .NET Framework-Arbeitsspeicherproblemen
Ermitteln Sie mithilfe des Analyzers für verwalteten Speicher von Visual Studio Speicherverluste und ineffiziente Arbeitsspeichernutzung in .NET Framework-Code. Die mindestens erforderliche .NET Framework-Version für den Zielcode ist .NET Framework 4.5.  
  
 Das arbeitsspeicheranalysetool analysiert Informationen in *Dumpdateien mit Heapdaten* , die eine Kopie der Objekte in einer app Speichers. Sie können Dumpdateien (.dmp) von der Visual Studio IDE oder mit anderen Systemtools sammeln.  
  
- Sie können eine einzelne Momentaufnahme analysieren, um die relativen Auswirkungen der Objekttypen auf die Arbeitsspeichernutzung zu verstehen und Code in der App zu suchen, die Arbeitsspeicher auf ineffiziente Weise verwendet.  
  
- Sie können auch vergleichen (*Diff*) zweier Momentaufnahmen einer App aus, um Bereiche in Ihrem Code, die dazu führen, den Arbeitsspeicher dass zu verwenden, um im Laufe der Zeit erhöhen.  
  
  Eine exemplarische Vorgehensweise des Analyzers für verwalteten Arbeitsspeicher finden Sie unter [mithilfe von Visual Studio 2013 to Diagnose .NET Memory Issues in Production](http://blogs.msdn.com/b/visualstudioalm/archive/2013/06/20/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production.aspx) auf dem Visual Studio ALM + Team Foundation Server-Blog.  
  
## <a name="BKMK_Contents"></a> Inhalt  
 [Arbeitsspeichernutzung in .NET Framework-apps](#BKMK_Memory_use_in__NET_Framework_apps)  
  
 [Erkennen eines Arbeitsspeicherproblems in einer app](#BKMK_Identify_a_memory_issue_in_an_app)  
  
 [Sammeln von Momentaufnahmen des Arbeitsspeichers](#BKMK_Collect_memory_snapshots)  
  
 [Analysieren der arbeitsspeichernutzung](#BKMK_Analyze_memory_use)  
  
## <a name="BKMK_Memory_use_in__NET_Framework_apps"></a> Arbeitsspeichernutzung in .NET Framework-apps  
 .NET Framework ist eine speicherbereinigte Laufzeitumgebung, sodass die Speichernutzung in den meisten Apps kein Problem darstellt. In Anwendungen mit langer Laufzeit jedoch, wie z. B. Webdienste und Anwendungen, sowie auf Geräten, die einen begrenzten Arbeitsspeicher haben, kann die Ansammlung von Objekten im Arbeitsspeicher die Leistung der App und auch das Gerät, auf dem sie ausgeführt wird, beeinträchtigen. Übermäßige Arbeitsspeichernutzung kann die Anwendung und den Computer durch Ressourcen blockieren, wenn der Garbage Collector zu häufig ausgeführt wird oder wenn das Betriebssystem gezwungen wird, Arbeitsspeicher zwischen RAM und Datenträger zu verschieben. Im ungünstigsten Fall kann eine Anwendung bei einer Ausnahme aufgrund "nicht genügend Arbeitsspeicher" abstürzen.  
  
 .NET *verwalteten Heap* ist ein Bereich des virtuellen Speichers, in dem Verweisobjekte, die von einer Anwendung erstellt gespeichert werden. Die Lebensdauer der Objekte wird vom Garbage Collector (GC) verwaltet. Der Garbage Collector verwendet Verweise, um Objekte zu verfolgen, die Speicherblöcke belegen. Ein Verweis wird erstellt, wenn ein Objekt erstellt und einer Variablen zugewiesen wird. Ein einzelnes Objekt kann mehrere Verweise haben. Beispielsweise können zusätzliche Verweise auf ein Objekt erstellt werden, indem das Objekt einer Klasse, Auflistung oder anderen Datenstruktur hinzufügt wird oder indem das Objekt einer zweiten Variable zugeordnet wird. Eine weniger offensichtliche Methode zum Erstellen eines Verweises besteht darin, dass ein Objekt einen Handler zum Ereignis eines anderen Objekts hinzufügt. In diesem Fall behält das zweite Objekt den Verweis zum ersten Objekt, bis der Handler explizit entfernt ist oder das zweite Objekt vernichtet wird.  
  
 Für jede Anwendung verwaltet das GC eine Verweisstruktur, die die Objekte verfolgt, auf die von der Anwendung verwiesen wird. Die *Verweisstruktur* verfügt über eine Reihe von Stammelementen, einschließlich globale und statische Objekte sowie zugeordnete Threadstapel und dynamisch instanziierte Objekte. Ein Objekt verfügt über einen Stamm, wenn das Objekt mindestens ein übergeordnetes Objekt hat, das einen Verweis darauf enthält. Das GC kann den Arbeitsspeicher eines Objekts nur dann freigeben, wenn kein anderes Objekt oder keine andere Variable in der Anwendung über einen Verweis darauf verfügt.  
  
 ![Zurück nach oben](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
## <a name="BKMK_Identify_a_memory_issue_in_an_app"></a> Erkennen eines Arbeitsspeicherproblems in einer app  
 Das sichtbarste Symptom von Arbeitsspeicherproblemen ist die Leistung der App, insbesondere dann, wenn die Leistung im Zeitverlauf abnimmt. Eine Verringerung der Leistung anderer Apps während der Ausführung Ihrer App kann ebenfalls auf ein Arbeitsspeicherproblem hinweisen. Wenn Sie ein Arbeitsspeicherproblem vermuten, verwenden Sie ein Tool wie Task-Manager oder [Windows Performance Monitor](http://technet.microsoft.com/library/cc749249.aspx) um weiter zu untersuchen. Schauen Sie beispielsweise, ob die Gesamtgröße des Speichers angestiegen ist, was sich aber nicht als potenzielle Quelle von Arbeitsspeicherverlusten erklären lässt:  
  
 ![Konsistente speichervergrößerung im Ressourcenmonitor](../misc/media/mngdmem-resourcemanagerconsistentgrowth.png "MNGDMEM_ResourceManagerConsistentGrowth")  
  
 Sie können auch Arbeitsspeicherspitzen beobachten, die größer sind, als sie es Ihrer Kenntnis des Codes nach vermuten würden, was möglicherweise auf eine ineffiziente Arbeitsspeicherverwendung in einer Prozedur hinweist:  
  
 ![Speicherspitzen im Ressourcen-Manager](../misc/media/mngdmem-resourcemanagerspikes.png "MNGDMEM_ResourceManagerSpikes")  
  
## <a name="BKMK_Collect_memory_snapshots"></a> Sammeln von Momentaufnahmen des Arbeitsspeichers  
 Das arbeitsspeicheranalysetool analysiert Informationen in *Dumpdateien* , die Heapinformationen enthalten. Sie können Dumpdateien in Visual Studio erstellen oder Sie können ein Tool wie [ProcDump](http://technet.microsoft.com/sysinternals/dd996900.aspx) aus [Windows Sysinternals](http://technet.microsoft.com/sysinternals). Finden Sie unter [Was ist ein Speicherabbild, und wie erstelle ich eine?](http://blogs.msdn.com/b/debugger/archive/2009/12/30/what-is-a-dump-and-how-do-i-create-one.aspx) Blog des Visual Studio Debugger Team.  
  
> [!NOTE]
>  Die meisten Tools können Dumpinformationen mit oder ohne vollständige Heapspeicherdaten sammeln. Die Speicheranalyse von Visual Studio erfordert vollständige Heapinformationen.  
  
 **Sammeln Sie einen Dump von Visual Studio**  
  
1. Sie können eine Dumpdatei für einen Prozess erstellen, der von einem Visual Studio-Projekt gestartet wurde, oder Sie fügen den Debugger an einen laufenden Prozess an. Finden Sie unter [Anfügen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
2. Beenden Sie die Ausführung. Der Debugger hält bei der Auswahl **alle unterbrechen** auf die **Debuggen** Menü oder bei einer Ausnahme oder an einem Haltepunkt  
  
3. Auf der **Debuggen** Menü wählen **Dump speichern unter**. In der **Dump speichern unter** Dialogfeld Feld, geben Sie einen Speicherort aus, und stellen Sie sicher, dass **Minidump mit Heap** (Standardeinstellung) ausgewählt ist, der **Dateityp** Liste.  
  
   **Zum Vergleichen von zwei Speichermomentaufnahmen**  
  
   Um die gestiegene Arbeitsspeichernutzung einer App zu analysieren, erfassen Sie zwei Dumpdateien aus einer einzelnen Instanz der App.  
  
   ![Zurück nach oben](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
## <a name="BKMK_Analyze_memory_use"></a> Analysieren der arbeitsspeichernutzung  
 [Die Liste der Objekte filtern](#BKMK_Filter_the_list_of_objects) **&#124;** [Analysieren der Arbeitsspeicherdaten von einer einzelnen Momentaufnahme](#BKMK_Analyze_memory_data_in_from_a_single_snapshot) **&#124;** [vergleichen zwei Momentaufnahmen](#BKMK_Compare_two_memory_snapshots)  
  
 So analysieren Sie eine Dumpdatei bei Problemen mit der Arbeitsspeichernutzung  
  
1. Wählen Sie in Visual Studio **Datei**, **öffnen** , und geben Sie die Dumpdatei.  
  
2. Auf der **Minidumpdatei-Zusammenfassung** Seite **verwalteten Speicher Debuggen**.  
  
    ![Dumpdatei-Zusammenfassungsseite](../misc/media/mngdmem-dumpfilesummary.png "MNGDMEM_DumpFileSummary")  
  
   Die Speicheranalyse startet eine Debugsitzung, um die Datei zu analysieren, und zeigt die Ergebnisse auf der Seite "Heap-Ansicht" an:  
  
   ![Zurück nach oben](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
### <a name="BKMK_Filter_the_list_of_objects"></a> Die Liste der Objekte filtern  
 Standardmäßig wird die Liste der Objekte in einer Speichermomentaufnahme von der Speicheranalyse gefiltert, um nur die Typen und die Instanzen anzuzeigen, die Benutzercode sind, und nur die Typen darzustellen, deren inklusive Gesamtgröße einen prozentualen Schwellenwert der gesamten Heapgröße überschreitet. Sie können diese Optionen im Ändern der **Ansichtseinstellungen** Liste:  
  
|||  
|-|-|  
|**Nur meinen Code aktivieren**|"Nur eigenen Code" blendet die häufigsten Systemobjekte aus, sodass nur die Typen, die Sie erstellen, in der Liste angezeigt werden.<br /><br /> Sie können auch die Option nur mein Code festlegen, in der Visual Studio **Optionen** Dialogfeld. Klicken Sie im Menü **Debuggen** auf **Optionen und Einstellungen**. In der **Debuggen**/**allgemeine** Registerkarte auswählen, oder deaktivieren Sie **nur mein Code**.|  
|**Kleine Objekte reduzieren**|**Kleine Objekte reduzieren** Blendet alle Typen, deren inklusive Gesamtgröße weniger als 0,5 Prozent der gesamten Heapgröße überschreitet.|  
  
 Sie können auch die Datentyp-Liste filtern, durch Eingabe einer Zeichenfolge in die **Suche** Feld. Die Liste enthält nur die Typen, deren Namen die Zeichenfolge enthalten.  
  
 ![Zurück nach oben](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
### <a name="BKMK_Analyze_memory_data_in_from_a_single_snapshot"></a> Analysieren der Arbeitsspeicherdaten von einer einzelnen Momentaufnahme  
 Visual Studio beginnt eine neue Debugsitzung zur Analyse der Datei und zeigt die Speicherdaten in einem Fenster Heap-Ansicht an.  
  
 ![Die objekttypliste](../misc/media/dbg-mma-objecttypelist.png "DBG_MMA_ObjectTypeList")  
  
 ![Zurück nach oben](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
#### <a name="object-type-table"></a>Objekttyptabelle  
 In der Tabelle ganz oben werden die Typen von Objekten aufgeführt, die im Arbeitsspeicher gespeichert werden.  
  
- **Anzahl** zeigt die Anzahl der Instanzen des Typs in der Momentaufnahme.  
  
- **Größe (Bytes)** ist die Größe aller Instanzen des Typs, ohne die Größe der Objekte, die er Verweise enthält. Die  
  
- **Inklusive Größe (Bytes)** schließt die Größen von referenzierten Objekten.  
  
  Sie können das instanzensymbol (![das Instanzsymbol in der Spalte Objekttyp](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon")) in der **Objekttyp** Spalte zum Anzeigen einer Liste der Instanzen von der Geben Sie ein.  
  
#### <a name="instance-table"></a>Instanztabelle  
 ![Instanzentabelle](../misc/media/dbg-mma-instancestable.png "DBG_MMA_InstancesTable")  
  
- **Instanz** ist die Speicheradresse des Objekts, das als die Objekt-ID des Objekts fungiert  
  
- **Wert** zeigt den tatsächlichen Wert von Werttypen. Sie können den Mauszeiger über den Namen eines Referenztyps bewegen, sodass sein Datenwert in einem Datentipp angezeigt wird.  
  
   ![Werte in einem Datentipp Instanz](../misc/media/dbg-mma-instancevaluesindatatip.png "DBG_MMA_InstanceValuesInDataTip")  
  
- **Größe (Bytes)** ist die Größe des Objekts, ohne die Größe der Objekte, die er Verweise enthält. Die  
  
- **Inklusive Größe (Bytes)** schließt die Größen von referenzierten Objekten.  
  
  In der Standardeinstellung Typen und Instanzen nach sortiert sind **inklusive Größe (Bytes)**. Wählen Sie eine Spaltenüberschrift in der Liste aus, um die Sortierreihenfolge ändern.  
  
#### <a name="paths-to-root"></a>Pfade zum Stamm  
  
- Für einen aus der **Objekttyp** Tabelle, die **Pfade zum Stamm** Tabelle werden den eindeutigen Typhierarchien, führen zu den Stammobjekten für alle Objekte des Typs führen, sowie die Anzahl der Verweise auf die Typ, der in der Hierarchie jeweils darüber liegt.  
  
- Für ein von der Instanz eines Typs ausgewähltes Objekt **Pfade zum Stamm** zeigt ein Diagramm der tatsächlichen Objekte an, die einen Verweis auf die Instanz enthalten. Sie können den Mauszeiger über den Namen des Objekts bewegen, sodass sein Datenwert in einem Datentipp angezeigt wird.  
  
#### <a name="referenced-types--referenced-objects"></a>Referenzierte Typen / Referenzierte Objekte  
  
- Für einen aus der **Objekttyp** Tabelle, die **referenzierte Typen** Registerkarte zeigt die Größe und Anzahl der referenzierten Typen, die von allen Objekten des ausgewählten Typs gespeichert.  
  
- Für eine ausgewählte Instanz eines Typs **referenzierte Objekte** zeigt die Objekte, die von der ausgewählten Instanz gespeichert werden. Sie können den Mauszeiger über den Namen bewegen, sodass sein Datenwert in einem Datentipp angezeigt wird.  
  
  **Zirkuläre Verweise**  
  
  Ein Objekt kann auf ein zweites Objekt verweisen, das direkt oder indirekt einen Verweis auf das erste Objekt enthält. Wenn die Speicheranalyse auf diese Situation stößt, wird die Erweiterung des Verweispfads beendet und fügt eine **[Schleife ermittelt]** Anmerkung zur Auflistung des ersten Objekts und wird beendet.  
  
  **Stammtypen**  
  
  Die Speicheranalyse fügt Stammobjekten Anmerkungen hinzu, die die Art des gespeicherten Verweises beschreiben:  
  
|Anmerkung|Beschreibung|  
|----------------|-----------------|  
|**Die statische variable** `VariableName`|Eine statische Variable. `VariableName` ist der Name der Variablen.|  
|**Abschlusshandle**|Ein Verweis von der Finalizer-Warteschlange|  
|**Lokale Variable**|Eine lokale Variable.|  
|**Starkes Handle**|Ein Handle für einen starken Verweis von der Objekthandletabelle.|  
|**Async. Fixiertes Handle**|Ein asynchrones angeheftetes Objekt von der Objekthandletabelle.|  
|**Abhängiges Handle**|Ein abhängiges Objekt von der Objekthandletabelle.|  
|**Fixiertes Handle**|Ein angehefteter starker Verweis von der Objekthandletabelle.|  
|**RefCount-Handle**|Ein Objekt mit Verweiszählung von der Objekthandletabelle.|  
|**SizedRef-Handle**|Ein starkes Handle, das eine ungefähre Größe des kollektiven Abschlusses aller Objekte und Objektstämme zur Garbage Collection-Zeit enthält.|  
|**Angeheftete lokale variable**|Eine angeheftete lokale Variable.|  
  
### <a name="BKMK_Compare_two_memory_snapshots"></a> Vergleich von zwei Speichermomentaufnahmen  
 Sie können zwei Dumpdateien eines Prozesses vergleichen, um nach Objekten zu suchen, die möglicherweise die Ursache von Speicherverlusten sind. Das Intervall zwischen der Auflistung aus der ersten (früheren) und zweiten (späteren) Datei sollte so groß sein, dass der Anstieg der Anzahl von Objekten, die Speicherverluste verursachen, leicht ersichtlich ist. So vergleichen Sie die beiden Dateien  
  
1. Öffnen Sie die zweite Dumpdatei, und wählen Sie dann **verwalteten Speicher Debuggen** auf die **Minidumpdatei-Zusammenfassung** Seite.  
  
2. Öffnen Sie auf der Berichtsseite der Speicheranalyse, die **wählen Baseline** aus, und klicken Sie dann auf **Durchsuchen** um die erste Dumpdatei anzugeben.  
  
   Die Analyse fügt Spalten hinzu, im oberen Bereich des Berichts, der den Unterschied zwischen anzuzeigen die **Anzahl**, **Größe**, und **inklusive Größe** der Typen, um diese Werte in der frühere Momentaufnahme.  
  
   ![Unterschiedliche Spalten in der Typliste](../misc/media/mngdmem-diffcolumns.png "MNGDMEM_DiffColumns")  
  
   Ein **Verweiszähler Diff** Spalte wurde auch die **Pfade zum Stamm** Tabelle.  
  
   ![Zurück nach oben](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Inhalt](#BKMK_Contents)  
  
## <a name="see-also"></a>Siehe auch  
 [VS ALM TFS-Blog: Mithilfe von Visual Studio 2013 zur Diagnose .NET Memory Issues in Production](http://blogs.msdn.com/b/visualstudioalm/archive/2013/06/20/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production.aspx)   
 [Channel 9 &#124; Visual Studio-TV &#124; verwaltet Analyse der Speicherauslastung](http://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Managed-Memory-Analysis)   
 [Channel 9 &#124; Visual Studio-Toolbox &#124; verwaltet Analyse der Speicherauslastung in Visual Studio 2013](http://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Managed-Memory-Analysis-in-Visual-Studio-2013)