---
title: "IEnumDebugAddresses::GetCount | Microsoft Docs"
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
  - "IEnumDebugAddresses::GetCount"
helpviewer_keywords: 
  - "IEnumDebugAddresses::GetCount-Methode"
ms.assetid: f2ca8ff8-539f-457c-83f8-9bbf97618065
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugAddresses::GetCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode gibt die Anzahl der Elemente in der Enumeration zurück.  
  
## Syntax  
  
```cpp#  
HRESULT GetCount(  
   [out] ULONG* pcelt  
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
 Diese Methode ist nicht Teil der üblichen COM\-Enumerations Oberfläche, die nur auf Weiter, Klon\- Schritte, und Zurücksetzen müssen implementiert werden.  
  
## Siehe auch  
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)