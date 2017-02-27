---
title: "IEnumDebugObjects::GetCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugObjects::GetCount"
helpviewer_keywords: 
  - "IEnumDebugObjects::GetCount-Methode"
ms.assetid: 9cbc5db4-03ae-479f-a664-13cad66ad210
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# IEnumDebugObjects::GetCount
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
 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)