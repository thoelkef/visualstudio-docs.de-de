---
title: IDebugBoundBreakpoint2::GetBreakpointResolution | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBoundBreakpoint2::GetBreakpointResolution
helpviewer_keywords:
- GetBreakpointResolution method
- IDebugBoundBreakpoint2::GetBreakpointResolution method
ms.assetid: 4479ac61-18a9-4a30-b213-9921c5af9a26
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af52b8f1047e806a3a64902584ad44ed534a3b83
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54944695"
---
# <a name="idebugboundbreakpoint2getbreakpointresolution"></a>IDebugBoundBreakpoint2::GetBreakpointResolution
Ruft die haltepunktauflösung, die diesem Breakpoint beschreibt.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetBreakpointResolution(   
   IDebugBreakpointResolution2** ppBPResolution  
);  
```  
  
```csharp  
int GetBreakpointResolution(   
   out IDebugBreakpointResolution2 ppBPResolution  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppBPResolution`  
 [out] Gibt die [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md) Schnittstelle, die einen der folgenden darstellt:  
  
-   Der Haltepunkt Auflösung-Objekt, das die Position im Code wird beschrieben, in denen ein codehaltepunkt gebunden wurde.  
  
-   Der Speicherort, in denen ein Datenhaltepunkt gebunden ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. Gibt `E_BP_DELETED` , wenn der Zustand des Objekts gebundene Haltepunkt, um festgelegt ist `BPS_DELETED` (Teil der [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) Enumeration).  
  
## <a name="remarks"></a>Hinweise  
 Rufen Sie die [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md) Methode, um zu bestimmen, ob es sich bei der haltepunktauflösung für Code- oder Datenmenge ist.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine einfache `CBoundBreakpoint` -Objekt, das macht die [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md) Schnittstelle.  
  
```  
HRESULT CBoundBreakpoint::GetBreakpointResolution(  
    IDebugBreakpointResolution2** ppBPResolution)  
{    
   HRESULT hr;    
  
   if (ppBPResolution)    
   {    
      // Verify that the bound breakpoint has not been deleted. If   
      // deleted, then return hr = E_BP_DELETED.    
      if (m_state != BPS_DELETED)    
      {    
         // Query for the IDebugBreakpointResolution2 interface.    
         hr = m_pBPRes->QueryInterface(IID_IDebugBreakpointResolution2,  
                                       (void **)ppBPResolution);  
         assert(hr == S_OK);    
      }    
      else    
      {    
         hr = E_BP_DELETED;    
      }    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)   
 [GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)