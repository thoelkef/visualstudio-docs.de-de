---
title: Senden der erforderlichen Ereignisse | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 457e2daf3e52c23ba9733d09d3aeb94750b5fab9
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2020
ms.locfileid: "90841271"
---
# <a name="sending-the-required-events"></a>Senden der erforderlichen Ereignisse
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Verwenden Sie dieses Verfahren, um erforderliche Ereignisse zu senden.  
  
## <a name="process-for-sending-required-events"></a>Prozess zum Senden erforderlicher Ereignisse  
 Die folgenden Ereignisse sind in dieser Reihenfolge erforderlich, wenn Sie eine Debug-Engine (de) erstellen und an ein Programm anfügen:  
  
1. Senden Sie ein [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) -Ereignis Objekt an den Sitzungs-Debug-Manager (SDM), wenn de zum Debuggen von einem oder mehreren Programmen in einem Prozess initialisiert wird.  
  
2. Wenn das zu dedebugging Ende Programm an angefügt ist, senden Sie ein [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) -Ereignis Objekt an SDM. Dieses Ereignis ist möglicherweise ein anhalteereignis, je nach Engine-Design.  
  
3. Wenn das Programm beim Starten des Prozesses an angefügt wird, senden Sie ein [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) -Ereignis Objekt an SDM, um die IDE des neuen Threads zu benachrichtigen. Dieses Ereignis ist möglicherweise ein anhalteereignis, je nach Engine-Design.  
  
4. Senden Sie ein [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) -Ereignis Objekt an SDM, wenn das Programm, das gerade deentschlgt wird, abgeschlossen ist oder wenn das Programm abgeschlossen ist. Dieses Ereignis muss ein anhalteereignis sein.  
  
5. Wenn die zu decodierende Anwendung gestartet wird, senden Sie ein [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) -Ereignis Objekt an SDM, wenn die erste Anweisung des Codes in der Lauf Zeit Architektur gerade ausgeführt wird. Dieses Ereignis ist immer ein anhalteereignis. Wenn Sie in die Debugsitzung eintreten, wird die IDE bei diesem Ereignis beendet.  
  
> [!NOTE]
> Viele Sprachen verwenden globale Initialisierer oder externe, vorkompilierte Funktionen (aus der CRT-Bibliothek oder _Main) am Anfang des Codes. Wenn die Sprache des Programms, das Sie Debuggen, einen dieser Elementtypen vor dem ersten Einstiegspunkt enthält, wird dieser Code ausgeführt, und das Einstiegspunkt Ereignis wird gesendet, wenn der Benutzer Einstiegspunkt, z. b. **Main** oder `WinMain` , erreicht wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aktivieren eines Programms für das Debuggen](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
