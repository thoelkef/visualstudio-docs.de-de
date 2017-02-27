---
title: "IDebugPendingBreakpoint2::Enable | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPendingBreakpoint2::Enable"
helpviewer_keywords: 
  - "IDebugPendingBreakpoint2::Enable-Methode"
  - "Enable-Methode"
ms.assetid: 09e32d05-464b-40a6-a41d-76f2759cf2cd
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPendingBreakpoint2::Enable
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Schaltet den aktivierten Zustand des anstehenden Haltepunkts.  
  
## Syntax  
  
```cpp#  
HRESULT Enable(   
   BOOL fEnable  
);  
```  
  
```c#  
int Enable(   
   int fEnable  
);  
```  
  
#### Parameter  
 `fEnable`  
 \[in\]  Position als ungleich 0 \(`TRUE`\), um einen ausstehenden Haltepunkte aktivieren oder auf Null \(`FALSE`\), um zu deaktivieren.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  Gibt `E_BP_DELETED` zurück, wenn der Haltepunkt gelöscht wurde.  
  
## Hinweise  
 Wenn ein anstehender Haltepunkt aktiviert oder deaktiviert ist, werden alle Haltepunkte, die von ihm gebunden sind, auf den gleichen Zustand festgelegt.  
  
 Diese Methode wird bei Bedarf beliebig oft aufgerufen werden, auch wenn der Haltepunkt bereits aktiviert oder deaktiviert wird.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie diese Methode für ein einfaches `CPendingBreakpoint`\-Objekt implementiert, das die [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)\-Schnittstelle verfügbar macht.  
  
```cpp#  
HRESULT CPendingBreakpoint::Enable(BOOL fEnable)    
{    
   HRESULT hr;    
  
   // Verify that the pending breakpoint has not been deleted. If deleted,   
   // then return hr = E_BP_DELETED.    
   if (m_state.state != PBPS_DELETED)    
   {    
      // If the bound breakpoint member variable is valid, then enable or   
      // disable the bound breakpoint.    
      if (m_pBoundBP)    
      {    
         m_pBoundBP->Enable(fEnable);    
      }    
      // Set the PENDING_BP_STATE in the PENDING_BP_STATE_INFO structure   
      // to enabled or disabled depending on the passed BOOL condition.    
      m_state.state = fEnable ? PBPS_ENABLED : PBPS_DISABLED;    
      hr = S_OK;    
  
   }    
   else    
   {    
      hr = E_BP_DELETED;    
   }    
  
   return hr;    
}    
```  
  
## Siehe auch  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)