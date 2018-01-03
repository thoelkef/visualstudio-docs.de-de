---
title: 'Aufrufstrukturansicht: Konfliktdaten | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Call Tree view
ms.assetid: 9bd4bde2-2ca3-446c-9ccc-7421522e03ae
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c829f11efd5eddda0ea819422856cb2bcc30c2ed
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="call-tree-view---contention-data"></a>Aufrufstrukturansicht: Konfliktdaten
In der Aufrufstrukturansicht werden die Funktionsausführungspfade angezeigt, die in der mit einem Profil versehenen Anwendung durchlaufen wurden. Der Stamm der Struktur ist der Einstiegspunkt in die Anwendung oder Komponente. Jeder Funktionsknoten führt Folgendes auf: Alle von ihm aufgerufenen Funktionen, wie oft die Funktion blockiert wurde und wie lange die Funktion blockiert war, weil sie mit anderen Threads oder Prozessen um eine Ressource konkurriert hat.  
  
 Die Werte in der Aufrufstrukturansicht beziehen sich auf die Funktionsinstanzen, die von der übergeordneten Funktion in der Aufrufstruktur aufgerufen wurden. Prozentwerte werden berechnet, indem der Funktionsinstanzwert mit der Gesamtanzahl der Konflikte in der Profilerstellung verglichen wird.  
  
## <a name="highlighting-the-execution-hot-path"></a>Hervorheben des langsamsten Ausführungspfads  
 Die Aufrufstrukturansicht kann erweitert werden und den Ausführungspfad des Prozesses oder der Funktion hervorheben, die die meisten Konflikte verursacht hat.  
  
-   Klicken Sie mit der rechten Maustaste auf den Prozess oder die Funktion, und klicken Sie dann auf **Langsamsten Pfad erweitern**, um den Pfad mit der höchsten Aktivität anzuzeigen.  
  
## <a name="setting-the-call-tree-root-node"></a>Festlegen des Stammknotens der Aufrufstruktur  
 Jeder Prozess in der Profilerstellung wird als Stammknoten angezeigt. Sie können den Startknoten der Aufrufstrukturansicht festlegen, indem Sie mit der rechten Maustaste auf den Knoten klicken, der als Startknoten festgelegt werden soll, und dann auf **Stamm festlegen** klicken.  
  
 Durch das Festlegen eines Stammknotens wird sichergestellt, dass in der Ansicht lediglich die Teilstruktur des ausgewählten Knotens angezeigt wird. Um den Stammknoten auf den ursprünglichen Knoten zurückzusetzen, klicken Sie mit der rechten Maustaste in der Aufrufstrukturansicht, und klicken Sie dann auf **Stamm zurücksetzen**.  
  
|Spalte|description|  
|------------|-----------------|  
|**Exklusive blockierte Zeit %**|Wie lange die Instanzen dieser Funktion in diesem Ausführungspfad während der Profilerstellung nicht ausgeführt werden konnten. Diese Zeit enthält nicht die Zeit, für die untergeordnete Funktionen blockiert wurden, die von der Funktion aufgerufen wurden.|  
|**Exklusive blockierte Zeit %**|Der Anteil der gesamten blockierten Zeit während der Profilerstellung, die der exklusiven blockierten Zeit für diese Funktion in diesem Ausführungspfad entspricht.|  
|**Exklusive Konflikte**|Die Anzahl von Konflikten, die in Instanzen dieser Funktion in diesem Ausführungspfad aufgetreten sind. Diese Anzahl enthält keine Konflikte von untergeordneten Funktionen, die von der Funktion aufgerufen wurden.|  
|**Exklusive Konflikte %**|Der Anteil aller Konflikte während der Profilerstellung, bei denen es sich um exklusive Konflikte der Instanzen dieser Funktion handelt, die von der übergeordneten Funktion in der Aufrufstruktur aufgerufen wurden.|  
|**Funktionsadresse**|Die Adresse der Funktion.|  
|**Funktionsname**|Der vollqualifizierte Name der Funktion.|  
|**Inklusive blockierte Zeit**|Wie lange die Instanzen dieser Funktion in diesem Ausführungspfad während der Profilerstellung insgesamt nicht ausgeführt werden konnten. Diese Zeit enthält die Zeit, für die untergeordnete Funktionen blockiert wurden, die von der Funktion aufgerufen wurden.|  
|**Inklusive blockierte Zeit %**|Der Anteil der gesamten blockierten Zeit während der Profilerstellung, die der inklusiven blockierten Zeit für die Instanzen dieser Funktion in diesem Ausführungspfad entspricht.|  
|**Inklusive Konflikte %**|Die Gesamtanzahl von Konflikten, die Instanzen dieser Funktion in diesem Ausführungspfad blockiert haben. Diese Anzahl enthält die Konflikte von untergeordneten Funktionen, die von der Funktion aufgerufen wurden.|  
|**Inklusive Konflikte %**|Der Anteil aller Konflikte während der Profilerstellung, bei denen es sich um inklusive Konflikte der Instanzen dieser Funktion in diesem Ausführungspfad handelt.|  
|**Ebene**|Die Ebene der Funktion in der Aufrufstruktur. Nur in VSReport-Befehlszeilenberichten. Weitere Informationen finden Sie unter [VSPerfReport](../profiling/vsperfreport.md).|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das die Funktion enthält.|  
|**Prozess-ID**|Die Prozess-ID (PID) der Profilerstellung.|  
|**Prozessname**|Der Prozessname.|  
|**Quelldatei**|Die Quelldatei, die die Definition der Funktion enthält.|  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md)   
 [Aufrufstrukturansicht](../profiling/call-tree-view.md)   
 [Aufrufstrukturansicht – .NET-Speicherinstrumentationsdaten im Profiler](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Aufrufstrukturansicht – .NET-Speichersamplingdaten im Profiler](../profiling/call-tree-view-dotnet-memory-sampling-data.md)   
 [Aufrufstrukturansicht](../profiling/call-tree-view-instrumentation-data.md)   
 [Aufrufstrukturansicht](../profiling/call-tree-view-sampling-data.md)