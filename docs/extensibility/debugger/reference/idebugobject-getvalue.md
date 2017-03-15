---
title: "IDebugObject::GetValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject::GetValue"
helpviewer_keywords: 
  - "IDebugObject::GetValue-Methode"
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugObject::GetValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Wert des Objekts als nachfolgende Folge von Bytes ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```c#  
int GetValue(  
   ref byte[] pValue,   
   uint nSize  
);  
```  
  
#### Parameter  
 `pValue`  
 \[in, out\]  Ein Array, das mit nachgestellten Folge von Bytes den Wert des Objekts darstellt, die gefüllt wird.  
  
 `nSize`  
 \[in\]  Die maximale Anzahl der abzurufenden Bytes.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Ruft die Gesamtzahl der Bytes ab, die Werte abgerufen werden können, indem die [GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)\-Methode aufruft.  
  
## Siehe auch  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)