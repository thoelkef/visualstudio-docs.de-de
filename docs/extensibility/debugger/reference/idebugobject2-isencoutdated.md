---
title: "IDebugObject2::IsEncOutdated | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject2::IsEncOutdated"
helpviewer_keywords: 
  - "IDebugObject2::IsEncOutdated-Methode"
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugObject2::IsEncOutdated
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode bestimmt, ob die Bearbeitung und setzt Status dieses Objekts fort, oder des übergeordneten Containers ist veraltet.  Ein benutzerdefinierter Ausdrucksauswertung diese Methode nicht implementiert und gibt immer `E_NOTIMPL`zurück.  
  
## Syntax  
  
```cpp  
HRESULT IsEncOutdated(  
   BOOL* pfEncOutdated  
);  
```  
  
```c#  
int IsEncOutdated(  
   out int pfEncOutdated  
);  
```  
  
#### Parameter  
 `pfEncOutdated`  
 \[out\]  Ein Wert ungleich 0 \(`TRUE`\), wenn das Bearbeiten und Fortfahren Zustand ist veraltet,`FALSE`fort \(null\), wenn dies nicht der Fall ist.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
> [!NOTE]
>  Ein benutzerdefinierter Ausdrucksauswertung sollte immer `E_NOTIMPL`zurückgeben.  
  
## Siehe auch  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)