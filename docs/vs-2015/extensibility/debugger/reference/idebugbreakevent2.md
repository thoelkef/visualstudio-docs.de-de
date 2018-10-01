---
title: IDebugBreakEvent2 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 02510353cbd160a3872d6580535414cd5500cde7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47509407"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugBreakEvent2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugbreakevent2).  
  
Diese Schnittstelle weist den sitzungsbasierter Debug-Manager (SDM), dass eine asynchrone Unterbrechung erfolgreich abgeschlossen wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugBreakEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die DE implementiert diese Schnittstelle, um Unterbrechungen für Benutzer in einem Programm zu unterstützen. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) Schnittstelle muss auf dasselbe Objekt wie diese Schnittstelle implementiert werden (wird verwendet, das SDM [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) für den Zugriff auf die `IDebugEvent2` Schnittstelle).  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die SDM-Aufrufe [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) Wenn der Benutzer hat angefordert, die zu debuggende Programm wird zum angehalten werden. Wenn die Anwendung wurde erfolgreich angehalten wurde, sendet der DE der `IDebugBreakEvent2` Ereignis. Dieses Ereignis wird gesendet, mit der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Callback-Funktion, die durch die SDM angegeben wird, wenn diese an die zu debuggende Programm wird angefügt.  
  
## <a name="remarks"></a>Hinweise  
 Ein Benutzer kann auswählen, z. B. die **alle unterbrechen** Befehl die **Debuggen** Menü, um ein Programm verlassen, der eine unendliche Schleife ausgeführt wird. Das SDM teilt dem Programm beenden durch Aufrufen von [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md). Der DE sendet `IDebugBreakEvent2` , die Anwendung schließlich nicht mehr.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)

