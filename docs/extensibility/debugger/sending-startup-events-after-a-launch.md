---
title: Senden von Startereignisse nach einem Start | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 65e05d7da2acf5bd3eaf8dab1e3781d3d5b244a0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="sending-startup-events-after-a-launch"></a>Senden von Startereignisse nach einem starten
Sobald die Debugging-Modul (DE) an die Anwendung angefügt ist, sendet er eine Reihe von Startereignisse die Debugsitzung an.  
  
 Startup-Ereignisse, die an Sie zurückgesendet und die Debugsitzung umfassen Folgendes:  
  
-   Ein Modul erstellen-Ereignis.  
  
-   Ein Programm erstellen-Ereignis.  
  
-   Thread-Erstellung und Ladeereignisse für Module.  
  
-   Eine vollständige Ladeereignis, gesendet, wenn der Code geladen und für die Ausführung bereit ist, aber bevor Code ausgeführt wird  
  
    > [!NOTE]
    >  Wenn dieses Ereignis fortgesetzt wird, globale Variablen werden initialisiert und startroutinen ausführen.  
  
-   Mögliche andere thread erstellen und Ladeereignisse für Module an.  
  
-   Ein Eintrag Punkt-Ereignis, das signalisiert, dass die Anwendung wie z. B. der Haupteinstiegspunkt erreicht hat **Main** oder `WinMain`. Dieses Ereignis wird nicht in der Regel gesendet, wenn die DE an ein Programm angefügt wird, die bereits ausgeführt wird.  
  
 Programmgesteuert, DE den Sitzungs-Manager (SDM) zuerst sendet eine [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) -Schnittstelle, die ein Modul Erstellung-Ereignis darstellt, gefolgt von einer [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , der ein Programm Erstellungsereignis darstellt.  
  
 Dies ist i. d. r. gefolgt von einem oder mehreren [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) Ereignisse beim Erstellen von Threads und [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) Ladeereignisse für Module.  
  
 Wenn der Code geladen und ausgeführt, aber bevor Code ausgeführt wird, der Deutschland die SDM sendet ein [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) Last ausgelöste Ereignis. Wenn das Programm nicht bereits ausgeführt wird, die DE sendet eine [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) Eintrag punktereignis, signalisieren, dass das Programm die Haupteinstiegspunkt erreicht hat und bereit für das Debuggen ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Steuerung der Ausführung](../../extensibility/debugger/control-of-execution.md)   
 [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)