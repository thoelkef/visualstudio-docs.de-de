---
title: "IEnumDebugFields | Microsoft Docs"
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
  - "IEnumDebugFields"
helpviewer_keywords: 
  - "IEnumDebugFields-Schnittstelle"
ms.assetid: 403c2a51-3ba5-431f-a1dd-2f3b2046c00c
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugFields
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt eine Auflistung von Objekten dar, auf die die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Schnittstelle implementieren.  
  
## Syntax  
  
```  
IEnumDebugFields : IUnknown  
```  
  
## Hinweise für Implementierer  
 Diese Schnittstelle wird durch den Anbieter Symbol implementiert, um Sätze Objekte bereitzustellen, die die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Schnittstelle implementieren.  Beachten Sie, dass dies keine Enumeration der Standardwert wegen des Vorhandenseins der COM [GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)\-Methode ist.  
  
## Hinweise für Aufrufer  
 Diese Schnittstelle wird von [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md) und [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)zurückgegeben.  
  
## Methoden in die Vtable\-Reihenfolge  
 Diese Schnittstelle implementiert die folgenden Methoden.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[Weiter](../../../extensibility/debugger/reference/ienumdebugfields-next.md)|Ruft die nächste Gruppe von [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Objekten aus der Enumeration ab.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugfields-skip.md)|Überspringt eine angegebene Anzahl Einträge.|  
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugfields-reset.md)|Setzt die Enumeration auf das erste Eintrag zurück.|  
|[Klonen](../../../extensibility/debugger/reference/ienumdebugfields-clone.md)|Ruft eine Kopie der aktuellen Enumeration ab.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugfields-getcount.md)|Ruft die Anzahl von Einträgen in der Enumeration ab.|  
  
## Hinweise  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Symbol\-Provider\-Schnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)   
 [GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)