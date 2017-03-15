---
title: "IEnumDebugErrorBreakpoints2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugErrorBreakpoints2"
helpviewer_keywords: 
  - "IEnumDebugErrorBreakpoints2"
ms.assetid: ffdad73d-969a-45ef-9ad1-7f5d3b814018
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugErrorBreakpoints2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle listet die Fehler von Haltepunkten aufgelistet, die mit einem anstehenden Haltepunkt zugeordnet sind.  
  
## Syntax  
  
```  
IEnumDebugErrorBreakpoints2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Das Debugmodul \(DE\) implementiert diese Schnittstelle als Teil der Unterstützung für Haltepunkte.  
  
## Hinweise für Aufrufer  
 Visual Studio ruft [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) an, die zum Abrufen dieser Schnittstelle, die eine Liste von Haltepunkten darstellt, die nicht gebunden werden kann, oder [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) , um diese Schnittstelle, die eine Liste von Haltepunkten darstellt, die nicht gebunden wurden.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IEnumDebugErrorBreakpoints2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[Weiter](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)|Ruft eine angegebene Anzahl von Fehlern von Haltepunkten in der Enumerationsfolge ab.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-skip.md)|Überspringt eine angegebene Anzahl von Fehlern von Haltepunkten in der Enumerationsfolge.|  
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-reset.md)|Setzt die Enumerationsfolge auf den Anfang zurück.|  
|[Klonen](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-getcount.md)|Ruft die Anzahl der Fehler von Haltepunkten in einem Enumerator ab.|  
  
## Hinweise  
 Diese Schnittstelle enthält eine Liste von [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)\-Schnittstellen, von denen jede einen Haltepunkt beschreibt, der nicht gebunden werden kann und warum er nicht gebunden werden kann.  Visual Studio verwendet die `IEnumDebugErrorBreakpoint2`\-Schnittstelle, um die Haltepunkte zu aktualisieren, die in der IDE angezeigt werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)