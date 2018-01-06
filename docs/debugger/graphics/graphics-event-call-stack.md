---
title: Aufrufliste des grafikereignisses | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.graphics.callstack
ms.assetid: 8a30168d-8b39-4de1-b094-c7356ba101a3
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 89e426c24f1f32161307d573c1ab06cdf459b1d6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="graphics-event-call-stack"></a>Aufrufliste des Grafikereignisses
Die Aufrufliste des Grafikereignisses in der Visual Studio-Grafikanalyse kann Ihnen die Zuordnung von Beziehungen zwischen Grafikereignissen und dem Quellcode Ihrer App erleichtern.  
  
 Dies ist das Aufruflistenfenster:  
  
 ![Die Aufrufliste vor einem DrawIndexed-Ereignis. ] (media/gfx_diag_demo_graphics_event_call_stack_orientation.png "Gfx_diag_demo_graphics_event_call_stack_orientation")  
  
## <a name="understanding-the-graphics-event-call-stack"></a>Verstehen der Aufrufliste des Grafikereignisses  
 Sie können mithilfe der Aufrufliste den Ablauf der Ausführung nachvollziehen, die zu einem bestimmten Direct3D-Ereignis geführt hat. Es ähnelt dem Aufruflistenfenster von Visual Studio, anstatt die aktuelle Aufrufliste des aktuellen Threads in einer ausgeführten app zu verwenden, sie die Aufrufliste zeigt, wie bei der das ausgewählte Direct3D-Ereignis aufgetreten ist an. Aus der Aufrufliste können Sie zur Aufrufsite des ausgewählten Direct3D-Ereignisses springen, um den umgebenden Code zu überprüfen.  
  
 Mithilfe der Aufrufliste zur Identifizierung des Codepfads, von dem ein Problemereignis ausgeht, können Sie Ihre Kenntnisse über die Codebasis nutzen, um mögliche Quellen des Problems abzuleiten, oder Sie können Haltepunkte im Quellcode Ihrer Anwendung hinzufügen, sodass Sie untersuchen, wie der Zustand der Anwendung oder die Ereignis-Parameter dazu führen, dass bei dem Ereignis ein Fehler auftritt. Diese Prüfung kann Ihnen bei der Suche nach Fehlern im Quellcode helfen, die nur als Renderingprobleme festgelegt werden.  
  
### <a name="graphics-event-call-stack-information"></a>Informationen zur Aufrufliste des Grafikereignisses  
 Die Aufrufliste unterstützt keine Frames vor dem Frame und keine benutzerdefinierten Ereignisse. Die Aufrufliste des Grafikereignisses wird in einem Tabellenformat angezeigt.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Name**|Ein Symbol, die eindeutig die Funktion identifiziert, die die Aufrufseite enthält. Das Debugsymbol für die Funktion wird angezeigt, wenn dieses verfügbar ist. Andernfalls wird der Offset der Funktion angezeigt.|  
|**Datei**|Der Dateiname der Quelldatei oder Bibliotheksdatei, die die Aufrufsite enthält.|  
|**Speicherort**|Die Zeilennummer der Aufrufsite.|  
  
### <a name="links-to-graphics-objects"></a>Links zu Grafikobjekten  
 Um die ausgewählten Grafiken zu verstehen, benötigen Sie möglicherweise Informationen über das Direct3D-Objekt, dem diese zugeordnet sind. Die **Aufrufliste des Grafikereignisses** Fenster enthält Links zu diesen Informationen.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Fehlende Objekte durch Vertex-Shading](walkthrough-missing-objects-due-to-vertex-shading.md)