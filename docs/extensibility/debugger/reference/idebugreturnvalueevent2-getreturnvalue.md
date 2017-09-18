---
title: "IDebugReturnValueEvent2::GetReturnValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReturnValueEvent2::GetReturnValue"
helpviewer_keywords: 
  - "IDebugReturnValueEvent2::GetReturnValue"
ms.assetid: 86c50d5a-6df6-4798-818a-c587a8741f90
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugReturnValueEvent2::GetReturnValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Wert ab, der für das schrittweise Ausführen oder über eine Funktion zurückgegeben wird.  
  
## Syntax  
  
```cpp#  
HRESULT GetReturnValue (   
   IDebugProperty2** ppReturnValue  
);  
```  
  
```c#  
int GetReturnValue (   
   out IDebugProperty2 ppReturnValue  
);  
```  
  
#### Parameter  
 `ppReturnValue`  
 \[out\]  Gibt ein [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)\-Objekt zurück, das den Wert darstellt, der abgerufen werden soll.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)