---
title: "IDebugExceptionEvent2::GetException | Microsoft Docs"
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
  - "IDebugExceptionEvent2::GetException"
helpviewer_keywords: 
  - "IDebugExceptionEvent2::GetException"
ms.assetid: 7c98f41d-322b-4e72-a514-cbd4823eb70d
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExceptionEvent2::GetException
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft eine ausführliche Beschreibung der Ausnahme ab, die das Ereignis ausgelöst hat.  
  
## Syntax  
  
```cpp#  
HRESULT GetException(   
   EXCEPTION_INFO* pExceptionInfo  
);  
```  
  
```c#  
int GetException(   
   EXCEPTION_INFO[] pExceptionInfo  
);  
```  
  
#### Parameter  
 `pExceptionInfo`  
 \[in, out\]  Eine [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md) Struktur, die mit der angegebenen Beschreibung der Ausnahme gefüllt wird.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 \[C\+\+\] Es ist der Aufrufer für die Freigabe aller Zeichenfolgen in der Struktur [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md) verantwortlich, sowie die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)\-Objekt in der Struktur Freigeben von.  
  
## Siehe auch  
 [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)   
 [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)