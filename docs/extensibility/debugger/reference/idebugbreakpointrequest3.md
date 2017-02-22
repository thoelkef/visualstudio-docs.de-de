---
title: "IDebugBreakpointRequest3 | Microsoft Docs"
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
  - "IDebugBreakpointRequest3"
helpviewer_keywords: 
  - "IDebugBreakpointRequest3"
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBreakpointRequest3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt Informationen dar, die erforderlich sind, um einen beliebigen Haltepunkttyp zu erstellen und zu binden.  Es handelt sich um eine Erweiterung von [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md).  
  
## Syntax  
  
```  
IDebugBreakpointRequest3 : IDebugBreakpointRequest2  
```  
  
## Hinweise für Implementierer  
 Der Debuginformationen Manager der Sitzung \(SDM\) implementiert normalerweise diese Schnittstelle.  
  
## Hinweise für Aufrufer  
 Das Debugmodul \(DE\) greift auf diese Schnittstelle, indem [QueryInterface](/visual-cpp/atl/queryinterface) über die Schnittstelle IDebugBreakpointRequest2 aufruft, die in einem Aufruf von [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)empfangen wird.  
  
## Methoden in die Vtable\-Reihenfolge  
 Zusätzlich zu den von [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) geerbten Methoden macht die `IDebugBreakpointRequest3`\-Schnittstelle die folgende Methode verfügbar.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Ruft den Haltepunkt anforderungs Informationen ab, die diese Anforderung Haltepunkt beschreibt.|  
  
## Hinweise  
 Diese Schnittstelle wird verwendet, um zusätzliche Informationen über die DE [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Struktur bereitzustellen.  Diese zusätzlichen Informationen enthält DEs Anbieter IDs \(in Form einer GUID\) den Namen eines Ablaufverfolgungspunkts und den Namen einer Haltepunkt KEY\-Einschränkung.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)