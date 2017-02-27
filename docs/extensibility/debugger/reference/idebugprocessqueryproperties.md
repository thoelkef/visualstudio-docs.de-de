---
title: "IDebugProcessQueryProperties | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProcessQueryProperties"
ms.assetid: ce29a248-81a0-42c0-99a7-1606e8c548ec
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugProcessQueryProperties
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle ist eine Erweiterung von [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) Implementierungen \- Schnittstelle implementiert wird.  Er ermöglicht es der Implementierung, um Informationen zu den Debugprozess Umgebungen abzurufen.  
  
## Syntax  
  
```  
IDebugProcessQueryProperties: IUnknown  
```  
  
## Hinweise für Implementierer  
 Implementieren Sie diese Schnittstelle, um Informationen zur Ausführungsumgebung Debuggen eines Prozesses abzurufen.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugProcessQueryProperties`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[QueryProperty](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperty.md)|Abfragen für einen Eigenschaftswert.|  
|[QueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties-queryproperties.md)|Abfragen für Eigenschaftswerte.|  
  
## Hinweise  
 Diese Schnittstelle wird selten implementiert.  
  
## Anforderungen  
 Header: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)