---
title: "IDebugReference2::GetDerivedMostReference | Microsoft Docs"
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
  - "IDebugReference2::GetDerivedMostReference"
helpviewer_keywords: 
  - "IDebugReference2::GetDerivedMostReference"
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugReference2::GetDerivedMostReference
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den ganz unten stehende Verweis eines Verweises ab.  Für zukünftige Verwendung reserviert.  
  
## Syntax  
  
```cpp#  
HRESULT GetDerivedMostReference(   
   IDebugReference2** ppDerivedMost  
);  
```  
  
```c#  
int GetDerivedMostReference(   
   out IDebugReference2 ppDerivedMost  
);  
```  
  
#### Parameter  
 `ppDerivedMost`  
 \[out\]  Gibt ein Objekt zurück, das die [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) ganz unten stehende Eigenschaft darstellt.  
  
## Rückgabewert  
 Gibt immer `E_NOTIMPL` zurück.  
  
## Hinweise  
 Wenn beispielsweise die folgende Eigenschaft ein Objekt beschreibt, das `ClassRoot` implementiert, aber das tatsächlich eine Instanziierung von `ClassDerived` ist, die von `ClassRoot`abgeleitet ist, gibt diese Methode ein [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)\-Objekt zurück, das einen Verweis auf das `ClassDerived`\-Objekt darstellt.  
  
## Siehe auch  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)