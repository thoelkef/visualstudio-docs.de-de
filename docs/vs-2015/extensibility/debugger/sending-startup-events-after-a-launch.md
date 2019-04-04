---
title: Senden von Startereignissen nach einem Start | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: eeb378b09ffc3e12de8996d7feabbd20a4b40068
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58959237"
---
# <a name="sending-startup-events-after-a-launch"></a>Senden von Startereignissen nach einem Start
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sobald die Debug-Engine (DE) an die Anwendung angefügt ist, sendet es eine Reihe von Startup-Ereignisse an die Debug-Sitzung.  
  
 Startup-Ereignisse, die an die Debug-Sitzung zurückgesendet umfassen Folgendes:  
  
- Ein Ereignis für den Engine-Erstellung.  
  
- Ein Programm erstellen-Ereignis.  
  
- Thread-Erstellung und Ladeereignisse für Module.  
  
- Eine vollständige Ladeereignis gesendet, wenn der Code geladen und für die Ausführung bereit ist, aber bevor irgendwelcher Code ausgeführt wird  
  
  > [!NOTE]
  >  Wenn dieses Ereignis fortgesetzt wird, globale Variablen werden initialisiert, und startroutinen ausführen.  
  
- Mögliche andere Threads erstellen und Ladeereignisse für Module an.  
  
- Ein punktereignis Eintrag, der signalisiert, dass die Anwendung der Haupteinstiegspunkt, z. B. erreicht hat **Main** oder `WinMain`. Dieses Ereignis wird nicht in der Regel gesendet werden, wenn die DE an ein Programm angefügt wird, die bereits ausgeführt wird.  
  
  Programmgesteuert, sendet der DE zuerst die sitzungsbasierter Debug-Manager (SDM) eine [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) -Schnittstelle, die ein Modul erstellen-Ereignis darstellt, gefolgt von einem [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , ein Programm Erstellungsereignis steht.  
  
  Dies ist in der Regel gefolgt von einem oder mehreren [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) thread-Ereignisse der diensterstellung und [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) Ladeereignisse für Module.  
  
  Wenn der Code geladen und ausgeführt, aber bevor Code ausgeführt wird, der DE das SDM sendet ein [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) vollständige Load-Ereignis. Schließlich sendet, wenn die Anwendung nicht bereits ausgeführt wird, die die DE eine [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) Eintrag punktereignis, damit an, dass das Programm seine Haupteinstiegspunkt erreicht hat und wird zum Debuggen bereit ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Steuern der Ausführung](../../extensibility/debugger/control-of-execution.md)   
 [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)
