---
title: "IEnumDebugAddresses | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugAddresses"
helpviewer_keywords: 
  - "IEnumDebugAddresses-Schnittstelle"
ms.assetid: 5f6f6751-e6d8-4c5a-8e81-414b6e5d8cc5
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IEnumDebugAddresses
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt eine Auflistung von Objekten dar, auf die die [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)\-Schnittstelle implementieren.  
  
## Syntax  
  
```  
IEnumDebugAdresses : IUnknown  
```  
  
## Hinweise für Implementierer  
 Diese Schnittstelle wird durch den Anbieter Symbol implementiert, um Sätze Objekte bereitzustellen, die die [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)\-Schnittstelle implementieren.  Beachten Sie, dass dies keine Enumeration der Standardwert wegen des Vorhandenseins der COM [GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)\-Methode ist.  
  
## Hinweise für Aufrufer  
 Diese Schnittstelle wird von [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md) und [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)zurückgegeben.  
  
## Methoden in die Vtable\-Reihenfolge  
 Diese Schnittstelle implementiert die folgenden Methoden.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[Weiter](../../../extensibility/debugger/reference/ienumdebugaddresses-next.md)|Ruft die nächste Gruppe von [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)\-Objekten aus der Enumeration ab.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugaddresses-skip.md)|Überspringt eine angegebene Anzahl Einträge.|  
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugaddresses-reset.md)|Setzt die Enumeration auf das erste Eintrag zurück.|  
|[Klonen](../../../extensibility/debugger/reference/ienumdebugaddresses-clone.md)|Ruft eine Kopie der aktuellen Enumeration ab.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugaddresses-getcount.md)|Ruft die Anzahl von Einträgen in der Enumeration ab.|  
  
## Hinweise  
 Diese Schnittstelle wird normalerweise durch das Debugmodul verwendet, um die entsprechende Adresse zu bestimmen, die dem Ausdrucksauswertung zu verleihen.  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Symbol\-Provider\-Schnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)   
 [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)