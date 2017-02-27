---
title: "IDebugReference2::SetValueAsReference | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReference2::SetValueAsReference"
helpviewer_keywords: 
  - "IDebugReference2::SetValueAsReference"
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugReference2::SetValueAsReference
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Legt den Wert eines Verweises auf einen anderen Verweis fest.  Für zukünftige Verwendung reserviert.  
  
## Syntax  
  
```cpp#  
HRESULT SetValueAsReference (   
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```cpp#  
int SetValueAsReference (   
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### Parameter  
 `rgpArgs`  
 \[in\]  Ein Array [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)\-Objekte verwendet, um zu bestimmen, wie der Verweiswert festlegt.  
  
 `dwArgCount`  
 \[in\]  Die Anzahl der Verweise im Array.  
  
 `pValue`  
 \[in\]  Das Objekt, für das ein [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) Festlegen des Eigenschaftswerts.  
  
 `dwTimeout`  
 \[in\]  Maximale Zeit in Millisekunden, bevor der Rückgabe dieser Methode zu warten.  `INFINITE` verwenden, um unbegrenzt zu warten.  
  
## Rückgabewert  
 Gibt immer `E_NOTIMPL` zurück.  
  
## Siehe auch  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)