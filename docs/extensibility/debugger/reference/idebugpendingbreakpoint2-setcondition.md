---
title: "IDebugPendingBreakpoint2::SetCondition | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPendingBreakpoint2::SetCondition"
helpviewer_keywords: 
  - "SetCondition-Methode"
  - "IDebugPendingBreakpoint2::SetCondition-Methode"
ms.assetid: 0534224f-654f-4862-bc4d-a9a81a5f8899
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPendingBreakpoint2::SetCondition
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Legt fest oder ändert die Bedingung, die mit dem anstehenden Haltepunkt zugeordnet ist.  
  
## Syntax  
  
```cpp#  
HRESULT SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
```c#  
int SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
#### Parameter  
 `bpCondition`  
 \[in\]  Eine [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) Struktur, die die Bedingung angeben, um festzulegen.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Jede Bedingung, die zuvor mit dem anstehenden Haltepunkt zugeordnet wurde, geht verloren.  Alle Haltepunkte, die von diesem anstehenden Haltepunkt gebunden sind, werden aufgerufen, um die Bedingung den Wert festzulegen, der im `bpCondition`\-Parameter angegeben wird.  
  
## Siehe auch  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)