---
title: "IDebugFunctionPosition2::GetFunctionName | Microsoft Docs"
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
  - "IDebugFunctionPosition2::GetFunctionName"
helpviewer_keywords: 
  - "IDebugFunctionPosition2::GetFunctionName"
ms.assetid: eb7a348e-a7f5-4f25-be68-80482d5482a8
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugFunctionPosition2::GetFunctionName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Namen der Funktion ab, zu der diese Aufnahmepunkte.  
  
## Syntax  
  
```cpp#  
HRESULT GetFunctionName(   
   BSTR* pbstrFunctionName  
);  
```  
  
```c#  
int GetFunctionName(  
   out string pbstrFunctionName  
);  
```  
  
#### Parameter  
 `pbstrFunctionName`  
 \[out\]  Gibt den Namen der Funktion zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)