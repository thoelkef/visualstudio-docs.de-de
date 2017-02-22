---
title: "IDebugEngine2::SetException | Microsoft Docs"
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
  - "IDebugEngine2::SetException"
helpviewer_keywords: 
  - "IDebugEngine2::SetException"
ms.assetid: e6f5ec48-09e8-4b9b-9dc9-55f8d883f1b7
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngine2::SetException
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt an, wie das Debugmodul \(DE\) eine bestimmte Ausnahme behandeln soll.  
  
## Syntax  
  
```cpp#  
HRESULT SetException(   
   EXCEPTION_INFO* pException  
);  
```  
  
```c#  
int SetException(   
   EXCEPTION_INFO[] pException  
);  
```  
  
#### Parameter  
 `pException`  
 \[in\]  Eine [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md) Struktur, in der die Ausnahme beschrieben wird und wie sie gedebuggt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 DE kann angewiesen werden, um das Programm anzuhalten, eine Ausnahme an die erste Möglichkeit zur zweiten Chance zu generieren oder überhaupt nicht.  
  
## Siehe auch  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md)