---
title: Senden die erforderlichen Ereignisse | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: deeffb814dacc58b1fb3a3f993203139d9b1a081
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126170"
---
# <a name="sending-the-required-events"></a>Senden die erforderlichen Ereignisse
Verwenden Sie dieses Verfahren für das Senden von Ereignissen Erforderlicher.  
  
## <a name="process-for-sending-required-events"></a>Prozess für das Senden von Ereignissen Erforderlicher  
 Die folgenden Ereignisse sind erforderlich, in der Reihenfolge, erstellen eine Debug-engine (Deutschland) und an ein Programm anzufügen:  
  
1.  Senden einer [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) Ereignisobjekt Sitzung Debug-Manager (SDM), wenn die DE initialisiert wird, für eine oder mehrere Programme in einem Prozess zu debuggen.  
  
2.  Wenn das Programm, das gedebuggt werden angefügt ist, senden wir Ihnen eine [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) Ereignisobjekt, das SDM. Dieses Ereignis möglicherweise je nach Entwurf des Datenbankmoduls ein Stopping-Ereignis.  
  
3.  Wenn die Anwendung angefügt ist, wenn der Prozess gestartet wird, senden Sie eine [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) Ereignisobjekt, das SDM der der neue Thread IDE benachrichtigt. Dieses Ereignis möglicherweise je nach Entwurf des Datenbankmoduls ein Stopping-Ereignis.  
  
4.  Senden einer [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) Ereignisobjekt, das SDM bei der zu debuggenden Programms ist, beendet das Laden oder wenn das Anfügen an das Programm abgeschlossen ist. Dieses Ereignis muss einen Stopping-Ereignis.  
  
5.  Wenn die zu debuggende Anwendung gestartet wird, senden Sie eine [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) Ereignisobjekt, das SDM bei die erste Anweisung des Codes in der Laufzeit-Architektur ausgeführt werden soll. Dieses Ereignis wird immer eine Stopping-Ereignis. Wenn die Debugsitzung schrittweise ausführen, wird die IDE auf dieses Ereignis beendet.  
  
> [!NOTE]
>  Viele Sprachen werden globale Initialisierer oder externe, vorkompilierte Funktionen (aus der CRT-Bibliothek oder _Main) am Anfang des Codes verwenden. Wenn die Sprache des Programms, das Sie Debuggen enthält diesen Typen von Elementen vor dem ersten Einstiegspunkt, dieser Code ausgeführt wird, und das punktereignis Eintrag wird gesendet. wenn der benutzerdefinierte Einstiegspunkt zeigen, wie z. B. **main** oder `WinMain`, erreicht ist.  
  
## <a name="see-also"></a>Siehe auch  
 [Aktivieren eines Programms für das Debuggen](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)