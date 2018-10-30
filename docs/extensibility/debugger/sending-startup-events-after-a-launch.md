---
title: Senden von Startereignissen nach einem Start | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 64a2423e3e6900d992ba1a2fafe13f72ab329520
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49927072"
---
# <a name="send-startup-events-after-a-launch"></a>Senden von Start-Ereignissen nach einem Start
Sobald die Debug-Engine (DE) an die Anwendung angefügt ist, sendet es eine Reihe von Startup-Ereignisse an die Debug-Sitzung.  
  
 Startup-Ereignisse, die an die Debug-Sitzung zurückgesendet gehören:  
  
- Ein Ereignis für den Engine-Erstellung.  
  
- Ein Programm erstellen-Ereignis.  
  
- Thread-Erstellung und Ladeereignisse für Module.  
  
- Ein Auslastungstest vollständiges Ereignis gesendet, wenn der Code geladen und für die Ausführung bereit ist, aber bevor irgendwelcher Code ausgeführt wird. 
  
  > [!NOTE]
  >  Wenn dieses Ereignis fortgesetzt wird, globale Variablen werden initialisiert, und startroutinen ausführen.  
  
- Mögliche andere Threads erstellen und Ladeereignisse für Module an.  
  
- Ein punktereignis Eintrag, der signalisiert, dass die Anwendung der Haupteinstiegspunkt, z. B. erreicht hat **Main** oder `WinMain`. Dieses Ereignis wird nicht in der Regel gesendet, wenn die DE an ein Programm angefügt wird, die bereits ausgeführt wird.  
  
  Programmgesteuert, sendet der DE zuerst die sitzungsbasierter Debug-Manager (SDM) eine [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) -Schnittstelle, die ein Modul erstellen-Ereignis darstellt, gefolgt von einem [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , ein Programm Erstellungsereignis steht.  
  
  Diese Ereignisse werden in der Regel durch eine oder mehrere befolgt [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) thread-Ereignisse der diensterstellung und [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) Ladeereignisse für Module.  
  
  Wenn der Code geladen und ausgeführt, aber bevor Code ausgeführt wird, der DE das SDM sendet ein [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) vollständige Load-Ereignis. Wenn die Anwendung nicht bereits ausgeführt wird, die DE sendet dann eine [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) Eintrag punktereignis, damit an, dass das Programm seine Haupteinstiegspunkt erreicht hat und wird zum Debuggen bereit ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Steuern der Ausführung](../../extensibility/debugger/control-of-execution.md)   
 [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)