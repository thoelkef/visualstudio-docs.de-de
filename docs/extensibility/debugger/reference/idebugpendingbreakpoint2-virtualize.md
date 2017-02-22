---
title: "IDebugPendingBreakpoint2::Virtualize | Microsoft Docs"
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
  - "IDebugPendingBreakpoint2::Virtualize"
helpviewer_keywords: 
  - "Virtualisierung-Methode"
  - "IDebugPendingBreakpoint2::Virtualize-Methode"
ms.assetid: 58c8e9a5-4494-47c2-bddb-56f628da6a2d
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPendingBreakpoint2::Virtualize
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Schaltet den virtualisierten Zustand dieses ausstehenden Haltepunkte um.  Wenn ein anstehender Haltepunkt virtualisiert wird, versucht das Debugmodul, diesen Code bei jedem Laden neuer im Programm zu binden.  
  
## Syntax  
  
```cpp#  
HRESULT Virtualize(   
   BOOL fVirtualize  
);  
```  
  
```cpp#  
int Virtualize(   
   int fVirtualize  
);  
```  
  
#### Parameter  
 `fVirtualize`  
 \[in\]  Position als ungleich 0 \(`TRUE`\), um den anstehenden Haltepunkts zu virtualisieren oder Null \(`FALSE`\), um die Virtualisierung zu deaktivieren.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  Gibt `E_BP_DELETED` zurück, wenn der Haltepunkt gelöscht wurde.  
  
## Hinweise  
 Ein virtualisierter Haltepunkt gebunden wird bei jedem Code geladen wird.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie diese Methode für ein einfaches `CPendingBreakpoint`\-Objekt implementiert, das die [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)\-Schnittstelle verfügbar macht.  
  
```cpp#  
HRESULT CPendingBreakpoint::Virtualize(BOOL fVirtualize)    
{    
   HRESULT hr;    
  
   // Verify that the pending breakpoint has not been deleted. If deleted,   
   // then return hr = E_BP_DELETED.    
   if (m_state.state != PBPS_DELETED)    
   {    
      if (fVirtualize)    
      {    
         // Set the PBPSF_VIRTUALIZED flag in the PENDING_BP_STATE_FLAGS   
         // structure.    
         SetFlag(m_state.flags, PBPSF_VIRTUALIZED);    
      }    
      else    
      {    
         // Clear the PBPSF_VIRTUALIZED flag in the PENDING_BP_STATE_FLAGS   
         // structure.    
         ClearFlag(m_state.flags, PBPSF_VIRTUALIZED);    
      }    
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