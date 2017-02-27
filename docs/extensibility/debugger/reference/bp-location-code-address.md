---
title: "BP_LOCATION_CODE_ADDRESS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_LOCATION_CODE_ADDRESS"
helpviewer_keywords: 
  - "BP_LOCATION_CODE_ADDRESS-Struktur"
ms.assetid: 83c9da8b-19d9-4be5-b225-854543654901
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# BP_LOCATION_CODE_ADDRESS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Beschreibt den Speicherort eines Haltepunkts an einer Adresse im Code.  
  
## Syntax  
  
```cpp#  
typedef struct _BP_LOCATION_CODE_ADDRESS {   
   BSTR bstrContext;  
   BSTR bstrModuleUrl;  
   BSTR bstrFunction;  
   BSTR bstrAddress;  
} BP_LOCATION_CODE_ADDRESS;  
```  
  
## Mitglieder  
 `bstrContext`  
 Der Kontext des Haltepunkts, i. d. R. eine Methode oder ein Funktionsname, wie auf einer Aufrufliste angezeigt.  
  
 `bstrModuleUrl`  
 Die URL des Moduls, das den Haltepunkt enthält.  
  
 `bstrFunction`  
 Der Name der Funktion, die den Haltepunkt enthält.  
  
 `bstrAddress`  
 Die Adresse des Haltepunkts, der von einer Ausdrucksauswertung analysiert wird, um sie zu einem [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)\-Objekt gebunden werden soll.  
  
## Hinweise  
 Diese Struktur ist ein Mitglied der [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Struktur als Teil einer Union.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)