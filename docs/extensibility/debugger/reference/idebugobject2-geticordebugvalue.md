---
title: "IDebugObject2::GetICorDebugValue | Microsoft Docs"
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
  - "IDebugObject2::GetICorDebugValue"
helpviewer_keywords: 
  - "IDebugObject2::GetICorDebugValue-Methode"
ms.assetid: bcd4355d-3fbe-483f-bb23-a44348323c6a
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject2::GetICorDebugValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft ein verwaltetes Codeobjekt ab, das den Wert darstellt, der diesem Objekt zugeordnet ist.  
  
## Syntax  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```c#  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### Parameter  
 `ppUnk`  
 \[out\]  `IUnknown`\-Schnittstelle, die diesen Alias darstellt.  Diese Schnittstelle kann für die `ICorDebugValue`\-Schnittstelle abgefragt werden.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Das `ICorDebugValue`\-Objekt ist eine Common Language Runtime\-Schnittstelle, die den Wert darstellt.  
  
## Siehe auch  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)