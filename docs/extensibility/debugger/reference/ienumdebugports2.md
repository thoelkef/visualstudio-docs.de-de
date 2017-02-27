---
title: "IEnumDebugPorts2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPorts2"
helpviewer_keywords: 
  - "IEnumDebugPorts2"
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IEnumDebugPorts2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle listet die Anschlüsse des Computers oder des Anschlusslieferanten auf.  
  
## Syntax  
  
```  
IEnumDebugPorts2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Ein benutzerdefinierter Port lieferant implementiert diese Schnittstelle, um eine Liste mit Anschlüssen darzustellen, die vom Lieferanten erstellt werden.  Visual Studio implementiert diese Schnittstelle zur Unterstützung von seinem eigenen Anschlusslieferanten.  
  
## Hinweise für Aufrufer  
 Rufen Sie [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) an, die zum Abrufen dieser Schnittstelle, die eine Liste von Anschlüssen darstellt, die vom Anschlusslieferanten erstellt werden.  Rufen Sie [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) an, die zum Abrufen dieser Schnittstelle, die eine Liste von Anschlüssen darstellt, die auf der Festplatte gespeichert wurden.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IEnumDebugPorts2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[Weiter](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|Ruft eine angegebene Anzahl von Ports in der Enumerationsfolge ab.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|Überspringt eine angegebene Anzahl von Ports in der Enumerationsfolge.|  
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|Setzt die Enumerationsfolge auf den Anfang zurück.|  
|[Klonen](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|Ruft die Anzahl von Ports in einem Enumerator ab.|  
  
## Hinweise  
 Visual Studio verwendet diese Schnittstelle, um eine Liste mit Anschlüssen aufzufüllen, die zum Anfügen an Prozesse verwendet werden.  
  
 Ein Debuggen Modul in der Regel verwendet diese Schnittstelle nicht.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)   
 [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)