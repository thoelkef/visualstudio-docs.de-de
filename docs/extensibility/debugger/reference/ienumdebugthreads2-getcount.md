---
title: "IEnumDebugThreads2::GetCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugThreads2::GetCount"
helpviewer_keywords: 
  - "IEnumDebugThreads2::GetCount"
ms.assetid: 81b7f139-d24e-4040-9adc-d664d77563ba
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IEnumDebugThreads2::GetCount
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
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)