---
title: "IDebugArrayField::GetRank | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayField::GetRank"
helpviewer_keywords: 
  - "IDebugArrayField::GetRank-Methode"
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugArrayField::GetRank
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Rang oder die Anzahl der Dimensionen des Arrays ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```c#  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### Parameter  
 `pdwRank`  
 \[out\]  Gibt den Rang zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der Rang eines Arrays entspricht der Anzahl der Dimensionen.  In C\+\+ und C\# mehrdimensionale Arrays sind tatsächlich Arrays von Arrays und können daher angenommen werden nur ein eindimensionales Array \(und die `GetRank`\-Methode gibt immer 1 zurück\).  In [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]mehrdimensionale Arrays sind hingegen anders behandelt, und der Rang eines solchen Arrays entspricht der Anzahl der Dimensionen \(und `GetRank`\-Methode gibt immer die Anzahl von Dimensionen zurück\).  
  
## Siehe auch  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)