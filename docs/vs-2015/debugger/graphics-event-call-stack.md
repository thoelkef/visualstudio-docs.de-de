---
title: Aufrufliste des grafikereignisses | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.callstack
ms.assetid: 8a30168d-8b39-4de1-b094-c7356ba101a3
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8344050d26286263e0c33974b976e4ae25ff18de
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68192753"
---
# <a name="graphics-event-call-stack"></a>Aufrufliste des Grafikereignisses
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Aufrufliste des Grafikereignisses in der Visual Studio-Grafikanalyse kann Ihnen die Zuordnung von Beziehungen zwischen Grafikereignissen und dem Quellcode Ihrer App erleichtern.  
  
 Dies ist das Aufruflistenfenster:  
  
 ![Die Aufrufliste vor einem DrawIndexed-Ereignis. ](../debugger/media/gfx-diag-demo-graphics-event-call-stack-orientation.png "Gfx_diag_demo_graphics_event_call_stack_orientation")  
  
## <a name="understanding-the-graphics-event-call-stack"></a>Verstehen der Aufrufliste des Grafikereignisses  
 Sie können mithilfe der Aufrufliste den Ablauf der Ausführung nachvollziehen, die zu einem bestimmten Direct3D-Ereignis geführt hat. Sie ähnelt dem Aufruflistenfenster in Visual Studio, mit der Ausnahme, dass anstelle der aktuellen Aufrufliste des aktiven Threads in einer laufenden Anwendung die Aufrufliste angezeigt wird, bei der das ausgewählte Direct3D-Ereignis eingetreten ist. Aus der Aufrufliste können Sie zur Aufrufsite des ausgewählten Direct3D-Ereignisses springen, um den umgebenden Code zu überprüfen.  
  
 Mithilfe der Aufrufliste zur Identifizierung des Codepfads, von dem ein Problemereignis ausgeht, können Sie Ihre Kenntnisse über die Codebasis nutzen, um mögliche Quellen des Problems abzuleiten, oder Sie können Haltepunkte im Quellcode Ihrer Anwendung hinzufügen, sodass Sie untersuchen, wie der Zustand der Anwendung oder die Ereignis-Parameter dazu führen, dass bei dem Ereignis ein Fehler auftritt. Diese Prüfung kann Ihnen bei der Suche nach Fehlern im Quellcode helfen, die nur als Renderingprobleme festgelegt werden.  
  
### <a name="graphics-event-call-stack-information"></a>Informationen zur Aufrufliste des Grafikereignisses  
 Die Aufrufliste unterstützt keine Frames vor dem Frame und keine benutzerdefinierten Ereignisse. Die Aufrufliste des Grafikereignisses wird in einem Tabellenformat angezeigt.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Name**|Ein Symbol, die eindeutig die Funktion identifiziert, die die Aufrufseite enthält. Das Debugsymbol für die Funktion wird angezeigt, wenn dieses verfügbar ist. Andernfalls wird der Offset der Funktion angezeigt.|  
|**File**|Der Dateiname der Quelldatei oder Bibliotheksdatei, die die Aufrufsite enthält.|  
|**Speicherort**|Die Zeilennummer der Aufrufsite.|  
  
### <a name="links-to-graphics-objects"></a>Links zu Grafikobjekten  
 Um die ausgewählten Grafiken zu verstehen, benötigen Sie möglicherweise Informationen über das Direct3D-Objekt, dem diese zugeordnet sind. Das Fenster **Aufrufliste des Grafikereignisses** enthält Links zu diesen Informationen.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Fehlende Objekte durch Vertex-Shading](../debugger/walkthrough-missing-objects-due-to-vertex-shading.md)
