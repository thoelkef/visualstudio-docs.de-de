---
title: "IDebugPortSupplierLocale2::SetLocale | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugPortSupplierLocale2::SetLocale"
ms.assetid: 21e88510-caac-405e-ba45-cb00e19a28bc
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugPortSupplierLocale2::SetLocale
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Legt das Gebietsschema für den Anschlusslieferanten ab.  
  
## Syntax  
  
```cpp#  
HRESULT SetLocale(  
   WORD wLangID  
);  
```  
  
```c#  
int SetLocale(  
   ushort wLangID  
);  
```  
  
#### Parameter  
 `wLangID`  
 Bezeichner für das Gebietsschema festlegen.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugPortSupplierLocale2](../../../extensibility/debugger/reference/idebugportsupplierlocale2.md)