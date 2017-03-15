---
title: "IDebugFunctionPosition2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionPosition2"
helpviewer_keywords: 
  - "IDebugFunctionPosition2-Schnittstelle"
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugFunctionPosition2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt eine abstrakte Position einer Funktion in einem Quelldokument dar.  
  
## Syntax  
  
```  
IDebugFunctionPosition2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Das Debugmodul \(DE\) implementiert diese Schnittstelle, um die Position einer Funktion innerhalb des Quelldokuments darzustellen.  
  
## Hinweise für Aufrufer  
 Diese Schnittstelle wird als Teil einer [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Union angegeben \(speziell eine [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) Struktur\) das wiederum Bestandteil der [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) Struktur wird verwendet, wenn einen ausstehenden Haltepunkt erstellt.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugFunctionPosition2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|Ruft den Namen der Funktion ab, die von dieser Position in Zusammenhang steht.|  
|[GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)|Ruft den Offset vom Beginn der Funktion ab.|  
  
## Hinweise  
 Die Position, die von dieser Schnittstelle dargestellt wird, ist der Text auf ausdrücklich eine [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) Struktur.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)