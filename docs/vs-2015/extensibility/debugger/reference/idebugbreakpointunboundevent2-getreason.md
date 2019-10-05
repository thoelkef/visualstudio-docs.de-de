---
title: IDebugBreakpointUnboundEvent2::GetReason | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBreakpointUnboundEvent2::GetReason
helpviewer_keywords:
- IDebugBreakpointUnboundEvent2::GetReason
ms.assetid: 0f8a4fec-d3eb-417d-8516-4f7b51904033
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6633fa2b3950d49a3db3b286157d50c026261300
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68160033"
---
# <a name="idebugbreakpointunboundevent2getreason"></a>IDebugBreakpointUnboundEvent2::GetReason
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ruft den Grund ab, die, den der Haltepunkt aufgehoben wurde.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetReason(   
   BP_UNBOUND_REASON* pdwUnboundReason  
);  
```  
  
```csharp  
int GetReason(   
   out enum_ BP_UNBOUND_REASON pdwUnboundReason  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdwUnboundReason`  
 [out] Gibt einen Wert aus der [BP_UNBOUND_REASON](../../../extensibility/debugger/reference/bp-unbound-reason.md) Enumeration, der den Grund, der der Haltepunkt aufgehoben wurde.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ursachen ein Haltepunkts wird erneut gebunden an einen anderen Speicherort nach einem bearbeiten und Fortfahren-Vorgang, oder eine Entscheidung treffen, dass ein Haltepunkt gebunden wurde.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine **CBreakpointUnboundDebugEventBase** -Objekt, das macht die [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) Schnittstelle.  
  
```cpp#  
STDMETHODIMP CBreakpointUnboundDebugEventBase::GetReason(  
    BP_UNBOUND_REASON* pdwUnboundReason)  
{  
    HRESULT hRes = E_FAIL;  
  
    if ( EVAL(pdwUnboundReason) )  
    {  
        *pdwUnboundReason = m_dwReason;  
  
        hRes = S_OK;  
    }  
    else  
        hRes = E_INVALIDARG;  
  
    return ( hRes );  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)
