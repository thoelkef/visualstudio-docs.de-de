---
title: "IDebugProgramNode2::GetHostMachineName_V7 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramNode2::GetHostMachineName"
helpviewer_keywords: 
  - "IDebugProgramNode2::GetHostMachineName_V7"
  - "IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName"
ms.assetid: a992f2c9-f68b-4146-8cc2-027753bf7ce6
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramNode2::GetHostMachineName_V7
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

VERALTET.  NOT TUN USE.  
  
## Syntax  
  
```cpp#  
HRESULT GetHostMachineName_V7 (   
   BSTR* pbstrHostMachineName  
);  
```  
  
```c#  
int GetHostMachineName_V7 (   
   out string pbstrHostMachineName  
);  
```  
  
#### Parameter  
 `pbstrHostMachineName`  
 \[out\]  Gibt den Namen des Computers zurück, auf dem das Programm ausgeführt wird.  
  
## Rückgabewert  
 Eine Implementierung sollte immer `E_NOTIMPL`zurückgeben.  
  
## Hinweise  
  
> [!WARNING]
>  Ab [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)]wird diese Methode nicht mehr verwendet und sollte immer `E_NOTIMPL`zurückgeben.  
  
## Siehe auch  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)