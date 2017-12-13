---
title: "Vorgehensweise: Sammeln von Daten der Ereignisablaufverfolgung für Windows (ETW) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.property.events
helpviewer_keywords:
- event trace providers, performance tools
- profiling tools, event trace providers
- performance tools, enabling event trace providers
ms.assetid: aa2261fe-d5f5-49fc-a171-d18842e1dc7d
caps.latest.revision: "26"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 66ad7c937ba6c3845e905abea31f4525198f8389
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2017
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>Gewusst wie: Sammeln von Daten der Ereignisablaufverfolgung für Windows (ETW)
Ereignisablaufverfolgung für Windows (ETW) ist eine effiziente Ablaufverfolgungsfunktion auf Kernelebene, mit dem der Profiler kernel- oder anwendungsdefinierte Ereignisse protokollieren kann. Die vom Ereignisanbieter gesammelten Daten können nur mithilfe der Option /**Summary:ETW** des Befehlszeilentools [VSPerfReport](../profiling/vsperfreport.md) angezeigt werden. In diesem Bericht können Sie bestimmen, wo Leistungsprobleme in der Anwendung aufgetreten.  
  
 **Anforderungen**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen UWP-Apps neue Erfassungsmethoden. Siehe [Leistungstools für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
### <a name="to-enable-event-trace-providers"></a>So aktivieren Sie Ereignisablaufverfolgungsanbieter  
  
1.  Klicken Sie im **Leistungs-Explorer**mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie in den **Eigenschaftenseiten** auf die Eigenschaften **Windows-Ereignisse** .  
  
3.  Wählen Sie von der Liste **Ereignisablaufverfolgungsanbieter zur Datensammlung auswählen** den gewünschten Ereignisanbieter zur Profilerstellung aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)