---
title: "IDebugProgram2::CanDetach | Microsoft Docs"
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
  - "IDebugProgram2::CanDetach"
helpviewer_keywords: 
  - "IDebugProgram2::CanDetach"
ms.assetid: dcd9ab6c-49e5-447e-aa7c-89f571f4a052
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::CanDetach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Bestimmt, ob eine Debug\- Modul \(DE\) vom Programm getrennt werden kann.  
  
## Syntax  
  
```cpp#  
HRESULT CanDetach(  
   void  
);  
```  
  
```c#  
int CanDetach();  
```  
  
## Rückgabewert  
 Wenn sich `S_OK`werden kann, gibt diese zurück. andernfalls gibt einen Fehlercode zurück.  Gibt `S_FALSE` zurück, wenn sich nicht vom Programm DE getrennt werden kann.  
  
## Siehe auch  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)