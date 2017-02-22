---
title: "IDebugStackFrame2::GetDebugProperty | Microsoft Docs"
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
  - "IDebugStackFrame2::GetDebugProperty"
helpviewer_keywords: 
  - "IDebugStackFrame2::GetDebugProperty"
ms.assetid: 02c2fa04-1424-4bca-9936-feaecd2afab6
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugStackFrame2::GetDebugProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft eine Beschreibung der Eigenschaften eines Stapelrahmens ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetDebugProperty (   
   IDebugProperty2** ppDebugProp  
);  
```  
  
```c#  
int GetDebugProperty (   
   out IDebugProperty2 ppDebugProp  
);  
```  
  
#### Parameter  
 `ppDebugProp`  
 \[out\]  Gibt ein [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)\-Objekt zurück, das die Eigenschaften dieses Stapelrahmens beschreibt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Durch Aufrufen der entsprechenden Methode mit [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) Filter kann die lokalen Variablen, die Methodenparameter, die Register und „this“ \- Zeiger abrufen, der dem Stapelrahmen zugeordnet ist.  
  
## Siehe auch  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)