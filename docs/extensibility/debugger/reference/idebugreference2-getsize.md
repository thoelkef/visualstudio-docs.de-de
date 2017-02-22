---
title: "IDebugReference2::GetSize | Microsoft Docs"
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
  - "IDebugReference2::GetSize"
helpviewer_keywords: 
  - "IDebugReference2::GetSize"
ms.assetid: a404ddd9-d940-4513-97cd-f52b8ab6a560
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugReference2::GetSize
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die Größe \(in Bytes\) des Werts des Verweises ab.  Für zukünftige Verwendung reserviert.  
  
## Syntax  
  
```cpp#  
HRESULT GetSize (   
   DWORD* pdwSize  
);  
```  
  
```c#  
int GetSize (   
   out uint pdwSize  
);  
```  
  
#### Parameter  
 `pdwSize`  
 \[out\]  Gibt die Größe \(in Bytes\) des Werts des Verweises zurück.  
  
## Rückgabewert  
 Gibt immer `E_NOTIMPL` zurück.  
  
## Siehe auch  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)