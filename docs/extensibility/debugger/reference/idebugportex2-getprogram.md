---
title: "IDebugPortEx2::GetProgram | Microsoft Docs"
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
  - "IDebugPortEx2::GetProgram"
helpviewer_keywords: 
  - "IDebugPortEx2::GetProgram"
ms.assetid: cd83a111-bfd5-4eae-b576-526466c6b6ec
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortEx2::GetProgram
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft das Programm ab, das einem Knoten Programm zugeordnet ist.  
  
## Syntax  
  
```cpp#  
HRESULT GetProgram(   
   IDebugProgramNode2* pProgramNode,  
   IDebugProgram2**    ppProgram  
);  
```  
  
```c#  
int GetProgram(   
   IDebugProgramNode2 pProgramNode,  
   out IDebugProgram2 ppProgram  
);  
```  
  
#### Parameter  
 `pProgramNode`  
 \[in\]  Ein [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)\-Objekt, das den Knoten darstellt programmieren.  
  
 `ppProgram`  
 \[out\]  Gibt ein [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)\-Objekt zurück, das das Programm darstellt, das dem Programm unter dem Knoten zugeordnet ist.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)