---
title: "IDebugStackFrame3::GetUnwindCodeContext | Microsoft Docs"
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
  - "IDebugStackFrame3::GetUnwindCodeContext"
helpviewer_keywords: 
  - "IDebugStackFrame3::GetUnwindCodeContext-Methode"
ms.assetid: b25f7e7d-2b24-48e4-93b3-829e61d73ebf
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugStackFrame3::GetUnwindCodeContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt den Code Elementkontext zurück, der einen Speicherort darstellt, wenn ein Stapel entladungs Vorgang aufgetreten ist.  
  
## Syntax  
  
```cpp#  
HRESULT GetUnwindCodeContext(  
   IDebugCodeContext2 **ppCodeContext  
);  
```  
  
```c#  
int GetUnwindCodeContext(  
   out IDebugCodeContext2 ppCodeContext  
);  
```  
  
#### Parameter  
 `ppCodeContext`  
 \[out\]  Gibt ein [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)\-Objekt zurück, das den Kontext darstellt, wenn der Code eine Stapel Entladen von aufgetreten ist.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Obwohl diese Methode möglicherweise einen Speicherort für den Kontext des Codes zurückgäbe, nachdem eine Stapel Entladen von bedeutet nicht notwendigerweise, kann die Stapel Entladen von tatsächlich im aktuellen Stapelrahmen auftreten.  
  
## Siehe auch  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)