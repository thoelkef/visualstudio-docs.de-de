---
title: "IDebugObject::GetSize | Microsoft Docs"
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
  - "IDebugObject::GetSize"
helpviewer_keywords: 
  - "IDebugObject::GetSize-Methode"
ms.assetid: 89af423b-36eb-479d-b2de-2693455eca15
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject::GetSize
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die Größe des Objekts in Bytes ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetSize(   
   UINT* pnSize  
);  
```  
  
```c#  
int GetSize(  
   out uint pnSize  
);  
```  
  
#### Parameter  
 `pnSize`  
 \[out\]  Gibt die Größe in Bytes zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Verwenden Sie die [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)\-Methode, um den Wert als Bytesequenz abzurufen.  
  
## Siehe auch  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)