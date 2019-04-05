---
title: IDebugBreakEvent2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4858d5086baf65b9d3e1e7c28fbd0d1707403412
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58956635"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
