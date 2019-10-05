---
title: IDebugBreakpointBoundEvent2::EnumBoundBreakpoints | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBreakpointBoundEvent2::EnumBoundBreakpoints
helpviewer_keywords:
- IDebugBreakpointBoundEvent2::EnumBoundBreakpoints
ms.assetid: 1f588feb-522e-488d-be92-7bc19b9e3688
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bc3d38344dccf93f4b032357b2cdef88a0a4a242
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68156128"
---
# <a name="idebugbreakpointboundevent2enumboundbreakpoints"></a>IDebugBreakpointBoundEvent2::EnumBoundBreakpoints
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Erstellt einen Enumerator von Haltepunkten, die auf dieses Ereignis gebunden wurden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT EnumBoundBreakpoints(   
   IEnumDebugBoundBreakpoints2** ppEnum  
);  
```  
  
```csharp  
int EnumBoundBreakpoints(   
   out IEnumDebugBoundBreakpoints2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppEnum`  
 [out] Gibt eine [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) -Objekt, das Listet alle Haltepunkte von diesem Ereignis gebunden.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` treten keine gebundene Haltepunkte; andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die Liste der gebundene Haltepunkte für diese Grenze auf dieses Ereignis ist und möglicherweise nicht die gesamte Liste der Haltepunkte ein ausstehender Haltepunkt gebunden. Rufen Sie zum Abrufen einer Liste aller Haltepunkte, die an ein ausstehender Haltepunkt gebunden der [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) -Methode zum Abrufen von der zugeordneten [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) Objekt und rufen Sie dann die [ EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) -Methode zum Abrufen einer [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md) Objekt, das die gebundene Haltepunkte für den ausstehenden Haltepunkt enthält.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine **CBreakpointSetDebugEventBase** -Objekt, das macht die [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) Schnittstelle.  
  
```cpp#  
STDMETHODIMP CBreakpointSetDebugEventBase::EnumBoundBreakpoints(  
    IEnumDebugBoundBreakpoints2 **ppEnum)  
{  
    HRESULT hRes = E_FAIL;  
  
    if ( ppEnum )  
    {  
        if ( m_pEnumBound )  
        {  
            hRes = m_pEnumBound->Clone(ppEnum);  
  
            if ( EVAL(S_OK == hRes) )  
                (*ppEnum)->Reset();  
        }  
        else  
            hRes = E_FAIL;  
    }  
    else  
        hRes = E_INVALIDARG;  
  
    return ( hRes );  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)   
 [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
