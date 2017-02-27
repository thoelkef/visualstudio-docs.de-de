---
title: "IEnumDebugCustomAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumCustomAttributes"
helpviewer_keywords: 
  - "IEnumDebugCustomAttributes-Schnittstelle"
ms.assetid: 11aa768d-1852-44d6-9de3-17f9bafaded2
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IEnumDebugCustomAttributes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Listet benutzerdefinierte Attribute auf.  
  
## Syntax  
  
```  
IEnumCustomAttributes : IUnknown  
```  
  
## Hinweise für Implementierer  
 Ein Symbol Anbieter implementiert diese Schnittstelle, um benutzerdefinierte Attribute zu unterstützen \(durch die [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)\-Schnittstelle\).  
  
## Hinweise für Aufrufer  
 [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) gibt diese Schnittstelle zurück.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IEnumDebugCustomAttributes`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[Weiter](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)|Ruft eine angegebene Anzahl von benutzerdefinierten Attributen in der Enumerationsfolge ab.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugcustomattributes-skip.md)|Überspringt eine angegebene Anzahl von benutzerdefinierten Attributen in der Enumerationsfolge.|  
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugcustomattributes-reset.md)|Setzt die Enumerationsfolge auf den Anfang zurück.|  
|[Klonen](../../../extensibility/debugger/reference/ienumdebugcustomattributes-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcustomattributes-getcount.md)|Ruft die Anzahl von benutzerdefinierten Attributen in einem Enumerator ab.|  
  
## Anforderungen  
 Header: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Symbol\-Provider\-Schnittstellen](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)   
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)