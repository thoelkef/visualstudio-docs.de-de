---
title: Senden von Start Ereignissen nach einem Start | Microsoft-Dokumentation
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
ms.openlocfilehash: caf36e6713e49bb1470cd720ba2d04f689abba43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841032"
---
# <a name="sending-startup-events-after-a-launch"></a>Senden von Startereignissen nach einem Start
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nachdem die Debug-Engine (de) an das Programm angefügt wurde, sendet Sie eine Reihe von Start Ereignissen an die Debugsitzung zurück.  
  
 Die an die Debugsitzung zurückgesendeten Start Ereignisse umfassen Folgendes:  
  
- Ein Engine-Erstellungs Ereignis.  
  
- Ein Programm Erstellungs Ereignis.  
  
- Thread Erstellung und Modul Lade Ereignisse.  
  
- Ein Load Complete-Ereignis, das gesendet wird, wenn der Code geladen und bereit ist, aber vor dem Ausführen von Code ausgeführt wird.  
  
  > [!NOTE]
  > Wenn dieses Ereignis fortgesetzt wird, werden globale Variablen initialisiert, und Start Routinen werden ausgeführt.  
  
- Mögliche andere Thread Erstellung und Modul Lade Ereignisse.  
  
- Ein Einstiegspunkt Ereignis, das signalisiert, dass das Programm den Haupteinstiegspunkt erreicht hat, z. b. **Main** oder `WinMain` . Dieses Ereignis wird in der Regel nicht gesendet, wenn die de an ein bereits ausgelaufendes Programm angefügt wird.  
  
  Programm gesteuert Sendet der de zuerst den Session Debug Manager (SDM) an eine [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) -Schnittstelle, die ein Engine-Erstellungs Ereignis darstellt, gefolgt von einem [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md), das ein Programm Erstellungs Ereignis darstellt.  
  
  In der Regel folgt ein oder mehrere [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) -Thread Erstellungs Ereignisse und [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) -Modul Lade Ereignisse.  
  
  Wenn der Code geladen und zur Ausführung bereit ist, aber bevor Code ausgeführt wird, sendet der de das SDM-Ereignis " [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) Load Complete". Wenn das Programm nicht bereits ausgeführt wird, sendet der de ein [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) -Einstiegspunkt Ereignis, das signalisiert, dass das Programm den Haupteinstiegspunkt erreicht hat und zum Debuggen bereit ist.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kontrolle der Ausführung](../../extensibility/debugger/control-of-execution.md)   
 [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)
