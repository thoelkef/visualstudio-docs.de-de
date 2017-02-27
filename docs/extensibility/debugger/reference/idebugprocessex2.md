---
title: "IDebugProcessEx2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcessEx2"
helpviewer_keywords: 
  - "IDebugProcessEx2-Schnittstelle"
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# IDebugProcessEx2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle ermöglicht die Sitzung, die Multithreaded Manager \(SDM\) einen Prozess benachrichtigen, dass er anfügt oder trennt sich vom Prozess.  
  
## Syntax  
  
```  
IDebugProcessEx2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Ein benutzerdefinierter Port lieferant implementiert diese Schnittstelle für dasselbe Objekt wie die [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)\-Schnittstelle zu:  
  
-   Sichern Sie die Nachverfolgung von Sitzungen, die an einen Prozess verbunden sind  
  
-   Unterstützung für mehrere Module Debuggen zu selbstklebend  
  
 Der benutzerdefinierte Port lieferant kann diese Schnittstelle implementieren, wenn er ausgewählt wird.  
  
## Hinweise für Aufrufer  
  
-   Das SDM ruft [QueryInterface](/visual-cpp/atl/queryinterface) auf einer `IDebugProcess2`\-Schnittstelle an, die zum Abrufen dieser Schnittstelle.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugProcessEx2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[Anfügen](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Informiert den Prozess, dass eine Sitzung jetzt den Prozess gedebuggt wird.|  
|[Trennen](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Informiert den Prozess, dass eine Sitzung nicht mehr den Prozess gedebuggt wird.|  
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Fügt dem Programm Eine Liste der Knoten Debuggen die Option Module hinzufügen.|  
  
## Hinweise  
 Diese Schnittstelle ist zwischen dem SDM und dem Prozess privat.  
  
## Anforderungen  
 Header: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)