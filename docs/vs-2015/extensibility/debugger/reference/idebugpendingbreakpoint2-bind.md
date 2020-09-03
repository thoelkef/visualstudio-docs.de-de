---
title: 'IDebugPendingBreakpoint2:: Bind | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::Bind
helpviewer_keywords:
- Bind method
- IDebugPendingBreakpoint2::Bind method
ms.assetid: 46e3f307-219d-40cd-a929-d41399c60ecf
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 33cdcad38e2f46962120dcd63c1be21675060be0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194534"
---
# <a name="idebugpendingbreakpoint2bind"></a>IDebugPendingBreakpoint2::Bind
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bindet diesen ausstehenden Breakpoint an einen oder mehrere Code Speicherorte.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Bind(   
   void   
);  
```  
  
```csharp  
int Bind();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Gibt zurück, `E_BP_DELETED` Wenn der Breakpoint gelöscht wurde.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn diese Methode aufgerufen wird, sollte eine Debug-Engine (de) versuchen, diesen ausstehenden Haltepunkt an alle Code Positionen zu binden, die mit identisch sind.  
  
 Nachdem diese Methode zurückgegeben wurde, muss der Aufrufer auf Ereignisse warten, die angeben, dass der ausstehende Haltepunkt gebunden wurde oder einen Fehler aufweist, bevor angenommen wird, dass Aufrufe von [enumboundbreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) oder [enumerrorbreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md).-Methoden alle gebundenen bzw. Fehler Breakpunkte auflisten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)   
 [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)   
 [Enumboundbreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
