---
title: "IDebugBoundBreakpoint2::GetState | Microsoft Docs"
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
  - "IDebugBoundBreakpoint2::GetState"
helpviewer_keywords: 
  - "GetState-Methode"
  - "IDebugBoundBreakpoint2::GetState-Methode"
ms.assetid: a40a8382-295e-4916-aae6-ffe3a9cd3f2d
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBoundBreakpoint2::GetState
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Zustand dieses springen Haltepunkt ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetState(   
   BP_STATE* pState  
);  
```  
  
```c#  
int GetState(   
   out enum_BP_STATE pState  
);  
```  
  
#### Parameter  
 `pState`  
 \[out\]  Gibt einen Wert aus der [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)\-Enumeration zurück, der den Zustand des Haltepunkts beschreibt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie diese Methode für ein einfaches `CBoundBreakpoint`\-Objekt implementiert, das die [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)\-Schnittstelle verfügbar macht.  
  
```  
HRESULT CBoundBreakpoint::GetState(BP_STATE* pState)    
{    
   HRESULT hr;    
  
   // Check for a valid pointer to pState and assign the local state variable.    
   if (pState)    
   {    
      *pState = m_state;    
      hr = S_OK;    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## Siehe auch  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)