---
title: Anfügen und trennen an ein Programm | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6e232a6f7fcb8813670ca6d949fdb6b3287bb79c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146444"
---
# <a name="attaching-and-detaching-to-a-program"></a>Anfügen an ein und Trennen von einem Programm
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Das Anfügen des Debuggers erfordert, dass die richtige Sequenz von Methoden und Ereignissen mit den richtigen Attributen gesendet wird.  
  
## <a name="sequence-of-methods-and-events"></a>Abfolge von Methoden und Ereignissen  
  
1. Der Sitzungs-Debug-Manager (SDM) Ruft die [onattach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) -Methode auf.  
  
    Basierend auf dem Prozessmodell der Debug-Engine (de) `IDebugProgramNodeAttach2::OnAttach` gibt die Methode eine der folgenden Methoden zurück, die bestimmt, was als nächstes geschieht.  
  
    Wenn `S_FALSE` zurückgegeben wird, wurde die Debug-Engine erfolgreich an das Programm angefügt. Andernfalls wird die [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) -Methode aufgerufen, um den Anfüge Vorgang abzuschließen.  
  
    Wenn `S_OK` zurückgegeben wird, muss de in demselben Prozess wie das SDM geladen werden. Der SDM führt die folgenden Aufgaben aus:  
  
   1. Ruft [getengineinfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) auf, um die Engine-Informationen von de zu erhalten.  
  
   2. Erstellt die de.  
  
   3. Aufrufe [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
2. Der de sendet ein [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) -Attribut mit einem-Attribut an die SDM `EVENT_SYNC` .  
  
3. Der de sendet ein [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) -Attribut mit einem-Attribut an die SDM `EVENT_SYNC` .  
  
4. Der de sendet ein [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) -Attribut mit einem-Attribut an die SDM `EVENT_SYNC_STOP` .  
  
   Das Trennen von einem Programm ist ein einfacher, zweistufiger Prozess:  
  
5. Die SDM-Aufrufe [trennen](../../extensibility/debugger/reference/idebugprogram2-detach.md).  
  
6. Der de sendet eine [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)
