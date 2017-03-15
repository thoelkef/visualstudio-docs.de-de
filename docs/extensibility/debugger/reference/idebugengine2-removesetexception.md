---
title: "IDebugEngine2::RemoveSetException | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::RemoveSetException"
helpviewer_keywords: 
  - "IDebugEngine2::RemoveSetException"
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugEngine2::RemoveSetException
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Entfernt die angegebene Ausnahme, sodass sie nicht mehr durch das Debugmodul behandelt.  
  
## Syntax  
  
```cpp#  
HRESULT RemoveSetException(   
   EXCEPTION_INFO* pException  
);  
```  
  
```c#  
int RemoveSetException(   
   EXCEPTION_INFO[] pException  
);  
```  
  
#### Parameter  
 `pException`  
 \[in\]  Eine [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md) Struktur, die die Ausnahme beschreibt, das entfernt werden soll.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Die Ausnahme, die entfernt wird, muss durch einen vorherigen Aufruf der [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)\-Methode bereits festgelegt worden sein.  
  
 Um alle festgelegten Ausnahmen sofort zu entfernen, rufen Sie die [RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)\-Methode auf.  
  
## Siehe auch  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md)