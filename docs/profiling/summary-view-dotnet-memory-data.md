---
title: "Zusammenfassungsansicht – .NET-Arbeitsspeicherdaten | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Summary view
ms.assetid: 0cb317c3-0ae6-4531-aaa8-447576eec037
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: c0223950fb5082c84de8026cb07778d1f7381a33
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="summary-view---net-memory-data"></a>Zusammenfassungsansicht – .NET-Arbeitsspeicherdaten
Die Zusammenfassung zeigt Informationen über die .NET-Funktionen und Typen, die den meisten Speicher belegen, und die Typen, die am häufigsten in einem Profilerstellungslauf erstellt wurden. Weitere Informationen, einschließlich einer Beschreibung der Benachrichtigungslinks und Berichtslisten, finden Sie unter [Zusammenfassungsansicht](../profiling/summary-view.md).  
  
## <a name="timeline-graph"></a>Zeitachsendiagramm  
 Die Zeitachse in der Zusammenfassungsansicht zeigt die Auslastung des Prozessors (CPU) durch die profilierte Anwendung während des Zeitraums an, in dem die Profilerstellung stattgefunden sind. Sie können das Zeitachsendiagramm zum Filtern der Ansicht in einem ausgewählten Zeitraum verwenden. Weitere Informationen finden Sie unter [Vorgehensweise: Filtern von Berichtsansichten aus der Zeitachsenübersicht](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="functions-allocating-most-memory"></a>Funktionen, die den meisten Speicher zuordnen  
 Listet die Funktionen auf, die die größte Anzahl von Bytes an Arbeitsspeicher im Profilerstellungslauf zugewiesen haben.  
  
|Spalte|description|  
|------------|-----------------|  
|**Name**|Der Name der Funktion.|  
|**Bytes %**|Der Prozentsatz aller zugewiesenen Bytes im Profilerstellungslauf, die von dieser Funktion oder einer untergeordneten Funktion, die von dieser Funktion aufgerufen wurde zugewiesen wurden.|  
  
## <a name="types-with-most-memory-allocated"></a>Typen mit der größten Speicherbelegung  
 Listet die Typen auf, für die die größte Anzahl von Bytes an Arbeitsspeicher im Profilerstellungslauf zugewiesen wurde.  
  
|Spalte|description|  
|------------|-----------------|  
|**Name**|Der Name des Typs.|  
|**Bytes %**|Der Prozentsatz aller zugewiesenen Bytes im Profilerstellungslauf, die für diesen Typ zugewiesen wurden.|  
  
## <a name="types-with-most-instances"></a>Typen mit den meisten Instanzen  
 Liste die Typen, die am häufigsten während des Profilerstellungslaufs erstellt wurden. had  
  
|Spalte|description|  
|------------|-----------------|  
|**Name**|Der Name des Typs.|  
|**Instancen %**|Der Prozentsatz der Gesamtzahl der .NET-Objekte, die beim Profilerstellungslauf erstellt wurden und Instanzen dieses Typs sind.|  
  
## <a name="see-also"></a>Siehe auch  
 [Zusammenfassungsansicht](../profiling/summary-view-sampling-data.md)   
 [Zusammenfassungsansicht](../profiling/summary-view-instrumentation-data.md)