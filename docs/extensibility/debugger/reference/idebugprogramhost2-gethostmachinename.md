---
title: "IDebugProgramHost2::GetHostMachineName | Microsoft Docs"
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
  - "IDebugProgramHost2::GetHostMachineName"
helpviewer_keywords: 
  - "IDebugProgramHost2::GetHostMachineName"
ms.assetid: 4677ffe4-aa9b-4450-a63b-74cd3984d956
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramHost2::GetHostMachineName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Namen des Computers ab, zu der das Hosten Prozess, das dieses Programm ausführt.  
  
## Syntax  
  
```cpp#  
HRESULT GetHostMachineName(   
   BSTR* pbstrHostMachineName  
);  
```  
  
```c#  
int GetHostMachineName(   
   out string pbstrHostMachineName  
);  
```  
  
#### Parameter  
 `pbstrHostMachineName`  
 \[out\]  Gibt den Namen des Computers zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)