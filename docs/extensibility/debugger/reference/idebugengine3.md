---
title: "IDebugEngine3 | Microsoft Docs"
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
  - "IDebugEngine3"
helpviewer_keywords: 
  - "IDebugEngine3-Schnittstelle"
ms.assetid: 8bdf4bb7-3b5d-4991-8981-772d4f6bb656
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngine3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Stellt ein einzelnes Modul \(Debug\), die Steuerelemente DE das Debuggen eines oder mehrerer Module dar.  
  
## Syntax  
  
```  
IDebugEngine3 : IDebugEngine2  
```  
  
## Hinweise für Implementierer  
 Diese Schnittstelle wird von benutzerdefinierten DE \(wenn sie Symbole unterstützt\) implementiert, um den JustMyCode\-Zustand zu aktivieren.  Diese Schnittstelle muss von DE implementiert werden, wenn sie Symbole und JustMyCode unterstützt.  
  
## Hinweise für Aufrufer  
 Diese Schnittstelle wird vom Debugbuild Manager der Sitzung \(SDM\) aufgerufen, um Speicherorte für Benutzeroptionen weiterzuleiten, von denen Symbole laden.  Sie wird auch aufgerufen, um die GUID des Moduls festzulegen, wenn sie instanziiert wird \(diese GUID basiert auf die Metrik seit Modul Registration\).  Das SDM ruft außerdem diese Schnittstelle, um den JustMyCode\-Zustand festzulegen und alle Ausnahmen festzulegen, die vom Debugger mit einem angegebenen Zustand bekannt sind.  
  
## Methoden in die Vtable\-Reihenfolge  
 Zusätzlich zu den von [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) geerbten Methoden macht die `IDebugEngine3`\-Schnittstelle die folgenden Methoden verfügbar.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)|Legt den Pfad oder die Pfade fest, die verwendet wird, um DE für Debugsymbole zu suchen.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)|Lädt die Symbole für alle Module, die noch nicht ihre geladenen Symbole aufweisen.|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)|Verweist auf DE über die JustMyCode\-Informationen.|  
|[SetEngineGuid](../../../extensibility/debugger/reference/idebugengine3-setengineguid.md)|Legt DE GUID aus der Metriken fest.|  
|[SetAllExceptions](../../../extensibility/debugger/reference/idebugengine3-setallexceptions.md)|Legen Sie alle Ausnahmen ab, die derzeit einem angegebenen Zustand aus.|  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)