---
title: "IDebugBreakpointResolution2 | Microsoft Docs"
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
  - "IDebugBreakpointResolution2"
helpviewer_keywords: 
  - "IDebugBreakpointRequest2-Schnittstelle"
ms.assetid: 451d5bce-b9c1-48ff-beaa-2b4c3e1ceea0
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBreakpointResolution2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt Informationen dar, die einen gebundenen Haltepunkt beschreibt.  
  
## Syntax  
  
```  
IDebugBreakpointResolution2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Das Debugmodul \(DE\) implementiert diese Schnittstelle als Teil der Unterstützung für Haltepunkte.  Diese Schnittstelle stellt eine Beschreibung eines gebundenen Haltepunkte, dass der Debug\- Manager der Sitzung wenn Benutzer Ansichten die Eigenschaften eines Haltepunkts verwendet.  
  
## Hinweise für Aufrufer  
 Ein Aufruf von [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) gibt diese Schnittstelle zurück.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugBreakpointResolution2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Ruft den Typ des Haltepunkts ab, der durch diese Lösung dargestellt wird.|  
|[GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Ruft den Haltepunkt auflösungs Informationen ab, die diesen Haltepunkt beschreibt.|  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)