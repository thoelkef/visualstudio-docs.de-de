---
title: "IDebugPort2::EnumProcesses | Microsoft Docs"
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
  - "IDebugPort2::EnumProcesses"
helpviewer_keywords: 
  - "IDebugPort2::EnumProcesses"
ms.assetid: aafb32c5-5790-4807-a448-878a80256438
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPort2::EnumProcesses
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt eine Liste aller Prozesse zurück, die für einen Port ausgeführt werden.  
  
## Syntax  
  
```cpp#  
HRESULT EnumProcesses(   
   IEnumDebugProcesses2** ppEnum  
);  
```  
  
```c#  
int EnumProcesses(   
   out IEnumDebugProcesses2 ppEnum  
);  
```  
  
#### Parameter  
 `ppEnum`  
 \[out\]  Gibt ein [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)\-Objekt zurück, das eine Liste aller Prozesse, die auf einen Port ausgeführt werden.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)