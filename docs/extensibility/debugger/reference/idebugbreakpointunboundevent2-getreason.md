---
title: "IDebugBreakpointUnboundEvent2::GetReason | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointUnboundEvent2::GetReason"
helpviewer_keywords: 
  - "IDebugBreakpointUnboundEvent2::GetReason"
ms.assetid: 0f8a4fec-d3eb-417d-8516-4f7b51904033
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBreakpointUnboundEvent2::GetReason
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Grund ab, den der Haltepunkt aufgehoben wurde.  
  
## Syntax  
  
```cpp#  
HRESULT GetReason(   
   BP_UNBOUND_REASON* pdwUnboundReason  
);  
```  
  
```c#  
int GetReason(   
   out enum_ BP_UNBOUND_REASON pdwUnboundReason  
);  
```  
  
#### Parameter  
 `pdwUnboundReason`  
 \[out\]  Gibt einen Wert aus der [BP\_UNBOUND\_REASON](../../../extensibility/debugger/reference/bp-unbound-reason.md)\-Enumeration zurück, der den Grund angibt, den der Haltepunkt aufgehoben wurde.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Gründe schließen, der ein Haltepunkt an einer anderen Stelle nach einem Bearbeiten und Fortfahren Vorgang erneut gebunden sind, oder eine Angabe, dass ein Haltepunkt im Fehler gebunden wurde.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie diese Methode für ein **CBreakpointUnboundDebugEventBase\-Objekt** implementiert, das die [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)\-Schnittstelle verfügbar macht.  
  
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
  
## Siehe auch  
 [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)