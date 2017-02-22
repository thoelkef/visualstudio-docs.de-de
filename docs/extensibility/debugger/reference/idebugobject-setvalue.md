---
title: "IDebugObject::SetValue | Microsoft Docs"
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
  - "IDebugObject::SetValue"
helpviewer_keywords: 
  - "IDebugObject::SetValue-Methode"
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject::SetValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Legt den Wert des Objekts aus aufeinander folgenden Folge von Bytes fest.  
  
## Syntax  
  
```cpp#  
HRESULT SetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```c#  
int SetValue(  
   byte[] pValue,   
   uint   nSize  
);  
```  
  
#### Parameter  
 `pValue`  
 \[in\]  Ein Bytearray, das den neuen Wert darstellt.  
  
 `nSize`  
 \[in\]  Die Größe des Werts in Bytes.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Die Werte im Array werden in dieses [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)\-Objekt kopiert und ersetzt jeden vorhandenen Wert.  Die Größe des neuen Werts kann als der vorhandene Wert größer oder kleiner sein.  Dieses `IDebugObject` kann kein NULL\-Verweis sein.  
  
## Siehe auch  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)