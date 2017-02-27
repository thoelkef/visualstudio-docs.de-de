---
title: "IDebugFunctionObject2::CreateStringObjectWithLength | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CreateStringObjectWithLength"
  - "IDebugFunctionObject2::CreateStringObjectWithLength"
ms.assetid: 1f43ec66-1615-4a4c-8b9d-e933f549f96d
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugFunctionObject2::CreateStringObjectWithLength
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Erstellt ein Zeichenfolgenobjekt, das die angegebene Länge verfügt.  
  
## Syntax  
  
```cpp#  
HRESULT CreateStringObjectWithLength (  
   LPCOLESTR      pcstrString,  
   UINT           uiLength,  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int CreateStringObjectWithLength (  
   string           pcstrString,  
   uint             uiLength,  
   out IDebugObject ppObject  
);  
```  
  
#### Parameter  
 `pcstrString`  
 \[in\]  Der Zeichenfolgenwert für das Zeichenfolgenobjekt.  
  
 `uiLength`  
 \[in\]  Die Länge der Zeichenfolge in Bytes.  
  
 `ppObject`  
 \[out\]  Gibt ein [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)\-Objekt zurück, das das neu erstellte Zeichenfolgenobjekt darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)