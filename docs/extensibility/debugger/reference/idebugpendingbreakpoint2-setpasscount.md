---
title: "IDebugPendingBreakpoint2::SetPassCount | Microsoft Docs"
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
  - "IDebugPendingBreakpoint2::SetPassCount"
helpviewer_keywords: 
  - "SetPassCount-Methode"
  - "IDebugPendingBreakpoint2::SetPassCount-Methode"
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPendingBreakpoint2::SetPassCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Anzahl der Änderungen übergeben oder legt diese fest, die dem anstehenden Haltepunkt.  
  
## Syntax  
  
```cpp#  
HRESULT SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
```c#  
int SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
#### Parameter  
 `bpPassCount`  
 \[in\]  Eine Struktur, die die [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) Anzahl übergeben.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  Gibt `E_BP_DELETED` zurück, wenn der Haltepunkt gelöscht wurde.  
  
## Hinweise  
 Jede gültige Anzahl, die zuvor mit dem anstehenden Haltepunkt zugeordnet wurde, geht verloren.  Alle Haltepunkte, die von diesem anstehenden Haltepunkt gebunden sind, werden aufgerufen, um die Anzahl der zum `bpPassCount` übergeben Parameter festzulegen.  
  
## Siehe auch  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)