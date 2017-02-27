---
title: "IEnumDebugPortSuppliers2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPortSuppliers2"
helpviewer_keywords: 
  - "IEnumDebugPortSuppliers2"
ms.assetid: cd0a73dc-dd25-46fd-8c4f-5b011501afeb
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IEnumDebugPortSuppliers2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle listet Anschlusslieferanten auf.  
  
## Syntax  
  
```  
IEnumDebugPortSuppliers2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Visual Studio implementiert diese Schnittstelle, um eine Liste von Anschlusslieferanten darzustellen.  
  
## Hinweise für Aufrufer  
 Rufen Sie zum Abrufen [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md) an eine Liste von Anschlusslieferanten.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IEnumDebugPortSuppliers2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[Weiter](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md)|Ruft eine angegebene Anzahl Anschlusslieferanten in der Enumerationsfolge ab.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-skip.md)|Überspringt eine angegebene Anzahl Anschlusslieferanten in der Enumerationsfolge.|  
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-reset.md)|Setzt die Enumerationsfolge auf den Anfang zurück.|  
|[Klonen](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-getcount.md)|Ruft die Anzahl der Anschlusslieferanten in einem Enumerator ab.|  
  
## Hinweise  
 Ein Debuggen Modul im Allgemeinen muss nicht zum Abrufen dieser Schnittstelle.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)