---
title: IDebugBreakEvent2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBreakEvent2
helpviewer_keywords: IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 41c63d947d1c59e041aef051fffc4def85e0bded
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
Diese Schnittstelle weist dem Sitzungs-Manager (SDM), dass eine asynchrone Unterbrechung erfolgreich abgeschlossen wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugBreakEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die DE implementiert diese Schnittstelle, um Benutzer Seitenumbrüche in einem Programm zu unterstützen. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss implementiert werden, auf das gleiche Objekt wie diese Schnittstelle (verwendet die SDM [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die `IDebugEvent2` Schnittstelle).  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Ruft die SDM [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) der Benutzer hat zu debuggenden Programms um angehalten werden, wenn angefordert. Wenn das Programm erfolgreich angehalten wurde, sendet der Deutschland die `IDebugBreakEvent2` Ereignis. Dieses Ereignis wird gesendet, mit der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion, die durch die SDM angegeben werden, wenn es an das derzeit debuggte Programm angefügt.  
  
## <a name="remarks"></a>Hinweise  
 Z. B. einen Benutzer auswählen kann die **alle unterbrechen** Befehl die **Debuggen** Menü außerhalb eines Programms unterbrechen, die eine Endlosschleife ausgeführt wird. Die SDM weist das Programm beenden durch Aufrufen von [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md). Sendet die DE `IDebugBreakEvent2` , schließlich das Programm nicht mehr.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)