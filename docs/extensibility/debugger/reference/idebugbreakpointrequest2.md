---
title: "IDebugBreakpointRequest2 | Microsoft Docs"
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
  - "IDebugBreakpointRequest2"
helpviewer_keywords: 
  - "IDebugBreakpointRequest2-Schnittstelle"
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBreakpointRequest2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt Informationen dar, die erforderlich sind, um einen beliebigen Haltepunkttyp zu erstellen und zu binden.  
  
## Syntax  
  
```  
IDebugBreakpointRequest2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Der Debuginformationen Manager der Sitzung \(SDM\) implementiert normalerweise diese Schnittstelle.  
  
## Hinweise für Aufrufer  
 Das Debugmodul \(DE\) empfängt diese Schnittstelle durch einen Aufruf von [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) , um einen anstehenden Haltepunkt zu erstellen.  Ein Aufruf von [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) kann diese Schnittstelle von DE abrufen.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugBreakpointRequest2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|Ruft den Typ dieser Haltepunkt Breakpointpositions Anforderung ab.|  
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|Ruft den Haltepunkt anforderungs Informationen ab, die diese Anforderung Haltepunkt beschreibt.|  
  
## Hinweise  
 Nach dem Programm, das gedebuggt wird, ist ein Aufruf [Binden](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) bindet einen ausstehenden Haltepunkt in den angeforderten Stelle im Programm geladen wurde.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)   
 [Binden](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)