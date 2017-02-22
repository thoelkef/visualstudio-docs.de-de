---
title: "BP_LOCATION_DATA_STRING | Microsoft Docs"
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
  - "BP_LOCATION_DATA_STRING"
helpviewer_keywords: 
  - "BP_LOCATION_DATA_STRING-Struktur"
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_LOCATION_DATA_STRING
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Wird zum Festlegen von Datenhaltepunkte, die auf eine Zeichenfolge handelt, die der Benutzer von der integrierten Entwicklungsumgebung \(IDE\) eingeben kann.  
  
## Syntax  
  
```cpp#  
typedef struct _BP_LOCATION_DATA_STRING {   
   IDebugThread2* pThread;  
   BSTR           bstrContext;  
   BSTR           bstrDataExpr;  
   DWORD          dwNumElements;  
} BP_LOCATION_DATA_STRING;  
```  
  
## Mitglieder  
 `pThread`  
 Das [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)\-Objekt, das den Thread darstellt, in dem der Haltepunkt auftritt.  
  
 `bstrContext`  
 Der Kontext des Haltepunkts innerhalb des Codes, i. d. R. eine Methode oder ein Funktionsname, wie auf einer Aufrufliste angezeigt.  
  
 `bstrDataExpr`  
 Die Daten, die der Benutzer eingibt, um den Haltepunkt festzulegen.  
  
 `dwNumElements`  
 Die Anzahl der Elemente in der Bezugspunkt, in der der Haltepunkt auftritt.  
  
## Hinweise  
 Diese Struktur ist ein Mitglied der [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Struktur als Teil einer Union.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)