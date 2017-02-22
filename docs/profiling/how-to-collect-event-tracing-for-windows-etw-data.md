---
title: "Gewusst wie: Sammeln von Daten der Ereignisablaufverfolgung f&#252;r Windows (ETW) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.events"
helpviewer_keywords: 
  - "Ereignisablaufverfolgungsanbieter, Leistungstools"
  - "Profilerstellungstools, Ereignisablaufverfolgungsanbieter"
  - "Leistungstools, Aktivieren von Ereignisablaufverfolgungsanbietern"
ms.assetid: aa2261fe-d5f5-49fc-a171-d18842e1dc7d
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Sammeln von Daten der Ereignisablaufverfolgung f&#252;r Windows (ETW)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Event Tracing for Windows \(ETW\) ist eine effiziente Verfolgungsfunktion auf Kernelebene, mit dem der Profiler kernel\- oder anwendungsdefinierte Ereignisse protokollieren kann.  Die vom Ereignisanbieter gesammelten Daten können nur mithilfe der \/**Summary:ETW**\-Option des Befehlszeilentools [VSPerfReport](../profiling/vsperfreport.md) angezeigt werden.  Mithilfe dieses Berichts können Sie die Bereiche identifizieren, in denen in der Anwendung Leistungsprobleme auftreten.  
  
 **Voraussetzungen**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio\-Profilers auf diesen Plattformen.  Außerdem benötigen Windows Store\-Apps neue Erfassungsmethoden.  Siehe [Profilerstellung für Windows 8\- und Windows Server 2012\-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
### So aktivieren Sie Ereignisablaufverfolgungsanbieter  
  
1.  Klicken Sie im **Leistungs\-Explorer** mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie in den **Eigenschaftenseiten** auf die Eigenschaften **Windows\-Ereignisse**.  
  
3.  Wählen Sie in der Liste **Ereignisablaufverfolgungsanbieter auswählen, von denen Daten erfasst werden sollen** die Ereignisablaufverfolgungsanbieter aus, die zum Erstellen des Profils für die Anwendung verwendet werden sollen.  
  
## Siehe auch  
 [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)