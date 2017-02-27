---
title: "BP_RESOLUTION_DATA | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_RESOLUTION_DATA"
helpviewer_keywords: 
  - "BP_RESOLUTION_DATA-Struktur"
ms.assetid: 9e0b9000-6a84-47b9-b07a-367a75764389
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# BP_RESOLUTION_DATA
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Beschreibt das Ergebnis des Bindens eines Datenhaltepunkte.  
  
## Syntax  
  
```cpp#  
typedef struct _BP_RESOLUTION_DATA {   
   BSTR              bstrDataExpr;  
   BSTR              bstrFunc;  
   BSTR              bstrImage;  
   BP_RES_DATA_FLAGS dwFlags;  
} BP_RESOLUTION_DATA;  
```  
  
```c#  
public struct BP_RESOLUTION_DATA {   
   public string bstrDataExpr;  
   public string bstrFunc;  
   public string bstrImage;  
   public uint   dwFlags;  
};  
```  
  
## Mitglieder  
 `bstrDataExpr`  
 Der Ausdruck, der Daten gebunden wurde.  
  
 `bstrFunc`  
 Der Name der Funktion, die der Datenhaltepunkt in gebunden hat \(sofern vorhanden\).  
  
 `bstrImage`  
 Der Name des Moduls MyModule.dll \(z. B.\), das der Datenhaltepunkt in gebunden ist.  
  
 `dwFlags`  
 Ein Wert aus der Enumeration, [BP\_RES\_DATA\_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md) beschreiben, wie der Datenhaltepunkt implementiert wird.  
  
## Hinweise  
 Diese Struktur ist ein Mitglied der [BP\_RESOLUTION\_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) Struktur, die wiederum Mitglied der [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) Struktur ist, die von der [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)\-Methode zurückgegeben wird.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_RESOLUTION\_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)