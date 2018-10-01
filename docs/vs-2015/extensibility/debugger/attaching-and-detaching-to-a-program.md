---
title: Anfügen und Trennen von einem Programm | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a7129fab85d405d941394c02abf79ba29e787f5b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511416"
---
# <a name="attaching-and-detaching-to-a-program"></a>Anfügen an ein und Trennen von einem Programm
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Anfügen und Trennen von einem Programm](https://docs.microsoft.com/visualstudio/extensibility/debugger/attaching-and-detaching-to-a-program).  
  
Das Anfügen des Debuggers gesendet werden müssen, der richtigen Sequenz von Methoden und Ereignisse mit den richtigen Attributen.  
  
## <a name="sequence-of-methods-and-events"></a>Sequenz von Methoden und Ereignisse  
  
1.  Ruft die Sitzungs-Debug-Manager (SDM) die [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) Methode.  
  
     Basierend auf der Debug-Engine (DE)-Prozessmodell der `IDebugProgramNodeAttach2::OnAttach` Methode gibt einen der folgenden Methoden, die bestimmt, was als Nächstes geschieht zurück.  
  
     Wenn `S_FALSE` zurückgegeben wird, wird die Debug-Engine wurde erfolgreich an das Programm angefügt wurde. Andernfalls die [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md) Methode wird aufgerufen, um den anfügungsprozess zu beenden.  
  
     Wenn `S_OK` zurückgegeben wird, ist der DE in demselben Prozess wie das SDM geladen werden. Das SDM führt die folgenden Aufgaben:  
  
    1.  Aufrufe [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) zum Abrufen der Engine Informationen des DE.  
  
    2.  Gemeinsam erstellt die DE.  
  
    3.  Aufrufe [Anfügen](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
2.  Der DE sendet eine [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) , das SDM mit einer `EVENT_SYNC` Attribut.  
  
3.  Der DE sendet eine [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , das SDM mit einer `EVENT_SYNC` Attribut.  
  
4.  Der DE sendet eine [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) , das SDM mit einer `EVENT_SYNC_STOP` Attribut.  
  
 Trennen von einem Programm ist eine einfache, zweistufiger Prozess, wie folgt:  
  
1.  Die SDM-Aufrufe [trennen](../../extensibility/debugger/reference/idebugprogram2-detach.md).  
  
2.  Der DE sendet eine [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)

