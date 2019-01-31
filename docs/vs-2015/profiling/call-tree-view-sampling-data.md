---
title: Aufrufstrukturansicht – Samplingdaten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method,Call Tree view
- Call Tree view
ms.assetid: 5c4e8ec3-d0d3-485a-93bd-9060df4eb739
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e5b15badb7b5e98c73ccadab41f67c64d60cb05e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54779225"
---
# <a name="call-tree-view---sampling-data"></a>Aufrufstrukturansicht – Samplingdaten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In der Aufrufstrukturansicht werden die Funktionsausführungspfade angezeigt, die in der mit einem Profil versehenen Anwendung durchlaufen wurden.  
  
> [!NOTE]
>  Verbesserte Sicherheitsfunktionen in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen Windows Store-Apps neue Erfassungsmethoden. Siehe [Profilerstellungstools für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Der Stamm der Struktur ist der Einstiegspunkt in die Anwendung oder Komponente. Unter den einzelnen Funktionsknoten werden alle Funktionen aufgeführt, die von dieser aufgerufen wurden. Zudem werden Leistungsdaten über diese Funktionsaufrufe angezeigt.  
  
 Die Werte in der Aufrufstrukturansicht beziehen sich auf die Funktionsinstanzen, die von der übergeordneten Funktion in der Aufrufstruktur aufgerufen wurden. Prozentwerte werden berechnet, indem der Funktionsinstanzwert mit der Gesamtzahl der Samplings in der Profilerstellung verglichen wird.  
  
## <a name="highlighting-the-execution-hot-path"></a>Hervorheben des langsamsten Ausführungspfads  
 Die Aufrufstrukturansicht kann erweitert werden und den Ausführungspfad des Prozesses oder der Funktion hervorheben, für die die meisten Samplings durchgeführt wurden. Um den aktivsten Pfad anzuzeigen, klicken Sie mit der rechten Maustaste auf den Prozess oder die Funktion, und klicken Sie dann auf **Langsamsten Pfad erweitern**.  
  
## <a name="setting-the-call-tree-root-node"></a>Festlegen des Stammknotens der Aufrufstruktur  
 Jeder Prozess in der Profilerstellung wird als Stammknoten angezeigt. Sie können den Startknoten der Aufrufstrukturansicht festlegen, indem Sie mit der rechten Maustaste auf den Knoten klicken, der als Startknoten festgelegt werden soll, und dann **Stamm festlegen** auswählen.  
  
 Durch das Festlegen eines Stammknotens wird sichergestellt, dass in der Ansicht lediglich die Teilstruktur des ausgewählten Knotens angezeigt wird. Um den Stammknoten auf den ursprünglichen Knoten zurückzusetzen, klicken Sie mit der rechten Maustaste auf das Fenster der Aufrufstrukturansicht, und wählen Sie dann **Stamm zurücksetzen** aus.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Prozess-ID**|Die Prozess-ID (PID) der Profilerstellung.|  
|**Prozessname**|Der Prozessname.|  
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das die Funktion enthält.|  
|**Quelldatei**|Die Quelldatei, die die Definition der Funktion enthält.|  
|**Funktionsname**|Der vollqualifizierte Name der Funktion.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Funktionsadresse**|Die Adresse der Funktion.|  
|**Ebene**|Die Tiefe dieser Funktion in der Aufrufstruktur. Nur in [VSPerfReport](../profiling/vsperfreport.md)-Befehlszeilenberichten.|  
|**Exklusive Samplings**|Die Anzahl der Samplings, die in dieser Funktion erfasst wurden, als sie von der in der Aufrufstruktur übergeordneten Funktion aufgerufen wurde. Diese Zahl umfasst keine Samplings, die in von der Funktion aufgerufenen Funktionen erfasst wurden.|  
|**Exklusive Samplings in %**|Der Prozentsatz aller Samplings während der Profilerstellung, die auf exklusive Samplings dieser Funktion entfallen, wenn diese von der übergeordneten Funktion in der Aufrufstruktur aufgerufen wurde.|  
|**Inklusive Samplings**|Die Anzahl der Samplings, die in dieser Funktion erfasst wurden, als sie von der in der Aufrufstruktur übergeordneten Funktion aufgerufen wurde. Diese Zahl umfasst Samplings, die in von der Funktion aufgerufenen Funktionen erfasst wurden.|  
|**Inklusive Samplings in %**|Der Prozentsatz aller Samplings während der Profilerstellung, die auf inklusive Samplings dieser Funktion entfallen, wenn diese von der übergeordneten Funktion in der Aufrufstruktur aufgerufen wurde.|  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md)   
 [Aufrufstrukturansicht - Profiler-Samplingdaten](../profiling/call-tree-view-sampling-data.md)   
 [Aufrufstrukturansicht – .NET-Speichersamplingdaten im Profiler](../profiling/call-tree-view-dotnet-memory-sampling-data.md)   
 [Aufrufstrukturansicht – .NET-Speicherinstrumentationsdaten im Profiler](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Aufrufstrukturansicht – Profiler-Instrumentationsdaten](../profiling/call-tree-view-instrumentation-data.md)
