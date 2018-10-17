---
title: Referenz zu den Leistungsregeln | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59fc9424-76ca-4365-ae47-bb14a736c9c2
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9276f567f0edf91111853e417f1f8dff1eb2a4df
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49227096"
---
# <a name="performance-rules-reference"></a>Referenz zu den Leistungsregeln
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Leistungsregeln der Profilerstellungstools bieten zusätzliche Warnungen und Informationen über die Leistung Ihrer Anwendung. Leistungsregeln analysieren Daten in einer Profilerstellung, die aus Quellen wie z.B. Windows und Prozessor-Leistungsindikatoren gesammelt werden. Regelnachrichten werden im Fenster Fehlerausgabe der [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]-IDE angezeigt. Nachrichten werden mit einer der folgenden Regelebenen aufgeführt:  
  
|||  
|-|-|  
|**Fehler**|Nur wenige Regeln generieren Fehlermeldungen, da die meisten Leistungsprobleme keine tatsächlichen Fehler sind. Eine Fehlermeldung kann einen Fehler beim Erfassen von Profilerstellungsdaten angeben.|  
|**Warnung**|Warnungen geben einen Bereich Ihrer Anwendung an, die eine Ursache von Leistungsproblemen sein oder die von Optimierungen profitieren können.|  
|**Information**|Informationsnachrichten geben entweder die Analyse einer Regelbedingung an, die den Schwellenwert zur Erstellung einer Fehlermeldung nicht erreicht hat, oder dass die Information in der Nachricht nützlich ist, jedoch nicht auf ein Leistungsproblem hinweist.|  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Leistungsregeln nach ID](../profiling/performance-rules-by-id.md)  
  
 Die Leistungsregeln der Profilerstellungstools sind in vier Kategorien unterteilt:  
  
|||  
|-|-|  
|[Leistungsregeln für die .NET Framework-Verwendung](../profiling/dotnet-framework-usage-performance-rules.md)|Regeln, mit denen Sie .NET Framework effizient verwenden können.|  
|[Leistungsregeln für Speicher und Auslagerung](../profiling/memory-and-paging-performance-rules.md)|Regeln, die den verwalteten Arbeitsspeicher und das Pagingverhalten Ihrer Anwendung analysieren.|  
|[Verwendungsregeln für Profilerstellungstools](../profiling/profiling-tools-usage-rules.md)|Regeln, mit denen Sie Profilerstellungstools effizient verwenden können.|  
|[Leistungsregeln für die Ressourcenüberwachung](../profiling/resource-monitoring-performance-rules.md)|Informationsnachrichten zur Auslastung von Prozessor und Arbeitsspeicher in einer Profilerstellung.|



