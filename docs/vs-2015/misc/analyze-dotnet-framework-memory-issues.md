---
title: Analyze .NET Framework memory issues | Microsoft Docs
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
  
 The memory analysis tool analyzes information in *dump files with heap data* that a copy of the objects in an app's memory. Sie können Dumpdateien (.dmp) von der Visual Studio IDE oder mit anderen Systemtools sammeln.  
  
- Sie können eine einzelne Momentaufnahme analysieren, um die relativen Auswirkungen der Objekttypen auf die Arbeitsspeichernutzung zu verstehen und Code in der App zu suchen, die Arbeitsspeicher auf ineffiziente Weise verwendet.  
  
- You can also compare (*diff*) two snapshots of an app to find areas in your code that cause the memory use to increase over time.  
  
  For a walkthrough of the managed memory analyzer, see [Using Visual Studio 2013 to Diagnose .NET Memory Issues in Production](https://devblogs.microsoft.com/devops/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production/) on the Visual Studio ALM + Team Foundation Server blog .  
  
## <a name="BKMK_Contents"></a> Inhalt  
 [Memory use in .NET Framework apps](#BKMK_Memory_use_in__NET_Framework_apps)  
  
 [Identify a memory issue in an app](#BKMK_Identify_a_memory_issue_in_an_app)  
  
 [Collect memory snapshots](#BKMK_Collect_memory_snapshots)  
  
 [Analyze memory use](#BKMK_Analyze_memory_use)  
  
## <a name="BKMK_Memory_use_in__NET_Framework_apps"></a> Memory use in .NET Framework apps  
 .NET Framework ist eine speicherbereinigte Laufzeitumgebung, sodass die Speichernutzung in den meisten Apps kein Problem darstellt. In Anwendungen mit langer Laufzeit jedoch, wie z. B. Webdienste und Anwendungen, sowie auf Geräten, die einen begrenzten Arbeitsspeicher haben, kann die Ansammlung von Objekten im Arbeitsspeicher die Leistung der App und auch das Gerät, auf dem sie ausgeführt wird, beeinträchtigen. Übermäßige Arbeitsspeichernutzung kann die Anwendung und den Computer durch Ressourcen blockieren, wenn der Garbage Collector zu häufig ausgeführt wird oder wenn das Betriebssystem gezwungen wird, Arbeitsspeicher zwischen RAM und Datenträger zu verschieben. Im ungünstigsten Fall kann eine Anwendung bei einer Ausnahme aufgrund "nicht genügend Arbeitsspeicher" abstürzen.  
  
 The .NET *managed heap* is a region of virtual memory where reference objects created by an app are stored. Die Lebensdauer der Objekte wird vom Garbage Collector (GC) verwaltet. Der Garbage Collector verwendet Verweise, um Objekte zu verfolgen, die Speicherblöcke belegen. Ein Verweis wird erstellt, wenn ein Objekt erstellt und einer Variablen zugewiesen wird. Ein einzelnes Objekt kann mehrere Verweise haben. Beispielsweise können zusätzliche Verweise auf ein Objekt erstellt werden, indem das Objekt einer Klasse, Auflistung oder anderen Datenstruktur hinzufügt wird oder indem das Objekt einer zweiten Variable zugeordnet wird. Eine weniger offensichtliche Methode zum Erstellen eines Verweises besteht darin, dass ein Objekt einen Handler zum Ereignis eines anderen Objekts hinzufügt. In diesem Fall behält das zweite Objekt den Verweis zum ersten Objekt, bis der Handler explizit entfernt ist oder das zweite Objekt vernichtet wird.  
  
 Für jede Anwendung verwaltet das GC eine Verweisstruktur, die die Objekte verfolgt, auf die von der Anwendung verwiesen wird. The *reference tree* has a set of roots, which includes global and static objects, as well as associated thread stacks and dynamically instantiated objects. Ein Objekt verfügt über einen Stamm, wenn das Objekt mindestens ein übergeordnetes Objekt hat, das einen Verweis darauf enthält. Das GC kann den Arbeitsspeicher eines Objekts nur dann freigeben, wenn kein anderes Objekt oder keine andere Variable in der Anwendung über einen Verweis darauf verfügt.  
  
 ![Back to top](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
## <a name="BKMK_Identify_a_memory_issue_in_an_app"></a> Identify a memory issue in an app  
 Das sichtbarste Symptom von Arbeitsspeicherproblemen ist die Leistung der App, insbesondere dann, wenn die Leistung im Zeitverlauf abnimmt. Eine Verringerung der Leistung anderer Apps während der Ausführung Ihrer App kann ebenfalls auf ein Arbeitsspeicherproblem hinweisen. If you suspect a memory issue, use a tool like Task Manager or [Windows Performance Monitor](https://technet.microsoft.com/library/cc749249.aspx) to investigate further. Schauen Sie beispielsweise, ob die Gesamtgröße des Speichers angestiegen ist, was sich aber nicht als potenzielle Quelle von Arbeitsspeicherverlusten erklären lässt:  
  
 ![Consistent memory growth in Resource Monitor](../misc/media/mngdmem-resourcemanagerconsistentgrowth.png "MNGDMEM_ResourceManagerConsistentGrowth")  
  
 Sie können auch Arbeitsspeicherspitzen beobachten, die größer sind, als sie es Ihrer Kenntnis des Codes nach vermuten würden, was möglicherweise auf eine ineffiziente Arbeitsspeicherverwendung in einer Prozedur hinweist:  
  
 ![Memory spikes in Resource Manager](../misc/media/mngdmem-resourcemanagerspikes.png "MNGDMEM_ResourceManagerSpikes")  
  
## <a name="BKMK_Collect_memory_snapshots"></a> Collect memory snapshots  
 The memory analysis tool analyzes information in *dump files* that contain heap information. You can create dump files in Visual Studio, or you can use a tool like [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx) from [Windows Sysinternals](https://technet.microsoft.com/sysinternals). See [What is a dump, and how do I create one?](https://blogs.msdn.microsoft.com/debugger/2009/12/30/what-is-a-dump-and-how-do-i-create-one/) on the Visual Studio Debugger Team blog.  
  
> [!NOTE]
> Die meisten Tools können Dumpinformationen mit oder ohne vollständige Heapspeicherdaten sammeln. Die Speicheranalyse von Visual Studio erfordert vollständige Heapinformationen.  
  
 **To collect a dump from Visual Studio**  
  
1. Sie können eine Dumpdatei für einen Prozess erstellen, der von einem Visual Studio-Projekt gestartet wurde, oder Sie fügen den Debugger an einen laufenden Prozess an. See [Attach to Running Processes](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
2. Beenden Sie die Ausführung. The debugger stops when you choose **Break All** on the **Debug** menu, or at an exception or at a breakpoint  
  
3. On the **Debug** menu, choose **Save Dump As**. In the **Save Dump As** dialog box, specify a location and make sure that **Minidump with Heap** (the default) is selected in the **Save as type** list.  
  
   **To compare two memory snapshots**  
  
   Um die gestiegene Arbeitsspeichernutzung einer App zu analysieren, erfassen Sie zwei Dumpdateien aus einer einzelnen Instanz der App.  
  
   ![Back to top](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
## <a name="BKMK_Analyze_memory_use"></a> Analyze memory use  
 [Filter the list of objects](#BKMK_Filter_the_list_of_objects) **&#124;** [Analyze memory data in from a single snapshot](#BKMK_Analyze_memory_data_in_from_a_single_snapshot) **&#124;** [Compare two memory snapshots](#BKMK_Compare_two_memory_snapshots)  
  
 So analysieren Sie eine Dumpdatei bei Problemen mit der Arbeitsspeichernutzung  
  
1. In Visual Studio, choose **File**, **Open** and specify the dump file.  
  
2. On the **Minidump File Summary** page, choose **Debug Managed Memory**.  
  
    ![Dump file summary page](../misc/media/mngdmem-dumpfilesummary.png "MNGDMEM_DumpFileSummary")  
  
   Die Speicheranalyse startet eine Debugsitzung, um die Datei zu analysieren, und zeigt die Ergebnisse auf der Seite "Heap-Ansicht" an:  
  
   ![Back to top](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
### <a name="BKMK_Filter_the_list_of_objects"></a> Filter the list of objects  
 Standardmäßig wird die Liste der Objekte in einer Speichermomentaufnahme von der Speicheranalyse gefiltert, um nur die Typen und die Instanzen anzuzeigen, die Benutzercode sind, und nur die Typen darzustellen, deren inklusive Gesamtgröße einen prozentualen Schwellenwert der gesamten Heapgröße überschreitet. You can change these options in the **View Settings** list:  
  
|||  
|-|-|  
|**Nur meinen Code aktivieren**|"Nur eigenen Code" blendet die häufigsten Systemobjekte aus, sodass nur die Typen, die Sie erstellen, in der Liste angezeigt werden.<br /><br /> You can also set the Just My Code option in the Visual Studio **Options** dialog box. Klicken Sie im Menü **Debuggen** auf **Optionen und Einstellungen**. In the **Debugging**/**General** tab, choose or clear **Just My Code**.|  
|**Collapse Small Objects**|**Collapse Small Objects** hides all types whose total inclusive size is less than 0.5 percent of the total heap size.|  
  
 You can also filter the type list by entering a string in the **Search** box. Die Liste enthält nur die Typen, deren Namen die Zeichenfolge enthalten.  
  
 ![Back to top](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
### <a name="BKMK_Analyze_memory_data_in_from_a_single_snapshot"></a> Analyze memory data in from a single snapshot  
 Visual Studio beginnt eine neue Debugsitzung zur Analyse der Datei und zeigt die Speicherdaten in einem Fenster Heap-Ansicht an.  
  
 ![The Object Type list](../misc/media/dbg-mma-objecttypelist.png "DBG_MMA_ObjectTypeList")  
  
 ![Back to top](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
#### <a name="object-type-table"></a>Objekttyptabelle  
 In der Tabelle ganz oben werden die Typen von Objekten aufgeführt, die im Arbeitsspeicher gespeichert werden.  
  
- **Count** shows the number of instances of the type in the snapshot.  
  
- **Size (Bytes)** is the size of the all instances of the type, excluding the size of objects it holds references to. Die  
  
- **Inclusive Size (Bytes)** includes the sizes of referenced objects.  
  
  You can choose the instances icon (![The instance icon in the Object Type column](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon")) in the **Object Type** column to view a list of the instances of the type.  
  
#### <a name="instance-table"></a>Instanztabelle  
 ![Instances table](../misc/media/dbg-mma-instancestable.png "DBG_MMA_InstancesTable")  
  
- **Instance** is the memory location of the object that serves as the object identifier of the object  
  
- **Value** shows the actual value of value types. Sie können den Mauszeiger über den Namen eines Referenztyps bewegen, sodass sein Datenwert in einem Datentipp angezeigt wird.  
  
   ![Instance values in a data tip](../misc/media/dbg-mma-instancevaluesindatatip.png "DBG_MMA_InstanceValuesInDataTip")  
  
- **Size (Bytes)** is the size of the object, excluding the size of objects it holds references to. Die  
  
- **Inclusive Size (Bytes)** includes the sizes of referenced objects.  
  
  By default, types and instances are sorted by **Inclusive Size (Bytes)** . Wählen Sie eine Spaltenüberschrift in der Liste aus, um die Sortierreihenfolge ändern.  
  
#### <a name="paths-to-root"></a>Pfade zum Stamm  
  
- For a type selected from the **Object Type** table, the **Paths to Root** table shows the unique type hierarchies that lead to root objects for all objects of the type, along with the number of references to the type that is above it in the hierarchy.  
  
- For an object selected from the instance of a type, **Paths to Root** shows a graph of the actual objects that hold a reference to the instance. Sie können den Mauszeiger über den Namen des Objekts bewegen, sodass sein Datenwert in einem Datentipp angezeigt wird.  
  
#### <a name="referenced-types--referenced-objects"></a>Referenzierte Typen / Referenzierte Objekte  
  
- For a type selected from the **Object Type** table, the **Referenced Types** tab shows the size and number of referenced types held by all objects of the selected type.  
  
- For a selected instance of a type, **Referenced Objects** shows the objects that are held by the selected instance. Sie können den Mauszeiger über den Namen bewegen, sodass sein Datenwert in einem Datentipp angezeigt wird.  
  
  **Circular references**  
  
  Ein Objekt kann auf ein zweites Objekt verweisen, das direkt oder indirekt einen Verweis auf das erste Objekt enthält. When the memory analyzer encounters this situation, it stops expanding the reference path and adds a **[Cycle Detected]** annotation to the listing of the first object and stops.  
  
  **Root types**  
  
  Die Speicheranalyse fügt Stammobjekten Anmerkungen hinzu, die die Art des gespeicherten Verweises beschreiben:  
  
|Anmerkung|Beschreibung|  
|----------------|-----------------|  
|**Static variable** `VariableName`|Eine statische Variable. `VariableName` ist der Name der Variablen.|  
|**Finalization Handle**|Ein Verweis von der Finalizer-Warteschlange|  
|**Local Variable**|Eine lokale Variable.|  
|**Strong Handle**|Ein Handle für einen starken Verweis von der Objekthandletabelle.|  
|**Async. Pinned Handle**|Ein asynchrones angeheftetes Objekt von der Objekthandletabelle.|  
|**Dependent Handle**|Ein abhängiges Objekt von der Objekthandletabelle.|  
|**Pinned Handle**|Ein angehefteter starker Verweis von der Objekthandletabelle.|  
|**RefCount Handle**|Ein Objekt mit Verweiszählung von der Objekthandletabelle.|  
|**SizedRef Handle**|Ein starkes Handle, das eine ungefähre Größe des kollektiven Abschlusses aller Objekte und Objektstämme zur Garbage Collection-Zeit enthält.|  
|**Pinned local variable**|Eine angeheftete lokale Variable.|  
  
### <a name="BKMK_Compare_two_memory_snapshots"></a> Compare two memory snapshots  
 Sie können zwei Dumpdateien eines Prozesses vergleichen, um nach Objekten zu suchen, die möglicherweise die Ursache von Speicherverlusten sind. Das Intervall zwischen der Auflistung aus der ersten (früheren) und zweiten (späteren) Datei sollte so groß sein, dass der Anstieg der Anzahl von Objekten, die Speicherverluste verursachen, leicht ersichtlich ist. So vergleichen Sie die beiden Dateien  
  
1. Open the second dump file, and then choose **Debug Managed Memory** on the **Minidump File Summary** page.  
  
2. On the memory analysis report page, open the **Select baseline** list, and then choose **Browse** to specify the first dump file.  
  
   The analyzer adds columns to the top pane of the report that display the difference between the **Count**, **Size**, and **Inclusive Size** of the types to those values in the earlier snapshot.  
  
   ![Diff columns in the type list](../misc/media/mngdmem-diffcolumns.png "MNGDMEM_DiffColumns")  
  
   A **Reference Count Diff** column is also added to the **Paths to Root** table.  
  
   ![Back to top](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [Contents](#BKMK_Contents)  
  
## <a name="see-also"></a>Siehe auch  
 [VS ALM TFS Blog: Using Visual Studio 2013 to Diagnose .NET Memory Issues in Production](https://devblogs.microsoft.com/devops/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production/)   
 [Channel 9 &#124; Visual Studio TV &#124; Managed Memory Analysis](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Managed-Memory-Analysis)   
 [Channel 9 &#124; Visual Studio Toolbox &#124; Managed Memory Analysis in Visual Studio 2013](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Managed-Memory-Analysis-in-Visual-Studio-2013)