---
title: Start basierte Anlage | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 09a6b39bef9ba6af098bf92d779a490e22492209
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203160"
---
# <a name="launch-based-attachment"></a>Startbasiertes Anfügen
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die Start basierte Anlage zu einem Programm erfolgt automatisch. Wenn der Prozess, in dem das Programm gehostet wird, von der SDM gestartet wird, folgt die Start basierte Anlage einem Pfad, der dem der manuellen Anlage-Methode ähnelt. Weitere Informationen finden [Sie unter Anhängen an das Programm](../../extensibility/debugger/attaching-to-the-program.md).  
  
## <a name="the-attaching-process"></a>Der Anfüge Vorgang  
 Der Hauptunterschied ist die Abfolge der Ereignisse nach dem **Anfüge** Befehl, wie folgt:  
  
1. Senden Sie ein **IDebugEngineCreateEvent2** -Ereignis Objekt an SDM. Weitere Informationen finden Sie unter [Senden von Ereignissen](../../extensibility/debugger/sending-events.md).  
  
2. Ruft die- `IDebugProgram2::GetProgramId` Methode für die an die **Attach** -Methode weiter gegebene **IDebugProgram2** -Schnittstelle auf.  
  
3. Senden Sie ein **IDebugProgramCreateEvent2** -Ereignis Objekt, um die SDM zu benachrichtigen, dass das lokale **IDebugProgram2** -Objekt erstellt wurde, um das Programm für die de darzustellen.  
  
4. Senden Sie ein [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) -Ereignis Objekt, um die SDM zu benachrichtigen, dass ein neuer Thread für den gestarteten Prozess erstellt wird.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Senden der erforderlichen Ereignisse](../../extensibility/debugger/sending-the-required-events.md)   
 [Aktivieren eines Programms für das Debuggen](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
