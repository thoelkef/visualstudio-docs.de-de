---
title: "Referenz zu den Leistungsregeln der Profilerstellungstools | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 59fc9424-76ca-4365-ae47-bb14a736c9c2
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Referenz zu den Leistungsregeln der Profilerstellungstools
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Leistungsregeln für die Profilerstellungstools stellen zusätzliche Warnungen und Informationen zur Leistung der Anwendung bereit.  Leistungsregeln analysieren während einer Profilerstellung Daten, die von verschiedenen Quellen abgerufen werden, z. B. von Windows\- oder Prozessorleistungsindikatoren.  Regelmeldungen werden im Fehlerausgabefenster der integrierten Entwicklungsumgebung von [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] angezeigt.  Meldungen werden mit einer der folgenden Regelebenen aufgeführt:  
  
|||  
|-|-|  
|**Fehler**|Nur wenige Regeln generieren Fehlermeldungen, da die meisten Leistungsprobleme keine tatsächlichen Fehler sind.  Eine Fehlermeldung kann z. B. anzeigen, dass Profilerstellungsdaten nicht erfasst werden konnten.|  
|**Warnung**|Warnungen weisen auf einen Bereich der Anwendung hin, der potenziell Leistungsprobleme verursachen bzw. optimiert werden könnte.|  
|**Information**|Informationsmeldungen geben an, dass die Analyse einer Regelbedingung entweder nicht den Schwellenwert erreicht hat, um eine Fehlermeldung zu generieren, oder dass die Informationen in der Meldung hilfreich sind, aber kein Leistungsproblem darstellen.|  
  
## In diesem Abschnitt  
 [Leistungsregeln nach ID](../profiling/performance-rules-by-id.md)  
  
 Die Leistungsregeln der Profilerstellungstools sind in vier Kategorien unterteilt:  
  
|||  
|-|-|  
|[Leistungsregeln für die .NET Framework\-Verwendung](../profiling/dotnet-framework-usage-performance-rules.md)|Regeln, die Ihnen bei der effizienten Verwendung von .NET Framework helfen.|  
|[Leistungsregeln für Speicher und Auslagerung](../profiling/memory-and-paging-performance-rules.md)|Regeln, die den verwalteten Arbeitsspeicher und das Pagingverhalten der Anwendung analysieren.|  
|[Verwendungsregeln für Profilerstellungstools](../profiling/profiling-tools-usage-rules.md)|Regeln, die Sie bei der effizienten Verwendung der Profilerstellungstools unterstützen.|  
|[Leistungsregeln für die Ressourcenüberwachung](../profiling/resource-monitoring-performance-rules.md)|Informationsmeldungen zur Prozessor\- und Arbeitsspeicherauslastung während einer Profilerstellung.|