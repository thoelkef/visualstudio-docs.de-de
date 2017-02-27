---
title: "IDebugProcess2::CanDetach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::CanDetach"
helpviewer_keywords: 
  - "IDebugProcess2::CanDetach"
ms.assetid: 2830f7c3-69fb-474a-97b8-5b869e38d546
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::CanDetach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Bestimmt, ob der Debug\- Manager der Sitzung \(SDM\) den Prozess trennen können.  
  
## Syntax  
  
```cpp#  
HRESULT CanDetach(  
   void  
);  
```  
  
```c#  
int CanDetach();  
```  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK.` zurückgibt `S_FALSE` zurück, wenn der Debugger nicht vom Prozess trennen können.  Andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)