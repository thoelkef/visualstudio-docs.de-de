---
title: "IDebugEvent2 | Microsoft Docs"
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
  - "IDebugEvent2"
helpviewer_keywords: 
  - "IDebugEvent2-Schnittstelle"
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle wird verwendet, um wichtige Debuginformationen das Beenden an einem Haltepunkt und nicht schwer wiegende Informationen, z. B. eine Debugmeldung zu übermitteln.  
  
## Syntax  
  
```  
IDebugEvent2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Das Debugmodul \(DE\) und Anschlusslieferanten benutzerdefiniertes implementieren diese Schnittstelle für dasselbe Objekt wie alle anderen Ereignisschnittstellen.  
  
## Hinweise für Aufrufer  
 Verwenden des Arguments der Schnittstellen\-ID \(Interface Identifier, IID\) angegeben [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) oder [Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md), die Aufrufe Debuggen [QueryInterface](/visual-cpp/atl/queryinterface) des Managers der Sitzung \(SDM\) in der `IDebugEvent2`\-Schnittstelle zu erhalten, die entsprechende Ereignisschnittstelle.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugEvent2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Ruft die Attribute für das Debugereignis ab.|  
  
## Hinweise  
 Die spezifischeren Ereignisschnittstellen, wie [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), berechnen, nicht von der Schnittstelle IDebugEvent2 sondern werden stattdessen als separate Schnittstelle für dasselbe Objekt wie `IDebugEvent2`implementiert.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)