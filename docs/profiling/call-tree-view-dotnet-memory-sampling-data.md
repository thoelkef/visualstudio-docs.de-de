---
title: "Aufrufstrukturansicht – .NET-Speichersamplingdaten | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Call Tree view
ms.assetid: fbb6cb60-420b-4ca9-8306-2494f7d321fe
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 5c81f9b5ff7d0bad9c0a05bd4b43374ac9451cf1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="call-tree-view---net-memory-sampling-data"></a>Aufrufstrukturansicht – .NET-Speichersamplingdaten
In der Aufrufstrukturansicht werden die Funktionsausführungspfade angezeigt, die in der mit einem Profil versehenen Anwendung durchlaufen wurden. Der Stamm der Struktur ist der Einstiegspunkt in die Anwendung oder Komponente. Unter den einzelnen Funktionsknoten werden alle Funktionen aufgeführt, die von dieser aufgerufen wurden. Zudem werden die Daten der .NET-Speicherbelegung über diese Funktionsaufrufe angezeigt.  
  
 Die Werte in der Aufrufstrukturansicht beziehen sich auf die Funktionsinstanzen, die von der übergeordneten Funktion in der Aufrufstruktur aufgerufen wurden. Prozentwerte werden berechnet, indem der Funktionsinstanzwert mit der Gesamtanzahl oder Größe der Zuordnungen bei der Profilerstellung verglichen wird.  
  
## <a name="highlighting-the-execution-hot-path"></a>Hervorheben des langsamsten Ausführungspfads  
 Die Aufrufstrukturansicht kann erweitert werden und den Ausführungspfad des Prozesses oder der Funktion hervorheben, für die die größten oder meisten Arbeitsspeicherobjekte erstellt wurden. Klicken Sie mit der rechten Maustaste auf den Prozess oder die Funktion, und klicken Sie dann auf **Langsamsten Pfad erweitern**, um den Pfad mit der höchsten Aktivität anzuzeigen.  
  
## <a name="setting-the-call-tree-root-node"></a>Festlegen des Stammknotens der Aufrufstruktur  
 Jeder Prozess in der Profilerstellung wird als Stammknoten angezeigt. Sie können den Startknoten der Aufrufstrukturansicht auf einen anderen Knoten festlegen, indem Sie mit der rechten Maustaste auf den Knoten klicken, der als Startknoten festgelegt werden soll, und dann **Stamm festlegen** auswählen.  
  
 Durch das Festlegen eines Stammknotens wird sichergestellt, dass in der Ansicht lediglich die Teilstruktur des ausgewählten Knotens angezeigt wird. Um den Stammknoten auf den ursprünglich angezeigten Knoten zurückzusetzen, klicken Sie mit der rechten Maustaste auf das Fenster der Aufrufstrukturansicht, und wählen Sie dann **Stamm zurücksetzen** aus.  
  
|Spalte|description|  
|------------|-----------------|  
|**Prozess-ID**|Die Prozess-ID (PID) der Profilerstellung.|  
|**Prozessname**|Der Prozessname.|  
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das die Funktion enthält.|  
|**Quelldatei**|Die Quelldatei, die die Definition der Funktion enthält.|  
|**Funktionsname**|Der vollqualifizierte Name der Funktion.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Funktionsadresse**|Die Adresse der Funktion.|  
|**Ebene**|Die Tiefe der Funktion in der Aufrufstruktur.|  
|**Inklusive Speicherbelegungen**|Die Anzahl von Objekten, die von den Instanzen dieser Funktion zugeordnet wurden, die von der übergeordneten Funktion in der Aufrufstruktur aufgerufen wurden. Diese Zahl beinhaltet Zuordnungen, die von untergeordneten Funktion erstellt wurden.|  
|**Inklusive Speicherbelegungen in %**|Der Prozentsatz aller Objekte, die während der Profilerstellung erstellt wurden und inklusive Belegungen dieser Funktion waren.|  
|**Exklusive Speicherbelegungen**|Die Anzahl von Objekten, die von den Instanzen dieser Funktion zugeordnet wurden, die von der übergeordneten Funktion in der Aufrufstruktur aufgerufen wurden. Diese Zahl beinhaltet keine Zuordnungen, die von untergeordneten Funktionen erstellt wurden.|  
|**Exklusive Zuordnungen %**|Der Anteil aller Objekte, die bei der Profilerstellung erstellt wurden und keine Zuordnungen der Funktionsinstanzen beinhalten, die von der übergeordneten Funktion in der Aufrufansicht aufgerufen wurden.|  
|**Inklusive Bytes in %**|Die Anzahl von Bytes im Arbeitsspeicher, die von den Instanzen dieser Funktion zugeordnet wurden, die von der übergeordneten Funktion in der Aufrufstruktur aufgerufen wurden. Diese Zahl beinhaltet Zuordnungen, die von untergeordneten Funktion erstellt wurden.|  
|**Inklusive Bytes in %**|Der Prozentsatz aller Bytes des Arbeitsspeichers, die während der Profilerstellung belegt wurden und inklusive Belegungen dieser Funktion waren.|  
|**Exklusive Bytes**|Die Anzahl von Bytes im Arbeitsspeicher, die von den Instanzen dieser Funktion zugeordnet wurden, die von der übergeordneten Funktion in der Aufrufstruktur aufgerufen wurden. Diese Zahl beinhaltet keine Zuordnungen, die von untergeordneten Funktionen erstellt wurden.|  
|**Exklusive Bytes %**|Der Prozentsatz aller Bytes des Arbeitsspeichers, die während der Profilerstellung belegt wurden und exklusive Belegungen dieser Funktion waren.|  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufstrukturansicht – .NET-Speicherinstrumentationsdaten im Profiler](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Aufrufstrukturansicht](../profiling/call-tree-view-sampling-data.md)   
 [Aufrufstrukturansicht](../profiling/call-tree-view-instrumentation-data.md)