---
title: 'Vorgehensweise: Sammeln von Daten der Ereignisablaufverfolgung für Windows (ETW) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.property.events
helpviewer_keywords:
- event trace providers, performance tools
- profiling tools, event trace providers
- performance tools, enabling event trace providers
ms.assetid: aa2261fe-d5f5-49fc-a171-d18842e1dc7d
caps.latest.revision: 31
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a9f3476a5aa27075f28d9d02f8ca7167cd3f7e64
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522467"
---
# <a name="how-to-collect-event-tracing-for-windows-etw-data"></a>Gewusst wie: Sammeln von Daten der Ereignisablaufverfolgung für Windows (ETW)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Sammeln von Event Tracing for Windows (ETW) Daten](https://docs.microsoft.com/visualstudio/profiling/how-to-collect-event-tracing-for-windows-etw-data).  
  
Ereignisablaufverfolgung für Windows (ETW) ist eine effiziente Ablaufverfolgungsfunktion auf Kernelebene, mit dem der Profiler kernel- oder anwendungsdefinierte Ereignisse protokollieren kann. Die vom Ereignisanbieter gesammelten Daten können nur mithilfe der Option /**Summary:ETW** des Befehlszeilentools [VSPerfReport](../profiling/vsperfreport.md) angezeigt werden. In diesem Bericht können Sie bestimmen, wo Leistungsprobleme in der Anwendung aufgetreten.  
  
 **Anforderungen**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
>  Verbesserte Sicherheitsfunktionen in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio-Profilers auf diesen Plattformen. Außerdem benötigen Windows Store-Apps neue Erfassungsmethoden. Siehe [Profilerstellungstools für Windows 8- und Windows Server 2012-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
### <a name="to-enable-event-trace-providers"></a>So aktivieren Sie Ereignisablaufverfolgungsanbieter  
  
1.  Klicken Sie im **Leistungs-Explorer**mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie in den **Eigenschaftenseiten** auf die Eigenschaften **Windows-Ereignisse** .  
  
3.  Wählen Sie von der Liste **Ereignisablaufverfolgungsanbieter zur Datensammlung auswählen** den gewünschten Ereignisanbieter zur Profilerstellung aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Konfigurieren von Leistungssitzungen](../profiling/configuring-performance-sessions.md)



