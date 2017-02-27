---
title: "IDebugProgramDestroyEvent2::GetExitCode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramDestroyEvent2::GetExitCode"
helpviewer_keywords: 
  - "IDebugProgramDestroyEvent2::GetExitCode"
ms.assetid: 7f540cf6-e2d1-42b0-913e-a26d654b7659
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgramDestroyEvent2::GetExitCode
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Exitcode des Programms ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetExitCode(   
   DWORD* pdwExit  
);  
```  
  
```c#  
int GetExitCode(   
   out uint pdwExit  
);  
```  
  
#### Parameter  
 `pdwExit`  
 \[out\]  Gibt den Exitcode des Programms zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)