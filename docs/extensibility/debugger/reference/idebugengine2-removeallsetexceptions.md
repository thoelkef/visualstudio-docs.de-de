---
title: "IDebugEngine2::RemoveAllSetExceptions | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::RemoveAllSetExceptions"
helpviewer_keywords: 
  - "IDebugEngine2::RemoveAllSetExceptions"
ms.assetid: 165fbe89-802d-4d99-85ca-c10fd6cccc09
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngine2::RemoveAllSetExceptions
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Entfernt die Ausnahmeliste, die die IDE für eine bestimmte Architektur der Common Language Runtime oder eine Sprache festgelegt wurde.  
  
## Syntax  
  
```cpp#  
HRESULT RemoveAllSetExceptions(   
   REFGUID guidType  
);  
```  
  
```c#  
int RemoveAllSetExceptions(   
   ref Guid guidType  
);  
```  
  
#### Parameter  
 `guidType`  
 \[in\]  Entweder die GUID für die Sprache bzw. die GUID für das Debugmodul, das in einer Architektur der Laufzeit bestimmt ist.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Die Ausnahmen, die von dieser Methode entfernt wurden, werden von früheren Aufrufen der [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)\-Methode festgelegt.  
  
 Um eine bestimmte Ausnahme zu entfernen, rufen Sie die [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)\-Methode auf.  
  
## Siehe auch  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)