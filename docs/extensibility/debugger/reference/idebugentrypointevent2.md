---
title: IDebugEntryPointEvent2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEntryPointEvent2
helpviewer_keywords:
- IDebugEntryPointEvent2 interface
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2205ef7d6fa8b270ce30224f867dd2c318272b37
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992281"
---
# <a name="idebugentrypointevent2"></a>IDebugEntryPointEvent2
Die Debug-Engine (DE) sendet diese Schnittstelle für die Sitzung Debug-Manager (SDM), wenn die Anwendung der ersten Anweisung des Benutzercodes ausgeführt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugEntryPointEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die DE implementiert diese Schnittstelle als Teil der normalen Vorgänge. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) Schnittstelle muss auf dasselbe Objekt wie diese Schnittstelle implementiert werden. Wird verwendet, das SDM [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die `IDebugEvent2` Schnittstelle.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die DE erstellt und dieses Ereignisobjekt sendet, wenn das derzeit debuggte Programm geladen wurde und bereit für die erste Anweisung des Benutzercodes ausgeführt wird. Das Ereignis gesendet wird, mithilfe der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Callback-Funktion, die durch die SDM bereitgestellt wird, wenn diese an die zu debuggende Programm wird angefügt.  
  
## <a name="remarks"></a>Hinweise  
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) wird gesendet, wenn die Anwendung die erste Anweisung ausgeführt wird. Z. B. `IDebugEntryPoint2` wird gesendet, wenn das Programm des Benutzers ausgeführt wird `main` Funktion.  
  
 Wenn die DE sendet `IDebugEntryPointEvent2`, die aktuelle Position der Code muss bei der ersten Anweisung des Benutzercodes, wie z. B. `main`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)