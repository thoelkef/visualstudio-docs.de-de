---
title: "IEnumDebugPropertyInfo2::GetCount | Microsoft Docs"
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
  - "IEnumDebugPropertyInfo2::GetCount"
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo2::GetCount"
ms.assetid: 9b0b3ce6-08cb-46fd-a6d9-92b36e60da19
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugPropertyInfo2::GetCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt die Anzahl der Elemente in der Enumeration zurück.  
  
## Syntax  
  
```cpp#  
HRESULT GetCount(  
   ULONG* pcelt  
);  
```  
  
```c#  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### Parameter  
 `pcelt`  
 \[out\]  Gibt die Anzahl der Elemente in der Enumeration zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode ist nicht Teil der üblichen COM\-Enumerations Oberfläche, die angibt, dass nur `Next`, `Clone`, `Skip``Reset` und Methoden implementiert werden müssen.  
  
## Siehe auch  
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)