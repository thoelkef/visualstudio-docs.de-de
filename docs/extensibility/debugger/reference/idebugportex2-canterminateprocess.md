---
title: "IDebugPortEx2::CanTerminateProcess | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortEx2::CanTerminateProcess"
helpviewer_keywords: 
  - "IDebugPortEx2::CanTerminateProcess"
ms.assetid: 111f65d8-5a1a-42b3-9de3-dd9bb03a33fd
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugPortEx2::CanTerminateProcess
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Bestimmt, ob ein Prozess beendet werden kann.  
  
## Syntax  
  
```cpp#  
HRESULT CanTerminateProcess(   
   IDebugProcess2* pPortProcess  
);  
```  
  
```c#  
HRESULT CanTerminateProcess(   
   IDebugProcess2 pPortProcess  
);  
```  
  
#### Parameter  
 `pPortProcess`  
 \[in\]  Ein [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)\-Objekt, das den Prozess darstellt beendet werden soll.  
  
## Rückgabewert  
 Gibt `S_OK` zurück, wenn der Prozess beendet werden kann. andernfalls gibt `S_FALSE`zurück.  
  
## Siehe auch  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)