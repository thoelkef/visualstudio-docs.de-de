---
title: "IDebugTypeFieldBuilder2::CreateArrayOfType | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugTypeFieldBuilder2::CreateArrayOfType"
  - "CreateArrayOfType"
ms.assetid: 85166ac9-0bff-49a0-b2fd-ca7f7a8eae4b
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugTypeFieldBuilder2::CreateArrayOfType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Erstellt ein Array des angegebenen Typs und Größe.  
  
## Syntax  
  
```cpp#  
HRESULT CreateArrayOfType (  
   IDebugField*  pTypeField,  
   DWORD         rank,  
   IDebugField** pArrayOfTypeField  
);  
```  
  
```c#  
int CreateArrayOfType (  
   IDebugField     pTypeField,  
   uint            rank,  
   out IDebugField pArrayOfTypeField  
);  
```  
  
#### Parameter  
 `pTypeField`  
 \[in\]  Der Typ der Elemente, die in das Array enthält.  
  
 `rank`  
 \[in\]  Die Anzahl der Elemente im Array.  
  
 `pArrayOfTypeField`  
 \[out\]  Gibt die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Objekten zurück, die das neue Array darstellen.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)