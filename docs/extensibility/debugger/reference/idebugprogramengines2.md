---
title: "IDebugProgramEngines2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramEngines2"
helpviewer_keywords: 
  - "IDebugProgramEngines2-Schnittstelle"
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProgramEngines2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle wird von Knoten Programm verwendet, um alle möglichen Debugmodule \(DE\) anzugeben, der dieses Programm debuggen können.  
  
## Syntax  
  
```  
IDebugProgramEngines2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 DE oder einen benutzerdefinierten Port lieferant implementiert diese Schnittstelle für dasselbe Objekt, das [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) implementiert, um das Einrichten eines bestimmten DE zu unterstützen, die für ein bestimmtes Programm verwendet werden soll.  
  
## Hinweise für Aufrufer  
 Rufen Sie [QueryInterface](/visual-cpp/atl/queryinterface) auf einer `IDebugProgramNode2`\-Schnittstelle an, die zum Abrufen dieser Schnittstelle.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugProgramEngines2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|Gibt alle möglichen DES, das dieses Programm gedebuggt werden kann.|  
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|Wählt DE aus, die für das Debuggen des Programms zu verwenden.|  
  
## Hinweise  
 Sobald DE vom Benutzer ausgewählt wird, ist diese Option mit dem Programm unter dem Knoten registriert, indem [SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)aufruft.  Das ausgewählte Modul wird das Modul, das von [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)zurückgegeben wurde.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)