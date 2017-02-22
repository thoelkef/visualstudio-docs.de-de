---
title: "IDebugPortSupplier3 | Microsoft Docs"
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
  - "IDebugPortSupplier3"
helpviewer_keywords: 
  - "IDebugPortSupplier3-Schnittstelle"
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortSupplier3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle ermöglicht es dem Aufrufer, um zu bestimmen, ob ein Anschluss lieferant Ports \(indem sie auf einen Datenträger geschrieben\) zwischen den Aufrufen des Debuggers beibehalten und eine Liste dieser beibehaltenen Ports dann abrufen kann.  
  
## Syntax  
  
```  
IDebugPortSupplier3 : IDebugPortSupplier2  
```  
  
## Hinweise für Implementierer  
 Ein benutzerdefinierter Port lieferant implementiert diese Schnittstelle, um das Beibehalten oder Speichern von Anschlussinformationen auf den Datenträger zu unterstützen.  Diese Schnittstelle muss auf dasselbe Objekt wie die [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)\-Schnittstelle implementiert werden.  
  
## Hinweise für Aufrufer  
 Rufen Sie [QueryInterface](/visual-cpp/atl/queryinterface) auf der `IDebugPortSupplier2`\-Schnittstelle an, die zum Abrufen dieser Schnittstelle.  
  
## Methoden in die Vtable\-Reihenfolge  
 Zusätzlich zu den Methoden, die von der [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)\-Schnittstelle geerbt werden, unterstützt diese Schnittstelle Folgendes:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Gibt zurück, ob der Port lieferant Ports \(indem sie auf einen Datenträger geschrieben\) zwischen den Aufrufen des Debuggers beibehalten kann.|  
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Gibt ein Objekt zurück, das verwendet werden kann, um alle Ports auflisten, die von diesem Anschlusslieferanten auf den Datenträger geschrieben wurden.|  
  
## Hinweise  
 Wenn ein Anschluss lieferant Anschlüsse über Aufrufe beibehalten kann, muss er diese Schnittstelle implementieren.  Anschlüsse geladen werden sollen, wenn sich der Port lieferant instanziiert wird und auf einen Datenträger geschrieben, wenn der Port lieferant zerstört wird.  
  
 Ein Debuggen Modul in der Regel interagiert nicht mit einem Anschlusslieferanten. Es wird keine Verwendung für diese Schnittstelle verfügen.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)