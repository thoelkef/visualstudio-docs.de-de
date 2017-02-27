---
title: "IDebugArrayObject2::GetBaseIndices | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetBaseIndices"
  - "IDebugArrayObject2::GetBaseIndices"
ms.assetid: 882951a2-3da0-49bf-8d1e-7daedd13ffe6
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugArrayObject2::GetBaseIndices
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die Untergrenze Indizes \(Basis\-\) für jeden angegebenen Index die Anzahl der Dimensionen im Array ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetBaseIndices (  
   DWORD  dwRank,  
   DWORD* dwIndices  
);  
```  
  
```c#  
int GetBaseIndices (  
   uint       dwRank,  
   out uint[] dwIndices  
);  
```  
  
#### Parameter  
 `dwRank`  
 \[in\]  Der Rang \(Anzahl der Dimensionen\) des Arrays.  
  
 `dwIndices`  
 \[out\]  Die Untergrenze Indizes \(Basis\-\) für das Array.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Als Beispiel kann diese Funktion „5 " für das Array zurückgeben, das durch den folgenden C\#\-Code erstellt wurde:  
  
```  
int[] lengths = { 12 };  
int[] lowerbounds = { 5 };  
Array.CreateInstance(typeof(int), lengths, lowerbounds);  
```  
  
## Siehe auch  
 [IDebugArrayObject2](../../../extensibility/debugger/reference/idebugarrayobject2.md)