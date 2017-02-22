---
title: "IDebugPortEx2::TerminateProcess | Microsoft Docs"
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
  - "IDebugPortEx2::TerminateProcess"
helpviewer_keywords: 
  - "IDebugPortEx2::TerminateProcess"
ms.assetid: bf8fa94c-6d9d-4e4f-ac08-3b44ba5ace68
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortEx2::TerminateProcess
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Beendet einen Prozess.  
  
## Syntax  
  
```cpp#  
HRESULT TerminateProcess(   
   IDebugProcess2* pPortProcess  
);  
```  
  
```c#  
int TerminateProcess(   
   IDebugProcess2 pPortProcess  
);  
```  
  
#### Parameter  
 `pPortProcess`  
 \[in\]  Ein [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)\-Objekt, das den Prozess darstellt beendet werden soll.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)