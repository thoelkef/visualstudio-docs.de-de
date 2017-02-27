---
title: "BP_LOCATION_CODE_FILE_LINE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_LOCATION_CODE_FILE_LINE"
helpviewer_keywords: 
  - "BP_LOCATION_CODE_FILE_LINE-Struktur"
ms.assetid: 3ff32032-d412-44d3-91bf-870cc354a09e
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_LOCATION_CODE_FILE_LINE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Enthält die Daten für den Speicherort eines Haltepunkts an einer bestimmten Zeile in einer Codequelldatei.  
  
## Syntax  
  
```cpp#  
typedef struct _BP_LOCATION_CODE_FILE_LINE {   
   BSTR                     bstrContext;  
   IDebugDocumentPosition2* pDocPos;  
} BP_LOCATION_CODE_FILE_LINE;  
```  
  
## Mitglieder  
 `bstrContext`  
 Der Kontext des Haltepunkts, i. d. R. eine Methode oder ein Funktionsname, wie auf einer Aufrufliste angezeigt.  
  
 `pDocPos`  
 Das [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)\-Objekt, das die Position des Haltepunkts darstellt.  
  
## Hinweise  
 Diese Struktur ist ein Mitglied der [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Struktur als Teil einer Union.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)